---
title: "Intrepid 8.10 &amp; fglrx"
date: 2008-10-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by mojo636 on 2008-10-19
Hi

I have browsed through numerous threads and read the notes about 8.10 on the ubuntu website and have found conflicting stories.
If i install 8.10 on my machine will i be able to use fglrx restricted drivers? Or are they still broken in intrpid?

I am currently runnning a ATI Radeon 9700

Thanks

---

### Post by wgrant on 2008-10-19
> **mojo636 said:**
> Hi

I have browsed through numerous threads and read the notes about 8.10 on the ubuntu website and have found conflicting stories.
If i install 8.10 on my machine will i be able to use fglrx restricted drivers? Or are they still broken in intrpid?

I am currently runnning a ATI Radeon 9700

Thanks

They were fixed just a few days ago. They now work fine.

---

### Post by Saint Angeles on 2008-10-19
so if i upgrade to intrepid now... fglrx will work, or will i have to download the official package from the ati website?

and it works with Xorg 7.4... right?

i'm just very curious because i upgraded in alpha and then when xorg 7.4 came out, i was left with horrible drivers and i had to downgrade to hardy. so before i re-upgrade to intrepid, i wanna be absolutely sure that fglrx will produce direct rendering.

---

### Post by ktp on 2008-10-19
Using it right now...so good to go.

---

### Post by wgrant on 2008-10-19
> **Saint Angeles said:**
> so if i upgrade to intrepid now... fglrx will work, or will i have to download the official package from the ati website?

and it works with Xorg 7.4... right?

i'm just very curious because i upgraded in alpha and then when xorg 7.4 came out, i was left with horrible drivers and i had to downgrade to hardy. so before i re-upgrade to intrepid, i wanna be absolutely sure that fglrx will produce direct rendering.

The restricted driver manager will install them for you. They work with Xorg 7.4, or they wouldn't work at all.

---

### Post by Saint Angeles on 2008-10-19
cool... so i can do that update-manager -d thing?

Is that the right command?

---

### Post by ktp on 2008-10-19
That will work.

---

### Post by kngunn on 2008-10-21
fglrx is a no-go for me with an ATI Mobility Radeon 3650 in a ThinkPad T500.  Just a word to the wise.  I'm still hacking away at it, but I haven't been able to get anything working (in terms of X) with Ibex.

8.04 loads fine, but under 8.10 with 7.4 I'm spinning my wheels.  Trying the RadeonHD driver next...

Oh, and I'm installing from the current alternate CD build to make sure the packages are up-to-date.

Just a warning, but this is the kind of problem we're trying to nail down, right?

---

### Post by Saint Angeles on 2008-10-21
i did the upgrade and everything is working great!

i have an ATI Radeon X1550

---

### Post by Fatalrewind on 2008-10-21
hi ,i have a lifebook s6120 with intel graphics ,the default driver that is running is perfectly fine for the desktop but very slow for games and crashes with other games like 3d chess -i am totaly new to linux and have no idea if theres a better driver to use for games,i am that much of a nubie
that i couldnt even tell you what version of ubuntu i have installed,downloaded the iso a 2 weeks ago.

sorry to post this here if its not aproprete,i dont think i can post on the
main page as i have just registered,cant find the post button.

---

### Post by kngunn on 2008-10-22
SOLVED IT!

> **kngunn said:**
> fglrx is a no-go for me with an ATI Mobility Radeon 3650 in a ThinkPad T500.  Just a word to the wise.  I'm still hacking away at it, but I haven't been able to get anything working (in terms of X) with Ibex.

The ThinkPad T500 has DUAL graphics graphics attached to a single display.  In the BIOS you'll find a display setting for "switchable", "discrete" or "integrated" and one to determine whether or not this should be detectable by the OS.  You need to turn OFF detectable and change "switchable" to "discrete".  Yesterday's Ibex daily (with the new fgrlx driver in it) now works like a champ.

No wonder it was confused about how to load drivers!

---

### Post by SpiritofElijah on 2008-10-22
From what has been said the shut down issues are fixed also? My machine would never shut down itself using the ATI drivers. I had to use the power button or the alternative drivers. So is it fixed as well?

---

### Post by Merovius on 2008-10-22
I tried the ATI drivers for my X1650 Pro and it would not work. Tried it for three days then went back to my 6800xe Nvidia.

---

### Post by kngunn on 2008-10-24
> **SpiritofElijah said:**
> From what has been said the shut down issues are fixed also? My machine would never shut down itself using the ATI drivers. I had to use the power button or the alternative drivers. So is it fixed as well?

My ATI-based ThinkPad T500 is not having any shutdown problems with the current Ibex daily build.

---

### Post by pulpo69 on 2008-10-24
no problems here with fglrx. atiX800 amd64

---

### Post by kcleong on 2008-10-26
My X1600 mobilty isn't working 100%. I've got 2D but 3D and xv-video aren't working.

Quering glxinfo gives a wierd error (same with fglrxinfo):
```
kcleong@kcleong-laptop:~/bin$ glxinfo 
name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  160 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10

```

In xorg log I see this error:
```
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

```

Anybody got a clue why this isn't working?

---

### Post by Yashiro on 2008-10-26
You will need the 8.11 Catalyst to be released to get full functionality back.

---

### Post by kcleong on 2008-10-26
OK, I fixed it. It seemed that a previous fglrx driver was interfering. I removed the fglrx driver thru the restricted hardware drivers tool. After installing the driver in the restricted tool all is fine!

---

### Post by Yashiro on 2008-10-27
What is the output of fglrxinfo with this driver?

---

### Post by Radeky on 2008-10-27
> -ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON X800 XL
OpenGL version string: 2.1.8087 Release

is what I get.

My issue is: [http://ubuntuforums.org/showthread.php?p=6041446#post6041446](http://ubuntuforums.org/showthread.php?p=6041446#post6041446)
basically, I can't get compiz to run on my dual-monitor set up.  Yet, the dual monitors work just fine.

---

### Post by Yashiro on 2008-10-27
Look like there's a proper Ati driver available from the restricted repo then.

That's good news for all the guys with 4xxx hardware.

---

### Post by scheuri on 2008-10-27
Having a Lenovo t400 with (dual) graphics I choose "discrete" at the BIOS and now working with the ATI Mobility Radeon HD 3470.

I installed Intrepid Ibex a few days ago and seem just be lucky enough to get the "good" driver for ATI.

It works so far (desktop), however I have no fancy 3d-stuff on the desktop working.
My only "problem" is that WoW is not working properly (graphic glitches).

So I can confirm that ATI Mobility is working with 8.10 as of today (even a bit earlier).

Cheers
scheuri

---

