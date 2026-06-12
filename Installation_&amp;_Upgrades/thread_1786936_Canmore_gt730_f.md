---
title: "Canmore gt730 f"
date: 2011-06-20
forum: Installation &amp; Upgrades
---

### Post by closbar on 2011-06-20
hey please I need to know how to install this gps receiver please I'm not very expert if someone can provide me very clear details of how to do it, will very apreciated Thanks

---

### Post by Herman on 2011-06-20
The simplest way to get started is to just install FoxtrotGPS  if you have the current release of Ubuntu, (code named 'Natty Narwhal'). 
Foxtrot GPS is called 'TangoGPS' in earlier versions.

Then just go outside or somewhere where the GPS receiver will have a good sky view and wait a few minutes with your GPS plugged in and Foxtrot GPS running.

In Unity in Natty Narwhal you can find Foxtrot GPS instantly by pressing your Ubuntu key on your keyboard or the Ubuntu button in the top right-hand corner of your display and typing the first two or three letters of the program you want, 'fox'... and the icons for any programs you have installed that start with 'fox' should be displayed, then just click on 'Foxtrot GPS'.
In older versions of Ubuntu, just go 'Applications', 'Accessories', 'TangoGPS'.

Full-screen it and click on the i (i for information button) and shortly if you have a good sky view you will start seeing valid GPS data starting to appear in the info sidebar and Foxtrot GPS should zoom in on your location.

If you click on the arrow buttons at the top of the sidebar again and switch to 'Tracks', you can enable and disable track logging or 'split' (stop a log and start a new one).
Track logs in case you don't already know are plain text files with lists of your coordinates taken every second or less which are very useful for recording your journeys in and to keep and use for later processing.

You can also re-load old track logs in Foxtrot GPS with the 'Load' button to see where you went, but track logs can be processed to make then appear in other programs like Google Earth and Quantum GIS, (professional map making software which can be installed in Ubuntu).

At first, Foxtrot GPS doesn't come with a lot of map data I guess to keep down the size of the download, you can see your position in a world OSm type map initially.
Switch the side bar to 'configuration' by clicking the arrows at the top and you should see a 'map types' button. 
You can choose 'OSM', Maps-for-free, 'Opencyclemap', Google Maps or 'Googe Sat'.
I like 'Google Sat' personally, but they're all good. To use 'Google Sat' maps or whatever kind you want for your specific area you need to connect to the internet and pan around at various zoom level using your keyboard or mouse. Make sure 'Auto download map tiles' is enabled, for Foxtrot GPS to save map tiles to your hard drive. The map tiles will get stored in your maps folder. Try to spend some time zooming and panning around to build up a good collection and you will be able to use them later when you're away from any internet connection. 
Once you have some map tiles collected, it's a good idea to include your Maps folder in future backups to save yourself having to spend time repeating the process.

More information on getting started with USB GPS in the following linked thread: [URL="http://ubuntuforums.org/showthread.php?t=1430516"]**usb gps on ubuntu. how to, maybe...**
[/URL] 
I haven't tried your specific make and model of USB GPS but if it's much the same as other USB GPS receivers it should just plug in and work.

If you have problems getting your gps working with Foxtrot at first you can install the command - line GPS tools gpsd and gpsd-clients, then when you type 'xgps' in a terminal you will see a command-line satellite viewer and you can test if that can 'see' satellites or not. If you can then wait longer or look for problems with Foxtrot GPS, if you cannot 'see' satellites in xgps then wait longer, go somewhere with a better sky view or think about what could be wrong with your GPS connection, (plug loose, extension cable too long, something unusual about your make and model of GPS reciever requiring special steps to get working in Ubuntu (rare but could happen), etc.).

---

