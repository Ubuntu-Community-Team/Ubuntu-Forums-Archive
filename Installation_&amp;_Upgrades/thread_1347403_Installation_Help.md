---
title: "Installation Help"
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by jncocontrol on 2009-12-06
I'm not sure what i'm doing wrong here.

I'm trying to install ubuntu with the CD, i put it in my Cd-Rom, restart my computer, i select "install ubuntu", and after that little flashy ubuntu logo stop flashing, It go's blank and i get a alot of errors. I don't know em all, But at the end it says something about smartbox.

What i'm trying to do is get a XP Primary and a Ubuntu Logical Partition going, and i'm getting quite aggrovatted over this.

Any help will be appreciated.

---

### Post by darkod on 2009-12-06
Boot with the cd but before Install Ubuntu use the Try Ubuntu first. It will run it from the cd and it can show driver/incompatibility problems. If that option is getting you to a desktop and working fine (internet, audio, video), then we'll see further.
Often it can be image that got corrupted during download, or during burning the CD (it has to be low speed, not more than 8x, todays CDs go up to 50x). There are various reasons not even connected to ubuntu.
See Try Ubuntu first, and tell us how it goes.

---

### Post by jncocontrol on 2009-12-06
It didn't work.

---

### Post by darkod on 2009-12-06
Well, it either can't work on your hardware which is highly unlikely, or this is a case of corrupted image/cd. If you can try the same image from a bootable usb stick. That will rule out badly burnt cd. Or just try downloading another image and see how that works.

---

### Post by jncocontrol on 2009-12-06
I don't think it's the CD, It was sent to me by Canonical via mail, so, i don't it's corrupted. Plus i got it to work on my computer a few months back when 9.0.4 was out, and had no trouble with it until now.


:confused:

---

### Post by presence1960 on 2009-12-06
> **darkod said:**
> Well, it either can't work on your hardware which is highly unlikely, or this is a case of corrupted image/cd. If you can try the same image from a bootable usb stick. That will rule out badly burnt cd. Or just try downloading another image and see how that works.

Start from scratch...

Did you [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") the downloaded iso prior to burning it to CD? All characters must match exactly or iso is not good. If your iso is no good try downloading via a torrent.

Did you burn it to CD at 4x-8x speed? As darkod mentioned speed is critical. fast speeds are ok for data & music files not an iso image. If one piece of info is incorrect the Cd will not work/install properly if at all. If your burning software does not allow you choose 4x-8x speed see [here]("https://help.ubuntu.com/9.10/switching/installing-burning.html") for Infra Recorder.

Boot from the CD and at the menu select "check disk for defects" prior to trying Ubuntu or installing Ubuntu. If the CD passes this check you are good to go, at least with the CD that is...report back please.

---

### Post by jncocontrol on 2009-12-07
> **presence1960 said:**
> Start from scratch...

Did you [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") the downloaded iso prior to burning it to CD? All characters must match exactly or iso is not good. If your iso is no good try downloading via a torrent.

Did you burn it to CD at 4x-8x speed? As darkod mentioned speed is critical. fast speeds are ok for data & music files not an iso image. If one piece of info is incorrect the Cd will not work/install properly if at all. If your burning software does not allow you choose 4x-8x speed see [here]("https://help.ubuntu.com/9.10/switching/installing-burning.html") for Infra Recorder.

Boot from the CD and at the menu select "check disk for defects" prior to trying Ubuntu or installing Ubuntu. If the CD passes this check you are good to go, at least with the CD that is...report back please.

I check my 9.10 CD for defects and turn out there was nothing wrong. 

After i did that i tried to install it (once again) and gave me a "terminated with status 127" error at the end.

I did read around that it has something to do with hardware. Can anyone confirm this?

And before i forget, here are my specs:

2GIG's of ram
Nvidia 8600 XFX GTS
Intel DG965RY MOBO
Intel duo core 2 processor E8200 (i think).

Any help would be appreciated.

EDIT: once i chose "demo install" i got this repeated error " Mounting /dev/sr0 on /cdrom Failed: Invalid Argument" Any idea on how to fix it?

EDIT 2: i did find a bit of a work around the installation, But really useless. I type in with special boot-load option (F6) and typed in alone side my "demo install" ```
intel_agp.blacklist=yes
```

and right now i'm using 9.10, But i very hardly doubt it's gonna though once i exit and try to boot Ubuntu again.

EDIT 3: I was right, It doesn't work. Any ideas?

---

### Post by jncocontrol on 2009-12-07
.

---

### Post by jncocontrol on 2009-12-07
Sorry for the constant bump, but i really would like some help with this issue of mine.

---

