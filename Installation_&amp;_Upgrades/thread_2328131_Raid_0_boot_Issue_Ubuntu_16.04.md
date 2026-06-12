---
title: "Raid 0 boot Issue Ubuntu 16.04"
date: 2016-06-17
forum: Installation &amp; Upgrades
---

### Post by maybememe on 2016-06-17
Hi guys, 

I have an Acer Aspire S7 ultrabook with two 128gb SSD's and bios controlled raid mode does not seem disable-able. 

So I figured out how to install Ubuntu Via raid 0 by following this guide on page 18. 

[http://dl.fullcirclemagazine.org/issue104_en.pdf](http://dl.fullcirclemagazine.org/issue104_en.pdf)

It was working OK, then for a moment would only boot to a blank underscore blinking.
I shut it off and on and it booted OK after that.

Now weeks or so later it's only booting to the blank underscore character blinking infinetly. 
Nothing I do now will help. 

I tried holding down shift at boot, yet no advanced grub options come up. I have verified all of the raid partitions are still intact via a live usb.
I also generated the following boot info and uploaded to paste bin via boot-repair

[http://paste2.org/YPAKvCKI](http://paste2.org/YPAKvCKI)

Can anyone help?

---

### Post by maybememe on 2016-06-28
Update: The system boots OK when I load first from what appears to be the Live USB thumb drive I used to first install the raid setup from. 
It loads the two SSD's configured in Raid as one striped partition, not the actual Live environment on the USB.

---

### Post by oldfred on 2016-06-28
Do not know RAID, but a couple of other S7's. Yours now seems to be a BIOS install, not UEFI.

 Acer S7 14.04 & Windows 8.1 RAID
[http://askubuntu.com/questions/590644/install-ubuntu-14-04-2-lts-alongside-windows-8-1-dual-boot-on-raid-acer-s7-quest](http://askubuntu.com/questions/590644/install-ubuntu-14-04-2-lts-alongside-windows-8-1-dual-boot-on-raid-acer-s7-quest)
acer aspire s7 Dual SSD RAID - [SOLVED] Installed Ubuntu on Pre- UEFI Win 
[http://ubuntuforums.org/showthread.php?t=2240043](http://ubuntuforums.org/showthread.php?t=2240043)
Acer Aspire S7 can't install ubuntu - UltraBook erased RAID meta-data
[http://ubuntuforums.org/showthread.php?t=2121187](http://ubuntuforums.org/showthread.php?t=2121187)

---

### Post by maybememe on 2016-07-18
Thanks for your reply, and to clarify, I have already installed Ubuntu 16.04 via Raid 0 by flipping legacy mode on and EFI off. 

The install initially worked fine. Then intermittently 2-3x would only boot to a black background and blinking underscore, I'd power cycle and it would be okay after several tries. 

Then I noticed I could boot no problem via sdc1 which is an adata 32gb flash drive I built a USB windows 10 install onto with  Linux Live USB creator. It contains GRUB and so when I hit fn+f12 to change the boot to occur from the USB drive instead of HD0 / sda1 it works. 

I have been attempting to utilize boot-repair to fix the situation, yet it hasn't worked no matter what advanced config I try. 

I have generated a boot config report to pastebin here for analysis: 
[http://paste2.org/ehffHNC8](http://paste2.org/ehffHNC8)

It has noted that...

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99-2.00)
    Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of 
                       sda1 and looks at sector 281538 of the same hard drive 
                       for core.img, but core.img can not be found at this 
                       location.
    Operating System:  
    Boot files:        /grub/grub.cfg


I suspect the error is in core.img not being found, yet am not sure how to fix it?

---

### Post by maybememe on 2016-07-18
So I ran the grub reinstall command manually on sda, that reinstalled grub but still found no kernels for loading. So I reran boot-repair and with grub on sda now it knew what to do this time it appears. I can now boot to Ubuntu.

---

