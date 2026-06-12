---
title: "grub rescue preventing USB boot"
date: 2010-12-15
forum: Installation &amp; Upgrades
---

### Post by elektrykia on 2010-12-15
So earlier today I was running out of space on my regular Windows 7 partition and I played around with extending it.  I ended up somehow deleting grub and messing up my entire system.  I've spent the last 2 hours looking for the answer to this and everyone has been saying to boot from a live disk and fix it that way.

Well, I've tried everything, the only way I can boot right now is via USB and it will NOT allow me to.  I checked on other computers and even re-installed and formatted by external hard drive to try and get it to work and it refuses.  I've changed my BIOS to boot from USB so I have no idea as to why this is happening.

Also, I've tried using the "ls" command to find my partition via "ls (hdX,Y)/" and all of them come up as unknown filesystems.

I have an exam in 6 hours and need to access my notes, so immediate feedback would be more than greatly appreciated.

---

### Post by elektrykia on 2010-12-15
So earlier today I was running out of space on my regular Windows 7  partition and I played around with extending it.  I ended up somehow  deleting grub and messing up my entire system.  I've spent the last 2  hours looking for the answer to this and everyone has been saying to  boot from a live disk and fix it that way.

Well, I've tried everything, the only way I can boot right now is via  USB and it will NOT allow me to.  I checked on other computers and even  re-installed and formatted by external hard drive to try and get it to  work and it refuses.  I've changed my BIOS to boot from USB so I have no  idea as to why this is happening.

Also, I've tried using the "ls" command to find my partition via "ls (hdX,Y)/" and all of them come up as unknown filesystems.

I have an exam in 6 hours and need to access my notes, so immediate feedback would be more than greatly appreciated.

---

### Post by wilee-nilee on 2010-12-15
There is a per-session boot menu key-prompt used like going to the bios at powering on. Mine is f12 yours could be the same or another key, it may say on the screen as it comes on what it is.

If you get booted into Ubuntu do this. So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between.

---

### Post by elektrykia on 2010-12-15
Magically, it made it to a boot menu for Ubuntu, however i get a whole bunch of different code which ends off with this...

(initramfs) Unable to find a medium containing a live file system

And sorry wilee-nilee, what you said I couldn't quite understand, I haven't really had much time to sleep in the last few days so you might have to dumb it down for me.

---

### Post by wilee-nilee on 2010-12-15
> **elektrykia said:**
> Magically, it made it to a boot menu for Ubuntu, however i get a whole bunch of different code which ends off with this...

(initramfs) Unable to find a medium containing a live file system

And sorry wilee-nilee, what you said I couldn't quite understand, I haven't really had much time to sleep in the last few days so you might have to dumb it down for me.

Since you have made so many attempts the bootscript will get to the point. Your computer will boot from a thumb if loaded correctly but you will have to use a key prompt it seems, at power on. Google per-session boot with your computer model and you will probably find it.

You can tell me the model and I will look.

---

### Post by elektrykia on 2010-12-15
Yeah I did that and on the umpteenth time as of 5 minutes ago, it manages to make it to the Ubuntu boot menu, but does not give me the chance to pick an option so I'm assuming its just running off the USB anyways.

It doesn't run a normal version of Ubuntu however, it basically looks like a command prompt and allows for pretty much nothing.

---

### Post by s.fox on 2010-12-15
Please do not create duplicate threads.  Thank you.

Threads Merged.

---

### Post by wilee-nilee on 2010-12-15
> **elektrykia said:**
> Yeah I did that and on the umpteenth time as of 5 minutes ago, it manages to make it to the Ubuntu boot menu, but does not give me the chance to pick an option so I'm assuming its just running off the USB anyways.

It doesn't run a normal version of Ubuntu however, it basically looks like a command prompt and allows for pretty much nothing.

If your seeing the grub menu your not booting the thumb.

---

### Post by elektrykia on 2010-12-15
I'm no longer seeing a grub menu, I thought I made that clear by saying that Ubuntu loaded?

However, no matter which command I choose from that menu (Install to harddrive, run from USB, etc.) I keep getting this message.

(initramfs) Unable to find a medium containing a live file system

---

### Post by wilee-nilee on 2010-12-15
> **elektrykia said:**
> I'm no longer seeing a grub menu, I thought I made that clear by saying that Ubuntu loaded?

However, no matter which command I choose from that menu (Install to harddrive, run from USB, etc.) I keep getting this message.

(initramfs) Unable to find a medium containing a live file system

Okay your stressed out and I have little patience in these sort of situations, I'm going to bed best of luck to you.

---

