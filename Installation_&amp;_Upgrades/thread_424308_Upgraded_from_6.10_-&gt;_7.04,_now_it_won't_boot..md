---
title: "Upgraded from 6.10 -&gt; 7.04, now it won't boot."
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by BrianK on 2007-04-26
I had a good working Ubuntu 6.10.  I went to the update manager & clicked the Upgrade to 7.04 button.  AFter an hour or so, it was ready to reboot (I did all the default options during the upgrade), but now it hangs on the loading screen - the one that would normally have the progress bar.  The progress bar just shows up, then everything stops.  No error message, nothing. (Why is there no longer output on this screen?? It's perfectly useless without showing what it's doing).

This is a 2.8 GHz machine with 2GB RAM and an nvidia card.  Like I said, everything was working fine when it was 6,10 & that was a pretty vanilla 6.10 - no funny configs or lots of extra apps.

I double checked the grub line to see that it was using the correct hard drive.  It appears to be.

Any ideas how I can find out what's even going on?  Maybe some diagnostic info during bootup instead of the useless progress bar?

---

### Post by PatrickE on 2007-04-26
> **BrianK said:**
> 
Any ideas how I can find out what's even going on?  Maybe some diagnostic info during bootup instead of the useless progress bar?

At startup, enter the boot menu by pressing ESC when the message "Press ESC for boot menu" (or so) appears (this message should be there for about 2 sec before the "BIOS screen" switches to Ubuntu's progress bar screen, after detecting the hard drives etc).
And then you should see Grub's boot menu where you can choose to start in recovery mode.
This should give you some error messages at least.

Good luck
Patrick

---

### Post by BrianK on 2007-04-26
> **PatrickE said:**
> At startup, enter the boot menu by pressing ESC when the message "Press ESC for boot menu" (or so) appears (this message should be there for about 2 sec before the "BIOS screen" switches to Ubuntu's progress bar screen, after detecting the hard drives etc).
And then you should see Grub's boot menu where you can choose to start in recovery mode.
This should give you some error messages at least.

Good luck
Patrick
That's a start - thanks!  So it loads (in recovery mode) until it gets to this point:

5.006867 ohci-1394: fw-host0 ...

it's the first 5.0 thing, everything before that was 4.x  

Does that mean anything to anyone?  Anyway to fix this?

---

### Post by PatrickE on 2007-04-27
> **BrianK said:**
> That's a start - thanks!  So it loads (in recovery mode) until it gets to this point:

5.006867 ohci-1394: fw-host0 ...


I'm also just guessing, but this seems to be some firewire driver. Do you have any firewire stuff connected to your pc? Maybe loading the proper drivers just needs ages.
(I experienced this once on a WinXP with usb: Starting it for the first time after installation made it stop for a longer while till drivers for the usb keyboard & mouse were loaded and configured or whatever...)

So as a try, I would suggest either to wait for a longer while (btw, how long did you wait when startup "stopped"?) or unconnect your firewire equipment (if any), and/or deactivate firewire.

---

### Post by BrianK on 2007-04-27
> **PatrickE said:**
> I'm also just guessing, but this seems to be some firewire driver. Do you have any firewire stuff connected to your pc? Maybe loading the proper drivers just needs ages.
(I experienced this once on a WinXP with usb: Starting it for the first time after installation made it stop for a longer while till drivers for the usb keyboard & mouse were loaded and configured or whatever...)

So as a try, I would suggest either to wait for a longer while (btw, how long did you wait when startup "stopped"?) or unconnect your firewire equipment (if any), and/or deactivate firewire.
No firewire equipment on this machine - there's not even a firewire port.

I've waited 12 hours.  think that's long enough?  ;)

I'm guessing it's the thing that loads after the first firewire driver is loaded & it dies before it prints out any message.

Still pretty bumbed about this.  I've just lost a computer by upgrading.

---

### Post by Aperium on 2007-04-27
I just updated from 6.10 to 7.04 in the same manner that BrianK did and have observed the freezing of the progress bar, just as described above.  

Restarting in recovery mode, it paused at :
```
Begin: Waiting for root file system... ...
[17179571.728000] input: AT Translated Set 2 keyboard as /class/input/input0
```

minuntes later it followed with:
```

Done.
ALERT! /dev/hda1 does not exist. Dropping to a shell!

Busybox v1.1.3 (Debian 1:1.1.2-2ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs) _

```


It's still sitting there.
Help me get it back running, please!

---

### Post by PatrickE on 2007-04-28
> **Aperium said:**
> 
/bin/sh: can't access tty; job control turned off
(initramfs) _


I know I'm not a big help here, but at least googling for this error message brought me to several hits, especially this:
[http://ubuntuforums.org/showthread.php?t=415009](http://ubuntuforums.org/showthread.php?t=415009)
and this:
[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/96084](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/96084)

So seems you are not alone, and seems this error can have quite many reasons... (Although I don't know if you both have the same problem since Brian doesn't report about such an error message)

Maybe these links will bring some solution. Or the ones you can find in Google...

Again, good luck
P.

**EDIT:**
Reading through brought me here: [http://ubuntuforums.org/showpost.php?p=2553305&postcount=133](http://ubuntuforums.org/showpost.php?p=2553305&postcount=133)
This looks like something that might work out

---

