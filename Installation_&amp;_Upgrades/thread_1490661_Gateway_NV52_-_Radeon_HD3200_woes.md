---
title: "Gateway NV52 - Radeon HD3200 woes"
date: 2010-05-22
forum: Installation &amp; Upgrades
---

### Post by AMiSMonster on 2010-05-22
Hi, all!
  I recently acquired a Gateway with a Radeon video adapter in it. I've tried both the proprietary and open drivers.  I've followed the installation instructions here:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

...to no avail.  I know that my video adapter is compatible with Ubuntu, because I have seen the explode/fade effect on launcher buttons -- until I reboot.  I have even seen all of the screensavers working properly, again, until I reboot.

  Is there a config file not being set up properly?  What terminal commands do I need to post the results of, to provide pertinent diagnostics to the forum?

Thanks, in advance, for your help.

Additionally, this is what Gateway says about the video adapter:

"ATI Radeon® HD 3200 Graphics with up to 1919MB of HyperMemory™ supporting Shader Model 4.0 and Microsoft® DirectX® 10 with AMD RS780MN Chipset"

It uses shared memory.

---

### Post by AMiSMonster on 2010-05-25
I got it going.  I purged the old binary driver and downloaded it again.  Compiz and everything works!  Awesome!  Gonna see if I can get Half-Life 2 working on Wine tomorrow!

---

### Post by Yehudah on 2010-05-28
> **AMiSMonster said:**
> I got it going.  I purged the old binary driver and downloaded it again.  Compiz and everything works!  Awesome!  Gonna see if I can get Half-Life 2 working on Wine tomorrow!

Can you tell me how you did that?  I'm having the same problem with the same video on a Dell laptop.

Thanks

---

### Post by AMiSMonster on 2010-05-28
> Can you tell me how you did that?  I'm having the same problem with the same video on a Dell laptop.  I got carried away with compiz, and it seemed to have conflicted with some of the Ubuntu stuff, like the astronomy backgrounds that change regularly.  I tried to install Wine, and it locked up when something was doing something with something else getting all weird, and I'm still new at this, so don't ask me. :confused:
   I'm trying to get it up again, and I'm not quite sure what worked.   The trick might be to purge the crap out of everything so it re-downloads.
   I'll get back and let you know.
   I had problems with the upgrade, so I went back to 9.10, which seems more stable on my system.

---

### Post by AMiSMonster on 2010-05-29
Ok, this is the typically noobish overkill, but it works:

First go to the Ubuntu Software Center
Search for "ATI"
Uninstall all the ATI stuff that comes up
I couldn't uninstall jockey-gtk drivers just yet, but be patient
Select "Software Sources" under "Edit" on the menu bar
Click the "Other Software" tab
Make sure the two URLs are checked
Close the Software Sources dialog
Reboot
Open the terminal
Enter and execute each of these four in turn:
```
  sudo apt-get remove --purge xorg-driver-fglrx
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri
  sudo dpkg-reconfigure xserver-xorg
  sudo apt-get install --reinstall xserver-xorg-core

```Reboot
Enter and execute each of these in turn:
```
 sudo /usr/share/ati/fglrx-uninstall.sh  # (if it exists)
  sudo apt-get remove --purge fglrx*
  sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
  sudo apt-get install xserver-xorg-video-ati
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
  sudo dpkg-reconfigure xserver-xorg
```Reboot
Go to the Ubuntu Software Center
Search for "ATI"
Uninstall the jockey-gtk driver
Again: 
Enter and execute each of these four in turn:
```
   sudo apt-get remove --purge xorg-driver-fglrx
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri
  sudo dpkg-reconfigure xserver-xorg
  sudo apt-get install --reinstall xserver-xorg-core

```Reboot
Enter and execute each of these in turn:
```
   sudo /usr/share/ati/fglrx-uninstall.sh  # (if it exists)
  sudo apt-get remove --purge fglrx*
  sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
  sudo apt-get install xserver-xorg-video-ati
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
  sudo dpkg-reconfigure xserver-xorg 
```Reboot
Go to the Ubuntu Software Center
 Search for "ATI"
Install the jockey-gtk driver
Install the ATI binary X.org driver
Catalyst should install by itself with one of these two
Reboot
Go to the "Hardware Drivers" utility in "Administration" (under "System" )
It will search for drivers, then a window will (finally) appear
Click on your driver, one-third of the way down the window. (in the wide, short box)
Click the "Activate" button 
A blue arrow will appear next to a message telling you to reboot
Close the window
Reboot

You can see if it worked by fiddling with the screen savers

Let me know how it works out!

---

### Post by darkod on 2010-05-29
I don't know if it helps, but I have desktop mobo with integrated HD3200 and in fact 9.10 wasn't working by default until I added new driver with EnvyNG.

But in 10.04 this was sorted out, 10.04 worked 'out of the box' for me. No need to fiddle around with the drivers.

---

### Post by AMiSMonster on 2010-05-29
Ubuntu has issues with the wireless on the NV52, and it seems worse with the upgrade. I read somewhere that this is a kernel issue. I used this to minimize the problem: [http://ubuntuforums.org/showthread.php?t=1374910](http://ubuntuforums.org/showthread.php?t=1374910)  
9.10 seems to just "flow" better on my machine.

---

### Post by Yehudah on 2010-05-30
So my problem isn't with Compiz.  I wish it were.

My problem is this:  I tried to update the ATI HD 3200 driver from ATI's site.  I downloaded it, and ran the update in the terminal window, got the Control Center GUI and thought I was golden.

I set the graphics to high, but did not download Compiz.

When I reboot, it tells me that it has to load in low graphics mode.  So I do.  And I have to start all over again.

I'm getting a little frustrated with this.  I hate to invoke the W word, but 7 didn't have a problem with my ATI chipset.

So I'm stumped.

I'm not a newby, but I'm not quite a novice.  If someone could lay it out for me logically, I'll happily give just about anything a shot.

---

### Post by AMiSMonster on 2010-05-30
I tried to download it directly from the site, but that just didn't work for me.  I've heard that that puts a watermark on your screen anyways.  My guess is that the driver that comes with ubuntu is just flaky and you just have to get rid of it altogether and re-acquire it.  ( see above )
I couldn't get Halflife 2 up yet, but Halflife 1 runs better through Wine than it ever did on windows!  I though it was just a glitchy game, but it turns out that windows is inferior after all.

edit: Yehudah, try deactivating, rebooting and reactivating.

---

### Post by darkod on 2010-05-31
Are all of you guys talking about 10.04? On my desktop with integrated HD3200 it works out of the box. Not even a single tweak needed for graphics to work at full resolution.

---

### Post by Yehudah on 2010-05-31
> **AMiSMonster said:**
> I tried to download it directly from the site, but that just didn't work for me.  I've heard that that puts a watermark on your screen anyways.  My guess is that the driver that comes with ubuntu is just flaky and you just have to get rid of it altogether and re-acquire it.  ( see above )
I couldn't get Halflife 2 up yet, but Halflife 1 runs better through Wine than it ever did on windows!  I though it was just a glitchy game, but it turns out that windows is inferior after all.

edit: Yehudah, try deactivating, rebooting and reactivating.

Done that already, now I get an error and it won't reactivate.  How do I wipe out the old/new drivers, and reinstall new ones to activate?

I thought I had done that, ...guess not.

---

### Post by darkod on 2010-05-31
> **Yehudah said:**
> Done that already, now I get an error and it won't reactivate.  How do I wipe out the old/new drivers, and reinstall new ones to activate?

I thought I had done that, ...guess not.

Depending how you installed it, there might be uninstall script in the folder where the driver was unpacked.

And are you using 10.04 and is it a clean install or upgrade from earlier version?

---

### Post by Yehudah on 2010-05-31
> **darkod said:**
> Depending how you installed it, there might be uninstall script in the folder where the driver was unpacked.

And are you using 10.04 and is it a clean install or upgrade from earlier version?

I'm using a clean install.

I have tried every variant of 2010 ATI HD 3200 driver.  I've tried reloading the driver that came with the image.

What I'd like to do is remove all ATI video gunk, default the video, and start over.

Is there a way I can do that?

---

### Post by darkod on 2010-05-31
> **Yehudah said:**
> I'm using a clean install.

I have tried every variant of 2010 ATI HD 3200 driver.  I've tried reloading the driver that came with the image.

What I'd like to do is remove all ATI video gunk, default the video, and start over.

Is there a way I can do that?

Did you check the folder where the driver got unpacked? Usually the file extracts into a folder with a similar name. Inside his folder sometimes there is uninstall script which can be called literary uninstall.sh or similar.

I am also running clean install of 10.04 64bit on my desktop with integrated HD3200 and it worked right from the start. No need to add any driver, ATI or other. That's why I am surprised you need to do all this.

---

### Post by Yehudah on 2010-05-31
> **darkod said:**
> Did you check the folder where the driver got unpacked? Usually the file extracts into a folder with a similar name. Inside his folder sometimes there is uninstall script which can be called literary uninstall.sh or similar.

I am also running clean install of 10.04 64bit on my desktop with integrated HD3200 and it worked right from the start. No need to add any driver, ATI or other. That's why I am surprised you need to do all this.

There is an fglrx uninstall script in the usr/share/ati folder.  Could that be the one?

---

### Post by Yehudah on 2010-05-31
This is what I get when I run that uninstall script:

[B]yehudah@yehudah-laptop:/usr/share/ati$ sudo sh ./fglrx-uninstall.sh

[Warning] Uninstall : inst_path_default or inst_path_override
 does not exist in /etc/ati.  This suggests that the ATI driver
 is not installed, the ATI driver is only partially installed,
 or the current ATI driver installed is an older version than the
 one this script was designed for.  Both files listed above are
 required for determining where installed files are located.
 To force uninstallation of the driver by guessing where the
 uninstallation files are located, set the FORCE_ATI_UNINSTALL
 environment variable and re-run ./fglrx-uninstall.sh (this is not recommended).[/B]

I think if I can uninstall the driver, and the associated files and start over, I can get this fixed.

Am I on the right track?

---

### Post by darkod on 2010-05-31
> **Yehudah said:**
> There is an fglrx uninstall script in the usr/share/ati folder.  Could that be the one?

I can't be sure, sorry.

You might visit again the ATI webpage where you got the driver and there should be instructions there for uninstall too. Or in a README file in the driver folder. In linux the readme files have more information about install and uninstall, it's not like in windows.

---

### Post by Yehudah on 2010-05-31
> **darkod said:**
> I can't be sure, sorry.

You might visit again the ATI webpage where you got the driver and there should be instructions there for uninstall too. Or in a README file in the driver folder. In linux the readme files have more information about install and uninstall, it's not like in windows.

I did exactly that.  I went to the AMD site and d/l'd the instructions on uninstallation.  I did what it said, uninstall, then copy the highest version of config file into the current one and reboot.

When I am back up, and try to activate the driver, I get this:
SystemError: installArchives() failed

fail.

---

### Post by Yehudah on 2010-06-06
Any insight, anyone?

---

### Post by AMiSMonster on 2010-06-06
Have you tried Synaptic?

---

### Post by AMiSMonster on 2010-06-06
I know, double reply, but it wouldn't let me attach to an edit.
I don't know if this helps, but this is a screenshot of my synaptic after searching for ATI. It's also ordered by what's installed.

---

