---
title: "Recovery on USB"
date: 2010-11-01
forum: Installation &amp; Upgrades
---

### Post by Jwood725 on 2010-11-01
I have both Ubuntu and Windows Vista on my hard drive as a dual-boot. Apparently when I installed Ubuntu it screwed up my Vista partition and made it impossible to boot into. I get an error like this: 

"Cannot find file:Z:\D2D\Images\*.WSI when trying to determine UI language"

Now the problem is that I cannot use a recovery cd, due to the fact that the cd reader in my laptop is broken. I have however downloaded a recovery.iso.

Is it possible to mount that .iso to a USB thumbdrive and use it to recover my vista? If so please explain how or provide a link. I have looked all over the internet and forums trying to recover my Vista please help.

Thank you,
   Joshua

---

### Post by Jahid65 on 2010-11-01
log into Ubuntu. Open terminal from Application> Accessories & type
```
sudo update-grub
```
you will be prompt for password. Give your password (password won't show). Then restart your PC & see if you can log into windows.

---

### Post by Jwood725 on 2010-11-02
> **Jahid65 said:**
> log into Ubuntu. Open terminal from Application> Accessories & type
```
sudo update-grub
```
you will be prompt for password. Give your password (password won't show). Then restart your PC & see if you can log into windows.

Well Jahid65 this did not work. Actually I didn't think it would, I'm pretty sure I've tried it before. I've tried so much that I can't remember what all I've done. I've been told and read a number of forums that say I will have to us an actually recovery cd. 

But like I said in above post that, that is a problem due to a broken cd drive. If you know how to mount a vista recovery to usb that would be great. Or if you have anymore things to try I am more than willing to try and learn.

Thanks, 
    Joshua

---

