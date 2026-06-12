---
title: "Error on Install from USB Drive!"
date: 2011-02-20
forum: Installation &amp; Upgrades
---

### Post by Ralm on 2011-02-20
Hi all,
After being using Windows server for a bit, I was to try Ubuntu server. I  saw the bootable USB drive, so I took that option ( Since I dont have CDs at home XD). I used the Universal-USB-Installer-1.8.3.4 (from Ubuntu website) and used the ISO image from Ubuntu website ( ubuntu-10.10-server-amd64.iso ).

Everything was running fine, I was able to choose Language, Location, Keyboard layout, then the instalation did a Hardware Scan, start loading some files then this:

--------------------------------| [!!] Load installer components from CD |--------------------------
There was a problem reading data from the CD-ROM. Please make sure it is in the drive. If retrying does not work, you should check the integrity of your CD-ROM.

Failed to copy file from CD-ROM. Retry?

<yes>                                                                                           <no>

-------------------------------------------------

So, I was using only a USB pen Drive, no CD-Rom.
Any tip??

Thanks.

P.S.: Im using a HP Compaq 6720s Laptop.

---

### Post by YellowHammer on 2011-02-20
I was doing the same thing today, and got exactly the same results.  I couldn't solve the problem, so I had to burn the ISO to CDROM.  Kinda sucks, because I didn't have a CD Drive installed when I started this project.

---

### Post by Hakunka-Matata on 2011-02-20
CD-ROM -- USB same thing.  Appears that something is not right on the USB stick.  Many people have trouble at first with making a good USB Install stick.  I've had good luck with unetbootin, [http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/")

---

### Post by Ralm on 2011-02-20
I tried with that program, and to install on USB drive no problem.

When I tried to install I choose default, Then in the same place ( after the Hardware scan), I got this:

-------------------| [!!] Detect and mount CD-ROM |------------------------------------
Your installation CD-ROM coudn't be mounted. This probably means that the CD-ROM was not in the drive. If so you can insert and try again.

Try again to mount the CD-ROM?

<Yes>                                                                            <No>

------------------------------------------------------------------------------------------------

Any tips??

Thanks

---

### Post by Ralm on 2011-02-21
Ok People, 
I just had to bought a CD ( the only one in months).
And its working.

One other very funny fact. 

If you burn the Ubuntu Image on a CD-Rom works, but if you burn it on a DvD it doesnt LOL what? yeah, dont know. XD

---

### Post by Quackers on 2011-02-21
That's odd. I've used a dvd or two in the past and they've been fine. The dvd type could be a problem (-R,+R, etc)

---

### Post by Ralm on 2011-02-21
I know. I used +R and it just doesnt Boot. (note: That DvD was burned in the same drive XD).

Anyway, Im trying to set up the instalation at the momment, Is taking forever to Erase a existing partition ( 32GB LOOL).

---

### Post by Dutch70 on 2011-02-21
> **Ralm said:**
> I know. I used +R and it just doesnt Boot. (note: That DvD was burned in the same drive XD).

Anyway, Im trying to set up the instalation at the momment, Is taking forever to Erase a existing partition ( 32GB LOOL).

Yeah, it reads/runs much slower from a cd/dvd that it does a usb stick, or your hdd of course.

As far as cd's go, I think -R is what you need.

---

### Post by Ralm on 2011-02-21
It shouldnt make any diference, the drive just need to support it. IF was the same drive that record the DvD it should boot with it, but it doesnst. I dont care now. I bought CDs and it0s working.

---

### Post by whizz on 2011-04-23
I'm sorry I'm replying to such an old thread, but I came across this topic when having the same problem, so I though I'd post the solution here.

Three files in the "\pool\main\l\linux" folder on the usb stick have incorrect naming:

firewire-core-modules-2.6.35-22-generic-di_2.6.35-22.33_amd64.ud
fs-secondary-modules-2.6.35-22-generic-di_2.6.35-22.33_amd64.ude
pcmcia-storage-modules-2.6.35-22-generic-di_2.6.35-22.33_amd64.u

They should read:

firewire-core-modules-2.6.35-22-generic-di_2.6.35-22.33_amd64.udeb
fs-secondary-modules-2.6.35-22-generic-di_2.6.35-22.33_amd64.udeb
pcmcia-storage-modules-2.6.35-22-generic-di_2.6.35-22.33_amd64.udeb

Apparently the filename is truncated to 64 characters. This seems to happen when the USB stick was created using the Universal-USB-Installer-1.8.3.4 running on Windows 7.

---

