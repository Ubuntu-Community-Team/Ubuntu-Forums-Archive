---
title: "Installing Ubuntu on Toshiba Satellite C655"
date: 2010-06-29
forum: Installation &amp; Upgrades
---

### Post by lolajl on 2010-06-29
I'm trying to get Ubuntu 10.04, 64bit working on my Laptop - Toshiba Satellite C655.   I need to keep both Windows 7 and Linux - this is essential for my web design work (I use a MBP most of the time).  I was able to run the installation process only after setting acpi=off.  

When I  boot into GRUB and select 1st option - ubuntu w/linux 2.6.32-21 generic, I then hit 'e', enter acpi=off, and press Ctrl-X to boot up.  However, I still get a list of strange strings, ending with "child_rip+0x0/0x20" and then a blinking cursor at the end.  I can't type anything in and have to hit the Power button to restart the PC.  how can I get past this and straight into Ubuntu GUI?

I know next to nothing about Windows 7, so I have no idea what extra steps I have to do to get around this.  I did do some preliminary research and it seems that Toshiba laptops have this same issue, but I haven't been able to see a workaround so far. Any suggestions?  I've heard so much about Ubuntu and I want to see if it's really true as to what is being said about it.

---

### Post by jeffreyldavidson on 2010-06-29
There was a long thread that discussed a kernel patch for 9.04 and 9.10 but it has not been updated for 10.4. I have a Toshiba L505 with the same problem and have tried a half dozen other distros with the same problem so it a problem with Toshiba bios and the linux kernel. Wish someone would get a fix though because Toshiba could care less. They just cater to M$.

---

### Post by finlost on 2010-06-30
I am looking at a Toshiba L505 on TigerDirect.  It is a Windows 7 64-bit that I would dual boot with either 9.10 or 10.04.  Is the consensus to avoid Toshiba lappies?

---

### Post by th0th696 on 2010-07-07
you have to add it to the line that has the kernel options so add "acpi=off" right before "splash"

then once you've installed edit the file /etc/default/grub

and find this and change it to look this:

```
GRUB_CMDLINE_LINUX_DEFAULT="acpi=off quiet splash"
```

then run:

```
sudo update-grub2
```

then you'll be booting, but this is far from perfect.  I will post here when I find a real solution.

---

### Post by th0th696 on 2010-07-08
Okay the solutions appears to be here on the 8th page of this thread:

[http://ubuntuforums.org/showthread.php?t=1301101&page=8](http://ubuntuforums.org/showthread.php?t=1301101&page=8)

after you finish installing the two deb files that are created during the process described during the first post you will also need to create the initramfs like so:

```
sudo update-initramfs -c -k 2.6.32.4-l505d
sudo update-grub2
```

then you can reboot and turn on acpi, and battery now appears when you pull out the plug! And both processor cores are working!  Yay, I will experiment more and see if things are complete.

---

### Post by cypress914 on 2010-08-15
> **th0th696 said:**
> you have to add it to the line that has the kernel options so add "acpi=off" right before "splash"

then once you've installed edit the file /etc/default/grub

and find this and change it to look this:

```
GRUB_CMDLINE_LINUX_DEFAULT="acpi=off quiet splash"
```then run:

```
sudo update-grub2
```then you'll be booting, but this is far from perfect.  I will post here when I find a real solution.



Can anyone tell me how to get to this point?  I have the Satellite C655d, installed Ubuntu 10.04 after turning off the acpi, but now it will not boot.  The only way I can get into the OS is to boot from the Live CD.  I made the above changes but still can't reboot the system.  Please help!!!

---

### Post by th0th696 on 2010-08-16
I think you are having the same problem as the original poster, to be pedantic about this:

boot into GRUB and select 1st option - ubuntu w/linux 2.6.32-21 generic, I then hit 'e',(/*ok here's where I change things from the original poster*/), hit down until you are on the line that begins "kernel", hit the END key, this places your cursor at the end of the line,(/*now proceed as the original poster*/) then enter acpi=off, and press Ctrl-X to boot up

Look at this page again:
[http://ubuntuforums.org/showthread.php?t=1301101&page=8](http://ubuntuforums.org/showthread.php?t=1301101&page=8)

once you have it up and running note that I followed post #71 

but on reply #79, he gives you his kernels which appear to work just fine, I'm still using the ones I compiled though:
[http://justkitchen.info/kernel/linux...stom_amd64.deb](http://justkitchen.info/kernel/linux...stom_amd64.deb)
[http://justkitchen.info/kernel/linux...stom_amd64.deb](http://justkitchen.info/kernel/linux...stom_amd64.deb)

---

### Post by th0th696 on 2010-08-16
The steps have all been detailed in this post and the other one I mentioned.  What problem are you having?  As I've said before, if you are still using the default kernel from the install, you'll need to add acpi=off to your kernel options, if you can't get the cd to boot, you need to add acpi=off to the kernel options there.  Once installed and booted using the default kernel, you'll only have 1 cpu core.  To get it running you'll need to install the kernels I linked to.  That's it.  Everything should work now, except for a couple of the 'blue' buttons (turn wifi doesn't work, but adjust screen brightness and volume work just fine).  These things will work themselves out over time as kernel patches make into the mainstream kernel.

---

### Post by th0th696 on 2010-09-23
On a plus note the aforementioned thread on l505d claims the new 10.10 beta cd's are working out of the box on at least the l505d. I tried a 2.6.35 kernel on my gentoo partition with no luck, I wonder if the ubuntu team is doing something special?  I'll report back when I upgrade to 10.10

---

### Post by CapPicard on 2011-10-16
I also have a Toshiba Satellite C655, namely the C655-S5082. I have to pass "nomce" (without the quotes) to the kernel boot command line, otherwise I receive the kernel panic message sometimes when I boot Ubuntu.

I am trying to find out about kernel support for the Insyde H2O Bios on this laptop. Perhaps, Intel has some info about this... the kernel ACPI modules are quite flaky on this Satellite.

---

