---
title: "screwed up my ubuntu system reinstall"
date: 2011-12-19
forum: Installation &amp; Upgrades
---

### Post by dgoddard on 2011-12-19
I did a clean reinstall of ubuntu moving up to 10.4 (I wanted the gnu interface not the one that comes with 11.10.)

I got some vague message about wifi that I could not make sense of during the install.

I did a reinstallation of my data files, preference, bookmarks, etc.etc.etc. and have been getting everything working just right using the laptop at home very successfully for a couple of weeks now.

Today I took it to the public library and tested the wi-fi.
 !!!!! NO WIFI  !!!!!!

I think what happened is that I had the hardware switch that shuts off wi-fi in the off positon during the install and the install could probably not find any wifi on the computer, and did not set it up.

---------- question ----------
How can I get the wifi up and running **_WITHOUT_** redoing all the install work I have already done.  
------------------------------
I only use wi-fi on this machine when I am traveling but I do need it then.

Hardware:
Dell Studio 1535 laptop.

---

### Post by yndesai on 2011-12-20
Try with the liveCD and check if wifi is working . . (keep the wifi switch on while booting from liveCD)

As far as I understand linux does not "installs" hardware drivers while initial installation
the complete kernel with all the supported hardware is installed (which is upto 36MB)
and it detects the hardware when you startup. So it must not matter if you did not turned the hardware ON while installation.

As you suggested there was some vague message regarding wifi check if the same appears 
while booting from the liveCD.

---

### Post by dgoddard on 2011-12-21
[QUOTE="yndesai"]Try with the liveCD and check if wifi is working[/QUOTE]
OK, that was a good suggestion.  After the boot up from the live CD the message that popped up  was about the need for a wireless driver and the availability of a driver called Broadcom B43.

I told it to go ahead and install that and it did.  It took about 4 minutes to finish the task.   But I am at home and have no wifi around me anywhere. so I cannot test it.

When I rebooted from the hard drive "Up/Down load icon menu said" 
> Wireless Networks
Device not Ready

I had been seeing the message
> Wireless Networks
disconnected.

I would assume that an install while running on the Live CD would not install the driver to my system on the hard drive.  So if I had to install it again I would have to find a wired ethernet connection, I have no idea where I would find one since everything is WiFi whereever I go  But unless I can get the driver installed I can't use wifi.

What would be the next thing to try.???

---

### Post by yndesai on 2012-01-03
If your laptop can get on the INTERNET it would be easy to install the driver using synaptic or apt-get. Since you cannot seem to get the internet on your laptop without the wifi you will have to do the installation over again.
:(

But now you know that the driver for the wifi is there on the liveCD and that it will get install if you give attention to the messages during installation phase.:)

---

