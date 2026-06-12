---
title: "Problem with new install on Dell Inspiron 640m"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by greenmaze on 2006-10-28
I'm new to Linux so please bear with me. I installed Kubuntu (Edgy) on a work computer today and liked it enough that I want to install it on my laptop. I downloaded Ubuntu (Edgy) to install on my laptop, but I get an error during the boot into Knoppix.

Failed to start X server...

(WW) I810: No matching Device section for instance (BusID PCI:0:2:1) found
(EE) I810(0): No Video BIOS modes for chosen depth.
(EE) Screen(s) found, but none have a usable configuration.

Thinking there might be something wrong with the CD, I tried the Kubuntu CD I used on another computer earlier. A similar problem occured.

The laptop is a Dell Inspiron 640m with a Duo processor.

Any suggestions? Should I wait for bugs to get worked out in this version and just use Dapper?

Thanks

---

### Post by vibestriton on 2006-10-28
System-specific documentation can be found [here]("https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron640m"); it appears to address your problem.  If not, drop a note... it may be a relatively easy-to-fix xorg.conf problem.  Good luck!

---

### Post by greenmaze on 2006-10-28
Thanks for the link. I'm not how sure that info helps since can't even boot to the CD. I'm just going to try installing Dapper, then maybe try upgrading to Edgy.

---

### Post by Augustus on 2006-10-28
Error, I accidently posted here...nevermind :P

---

### Post by greenmaze on 2006-10-28
Well, I was able to install Dapper and then upgrade to Edgy, but I do have one problem (that I know of so far). Prior to upgrading to Edgy, I installed multicore support. This gave me an option at the boot screen to boot into a i686 kernel. After upgrading to Edgy, I only have the option to boot to a i386 kernel. I removed the linux-686-smp via apt-get and then reinstalled it, but this did not solve the problem. Any ideas?

---

### Post by vibestriton on 2006-10-28
```
sudo apt-get install linux-generic

```
Make sure linux-generic is added to your bootloader configation

GRUB default = /boot/grub/menu.lst
LILO default = /etc/lilo.conf

restart and boot using linux-generic option

```
sudo apt-get remove linux-383 linux-686 linux-686-smp
sudo apt-get autoremove
```

---

