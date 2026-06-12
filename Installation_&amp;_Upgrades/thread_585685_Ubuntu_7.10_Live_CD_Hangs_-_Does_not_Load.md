---
title: "Ubuntu 7.10 Live CD Hangs - Does not Load"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by mahesh102 on 2007-10-21
Hi, I have an HP Pavillion A1010y. I'm trying to install Ubuntu linux on my computer. I have XP on my primary hard drive. I put in the live CD and click _Start or Install..._ ...the very top option...It takes me  to a screen with an orange thing moving back and forth, so it's loading something...then a bar starts to fill up orange...the bar goes a certain distance and just stops..my CD drive stops blinking and it just hangs there....and it hangs at the same spot every time...

I have intel pentium 4
Nvidia Ge force FX 5200 Graphics card

Any ideas?

Sorry I'm new at linux so if you need more info just let me know

Thanks!

---

### Post by zx80user on 2007-10-21
I had this because my BIOS was reporting a floppy disk, which was not installed. Removing this allowed the CD to boot.

Alternatively press '6' on the boot menu and edit out 'quiet' on the boot command and then you'll be able to see what part of the boot process is holding things up.

---

### Post by bliffle on 2007-10-21
Might be a bad DL or burn (I've had both). 

Best thing to do is follow the process for checking the "MD5SUM", which is described elsewhere at the ubuntu.org site. You perform that test with the CD you burned on a machine with a known good windows or linux system, using the CD you were trying to boot from.

---

### Post by mahesh102 on 2007-10-21
Thanks for the help! 

I tried disabling the floppy drive and I still have the same problem. I also know that the CD that I burned works because I tried loading it on my roommates laptop, and it loads fine. Another option that I tried was getting the alternative version, which is the text install. This installed Linux perfectly on to my 2nd hard drive and game me a boot menu. I try loading linux and I get a bar again filling up orange, and again it freezes at the exact point as it always has. I've looked up my hardware on the site, and all my hardware seems to be compatible. Is there anything else I can try doing?

Thanks!

---

### Post by zx80user on 2007-10-22
Edit the boot menu in grub to remove the "splash" and "quiet" options - then you will get a lot of messages on the screen during the boot. these should help determine what is wrong or at least where the hold up is.

---

### Post by mahesh102 on 2007-10-22
> **zx80user said:**
> Edit the boot menu in grub to remove the "splash" and "quiet" options - then you will get a lot of messages on the screen during the boot. these should help determine what is wrong or at least where the hold up is.

Thanks for the help!

I went ahead and removed splash quiet and it goes through a bunch of text, in which it checks my hardware...and then it goes through some script that I totally don't understand and then it hangs. Is there any other way to install linux? I managed to get it to install using the alternate CD, however when it tries to load linux off of the HD, a progress bar appears again and gets filled up with orange. It hangs at the exact same spot as the CD.

Thanks!

---

### Post by pkeegan on 2007-10-22
I'm having the same issue. I tried the "Live" CD on an IBM T42p and the load from CD went without issue. I took the CD and then tried to boot up a Toshiba 3005-S303. It stalled in the manner you describe. I believe it to be a video driver issue. The Toshiba uses an Nvidia Geforce2 GO chip. I haven't tried the Alternative CD yet. I hoping it will allow me to install a video driver after I get the system up and running with the base driver. Nvidia drivers can be problematic. Note. I was able to install Edgy & Feisty from Live CDs without issue on this same computer. I prefer to do fresh installs and that's what I hope to do with Gusty.

---

### Post by angloman on 2007-10-23
Im having a similar experience.

I've got a Intel Core 2 Quad Q6600 which installed Ubuntu 7.10 64bit with no problems. Well, except that my wireless card and gfx won't work under the restricted driver system... so I have poor graphics and no internet.

I thought I'd try ubuntu i386 but it just hangs at the ubuntu splash screen for the live CD. after about 10 minutes it displays some screen talking about some FS or something... anyone have any ideas?

---

### Post by super-sauce on 2007-10-23
I'm experiencing a similar issue as well.  When I try to install either 7.04 or 7.10, both will get to the ubuntu splash screen with the little orange bar then it all just seems to quit.  If u let it sit there eventually the splash screen goes away and a little white blinking cursor appears in the top-right corner of the monitor.  Then after a while a message something like "logical read error" or something along those lines, I'll do it again and actuall write it down nxt time ;).  Anyway so i'm ***still*** using 6.06.  I like it dapper is rock solid, and stable, but I wouldnt mind trying out 7.10 or 7.04.  My specs are as follows:

Mobo: gigabyte k8u-939
cpu: AMD athlon 64 3000+
ram: 2gb
gfx: Nvidia GeForce 6800XT
hd's: one 40gb IDE and one 500gb SATA
running ubuntu dapper drake, and xp pro in dual boot.

---

### Post by mahesh102 on 2007-10-23
So is there any way to tell the linux CD to ignore the Nvidia graphics card? I know there's an option on the CD itself, which I tried, but it hangs at the same spot.

Thanks!

---

### Post by mahesh102 on 2007-10-23
Here is more information and things I've tried:

I tried installing with the F6 option and removing the splash. It goes through some scrips and then says Begin: Running/ Scripts/ init-bottom. Then there are a bunch of scripts that I can't read because it goes too fast but then it just stops at this:

[138.585867] [<c010432e> work_notifying + 0x13/0x25
[133.585867] ==============================

I have no idea what that means,  but right at that script my CD drive stops humming and the light turns off and it hangs again.

I also tried adding the ACPI=off; in this instance the script just kept running continuously really fast; after about 5 minutes my CD drive again stopped humming; I still let it run for another 30 minutes but it seemed to be repeating itself and was going too fast for me to able to read anything

I also tried adding nodma; When I did this I read a few errors: one of the errors was an "ACPI error"; the "method parse/execution failed; ACPI exception" and then it did that continuous fast script thing, which I let run 30 minutes again; I also tried nofloppy, and again it did that continuous scrip thing, and my CD ROM drive stopped humming and went silent...I again waited 30minutes and then just turned off my computer...

I've also tried the alternative CD...It installed linux perfectly but when I tried to load it from my dual boot menu it again gave me a progress bar and the bar filled to the same exact spot and again just rolled over and died; I basically can't think of any more options...Is there anything else I can do?

Thanks!

---

### Post by Bieghe on 2007-10-24
I receive this same exact error, it when I turn off quit mode and the splash screen, it hangs up at the point when it starts to check for hardware drivers.  Does anyone know any possible solution?

---

### Post by Luis Marks on 2007-10-25
I have the same problem. When goes to enter in graphic mode the computer reset, how in button power reset. I post a bug report, but i have no answers. I have a 6800XT Nvidia, and with a 5500 Nvidia works.

[https://bugs.launchpad.net/ubuntu/+bug/151274](https://bugs.launchpad.net/ubuntu/+bug/151274)

---

### Post by Luis Marks on 2007-10-25
I solve my problem, Ubuntu has configuring my video how "vesa" in the xorg.conf. This cause the reboot. To solve this is necessary to boot in single mode (press F6 in livecd menu boot, delete "quiet" and "splash" options and include "single") and edit the /etc/X11/xorg.conf (pico /etc/X11/xorg.conf). My video card is a Nvidia, so i use the "nv" driver. Go to the section "Device" and change the driver from "vesa" to "nv". Save the xorg.conf (in pico CTRL+O) and use the command "init 5" to boot in graphical mode...

---

### Post by kulikov on 2007-11-02
I had the same problem.
After booting kernel from CD I killed gdm and watched xorg.conf. I found that section "Screen" didn't have subsection "Display". So I added it with mode "1024x768". After that restarted gdm, everything was ok.

---

