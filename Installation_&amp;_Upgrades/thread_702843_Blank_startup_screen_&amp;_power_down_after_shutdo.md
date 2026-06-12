---
title: "Blank startup screen &amp; power down after shutdown problem"
date: 2008-02-20
forum: Installation &amp; Upgrades
---

### Post by doclord on 2008-02-20
After many years of absence I have finally returned to UNIX, namely Ubuntu 7.1.  As you can imagine I am somewhat rusty, but luckily it all seems to be coming back to me!  I am using a dual boot (Win2000) IBM T22 laptop with only 256 MB RAM and a 20 GB harddisk.  What is really great is that this ancient and previously unused machine is now having a new lease of life!  Saying that I do have a few teething installation issues and would really appreciate some help...
I initially experienced what appears to be a common blank screen on start-up problem.  When I chose Ubuntu 7.1 in the Grub bootloader, everything went OK until the status bar reached full and then the system just stopped on a totally blank black screen.  Shutdown was OK though.  The graphics card I have is an S3 Savage / IX 1014.  Ubuntu seemed to have detected the appropriate driver (namely "S3 Inc. 86C270-294 Savage/IX-MV"), but after reading up I edited the /etc/X11/xorg.conf file and changed the 'Section "Device"' to have 'Driver "vesa"', rather than 'Driver "savage"'.  Startup is now perfect, but power down after shutdown no longer works properly (another commonly reported problem, a while back).  Now, when I attempt to preform a Shut Down, Restart, Suspend, Switch User, etc. the screen goes blank, but it is still lit up.  The only way I have found to switch the laptop off completely is to hold down the power-on button for a few seconds.  I get a similar problem if I start the "Screen and Graphics Preferences" admin utility and try to perform a Screen 1 Test function.  I have tried adding "apm power_off=1" to /etc/modules, but this made no difference.  In addition, I tried passing "acpi=force" and "lapic" to the standard kernel as arguments (via editing  /boot/grub/menu.lst, running 'sudo update-grub', and rebooting), but this also made no difference.  Please help??

---

### Post by phrawzty on 2008-02-21
Hello,

I had a similar (the same?) problem on a fresh Ubuntu install not three days ago.  It had to do with Usplash attempting to use an incompatible resolution, as described in [bug 150930]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/150930").

The solution was to boot into text mode, then edit the usplash configuration.  It will look something like this :
```
$ cat /etc/usplash.conf 
# Usplash configuration file
xres=1024
yres=768
```

Just change the X and Y to a resolution that your display supports.  As always, starting at something easy like 800x600 is a safe bet. :)

---

### Post by doclord on 2008-02-21
Thanks phrawzty,
I will give it a go now...

---

### Post by plucky on 2008-02-21
doclord,


If the usplash thing doesn't work,I have found that adding ```
acpi=off apm=on
``` to the end of the kernel line should work.

Good luck.

P.s. You might also have to add it the ```
# defoptions=splash
``` in the **menu.lst** file so that it stays after a kernel upgrade if it works.

---

### Post by doclord on 2008-02-21
Tried the Usplash configuration file resolution change but, unfortunately, it made no difference.  The resolution in the file was 1024x768, but so was the resolution of the default screen in the "Screen and Graphics Preferences" admin utility.  Thanks anyway!  Onwards...

---

### Post by Partyboi2 on 2008-02-21
try looking under the power management options in your bios. Awhile ago I had a machine that would not turn off and it was a setting in the power management that needed to be changed.

Edit: Welcome back to linux

---

### Post by doclord on 2008-02-21
Thanks Partyboi2,
I have taken your advice and investigated the BIOS power management options.  Couldn't find/change anything that improves the situation.  Key issue is that power down worked fine until I changed from "savage" display to "vesa" display (see original posting for more details).  However, without "vesa", startup doesn't work properly - very frustrating, to say the least!!  Would it be worth showing any of the log files?  Main problem now is that preforming a Shut Down, Restart, Suspend, Switch User, etc. doesn't work properly.  More help would be very much appreciated...

---

### Post by doclord on 2008-02-21
Interesting update...
If I boot to Windows (2000, on my aging IBM T22 laptop) and then restart and go back to ubuntu (7.1), the ubuntu shutdown appears to work properly.  I even get a ubuntu splash screen as it shuts down.  I have never seen this before!  Unfortunately, if I restart ubuntu then the problem is reinstated. I have updated a dump from the lshal command, listing all the HAL devices for a separate wireless connection problem.  If this may help, then please see [http://ubuntuforums.org/showthread.php?t=703233]("http://ubuntuforums.org/showthread.php?t=703233")

---

