---
title: "Upgrade to Karmic beta won't boot"
date: 2009-10-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by strangeluck on 2009-10-13
I just attempted to upgrade my laptop (a Lenovo Thinkpad SL300) from jaunty to the karmic beta using update-manager. It seemed to go fine, but after all the packages were finished installing and I rebooted, Ubuntu won't start. What happens is that I get the splash screen of the white Ubuntu logo for a while, and then the screen goes black and nothing happens. I let it run for a half hour, but ultimately had to use ctrl-alt-delete to reboot. I'm able to boot to a command line using recovery mode and used aptitude to make sure everything is installed correctly. I'd like to be able to see the boot process as it loads, so I can see where it's getting stuck, but I don't know how to disable the splash screen.

---

### Post by marshmallow1304 on 2009-10-13
You can use Ctrl+Alt+F1 to see what's going on.

Also, you may want to run fsck in recovery mode.

---

### Post by cholericfun on 2009-10-13
are you sure your system isnt booting,
the "black screen of death" usually has to do with display not working correctly

---

### Post by strangeluck on 2009-10-13
Ctrl-alt-f1 just gives me the same black screen. As far as the display not working, I'm not really sure how to check that, but I don't think that's the problem since the splash image displays.

---

### Post by TenPlus1 on 2009-10-13
Press ESC during boot menu, select recovery mode, when logged in at prompt run FSCK and answer yes to repair then type REBOOT to restart and it should work fine...

---

### Post by strangeluck on 2009-10-13
So I decided to check whether it was just a display problem by erasing my xorg.conf file, and it booted right up! Thanks a lot.

---

### Post by cholericfun on 2009-10-14
i'd love if someone explain to me how removing xorg.conf would fix the screen problem (not an expert myself evidently...)

glad it worked. i've seen this before and was wildly confused how the load-up screen was displayed but the desktop is blank.

---

### Post by philinux on 2009-10-14
> **cholericfun said:**
> i'd love if someone explain to me how removing xorg.conf would fix the screen problem (not an expert myself evidently...)

glad it worked. i've seen this before and was wildly confused how the load-up screen was displayed but the desktop is blank.

Since it was an upgrade the old xorg.conf was still in place. Normally now it is not needed except for special settings like twinview etc. There must have been settings in there that conflicted with the new system.

My clean install generated one as I use the nvidia driver.

---

### Post by ranch hand on 2009-10-14
Your xorg stuff is not up yet when you see the first screen.

As to why removing the bugger works - beats tarnation out of me.

I assume you have an ATI video card (I do).

---

### Post by philinux on 2009-10-14
Hi Ranch,

Cant remember off hand but when does xorg kick in?

---

### Post by ranch hand on 2009-10-14
I think that it starts when GDM starts so that you can have the choices you have at login (Gnome, Xterm, etc).

I may be full of it too.

---

### Post by cholericfun on 2009-10-14
ah, thats why i sometimes get this error message window saying that GDM didnt load yet i dont see a difference. (i guess)

thanks for the explanations

---

### Post by VMC on 2009-10-14
> **strangeluck said:**
> So I decided to check whether it was just a display problem by erasing my xorg.conf file, and it booted right up! Thanks a lot.

How did it get in there in the first place? Did you create it, and if so were you changing any values?

Maybe it was leftover from the jaunty upgrade.

---

### Post by Longinus00 on 2009-10-14
> **VMC said:**
> How did it get in there in the first place? Did you create it, and if so were you changing any values?

Maybe it was leftover from the jaunty upgrade.

I believe jaunty created a xorg.conf by default, even if it was very empty.

---

### Post by fezzik1620 on 2009-10-15
Hi all,
I was having this same problem and am happy to report that this solution worked for me as well.  I have attached a copy of my xorg.conf file that was causing problems.  I also upgraded to Karmic from Jaunty.  My xorg.conf file was so configured because I was using the nvidia proprietary driver and using twinview and wanted to specify my refresh rates on a couple of older 19" CRT monitors.

Thanks!

---

### Post by sdunlapa on 2009-10-24
Removing my xorg file out of the way worked for me as well

---

### Post by fezzik1620 on 2009-10-26
There's more to my story.

After removing the xorg.conf file I was able to get X to boot, but at a very low resolution.  I found that the nVidia driver (185) that I had been using with Jaunty was disabled.  I re-enabled it and restarted and once again got my black screen when X tried to load.  I restarted in recovery mode, deleted xorg.conf again, and was able to get it to start.

So, the problem seems to be an issue with the nVidia restricted driver and Karmic.  I did some searching around and came across [this post]("http://ubuntuforums.org/showthread.php?t=1288302").  In [reply #4]("http://ubuntuforums.org/showpost.php?p=8101758&postcount=4") Mils mentions that he got the nVidia drivers to work with the command:
> dpkg-reconfigure nvidia-185-kernel-source
He doesn't mention where this information came from (and I'm not as Linux savvy as I used to be), but according to another post it appears that this rebuilds the module for the driver.

I did that and it worked.  Not only was I successfully able to start X with the nVidia restricted drivers, but I was also able to restore my previous xorg.conf file and use it with all my settings from Jaunty.

Hope this helps.

---

