---
title: "ubuntu no longer starts, can't diagnose error"
date: 2009-12-02
forum: Installation &amp; Upgrades
---

### Post by eje211 on 2009-12-02
My ubuntu (kubuntu, actually), 9.10 karmic, no longer starts. All I did was a regular daily upgrade and now it's broken. X begins to start, then I get a series of strange windows that appear fuzzy on my screen, so I can't read them. I'm runnig ubuntu from a disc, now. The following is from the old machine's disc:

```

ubuntu@ubuntu:/media/ubuntu$ cd var/log/

ubuntu@ubuntu:/media/ubuntu/var/log$ cat dmesg |tail
[   28.487076] type=1505 audit(1259800302.224:17): operation="profile_replace" pid=1146 name=/usr/bin/evince-previewer
[   28.495597] type=1505 audit(1259800302.234:18): operation="profile_replace" pid=1146 name=/usr/bin/evince-thumbnailer
[   28.506829] type=1505 audit(1259800302.244:19): operation="profile_replace" pid=1148 name=/usr/lib/cups/backend/cups-pdf
[   28.507855] type=1505 audit(1259800302.244:20): operation="profile_replace" pid=1148 name=/usr/sbin/cupsd
[   28.522113] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.554764] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   28.618289] type=1505 audit(1259800302.354:21): operation="profile_replace" pid=1149 name=/usr/sbin/mysqld
[   28.620978] type=1505 audit(1259800302.364:22): operation="profile_replace" pid=1155 name=/usr/sbin/mysqld-akonadi
[   28.940720] cfg80211: Found new beacon on frequency: 2472 MHz (Ch 13) on phy0
[   28.948396] cfg80211: Found new beacon on frequency: 2467 MHz (Ch 12) on phy0

ubuntu@ubuntu:/media/ubuntu/var/log$ cat syslog |tail
Dec  3 00:31:47 Dual-Core udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:1d.7/usb1/1-4
Dec  3 00:31:47 Dual-Core udev-configure-printer: Device vendor/product is 05AC:1209
Dec  3 00:31:47 Dual-Core udev-configure-printer: invalid or missing IEEE 1284 Device ID
Dec  3 00:31:47 Dual-Core bluetoothd[1820]: Parsing /etc/bluetooth/serial.conf failed: No such file or directory
Dec  3 00:31:47 Dual-Core bluetoothd[1820]: probe failed with driver input-headset for device /org/bluez/1803/hci0/dev_00_1F_00_22_A8_22
Dec  3 00:31:47 Dual-Core bluetoothd[1820]: Adapter /org/bluez/1803/hci0 has been enabled
Dec  3 00:31:48 Dual-Core pulseaudio[2195]: core-util.c: Home directory /etc/timidity not ours.
Dec  3 00:31:48 Dual-Core pulseaudio[2195]: lock-autospawn.c: Cannot access autospawn lock.
Dec  3 00:31:48 Dual-Core pulseaudio[2195]: main.c: Failed to acquire autospawn lock
Dec  3 00:31:51 Dual-Core kernel: Kernel logging (proc) stopped.

ubuntu@ubuntu:/media/ubuntu/var/log$ cat Xorg.0.log
_XSERVTransSocketUNIXCreateListener: ...SocketCreateListener() failed
_XSERVTransMakeAllCOTSServerListeners: server already running

Fatal server error:
Cannot establish any listening sockets - Make sure an X server isn't already running

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor
(WW) xf86OpenConsole: VT_GETSTATE failed: Bad file descriptor
 ddxSigGiveUp: Closing log
ubuntu@ubuntu:/media/ubuntu/var/log$ 

```

It looks like X is to blame, but why? And how can I fix it?

---

### Post by brhokla on 2009-12-02
Mine was working fine till I did the update also and now it won't start and the screen just goes black.

---

### Post by eje211 on 2009-12-03
That's another thing: the screen buffer goes black on all terminals. It's not even possible to use ctr-alt-F1, etc. Text appears for an instant and then it's all black.

---

### Post by akudewan on 2009-12-03
I'm having the same problem. If I remember correctly, there was some update that replaced/upgraded the "upstart" package. Maybe this is the cause.

Also, I cannot press 'e' or 'c' in Grub to edit any options. "Recovery mode" also has the same problem (which is extremely retarded, IMO).

Any help/solution/workaround would be appreciated.

---

### Post by PAC1 on 2009-12-03
Same here.  This is really dumb.  I can read the message if I choose to boot a 2.6.28-16 kernel buts its all mushed up with 2.16.31-14 / 2.6.31-15.  The message is basically trying to tell me that Ubuntu is running in low graphics mode.  Under the 2.6.28-16 kernel I can get to a console and manually startx at which point it appears everything but my synaptics touchpad works (external mouse works).

Now I know what the menu is saying I can navigate it under 2.6.31-15 but I don't get a console just blank screens.

My hardware is okay as I can boot from a Ubuntu CD and everything works.

---

### Post by eje211 on 2009-12-03
I figured out that my problem was that X starts twice, the second time being the "good" one. Frantically typing ctrl-alt-backspace again and again got me to boot normally. But this is obviously a workaround, not a solution.

---

### Post by PAC1 on 2009-12-04
Okay sorted my problem.  I had been trying to install alternative input methods for Chinese/Japanese seems I broke HAL.  I eventually noticed the line "config/hal: couldn't initialise context: unknown error (null)" in /var/log/Xorg.failsafe.log.  So in my case apt-get reinstalling hal fixed my system.

I think there is still an underlying problem with "upstart" and 2.6.31 kernels.

No expert but the following also from /var/log/Xorg.failsafe.log might be relevant:

(WW) VESA(0): Unable to estimate virtual size
(WW) VESA(0): No valid modes left. Trying less strict filter...
(WW) VESA(0): Unable to estimate virtual size
(WW) VESA(0): No valid modes left. Trying aggressive sync range...
(WW) VESA(0): Unable to estimate virtual size

System is a DELL laptop XPS M1210

---

### Post by PAC1 on 2009-12-04
In case you want to comment on it I've filed a bug report on "upstart" and 2.6.31 kernels.

[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/492270](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/492270)

---

### Post by Cippa Lippa on 2009-12-04
same problem here guys, exactly the same "low graphics mode" thingy/ The whole bootup is completely random - I cannot see the console text, it all mushed up. Are we sure this is not an NVIDIA driver problem? I remember updating the driver not too long ago.

I have one more aspect that might be relevant for diagnosis.
When I boot, the Kubuntu loading bar appears. When the bar reaches about 50% the screen disappears and I get a blinking cursor at the top of the screen. After a few minutes, sometimes, something happens and the cursor rapidly moves to the bottom of the screen, and then the OS starts normally

it seems to me this is a serious problem. I hope this will be dealt soon because the system is essentially not functional anymore.

My system is a dell latitude d830 with ubuntu64 on kde dualbooting windows 7 ultimate

---

### Post by mkleczek on 2009-12-04
Looks like I have the same problem - my sysem is almost unusable after update.
After showing splash screen the screen goes blank with a blinking cursor in top-left corner.
Pressing Alt-Fx does not change anything - sometimes there are only some white dots on the screen.
It is not nvidia related - I have Intel card.
After adding removing splash and adding i915.modeset=0 on boot a popup with "Failed to load i810 module" message or similar appears and I can login in text mode. Then I can issue startx and wow - GNOME starts normally.

---

### Post by PAC1 on 2009-12-04
I can also confirm the mushed up menus are not Nvidia related, my machine is Intel, normally runs with i915 module.

---

### Post by Cippa Lippa on 2009-12-04
> **mkleczek said:**
> Looks like I have the same problem - my sysem is almost unusable after update.
After showing splash screen the screen goes blank with a blinking cursor in top-left corner.
Pressing Alt-Fx does not change anything - sometimes there are only some white dots on the screen.
It is not nvidia related - I have Intel card.
After adding removing splash and adding i915.modeset=0 on boot a popup with "Failed to load i810 module" message or similar appears and I can login in text mode. Then I can issue startx and wow - GNOME starts normally.

can you please detail the steps you made to get into the working desktop?
how do you remove splash and add i915.modeset=0 on boot?

---

### Post by mkleczek on 2009-12-04
> **Cippa Lippa said:**
> can you please detail the steps you made to get into the working desktop?
how do you remove splash and add i915.modeset=0 on boot?
I have GRUB configured to display boot menu. If it does not I guess you have to press SHIFT during boot.
Press 'e' to edit boot menu option.
Go to the end of line starting with 'linux...'.
Remove 'splash' and add 'i915.modeset=0'.
Press Ctxl+x to boot.

Does anybody know if there is a bug reported and if the issue is being worked on?
Ubuntu worked like charm for me for quite some time for me after moving from Fedora (which I considered not stable enough for me). Now it looks like this distro is broken as well... Time to pay for Windows :(

---

### Post by manishsk on 2009-12-04
Hi guys if you are facing low-graphics mode issue please check this.

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/491483]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/491483")

Degrading the latest updates and for the time being shifting to GDM may help.

Let me know if the suggested approaches do not work.

---

### Post by Cippa Lippa on 2009-12-04
> **mkleczek said:**
> I have GRUB configured to display boot menu. If it does not I guess you have to press SHIFT during boot.
Press 'e' to edit boot menu option.
Go to the end of line starting with 'linux...'.
Remove 'splash' and add 'i915.modeset=0'.
Press Ctxl+x to boot.

Does anybody know if there is a bug reported and if the issue is being worked on?
Ubuntu worked like charm for me for quite some time for me after moving from Fedora (which I considered not stable enough for me). Now it looks like this distro is broken as well... Time to pay for Windows :(

After doing this trick I can now login but I get the low graphics mode thingy, which I can click through to get to the working desktop.
This is NOT good guys, this is really NOT good

Windows 7 seems to be having big problems as well - I am getting BSODs like there is no tomorrow. Bad news for doing actual work with PCs.

---

### Post by manishsk on 2009-12-04
> **Cippa Lippa said:**
> After doing this trick I can now login but I get the low graphics mode thingy, which I can click through to get to the working desktop.
This is NOT good guys, this is really NOT good

Windows 7 seems to be having big problems as well - I am getting BSODs like there is no tomorrow. Bad news for doing actual work with PCs.

check this out for "low graphics mode"
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/491483](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/491483)

---

### Post by Cippa Lippa on 2009-12-04
> **manishsk said:**
> check this out for "low graphics mode"
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/491483](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/491483)

switching to GDM doesn't seem to be a solution! I was an arch linux user... and even there they didn't have these kind of problems... amazing.

---

### Post by PAC1 on 2009-12-04
> **manishsk said:**
> check this out for "low graphics mode"
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/491483](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/491483)

Seems I spoke in haste when I said I'd fixed my system earlier.  It only stayed fixed for one reboot?! - My best guess is reinstalling hal fixed something that X, kdm or kde subsequently broke again?

Looks like the xorg update mentioned in the above bug report might be to blame.  Rolled back as described in post #19 and my system is still working (after 3 reboots) with kernel 2.6.31-15 and using kdm/kde. ( no need for gnome nonsense ;-) )

---

### Post by PAC1 on 2009-12-04
Looks like this is the same issue but reported by those lucky people who can actually read their screens following X/KDM/Upstarts failure:

 [http://ubuntuforums.org/showthread.php?t=1343261](http://ubuntuforums.org/showthread.php?t=1343261)

To summaries looks like there are currently two solutions: (i) used gdm (and forget being able to shutdown from inside kde) or (ii) roll back the X updates.

---

### Post by mkleczek on 2009-12-04
> **PAC1 said:**
> Looks like this is the same issue but reported by those lucky people who can actually read their screens following X/KDM/Upstarts failure:

 [http://ubuntuforums.org/showthread.php?t=1343261](http://ubuntuforums.org/showthread.php?t=1343261)

To summaries looks like there are currently two solutions: (i) used gdm (and forget being able to shutdown from inside kde) or (ii) roll back the X updates.

Switching to gdm indeed works. But still - fonts are messed up in KDE.
Downgrading looks like the best solution for now. Thanks

---

### Post by mkleczek on 2009-12-05
> **mkleczek said:**
> 
Downgrading looks like the best solution for now. Thanks

So... I've turned on my laptop this morning (yesterday I've downgraded packages as described in above mentioned thread. Same thing - no kdm login screen.
Added nosplash nomodeset options to 2.6.31-15 kernel in GRUB and it worked.

---

### Post by tutwabee on 2009-12-06
I encountered this error after upgrading my packages two days ago

While booting, text flew across the screen as usual and at the point in boot when the text becomes more graphically advanced-looking, I receive a black screen with some garbled quickly flashing white characters or cursor marks.  After trying various key combinations sometimes the screen will turn a faded bright blue color before I have to force shutdown the computer.

Recovery mode for both of the kernels in grub (both .15) had the same problem.

I found that while starting up the system if I mash Pause and Break repeatedly, about one out of five times, I will come to a prompt that gives me the option to boot in single-user mode.  From here I can run gdm.

---

### Post by tutwabee on 2009-12-06
> **manishsk said:**
> check this out for "low graphics mode"
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/491483](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/491483)

I was using slim as my login manager and that was the problem.  As suggested in this bug report, switching to GDM worked for me.

Switching to GDM can be done like this:
```
sudo dpkg-reconfigure gdm
```

---

### Post by Cippa Lippa on 2009-12-08
guys, there still seem to be problems. I have downgraded the Xorg and added the boot option discussed earlier. 
The result is that now, for unfathomable reasons, the system won't boot into the latest kernel (ending in .15) so I have to log in with the .14.

I mean, this is ridiculous. I have worked on linux for years now. I have never quite seen an instability problem like this one before, especially with no clear resolution in days...

unbelievable.

---

### Post by akudewan on 2009-12-08
> **Cippa Lippa said:**
> 
I mean, this is ridiculous. I have worked on linux for years now. I have never quite seen an instability problem like this one before, especially with no clear resolution in days...

unbelievable.

Indeed. I, too, have been using Linux since eight years. The inability to get a recovery console to try to manually solve this was what annoyed me the most. (I didn't have a LiveCD lying around).

I have moved over to Arch Linux. Now I am responsible for maintaining and upgrading my system myself.

(Disclaimer: I'm not posting this as flamebait, but these are just my thoughts. Ubuntu is a great distro, and I'd recommend it to any newbie)

---

### Post by Cippa Lippa on 2009-12-11
Has this problem been fixed now with the new upgrades. I am not upgrading anymore since this problem showed up...

---

### Post by Cippa Lippa on 2009-12-21
bump

---

