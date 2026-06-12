---
title: "Ubuntu 10.04 beta 2 live cd won't boot"
date: 2010-04-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by pmalvr on 2010-04-10
Hi,

I have a pc with an nvidia graphics driver and just like with the alpha's and beta 1 live cd's, i cannot boot into Ubuntu with the new beta 2 live cd. It hangs up at the new boot logo animation.

Does anyone else has the same problem?

Thanks.

---

### Post by motsteve on 2010-04-10
It sounds like the xorg.conf file is messed up, but that is on the CD and I don't have enough expertise to tell you have to fix that.  Do you get a menu of selections when boot off of the CD or does it never get that far?

---

### Post by pmalvr on 2010-04-10
> **motsteve said:**
> It sounds like the xorg.conf file is messed up, but that is on the CD and I don't have enough expertise to tell you have to fix that.  Do you get a menu of selections when boot off of the CD or does it never get that far?

When I boot from the Live CD I can change languages and chose how to install Ubuntu 10.04, after that, the content of the cd is loaded, the ubuntu logo is displayed, but at some point it stops, nothing happens.

---

### Post by cdude42 on 2010-04-10
it happened to my bro. Just redownload and chek it for defects before you try to install.

---

### Post by pmalvr on 2010-04-10
> **cdude42 said:**
> it happened to my bro. Just redownload and chek it for defects before you try to install.

I already did that and it continues to stop at boot. How can I submit this bug and where ? thanks

---

### Post by howefield on 2010-04-10
Try removing quiet splash-- from the boot line. Worked for me.

When you boot the CD, select the language, then press F6 and escape. Remove from the end of the line... quiet splash--  I might be wrong with the exact wording but it should be obvious.

I was able to boot and install after that. Of course, I had the same issue on booting from the hard disk with the fresh install, fixed by booting recovery mode, selecting root terminal, logging in to desktop and updating graphics drivers.

Now seems fine apart from a grotty looking splash screen.

PS. This isn't a topic for General Help, should be posted in the Lucid forum.

---

### Post by JHCKX on 2010-04-12
> **pmalvr said:**
> Hi,

I have a pc with an nvidia graphics driver and just like with the alpha's and beta 1 live cd's, i cannot boot into Ubuntu with the new beta 2 live cd. It hangs up at the new boot logo animation.

Does anyone else has the same problem?

Thanks.

I have a similar problem but I have an ATI graphics driver (a radeon 200M on a Packard Bell mz35). I submitted a bug report a few days ago, see [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/560248](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/560248)

On two attempts, I couldn't get to the language selection screen, all I got was a white square. On my third try, I could see the language selection menu but it was frozen. I could open a console window though with Ctrl-alt-F1, can you do that?

---

### Post by alanrr_sr on 2010-04-13
Same here. The ubuntu logo with sequenced dots stays forever. After pressing esc I can see messages about chroot/debconf-communicate.

---

### Post by Cringer on 2010-04-13
It is hanging for me as well. Pressing ESC doesn't do anything for me though, only thing I can do is power down. I will try howefield's suggestion.

edit: howefield's suggestion works for me, hit F6, esc, then take off quiet splash-- before booting.

---

### Post by alanrr_sr on 2010-04-14
> **alanrr_sr said:**
> Same here. The ubuntu logo with sequenced dots stays forever. After pressing esc I can see messages about chroot/debconf-communicate.

The problem was the cd-r unit.... :lolflag:

---

### Post by basilwatson on 2010-04-19
happening to me as well 

tried booting off a usb stick and from live CD same problem 

Usb stick says boot error , Cd hangs on quiet splash 

I also have Nvidia graphics card for what is worth 

Stephen

---

### Post by perika on 2010-04-19
Hello, I have the same problem! Hangs on the Ubuntu screen. Also Nvidia.
/Per

---

### Post by digitalbrain on 2010-04-19
You may download the daily (updated) versions from here: [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

