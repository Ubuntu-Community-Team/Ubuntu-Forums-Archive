---
title: "Ubuntu takes hours to boot, then runs slow"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by jmaridon on 2009-12-03
I have a Dell Inspiron 2500, 1G proc, 1G ram, 10 G harddrive. I did a full install of Ubuntu (overnight). I get the grub menu with 4 choices (Ubuntu, Linux 2.6.31-14-generic, Ubuntu, Linux 2.6.31-14-generic [recovery mode], and 2 memory test options). If I choose the first option, the screen goes blank (the backlight is on, there is a blinking cursor at the top left, then that goes away). If I leave it, it will eventually (3 -4 hours) get to a log in screen, then I can type the login and startx and the GUI will start, but it runs very slow. I tried running Xubuntu from a livecd, the same thing happened. I got it to boot will little trouble with Feather Linux, but that OS is a little light for what I want to do, and it has trouble recognizing the lan and wireless cards.
 
I am new to Ubuntu. My linux experience is very limited. Any ideas or pointing in the right direction would be appreciated.

---

### Post by plusnplus on 2009-12-03
Hi jmaridon,
Did you install windows before at that notebook? did it run normal/ faster?

---

### Post by grandtoubab on 2009-12-03
First did you choose the netbook version of Ubuntu ?
[http://www.ubuntu.com/getubuntu/download-netbook](http://www.ubuntu.com/getubuntu/download-netbook)
[https://wiki.ubuntu.com/UNR](https://wiki.ubuntu.com/UNR)

second 2.6.31.14 is not the last Kernel, you need to update

boot in recovery mode (second choice in grub)
**choose root with network**

verify you are on the net
```
ping www.google.com

```if no error
type 
```
apt-get update
``````
apt-get upgrade
```if things goes well, no errors during upgrade
```
reboot
```

---

### Post by sites on 2009-12-03
Try memtest.  If that doesn't return errors then boot into single user mode and run badblocks to test the hard drive.  That drive has to be about 10 years old.  Good luck with that thing.

---

### Post by jmaridon on 2009-12-03
> **plusnplus said:**
> Hi jmaridon,
Did you install windows before at that notebook? did it run normal/ faster?
I ran XP for the last eight years. It ran relatively well, except the hard drive was almost full and I did not use it enough to keep the updates current, so when I did use it it took a while to get it up and going.

---

### Post by iponeverything on 2009-12-03
> **jmaridon said:**
> I have a Dell Inspiron 2500, 1G proc, 1G ram, 10 G harddrive. I did a full install of Ubuntu (overnight). I get the grub menu with 4 choices (Ubuntu, Linux 2.6.31-14-generic, Ubuntu, Linux 2.6.31-14-generic [recovery mode], and 2 memory test options). If I choose the first option, the screen goes blank (the backlight is on, there is a blinking cursor at the top left, then that goes away). If I leave it, it will eventually (3 -4 hours) get to a log in screen, then I can type the login and startx and the GUI will start, but it runs very slow. I tried running Xubuntu from a livecd, the same thing happened. I got it to boot will little trouble with Feather Linux, but that OS is a little light for what I want to do, and it has trouble recognizing the lan and wireless cards.
 
I am new to Ubuntu. My linux experience is very limited. Any ideas or pointing in the right direction would be appreciated.

When you system goes to the boot grub menu, hit "e"

Go the second line and remove the words "quiet splash"

this it "b" for boot. This will allow you to see that is happening during the boot process.  My guess is that you are having an IRQ issue.

---

### Post by jmaridon on 2009-12-03
> **sites said:**
> Try memtest.  If that doesn't return errors then boot into single user mode and run badblocks to test the hard drive.  That drive has to be about 10 years old.  Good luck with that thing.
I appreciate the comment about the hard drive, it is getting long in the tooth, but doesn't booting from a livecd take that out of the equation? It boots the same way from either the HD or a cd.

---

### Post by jmaridon on 2009-12-03
> **iponeverything said:**
> When you system goes to the boot grub menu, hit "e"

Go the second line and remove the words "quiet splash"

this it "b" for boot. This will allow you to see that is happening during the boot process.  My guess is that you are having an IRQ issue.
I took your advice. Whether I take out the quiet splash or just boot in recovery mode, it gets hung up on what seems to me to be the pci config, the last 4 lines when it first hangs says, 
 
[  0.180964] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
[  0.181030] pci 0000:00:1e.0:   IO window: 0x2000-0x2fff
[  0.181098] pci 0000:00:1e.0:   MEM window: 0xf4100000-0xf42fffff
[  0.181167] pci 0000:00:1e.0:   PREFETCH window: 0x10000000-0x19ffffff
 
I guess I don't understand how an IRQ conflict would arise, or how to recocnize such a conflict, and obviously I don't know how to fix it.

---

### Post by jmaridon on 2009-12-03
> **grandtoubab said:**
> First did you choose the netbook version of Ubuntu ?
[http://www.ubuntu.com/getubuntu/download-netbook](http://www.ubuntu.com/getubuntu/download-netbook)
[https://wiki.ubuntu.com/UNR](https://wiki.ubuntu.com/UNR)
 
[COLOR=red]No, the 2500 is not a netbook.[/COLOR]

second 2.6.31.14 is not the last Kernel, you need to update
 
boot in recovery mode (second choice in grub)
**choose root with network**
 
verify you are on the net
```
ping www.google.com

```if no error
type 
```
apt-get update
``````
apt-get upgrade
```if things goes well, no errors during upgrade
```
reboot
```
 
[COLOR=red]I will give this a try.[/COLOR]
[COLOR=#ff0000][/COLOR] 
[COLOR=#ff0000]Edit: I tried this. The update and upgrade appeared to go as planned; however, when I did the reboot, it just stalled again. I shut it down and rebooted to the grub menu and it gave me the same 2.6.31.14 options. Trying to boot in recovery mode resulted in the same thing.[/COLOR]

---

### Post by iponeverything on 2009-12-03
Try booting with some or all of these options in grub:

acpi=noirq  noapic pci=routeirq

---

### Post by jmaridon on 2009-12-03
> **iponeverything said:**
> Try booting with some or all of these options in grub:

acpi=noirq  noapic pci=routeirq
I tried all three individually and all together. It did make any difference.

---

### Post by jmaridon on 2009-12-04
I figured out the solution on my own. Thanks everyone for the responses and help.
 
I started to read the documentation (may have helped to read earlier, but not as fun) and it makes several suggestions regarding compatibility issues. The very first thing it suggests is to run the os from the livecd to make sure that the system is compatible. I was never able to get the system to work properly from a livecd or a full install suggesting that Ubuntu is not compatible with the Dell Inspiron 2500.
 
Further, I googled linux for laptops and (amazingly) found [http://www.linux-laptop.net/](http://www.linux-laptop.net/) This website suggests Debian for this Dell, along with specific parameters to make it work.
 
So, ultimately, the solution is to abandon a perfectly good, but incompatible OS for a more compatible one.

---

