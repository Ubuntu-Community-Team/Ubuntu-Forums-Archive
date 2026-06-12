---
title: "Need assistance with full installation to external hard drive"
date: 2018-07-18
forum: Installation &amp; Upgrades
---

### Post by shadarack on 2018-07-18
I have a Dell Chromebook 11 with Ubuntu installed onto it, but it only has a 16 GB SSD, which is really just too small for me. I was recently gifted a much larger compatible SSD to put in this thing, and need to install Ubuntu on it. Now here's the thing - finances are tight for me - which is why I have an older model Chromebook instead of something much more suitable. I do have a rather nifty piece of hardware that allows me to mount sata drives as an external USB drive.

Is there some way I can install Ubuntu to the new SSD while it is hooked up externally, and then physically install it into the chromebook? This thing is really tricky to get to boot to a live USB. Any advice(other than buy a real computer!) would be greatly appreciated.

---

### Post by TheFu on 2018-07-18
I've swapped out 16G -->64G-->120G SSDs in my chromebook. I used dd (really ddrescue) to clone the entire disk onto the newer ones. When the 120G failed, I moved back onto the 64G. The only trick is that  you need to boot off a flash drive so sda isn't active during the dd process.

If you post the URL to boot info (there's a script), then more detailed instructions can be provided.

But really the best way to do this is to use your normal backup and restore methods.  If you don't have one, make it now, while there isn't anything at risk. Be certain to test it.

---

### Post by shadarack on 2018-07-18
Hmmmm. Sounds like I might just have to knuckle down and figure out how to get this silly thing to boot from USB after all...

---

### Post by C.S.Cameron on 2018-07-18
Clone, (dd), the 16GB drive to the larger drive using another computer.

---

### Post by TheFu on 2018-07-18
> **shadarack said:**
> Hmmmm. Sounds like I might just have to knuckle down and figure out how to get this silly thing to boot from USB after all...

[https://mrchromebox.tech/#devices](https://mrchromebox.tech/#devices) says some Dell 11's have legacy boot support, so USB boot shouldn't be hard. You didn't say which model, but the device table has some.

---

### Post by shadarack on 2018-07-19
It does indeed have Lagacy boot, and in fact that is how I got Ubuntu to run on it to begin with. I did attempt and failed to get a live USB to boot on it using Legacy boot, and ended up using MrChromeBox to install Ubuntu.

I was just hoping someone knew an easy way to install to USB in such a way I could just do that, then swap the drives, but no luck it seems.

---

### Post by shadarack on 2018-07-19
> **C.S.Cameron said:**
> Clone, (dd), the 16GB drive to the larger drive using another computer.

Yeah, don't have another computer.

---

### Post by C.S.Cameron on 2018-07-20
There are various ways to create a small partition on the 16 GB SSD and install puppy on that, (runs in RAM).
The Puppy OS running in RAM, has all the tools you need to clone the 16 GB SSD to the much larger SSD.

---

