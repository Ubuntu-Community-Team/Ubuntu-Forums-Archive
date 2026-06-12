---
title: "blank screen at boot"
date: 2011-01-26
forum: Installation &amp; Upgrades
---

### Post by paulof on 2011-01-26
I'm a linux weakling. I've just did a complete install of 64 bit ubuntu 10.10 on a dell with a xeon processor and 4-disc RAID (controlled by bios). [previously had RHEL5]. I got no error messages during the installation and the OS runs fine from the cd. But when i try to boot from the hard disc i end up with a blank screen. I get a little of bios information scrolling up - it detects the RAID, but just when I think it should be loading the OS, I get a little blinking cursor for a few seconds and then the monitor tells me  that there is no signal coming from the computer. I see no harddrive activity.
This computer only has dvi outputs, and I've seen some posts on the web about problems with ubuntu and dvi - but as I said, there's no problem when running from cd. I've also seen that people had problems with RAID, but it seems to be related to software RAID (which I don't think I have...)
I don't know whether its a video problem, or a boot problem. Any help would be appreciated.
P

---

### Post by gordintoronto on 2011-01-26
Have a look at this:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by IWantFroyo on 2011-01-26
Some hard drive stuff might be conflicting. Try booting off GParted and wiping your hard drive. Alternately, it might be boot options like gordintoronto posted.

---

### Post by Jazzmaster94 on 2011-01-26
The cause could be your graphics card.  If you have an outdated ATI card (Radeon xxxx or Radeon Xyyyy series cards are affected) you may need to disable Kernel Mode Setting.  At boot you need to temporarily change the Boot Parameters in GRUB to add "nomodeset".  Once you're in Ubuntu, you will need to change your GRUB configuration file to add "nomodeset" to your boot parameters permanently.  If I were you I would search "boot options" at help.ubuntu.com to find the correct procedure.  I have used "nomodeset" to fix an issue with my own graphics card causing these issues.

---

### Post by paulof on 2011-01-27
Solved, thanks. it was a graphics problem, and putting nonodeset in the grub configuration file did the trick.
In case it's useful information to anyone, the graphics card is described as
256 MB Quadro NVIDIA NVS 295 - 2 DP (ULGA9)
P

---

