---
title: "all live cds boot into unetbootin image I made, weird"
date: 2010-02-23
forum: Installation &amp; Upgrades
---

### Post by v1nsai on 2010-02-23
I used unetbootin to install a custom livecd I made with remastersys to a usb stick.  I wanted to boot it from my hard drive, so I used unetbootin to install it to my hard drive, then reinstalled grub and booted the unetbootin kernel and initrd.  Using unetbootin was the only way to stop getting errors about my ext4 partitions that looped and prevented booting, the initrd image created by unetbootin was skipping that step apparently.

However, now when I try to boot any other live cd, it boots into the desktop of the unetbooin image I made, or at least it appears to.  It looks just like it, but when I try to run anything it throws errors.  

I changed the name of the directory containing all the files, but it still boots into it so I'm guessing this is something that I installed into the MBR with unetbootin.

I've been picking through the unetbootin source to figure out what exactly it puts on there, but I'm not much of a programmer at the moment.  Anyone have any idea what I have done and how to fix it?

---

### Post by v1nsai on 2010-02-23
I always find an answer after I post -_-

Anyway, I ended up nuking my mbr to hell and starting over, it was real simple actually, I just used 
```
dd if=/dev/zero of=/dev/sda bs=446 count=1
```
And then booted a livecd and used it to reinstall grub-pc to the mbr.  Maybe this will help someone, I had to dig through some pretty old threads to find it

---

