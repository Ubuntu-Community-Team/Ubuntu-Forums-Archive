---
title: "Ubuntu bootable usb pxe-e61 error"
date: 2011-08-22
forum: Installation &amp; Upgrades
---

### Post by superg33k on 2011-08-22
Hi,

I did something stupid. I want to get Ubuntu on my laptop (portege-r200) so I made a bootable usb, booted it live a few times and it worked fine. So I went for the install. It was taking ages so I stupidly restarted it so I could try again, and it all went downhill from there. After restarting it the usb didn.t work and the laptop has nothing to boot into. So I'm using my girlfriends mac and following these instructions [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download) to remake the bootable usb. But everytime I do I get "PXE-E61: Media test failure, check cable" error.

So far I've checked the downloaded md5 sum so the image is fine. And I tried redownloading it anyway, still same error. I've reset bios to default just incase, still same error. And the usb hardware must be fine cuz the mac see's it everytime and it was working fine before! I tried a different usb port. Btw, the portege doesn't have a cd-rom drive.

To experiment, trying without the usb just gives a blank screen. But formatting the usb and putting it in blank just gives the same error. So my guess is its reading the usb but doesn't see any stuff to boot.

Thanks for any help.

---

### Post by superg33k on 2011-08-22
There is a program available at [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) which created a bootable usb for me. I don't know why the command line instructions didn't work but this did the job fine. Thanks for my awesome helping of me!

---

