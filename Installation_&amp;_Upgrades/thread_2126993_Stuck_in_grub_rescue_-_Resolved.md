---
title: "Stuck in grub rescue - Resolved"
date: 2013-03-18
forum: Installation &amp; Upgrades
---

### Post by UnknownTBeast on 2013-03-18
OK, 99% noob here at any Linux distro. Please keep that in mind while replying.

My computer recently went caput. One of the 4 SSDs I have died (had a RAID 5 array via the mobo). Since I was unable to rebuild the array, I decided to reinstall Windows 7. For reasons beyond me, other things sempt to go wrong setting things back up. So I said screw Windows, so I installed Ubuntu. I had installed it before for a college class, and I liked it. That was v11.04.

Since I wasn't able to burn a DVD with my spare computer, and didn't want to bother doing it via USB, I used my 11.04 over the newer 12.10. Installation was hell I was finally able to install Ubuntu, but grub would not install. When it asked me if I wanted to install it elsewhere, it froze. I assumed it was v1.99 since I read somewhere that is what shipped with 11.04. I booted to the CD again this morning, and while reading found a way to mount that drive with Ubuntu installed on it, and get grub installed. It worked.

So then I decided on taking on the challenge of installing 12.10. I burned the DVD from my now working Ubuntu system and booted to the disk. I choose the Upgrade 11.04 to 12.10 option. Installation went fine (remembered how I did it before with 11.04, that helped) then came the grub install error again. However, this time I was able to choose another device, then something caught my eye. After the 4th SSD failed I had 3 left. The one I was able to install it on was /dev/sdc, but the error message said it failed to install on /dev/sda. Why was it trying to install on the other drive I asked myself. So I chose my drive /dev/sdc. BAM! Right away it said installation was complete and I needed to reboot. I did read while on some other support forum that another user was trying to install grub on another drive, but quickly after he clicked to proceed, it said it fail, and it sempt like it didn't even try. I started to think that it said it installed, but didn't.

So all that leads up to now. I rebooted, and I was sent to the grub rescue console. It seems like the only command that works is 'ls' to show the drives. Then I unplugged all but the one drive that had Ubuntu installed on it. I was going to try and reinstall 12.10 from the start, and since only that one SSD was plugged in, along with the DVD, I figured it would try and install straight to that drive.

Wrong! I can't even boot to the DVD. I get straight to the grub rescue console. Yes, before you ask, I did select the DVD from the boot list. I saw somewhere that provided a list of usable commands for grub rescue console, but the only one I was able to get to work was 'ls' (only tried about 5 though, but command not found was all I got back). I found elsewhere that I could mount that drive, and re-install grub, but 'mount' doesn't work there.

So there you have it. My computer is completely stuck, as am I. Any help would be great.

Thanks,

Randall

---

### Post by UnknownTBeast on 2013-03-18
Oh and just so you see what I see, this is what I see:

error: file not found.
grub resuce> ls
(hd0) (hd0,msdos5) (hd0,msdos1)
grub resuce>

---

### Post by FabulousCabbage on 2013-03-18
I don't know why you cannot boot into the DVD, but you could try using Unetbootin to install Ubuntu onto a USB stick, then boot from the USB stick, because I know for sure that it will not use your current grub configuration to boot.
When prompted, make sure you select "Try Ubuntu without installing", Once you manage to boot Ubuntu, you can install and run the Ubuntu boot repair tool (assuming you have an internet connection), which has fixed every grub problem I've ever had.

Unetbootin:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

Ubuntu Boot-Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by UnknownTBeast on 2013-03-18
Wow, now don't I feel stupid. The disk that I put in to the drive was a blank CD that was labeled "Ubuntu 12.10". I couldn't burn the ISO to that disk because the CD was too small. No wonder why it kept going straight to grub rescue.

I booted back to the LIVE DVD and within terminal got me partitions listed:

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   112471064    56235501   83  Linux
/dev/sda2       112472062   125044735     6286337    5  Extended
/dev/sda5       112472064   125044735     6286336   82  Linux swap / Solaris

Last time I went with "Linux". Not sure what the "Extended" was though, but I am only able to mount /dev/sda1, so I still assume that is the right one. But when I go to run:

sudo grub-install /dev/sda1

I get:

Path `/boot/grub' is not readable by GRUB on boot. Installation is impossible. Aborting.

Now that I was able to boot, at least to the DVD, I will try the repair tool.

---

### Post by UnknownTBeast on 2013-03-18
Thank you for referring me to the repair tool. Worked wonderfully.

---

### Post by FabulousCabbage on 2013-03-19
No problem, glad i could help.

---

