---
title: "Installtion of 9.04 via 1GB USB Stick"
date: 2013-10-21
forum: Installation &amp; Upgrades
---

### Post by NoFriends on 2013-10-21
Hi Guys,

Haven't been online or used ubuntu for over 1 year, but thought it was time to start using it again and facing my first issue already.

I've trying to install ubuntu 9.04 using 1GB USB Stick and using unetbootin for windows as i want to run ubuntu alongside windows.

This is where the boot is getting stuck

SYSLINUX 4.04 EDD 2011-04-18 Copyright (C) 1994-2011 H. Peter Anvin et al

Please ignore the dates on the error as I've copied the exact error i am getting.

---

### Post by heir4c on 2013-10-21
Don't use 9.04, it's end of live.
Download the 12.04 LTS to install. Support till 2017.

---

### Post by NoFriends on 2013-10-21
> **heir4c said:**
> Don't use 9.04, it's end of live.
Download the 12.04 LTS to install. Support till 2017.

Thanks for the response, i am currently using [COLOR=#000000]unetbootin to download and install 12.04 Live to my USB Stick.

Let's hope this shall work it's been formatted to FAT32 and i'm letting [/COLOR][COLOR=#000000]unetbootin do the rest, what shall i do for the next step 
if i get the same error code if the boot gets stuck on SYSLINUX again ?

Thanks[/COLOR]

---

### Post by heir4c on 2013-10-21
I hope in the first place that it will install on the 1GB usb. I hope it's not to small.
When you have that message probably it is not good set on the usb. I hope it will now go right.
Or you can use a dvd-rw to make a image to boot if you can boot with a dvd. The iso of the new Ubuntu releases are to big for a cd. (unfortunately)

---

### Post by NoFriends on 2013-10-21
> **heir4c said:**
> I hope in the first place that it will install on the 1GB usb. I hope it's not to small.
When you have that message probably it is not good set on the usb. I hope it will now go right.
Or you can use a dvd-rw to make a image to boot if you can boot with a dvd. The iso of the new Ubuntu releases are to big for a cd. (unfortunately)

Just attempted it again using the USB Stick with 12.04 and i still get the message below:

SYSLINUX 4.03 2010-10-22 EDD COPYRIGHT (C) 1994-2010 H. PETER ANVIN ET AL

---

### Post by ubfan1 on 2013-10-21
Did you hash check the downloaded iso with md5sum?  Don't know where the Windows version of md5sum is, google it.  The good hashes are listed at the releases.ubuntu.com site under the names/ MD5DUMS.  That was 12.04.3 you downloaded right?  That has a year's worth of downloaded included over the original 12.04.

---

### Post by NoFriends on 2013-10-21
> **ubfan1 said:**
> Did you hash check the downloaded iso with md5sum?  Don't know where the Windows version of md5sum is, google it.  The good hashes are listed at the releases.ubuntu.com site under the names/ MD5DUMS.  That was 12.04.3 you downloaded right?  That has a year's worth of downloaded included over the original 12.04.

I haven't hash checked it, i have just downloaded md5sum and i yes i have downloaded 12.04.03

---

