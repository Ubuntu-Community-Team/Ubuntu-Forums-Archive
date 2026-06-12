---
title: "No normal boot after upgrading from 16.04 to 18.04"
date: 2018-08-24
forum: Installation &amp; Upgrades
---

### Post by danielsender on 2018-08-24
I have a Dell Dimension 1100 (32b) that had 16.04 running perfectly. Given that I also have other 32b machines that I was able to successfully do the same upgrade I decided to do the same on this one. However after the process was completed with the success message I cannot boot it normally, after a fairly long time I catch a message line that the volume sda is clean and it would go on recovery mode and within that I cannot execute any of the options listed in that menu such as Network, FailsafeX, etc. So these are the steps that I did:


[LIST=1]
[*=1]With a Boot Repair CD I re-installed grub just in case,
[*=1]With a live CD I mounted /dev, /proc, /sys and /run to did a chroot and:
[/LIST]
[INDENT=2]a. dpkg --configure -a (it returned immediately without any action shown)
b. apt update && apt upgrade (it installed some updates, apparently successfully)[/INDENT]



I'm attaching some log files of the last boot attempt, I retrieved these with the live CD.
[INDENT]Many thanks in advance.[/INDENT]
[INDENT]
[/INDENT]

---

### Post by oldfred on 2018-08-25
Post link to summary report that Boot-Repair gives.
If you did not save it, just rerun report & post that link.

---

### Post by danielsender on 2018-08-25
[http://paste.ubuntu.com/p/mP2FQqwTqv/](http://paste.ubuntu.com/p/mP2FQqwTqv/)

Thanks

---

### Post by justen_m on 2018-08-25
Similar problem on a 32-bit system. Ubuntu asked if I wanted to upgrade (from 16.04.5LTS to 18.04), I clicked yes, and system bricked.  Do you undertand? I clicked yes to upgrade, and you destroyed my system. 

Screw you Ubuntu. I had to wipe the system and re-install 16.04.5LTS from an image on my server.

---

### Post by oldfred on 2018-08-25
+1 for justen_m having good backups.

While I believe you can upgrade a 32 bit system, it is being discontinued with standard Ubuntu. The lighter weight flavors may still offer 32 bit for a while. Any system that has to have 32 bit, is so limited that full Ubuntu will not run well with it.  System is either very old a a very lightweight tablet type system.

In your fstab you have these. Do they still exist as it used to be that boot would try and fail, but ask if you wanted to still boot. But now it just seems to fail if any entry in fstab is not correct.
If not current, comment or delete these lines.

> 
# /dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/VolGroup00/LogVol00        /oldbebita  ext3    defaults 1 1
# This is NFS stuff (11/30/2011)
/home    /export/users    none bind    0    0


---

### Post by danielsender on 2018-08-25
> **oldfred said:**
> +1 for justen_m having good backups.

While I believe you can upgrade a 32 bit system, it is being discontinued with standard Ubuntu. The lighter weight flavors may still offer 32 bit for a while. Any system that has to have 32 bit, is so limited that full Ubuntu will not run well with it.  System is either very old a a very lightweight tablet type system.

In your fstab you have these. Do they still exist as it used to be that boot would try and fail, but ask if you wanted to still boot. But now it just seems to fail if any entry in fstab is not correct.
If not current, comment or delete these lines.

I commented out those two lines in fstab but unfortunately the behaviour is still the same, that is: it starts with the red screen with the ubuntu word and the five dots roll to red for a while until they stop rolling, after about 5 minutes the screen goes black, with the monitor LED going from green to amber, possibly indicating that there is no video being received.

---

### Post by oldfred on 2018-08-25
What video card/chip?
If nVidia, you should always uninstall proprietary drivers before upgrade.
And if you have any ppas you have to remove them, or upgrade does not complete if any ppa is not available with new version.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Did you have any other boot parameters set?
If you actually need the now very old 304.xx nVidia driver I believe it is not supported with 18.04.
Not sure if nouveau then works or also needs nomodeset.
My somewhat newer 620gt seems to be same whether I have nVidia driver or not.

---

### Post by danielsender on 2018-08-25
> **oldfred said:**
> What video card/chip?
If nVidia, you should always uninstall proprietary drivers before upgrade.
And if you have any ppas you have to remove them, or upgrade does not complete if any ppa is not available with new version.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Did you have any other boot parameters set?
If you actually need the now very old 304.xx nVidia driver I believe it is not supported with 18.04.
Not sure if nouveau then works or also needs nomodeset.
My somewhat newer 620gt seems to be same whether I have nVidia driver or not.
This machine has integrated graphic system "Integrated Intel Extreme Graphics 2", so the Nvidia driver was never used. I tried entering nomodeset at boot time but it still didn't boot normally, however I was able to go into FailsafeX, and I retrieved the /etc/default/grub file that I attach here.
```
# If you change this file, run 'update-grub' afterwards to update# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"


# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console


# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480


# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true


# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"


# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

---

### Post by oldfred on 2018-08-25
Frankly, if 16.04 ran well I would have stayed with it.
Each update to standard Ubuntu assumes newer hardware and is designed to work well with that newer hard ware. 
Or lighter weight flavors may still work.

Old hardware, post has been updated.
[https://ubuntuforums.org/showthread.php?t=2130640](https://ubuntuforums.org/showthread.php?t=2130640)

       Ubuntu Budgie, Ubuntu MATE, and now Ubuntu Studio have all announced they are ending their 32-bit/i386 images as of the next release, Ubuntu 18.10.
Proposed end of Ubuntu i386  32-bit images 
[https://ubuntuforums.org/showthread.php?t=2312451](https://ubuntuforums.org/showthread.php?t=2312451)
Lubuntu still i386 for 18.04 
[https://www.reddit.com/r/Lubuntu/comments/4qy25y/is_lubuntu_dropping_32bit_support/](https://www.reddit.com/r/Lubuntu/comments/4qy25y/is_lubuntu_dropping_32bit_support/)
NVIDIA To Stop Offering 32-bit Driver Support
[https://www.phoronix.com/scan.php?page=news_item&px=32-bit-NVIDIA-Drop-Dropping](https://www.phoronix.com/scan.php?page=news_item&px=32-bit-NVIDIA-Drop-Dropping)
he upcoming NVIDIA 390.xx drivers will be the last to offer 32-bit support,

---

### Post by danielsender on 2018-08-25
I always upgrade, and in this case I first tried with an even older machine (Inspiron) and the upgrade went well. In any case I should have seen that we are getting to the end of the road of 32 bit machines so it would have been wise not to upgrade.

However I made some progress for this particular case, I had an old graphic card (Matrox MGA 1064SG) that I plugged into a PCI socket, and now if I enter nomodeset at boot time, it will boot pretty normally. The resolution is not what the monitor can do, so I assume that there must be some Matrox driver, but I don't find it in synaptic.

---

### Post by oldfred on 2018-08-25
Do not know if your driver was in this group.

       Ubuntu 17.04 Drops DRM Support For Old VIA, SiS, R128 GPUs
[https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-17.04-Slimmer-DRM](https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-17.04-Slimmer-DRM)
The developer wrote, "This and a handful of other DRM drivers got disabled because they present insecure APIs to userspace. 
SIS driver see post #9 by Temüjin
[https://ubuntuforums.org/showthread.php?t=2371684](https://ubuntuforums.org/showthread.php?t=2371684)
The stock kernel of Ubuntu 17.04 is doing away with Direct Rendering Manager (DRM) support for a number of ancient graphics processors.
3Dfx Banshee/Voodoo3+, ATI Rage 128, Matrox G200/G400, SIS, VIA, and Savage hardware
This was done because they expose insecure APIs to user-space. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1680276](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1680276)
[https://www.phoronix.com/scan.php?page=news_item&px=ATI-RAGE-128-DDX-6.11.0](https://www.phoronix.com/scan.php?page=news_item&px=ATI-RAGE-128-DDX-6.11.0)

---

### Post by mörgæs on 2018-08-26
> **oldfred said:**
> 

While I believe you can upgrade a 32 bit system, it is being discontinued with standard Ubuntu.

Well, the 32 bit Ubuntu ISO is not created any more but all 32 bit software in the repositories is still there. One can install a minimal 32 bit 18.04 ISO and then add the Ubuntu desktop from the repositories. 

> **oldfred said:**
> 
Any system that has to have 32 bit, is so limited that full Ubuntu will not run well with it.

Yes, a lighter Buntu will perform better.

---

### Post by justen_m on 2018-08-26
LOL, the system I tried to upgrade was a 10 year old netbook with an Atom N270 processor. 32-bit, 1.6GHz, 1.5Gigs of RAM. I've got four other systems running 18.04.1LTS fine. They're all 64-bit.

> [COLOR=#000000]Frankly, if 16.04 ran well I would have stayed with it.
Yeah, that's the plan now. ;)
[/COLOR]

---

### Post by mörgæs on 2018-08-27
> **justen_m said:**
> Ubuntu asked if I wanted to upgrade (from 16.04.5LTS to 18.04), I clicked yes, and system bricked.

> **justen_m said:**
> I had to wipe the system and re-install 16.04.5LTS from an image on my server.

If you can reinstall then the system is not bricked.

How does a fresh install of 18.04.1 (beginning from the minimal ISO) behave?

---

### Post by danielsender on 2018-08-28
I think that the problem I'm having has been nailed down to an inept integrated graphic card. When I inserted a Matrox card, the system booted almost normally except for the screen resolution that I assume is a driver problem. I just ordered another card from Ebay that has the Nvidia chipset, that hopefully will work. But the interesting part is that I also upgraded from 16.04 to 18.04 to an even older machine, an Inspiron that it doesn't even have the SSE2 code, but it works just perfectly with 18.04. Unfortunately, the most common browsers, Firefox, Chrome, etc. don't work with this machine, but a version of PaleMoon does.

---

### Post by mörgæs on 2018-08-28
Would this be of interest to you?

[https://ubuntuforums.org/showthread.php?t=2130640&page=20&p=13793704&viewfull=1#post13793704](https://ubuntuforums.org/showthread.php?t=2130640&page=20&p=13793704&viewfull=1#post13793704)

---

### Post by danielsender on 2018-08-28
Even before I upgraded from 16.04 to 18.04 on that machine without SSE2 I couldn't use the most popular browsers such as Chrome/ium, Firefox, etc. But there is a group of people who generated a version of Firefox/PaleMoon that works on machines without SSE2: [https://forum.palemoon.org/viewtopic.php?f=40&t=13530&sid=85903f691cc33017a948b92d8950c368&start=180](https://forum.palemoon.org/viewtopic.php?f=40&t=13530&sid=85903f691cc33017a948b92d8950c368&start=180)

---

### Post by danielsender on 2018-08-30
Finally I narrowed down the problem to the graphic subsystem. This motherboard has an Intel integrated graphic controller 82865G. So I put an old Matrox graphic card that I had. With that, the system boot but without full resolution. Apparently there is no support for Matrox cards. Attempting to 'modprobe' its module mgag200 is refused with the message "invalid argument". So I bought another card on Ebay ($25) with the Nvidia chip set (GeForce FX 5200) and this time I got the full resolution of the monitor. So far, it seems that everything works just fine. More over, it seems faster, probably because of the external card.

Thanks guys for your help.

---

### Post by mörgæs on 2018-08-31
Sounds like a good solution. Memory and GPU upgrades are often worth considering when dealing with old hardware, CPU upgrades less so.

In case other people are following the thread this might give some inspiration:
[https://www.videocardbenchmark.net/low_end_gpus.html](https://www.videocardbenchmark.net/low_end_gpus.html)

Don't be scared by the 'low end' title in the link. Many of the GPU's are useful also by today's standards.

---

### Post by danielsender on 2018-08-31
According to the chart in your link, this card that I got is at the bottom of the rank, but what the heck, my machine is not a Ferrari, but more like a Ford Pinto!

Nice chart.

---

### Post by mörgæs on 2018-09-02
... but even the slowest of the 5200's is clearly above an 82865G.

---

### Post by nfeerdaws on 2018-09-03
nice

---

