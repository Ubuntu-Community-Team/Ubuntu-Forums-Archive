---
title: "Booting from USB problems on HP pavilion zd8000"
date: 2013-01-20
forum: Installation &amp; Upgrades
---

### Post by BeeDeeGee on 2013-01-20
So this laptop is pretty shot, it was purchased sometime in 2004 and a couple years ago I successfully installed ubuntu on a partition with XP on the other. Since then the CD/DVD drive stopped working, so booting from the Ubuntu CD doesn't work, and ubuntu was un installed, now I would like to re-install it as the only OS.

I've created a bootable USB with Universal USB installer, and tested it on my desktop and it boots fine there. I have changed the boot order, and I can see the computer recognizes that the usb is connected but it will not boot. The light on the drive blinks for a few seconds then nothing.

I'm thinking maybe I need to update the USB drivers? But this PC is so slow it's near impossible. Any suggestions?

---

### Post by BeeDeeGee on 2013-01-20
I've just noticed something new while playing in the BIOS. When I go to the boot order menu, and expand the hard drive option, my USB is listed there. But it's listed last, so the hard drive boots before the USB, and I can't change that order. The BIOS is recognizing the USB as a hard drive instead of a floppy like I thought.

---

### Post by Mark Phelps on 2013-01-20
Unfortunately, it's likely that a PC that old does not actually have an option to boot from USB.

Sometimes, they have a one-time boot selection menu that shows up when you press F12 or F8.  If you do that and it works, you will see a list of devices, and if the USB is in the list, you should be able to select it.

If it's not in the list, you are stuck -- as the BIOS does not support booting from USB.

---

### Post by BeeDeeGee on 2013-01-20
I was able to get it to boot from the USB finally. It was recognizing it as a hard drive, and I thought it would see it as a floppy diskette.

I installed the newest Ubuntu, but it runs incredibly slow. I'm currently installing Mint to see if that runs better at all.

---

### Post by BeeDeeGee on 2013-01-20
Mint is incredibly slow as well, I'll try Xubuntu

---

### Post by evamvid on 2013-12-12
That's weird; Ubuntu 12.04 runs really well on mine. Granted, mine probably hasn't been used as much; it's been in storage for a long time. If you have problems with the wireless, I can help... I just finished fixing mine!

---

### Post by evamvid on 2013-12-12
Also, try using the CDROM; that's how I did it, off of an old LiveCD

---

