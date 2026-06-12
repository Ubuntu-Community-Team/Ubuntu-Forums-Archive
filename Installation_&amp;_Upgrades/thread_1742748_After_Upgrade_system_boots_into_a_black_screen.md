---
title: "After Upgrade system boots into a black screen"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by Cotopaxi on 2011-04-29
Hi all,

I upgraded from 10.10 to 11.04 and after the upgrade 

- the system boots,
- the grub menu appears,
- the splash screen comes up and then
- I have a black screen and that's it!

I saw, at the end of the installation process, that the driver for the nVidia video card was removed.

Can anyone give me a helping hand please?

---

### Post by dino99 on 2011-04-29
from grub menu: remove "splash"

or

boot in recovery mode, either choose "repair packages" or "graphic failsafe"

then check that: nvidia-current, nvidia-common, nvidia-settings are installed

remove xorg.conf: sudo rm /etc/X11/xorg.conf

reboot

---

### Post by Cotopaxi on 2011-04-29
Hi dino,

First of all, thanks very much indeed for your help.

I am an extreme beginner and I do not even know, how to boot into recovery mode!

After the bios screen, I hold the shift key and the grub menu appears. That's all, I am able to do.

Can you give me a helping hand from here?

Thanks again! :popcorn:

---

### Post by dino99 on 2011-04-29
recovery mode is the second line choice from grub menu, select it (highlighted) then hit "E" to edit, then wipe "splash" at end of the line, then hit "X" to boot

(everything is shown on grub menu bottom line)

---

### Post by Cotopaxi on 2011-04-29
Thanks again Dino!

In the recovery mode option, there is no splash instruction in the line:> linux /boot.....

The only thing there is, at the very end of the line is:

> vga=769

In the generic boot option, there is at the very end:
> vga=769  quiet splash

when choose a kernel, the next information, that appears on screen is:
> inux-bzImage, setup=0x3400, size=0x3bf460]
vga=769 is depreciated. Use set gfxpayload=640x480x8,640x480 before linux comm and instead

In the ongoing of the boot it says:
> failure: appArmour profiles failed to load

I managed to have a Recovery mode screen where I have the options:
> failsafeX Run in failsafe graphic mode
netroot Drop to root shell with networking
root Drop to root shell prompt
How shall I go on from here?

Thanks very much indeed again! :popcorn:

---

### Post by Cotopaxi on 2011-04-29
One more thing:

It is a lenovo laptop with an nVidia video card.

On other part of this forum I read, that the 11.04 version had backlight issues, so I plugged in the external monitor. But the external monitor gave me exactly the same information as the laptop screen: none at all.

Thanks again for your help! :popcorn: :popcorn:

---

### Post by Cotopaxi on 2011-04-29
the command:
> sudo apt-get install nvidia-current
gave me the answer that it could not locate the server for download.

---

### Post by Cotopaxi on 2011-04-29
Jeez guys

I really need a helping hand!

Can anyone tell me what I should try next?

---

### Post by dino99 on 2011-04-29
check: system admin network

or into a terminal: ifconfig

or simply reboot

---

### Post by Cotopaxi on 2011-04-29
hi Dino,
the output of ifconfig is:

> Link encap:Local Loopback
inet addr:137.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
Rx packets:8 errors:0 dropped:0 overruns:0 frame:0
TX packets:8 errors:0 dropped:0 overruns:0 frame:0
collisions:0 txqueuelen:0
RX bytes:480 (480.0B) TX bytes:480 (480.0B)

Thanks again! :popcorn:

Sorry, I can not give you caviar and champaign, there is only pocorn availiable!

---

### Post by Cotopaxi on 2011-04-29
about the command: sudo apt-get install nvidia-current, I will type one line of response:

> Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/n/nvidia-settings//nvidia-settings_270.29-Oubuntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/nvidia-settings//nvidia-settings_270.29-Oubuntu1_amd64.deb) Could not resolve 'archive.ubuntu.com'

There are a total of 5 of these error messanges.

The problem is that I am on the Desktop machine of my son and I have to re-type everything from the laptop's screen.

Thanks again!

---

### Post by Cotopaxi on 2011-04-29
One question:

I am downloading the Installation CD for 11.04 and it will still take some 4 hours to have the download completed.

Can I just insert a 10.04 (Lucid Lynx) Installation CD and install that, of course without formatting the 'home' directory?

Thanks again!

---

### Post by dino99 on 2011-04-29
better to wait a few days as servers are very busy right now, so no need to add more work on them.

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by Cotopaxi on 2011-04-29
The problem is, I am without computer right now.

Can I just install the 10.04 version again, to be up and running again?

Thanks!

---

### Post by Cotopaxi on 2011-04-29
The problem is, I am without computer right now.

Can I just install the 10.04 from my CD version again (no load to the servers), to be up and running again?

Thanks!

---

### Post by Cotopaxi on 2011-04-29
I apologize for insisting:

Can I just slide a 10.04 Installation CD (which is already burned) into the computer and make an install of the 10.04 version over the crashed 11.04?

---

### Post by epicoder on 2011-04-29
> **Cotopaxi said:**
> Can I just slide a 10.04 Installation CD (which is already burned) into  the computer and make an install of the 10.04 version over the crashed  11.04?     

I think it's possible, but before you do that try this:

boot into recovery mode via GRUB (usually the second menu choice)
use a networked root shell (labeled "netroot" on the left)
If possible, plug your laptop into ethernet (wired internet)
If you have ethernet, then run these commands:
```
ifconfig eth0 up
dhclient eth0
```If you have to use a wireless network, run these commands:
```
ifconfig wlan0 up
iwconfig essid [name of the network enclosed in ""] [wireless password] #if your network password is plain text instead of a hex number (hex looks like f34fa76ddb6), prepend an "s:" without the quotes to the password
dhclient wlan0
```That will connect you to the internet. Then you can install the nvidia drivers via:
```
sudo apt-get update
sudo apt-get install nvidia-current

```Once you have done that, reboot normally and see what happens.
```
shutdown -r now
```
 Good luck.

---

