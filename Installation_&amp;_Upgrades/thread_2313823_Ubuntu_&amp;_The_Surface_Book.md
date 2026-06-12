---
title: "Ubuntu &amp; The Surface Book"
date: 2016-02-16
forum: Installation &amp; Upgrades
---

### Post by Denakee on 2016-02-16
So.... I had ubuntu 15.10 installed on my surface book for about 4 months now. All was good but then I decided to upgrade to 16.04. Everything went down the drain. After re-installing windows, I tried to, once again, partition off my drive and install ubuntu. However, this time, no matter how I configure secure boot and rapid boot, I can't get Grub to show up. I've tried installing ubuntu over 6 times so far and still no luck. I'm at a loss for what to do now so I'm starting to post around for assistance. If you have any ideas as to something I missed or another way to boot then please let me know.

---

### Post by grahammechanical on 2016-02-16
Boot Repair?

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Pull off the Bootinfo summary report. It will be stored online and you will be given a URL address to where the report is stored. Post the URL in your thread and then we will have a better idea of the situation. Boot Repair will also offer to fix boot problems but let us have a look at the report first.

Also, I am not familiar with "went down the drain" as a symptom of an OS not working properly. You might have had better success trying to fix what was wrong. Ubuntu 16.04 is not yet released. So you would have upgraded to a pre-release version. With pre-release (development) versions things often get fixed by updating daily.

With any upgrade to a newer version of Ubuntu we need to revert to using a proprietary video driver, revert the desktop to as close to default as possible. We do these things to lessen the risk of things going down the drain, as you say.

I have been running 16.04 since the beginning of it 26 week development period back in October. I find it very stable. But I would never upgrade my only install of Ubuntu to the next release of Ubuntu until it has been released. I would rather dual boot with the development version.

Regards.

---

### Post by Denakee on 2016-02-16
Ah, what I meant by 'went down the drain' is the upgrade partially completed leaving mostly everything broken. I couldn't even use apt-get correctly and the boots were completely broken. Then I accidentally wiped out my windows partition while re-installing ubuntu.

As for the boot info... [http://paste.ubuntu.com/15092336/](http://paste.ubuntu.com/15092336/)

And, if it means anything to you... Whenever I run boot repair, it repeatedly tells me "Filesystem repair requires to unmount partitions. Please close all your programs. Then close this window." There are no other windows open when I run it.

Edit: I forgot to mention that secure boot was disabled when I ran boot-repair.

Edit 2: I tried booting through grub command line off a live-usb following the instructions found here under "Appendix: Manually Booting Ubuntu": [http://blog.davidelner.com/dual-booting-ubuntu-14-10-on-the-surface-pro-3/](http://blog.davidelner.com/dual-booting-ubuntu-14-10-on-the-surface-pro-3/)
No success.

---

