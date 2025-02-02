<script>
  // Center on the North Atlantic Ocean (between Portugal & New Jersey)
  export let lat = 35.0;
  export let lng = -40.0;

  // Set default zoom levels for desktop & mobile
  let zoom = window.innerWidth < 500 ? 1 : 3; // Mobile: 3, Desktop: 5

  // Function to generate the Google Maps embed URL dynamically
  function getMapSrc() {
    return `https://www.google.com/maps/d/u/1/embed?mid=1JF68XL8SQtNMF6ReUj68CcDAu1n3Vi8&ehbc=2E312F&z=${zoom}&ll=${lat},${lng}`;
  }

  // Initialize src
  export let src = getMapSrc();

  // Dynamically update zoom when resizing
  function updateZoom() {
    zoom = window.innerWidth < 500 ? 1 : 3;
    src = getMapSrc();
  }

  // Listen for window resize events
  window.addEventListener('resize', updateZoom);

  export let width = "100%";
  export let height = "450px";
  export let style = "border:0;";
  export let loading = "lazy";
  export let referrerpolicy = "no-referrer-when-downgrade";
</script>

<style>
  .map-container {
    position: relative;
    width: 100%;
    height: 0;
    padding-bottom: 75%; /* 4:3 aspect ratio for desktop */
  }

  .map-container iframe {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    border: none;
  }

  @media (max-width: 768px) {
    .map-container {
      padding-bottom: 190%; /* Taller for mobile */
    }
  }
</style>

<div class="map-container">
  <iframe
    src={src}
    width={width}
    height={height}
    style={style}
    allowfullscreen="true"
    loading={loading}
    referrerpolicy={referrerpolicy}>
  </iframe>
</div>
