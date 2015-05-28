# LocationFetch-android
This is the demo application for fetching the current location using the simple-location jar. Easy to use and integrate.

For fine location (GPS location), add the following permission in your AndroidManifest.xml:

<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
For coarse location (network location), add the following permission in your AndroidManifest.xml:

<uses-permission android:name="android.permission.ACCESS_COARSE_LOCATION" />
Retrieve the location from the device

public class MyActivity extends Activity {

    private SimpleLocation location;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);

        // ...

        // construct a new instance of SimpleLocation
        location = new SimpleLocation(this);

        // if we can't access the location yet
        if (!location.hasLocationEnabled()) {
            // ask the user to enable location access
            SimpleLocation.openSettings(this);
        }

        findViewById(R.id.someView).setOnClickListener(new View.OnClickListener() {

            @Override
            public void onClick(View v) {
                final double latitude = location.getLatitude();
                final double longitude = location.getLatitude();

                // TODO
            }

        });
    }

    @Override
    protected void onResume() {
        super.onResume();

        // make the device update its location
        location.beginUpdates();

        // ...
    }

    @Override
    protected void onPause() {
        // stop location updates (saves battery)
        location.endUpdates();

        // ...

        super.onPause();
    }

}
