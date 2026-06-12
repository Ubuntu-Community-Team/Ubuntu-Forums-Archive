---
title: "Upgrade issue - from 9.10 to 10.04 LTS"
date: 2010-07-30
forum: Installation &amp; Upgrades
---

### Post by Wins2LinX on 2010-07-30
I have installed Ubuntu 9.10 GNOME as a Linux partition on my hp "Compaq nc6400" laptop.
The default OS is Win XP SP3.

The current Ubuntu version is working fine. but the system is not able to upgrade to the latest 10.04 LTS version from 9.10 to 10.04 LTS.

I am not much familiar with Linux, so I request you to provide a detail step-by-step method approach. Thanks in advance.

The Issue - 
I go to "System > Administration > Update Manager .
The update manager opens with the new upgrade 10.04 (Lucid Linux) now available for upgrade. I initiate the upgrade process.
It opens a small window "Distribute upgrade" and continues to do the "preparation for upgrade, Setting new software channels (at this time a pop-up box shows as "Third party sources disabled" and follows "Support for some applications ended" screen.
the Next "Do you want to start the upgrade?" screen pops-up with number of packages to be removed and new packages will be installed.  Once "Start Upgrade" is confirmed, System moves to "Getting new packages" and "Could not download the upgrades" screen and fails.
Error detail - 
Failed to fetch [http://astromirror.uchicago.edu/ubuntu/pool/universe/g/gst-plugins-bad0.10/gstreamer0.10-sdl_0.10.18-1ubuntu1_i386.deb](http://astromirror.uchicago.edu/ubuntu/pool/universe/g/gst-plugins-bad0.10/gstreamer0.10-sdl_0.10.18-1ubuntu1_i386.deb) 404  Not Found
Failed to fetch [http://astromirror.uchicago.edu/ubuntu/pool/universe/g/gst-plugins-ugly0.10/gstreamer0.10-plugins-ugly_0.10.14-1_i386.deb](http://astromirror.uchicago.edu/ubuntu/pool/universe/g/gst-plugins-ugly0.10/gstreamer0.10-plugins-ugly_0.10.14-1_i386.deb) 404  Not Found
Failed to fetch [http://astromirror.uchicago.edu/ubuntu/pool/universe/g/gst-plugins-bad0.10/gstreamer0.10-plugins-bad_0.10.18-1ubuntu1_i386.deb](http://astromirror.uchicago.edu/ubuntu/pool/universe/g/gst-plugins-bad0.10/gstreamer0.10-plugins-bad_0.10.18-1ubuntu1_i386.deb) 404  Not Found
Failed to fetch [http://astromirror.uchicago.edu/ubuntu/pool/universe/d/dirac/libdirac-encoder0_1.0.2-2_i386.deb](http://astromirror.uchicago.edu/ubuntu/pool/universe/d/dirac/libdirac-encoder0_1.0.2-2_i386.deb) 404  Not Found
Failed to fetch [http://astromirror.uchicago.edu/ubuntu/pool/universe/s/seed/libseed0_2.28.1-1_i386.deb](http://astromirror.uchicago.edu/ubuntu/pool/universe/s/seed/libseed0_2.28.1-1_i386.deb) 404  Not Found
Failed to fetch [http://astromirror.uchicago.edu/ubuntu/pool/universe/s/seed/seed_2.28.1-1_i386.deb](http://astromirror.uchicago.edu/ubuntu/pool/universe/s/seed/seed_2.28.1-1_i386.deb) 404  Not Found
Failed to fetch [http://astromirror.uchicago.edu/ubuntu/pool/universe/c/clutter-gtk-0.10/gir1.0-clutter-gtk-0.10_0.10.4-0ubuntu1_i386.deb](http://astromirror.uchicago.edu/ubuntu/pool/universe/c/clutter-gtk-0.10/gir1.0-clutter-gtk-0.10_0.10.4-0ubuntu1_i386.deb) 404  Not Found
Failed to fetch [http://astromirror.uchicago.edu/ubuntu/pool/universe/s/slib/slib_3b1-3ubuntu1_all.deb](http://astromirror.uchicago.edu/ubuntu/pool/universe/s/slib/slib_3b1-3ubuntu1_all.deb) 404  Not Found
Failed to fetch [http://astromirror.uchicago.edu/ubuntu/pool/universe/a/adblock-plus/adblock-plus_1.1.3-1build1_all.deb](http://astromirror.uchicago.edu/ubuntu/pool/universe/a/adblock-plus/adblock-plus_1.1.3-1build1_all.deb) 404  Not Found
Failed to fetch [http://astromirror.uchicago.edu/ubuntu/pool/universe/a/adblock-plus/xul-ext-adblock-plus_1.1.3-1build1_all.deb](http://astromirror.uchicago.edu/ubuntu/pool/universe/a/adblock-plus/xul-ext-adblock-plus_1.1.3-1build1_all.deb) 404  Not Found
Failed to fetch [http://astromirror.uchicago.edu/ubuntu/pool/universe/s/snack/libsnack2-alsa_2.2.10-dfsg1-9_i386.deb](http://astromirror.uchicago.edu/ubuntu/pool/universe/s/snack/libsnack2-alsa_2.2.10-dfsg1-9_i386.deb) 404  Not Found
Failed to fetch [http://astromirror.uchicago.edu/ubuntu/pool/universe/s/svgalib/libsvga1_1.4.3-29_i386.deb](http://astromirror.uchicago.edu/ubuntu/pool/universe/s/svgalib/libsvga1_1.4.3-29_i386.deb) 404  Not Found
Failed to fetch [http://astromirror.uchicago.edu/ubuntu/pool/universe/x/x264/libx264-85_0.85.1448+git1a6d32-4_i386.deb](http://astromirror.uchicago.edu/ubuntu/pool/universe/x/x264/libx264-85_0.85.1448+git1a6d32-4_i386.deb) 404  Not Found
Failed to fetch [http://astromirror.uchicago.edu/ubuntu/pool/universe/x/xvidcore/libxvidcore4_1.2.2+debian-0ubuntu2_i386.deb](http://astromirror.uchicago.edu/ubuntu/pool/universe/x/xvidcore/libxvidcore4_1.2.2+debian-0ubuntu2_i386.deb) 404  Not Found
Failed to fetch [http://astromirror.uchicago.edu/ubuntu/pool/universe/g/gstreamer0.10-ffmpeg/gstreamer0.10-ffmpeg_0.10.10-1_i386.deb](http://astromirror.uchicago.edu/ubuntu/pool/universe/g/gstreamer0.10-ffmpeg/gstreamer0.10-ffmpeg_0.10.10-1_i386.deb) 404  Not Found
Failed to fetch [http://astromirror.uchicago.edu/ubuntu/pool/universe/g/gst-fluendo-mp3/gstreamer0.10-fluendo-mp3_0.10.12.debian-2_i386.deb](http://astromirror.uchicago.edu/ubuntu/pool/universe/g/gst-fluendo-mp3/gstreamer0.10-fluendo-mp3_0.10.12.debian-2_i386.deb) 404  Not Found
Failed to fetch [http://astromirror.uchicago.edu/ubuntu/pool/universe/t/tracker/libtrackerclient0_0.6.95-1ubuntu6_i386.deb](http://astromirror.uchicago.edu/ubuntu/pool/universe/t/tracker/libtrackerclient0_0.6.95-1ubuntu6_i386.deb) 404  Not Found
Failed to fetch [http://astromirror.uchicago.edu/ubuntu/pool/universe/u/usplash/libusplash0_0.5.51_i386.deb](http://astromirror.uchicago.edu/ubuntu/pool/universe/u/usplash/libusplash0_0.5.51_i386.deb) 404  Not Found
Failed to fetch [http://astromirror.uchicago.edu/ubuntu/pool/universe/s/sexy-python/python-sexy_0.1.9-1ubuntu3_i386.deb](http://astromirror.uchicago.edu/ubuntu/pool/universe/s/sexy-python/python-sexy_0.1.9-1ubuntu3_i386.deb) 404  Not Found
Failed to fetch [http://astromirror.uchicago.edu/ubuntu/pool/universe/u/ureadahead/sreadahead_0.100.0-4.1_i386.deb](http://astromirror.uchicago.edu/ubuntu/pool/universe/u/ureadahead/sreadahead_0.100.0-4.1_i386.deb) 404  Not Found
Failed to fetch [http://astromirror.uchicago.edu/ubuntu/pool/universe/x/xsplash/ubuntu-xsplash-artwork_0.8.5-0ubuntu2_i386.deb](http://astromirror.uchicago.edu/ubuntu/pool/universe/x/xsplash/ubuntu-xsplash-artwork_0.8.5-0ubuntu2_i386.deb) 404  Not Found
Failed to fetch [http://astromirror.uchicago.edu/ubuntu/pool/universe/x/xsane/xsane_0.996-2ubuntu3_i386.deb](http://astromirror.uchicago.edu/ubuntu/pool/universe/x/xsane/xsane_0.996-2ubuntu3_i386.deb) 404  Not Found
Failed to fetch [http://astromirror.uchicago.edu/ubuntu/pool/universe/x/xsane/xsane-common_0.996-2ubuntu3_all.deb](http://astromirror.uchicago.edu/ubuntu/pool/universe/x/xsane/xsane-common_0.996-2ubuntu3_all.deb) 404  Not Found
Failed to fetch [http://astromirror.uchicago.edu/ubuntu/pool/universe/x/xsplash/xsplash_0.8.5-0ubuntu2_i386.deb](http://astromirror.uchicago.edu/ubuntu/pool/universe/x/xsplash/xsplash_0.8.5-0ubuntu2_i386.deb) 404  Not Found

After this error, the only option available is "Close" and the upgrade does not take place.

Please help me.

Thanks
Wins2Linx

---

### Post by sikander3786 on 2010-07-30
Did you try another mirror?

---

### Post by QIII on 2010-07-30
Try "Main" or "US" mirror, since it appears you are in the US.

---

### Post by Wins2LinX on 2010-08-24
Sorry, I am new. How do I change to 'Main' or other mirror?

I am relatively Windows person. Learning Ubuntu lately. So can you please help me with the detail steps.

Thanks.

---

### Post by dai_bach on 2010-08-24
Go to System > Administration > Software Sources then in the Ubuntu Software tab choose your server from the "Download from:" list (drop down menu).  The obvious choices for you should be Main or US on this list.

Good luck and enjoy Ubuntu!

---

### Post by jeddycakes on 2010-08-24
Or....just take the plunge and purge Windoze from your life all together. 

You'll find yourself more actively fixing problems like this and succeeding, rather than falling back into nice comfortable dirty Windoze.

Do it. You know you want to....

---

### Post by Wins2LinX on 2010-08-24
Your steps are precise, Thanks dai_bach =D>. 

Now I have upgraded to new 10.04LTS .

Looking forward for some more research, Learning and adventure in Ubuntu world.

Case closed

Thanks again..

---

