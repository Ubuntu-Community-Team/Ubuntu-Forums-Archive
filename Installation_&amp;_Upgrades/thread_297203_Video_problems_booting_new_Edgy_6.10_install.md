---
title: "Video problems booting new Edgy 6.10 install"
date: 2006-11-10
forum: Installation &amp; Upgrades
---

### Post by willywag on 2006-11-10
Hey folks. I've just installed from an x86 64-bit alternative-install CD I burned from a downloaded image. The install went fine, but my video cuts out whenever I try to boot Ubuntu. 

After selecting it in GRUB, I get a grey and white Ubuntu logo with a dark grey progress bar and no text. When the progress bar fills, the logo disappears and a blinking cursor appears for a moment in the corner; then the video cuts out entirely and my monitor displays "NO SIGNAL". 

I've seen some on this forum offer advice in the form of various commands to add to the GRUB menu entry, such as "noapic", but I'm having trouble with that too. I've never used GRUB before, and either I'm missing something painfully obvious or I'm just sleep-deprived. I'm able to edit the entries in the GRUB menu, but when I press "b" to boot, my system restarts entirely, and just takes me back to GRUB again. Any changes I've made to the boot commands have disappeared.

Can anyone help me out with either issue or both? Thanks in advance.

Specs
-----
CPU: AMD Athlon64 "NewCastle" 3200+ (2.2GHz)
MB: Asus K8V SE Deluxe
RAM: 768MB
Video: ATI Radeon X850 256MB (AGP)
Audio: Creative SB Audigy 2
Drives: 100 GB Maxtor 6L100P0 (pre-existing WinXP Pro install)
         40 GB Maxtor 6E040L0 (new Ubuntu Edgy 6.10 install)
        DVD-RW DRW-6S160H

---

### Post by ReaderRat on 2006-11-10
Have you tried booting in Recovery Mode to fix it? 
Or run this code to set up video?
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
```
sudo dpkg-reconfigure xserver-xorg
```
You will need to get the most recent ATI video driver

ATI Video - How to install the drivers
          **[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)**

---

### Post by ryan on 2006-11-16
> **ReaderRat said:**
> Have you tried booting in Recovery Mode to fix it? 
Or run this code to set up video?
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
```
sudo dpkg-reconfigure xserver-xorg
```
You will need to get the most recent ATI video driver

ATI Video - How to install the drivers
          **[http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)**

I had something similar happen. I was trying to do a clean install on top of a Dapper > Edgy upgrade. Which was not working so well. I got to a certain point and then I got a message that Xorg.conf was whacked and the installation would go no further. I figured it might be the "ati" driver that was set in Xorg.conf and tryed to change it but couldn't or the change wouldn't take. I guess since there was already a Edgy install it checked for the various conf files to see what was there and then tryed to start the X server according to the "xorg.conf". I would still like to reinstall so I was thinking that before I shut down I would edit Xorg.conf to something vanilla like change "ati" for "vesa" in the driver section and hope that the install would go without any problems. Any thoughts on this ? Does this seem like a good approach to get past the "xorg" weirdness ?

---

