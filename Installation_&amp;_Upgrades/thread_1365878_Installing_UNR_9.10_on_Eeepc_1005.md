---
title: "Installing UNR 9.10 on Eeepc 1005"
date: 2009-12-27
forum: Installation &amp; Upgrades
---

### Post by bleepbloop on 2009-12-27
So I'm trying to put Ubuntu Netbook Remix 9.10 on my Eeepc 1005:
I downloaded the .iso for UNR 9.10, and used unetbootin to put it on my USB stick.  Then I did all the stuff in BIOS and start the computer using the USB stick.
I've done this a number of times, but each time I run into the same problem: whenever I try to boot into Ubuntu from the USB stick, it goes through the stuff with the ubuntu symbol, but always ends up stuck on a spinning grey circle-thing.  I've poked around a bunch and searched the forums but cant seem to find much on this.  (Windows 7 is already on the netbook so that's what I'm using to do all of this stuff.) 
p.s. I checked the md5sum thingey for the .iso and that is fine.


I feel like I'm not doing something essential in the area of formatting the the USB stick initially, but I'm not sure an am pretty lost, so any help would be greatly appreciated.

---

### Post by rad_sci_guy on 2009-12-27
I installed unr 9.10 on my eee 1005ha.  I used the usb key creator on my desktop ubuntu system to make the key instead of unetbootin.  If you have ubuntu on another computer give that a try.

If you can only use the netbook to do it, try using win32diskimager for windows systems, link is below.  I found that program on the OpenSuse instructions page for creating an install usb key.  I've used it as well and it also works.

[http://launchpad.net/win32-image-writer/0.2/0.2/+download/win32diskimager-RELEASE-0.2-r23-win32.zip](http://launchpad.net/win32-image-writer/0.2/0.2/+download/win32diskimager-RELEASE-0.2-r23-win32.zip)

---

### Post by aljoriz on 2009-12-28
kindly compare the md5sum of your UNR download with the original UNR md5sum at the site.  

BTW you can install UNR after the spinning gray thinggy.  On the favorite tab, there's an install icon, click it.

---

### Post by bleepbloop on 2009-12-30
I compared the md5sum and it matches the original;  in terms of the spinning grey thingey, I mean that it never goes beyond that, i.e. it gets stuck on a completely black screen with the spinning grey thingey as the cursor

---

### Post by blur xc on 2009-12-30
> **bleepbloop said:**
> I compared the md5sum and it matches the original;  in terms of the spinning grey thingey, I mean that it never goes beyond that, i.e. it gets stuck on a completely black screen with the spinning grey thingey as the cursor

How long is forever?  I had some install disks seem like they froze, but they were really taking just that long ot make it work.  The USB stick boots a lot slower that a normal OS.

I installed Karmic NBR on two netbooks, on one I used the ubuntu usb dealy, and on another I used unetbootin to create a bootable sd card (left my usb dirve and home, had the netbook at work) with good success.  And one was on an EeePC.  Dunno which one though, 9", disney princess edition.

And a piece of advice- (disregard if old news or if you know better) when it does load, select the "try ubuntu w/o installing" first.  When booted up, fire up gparted and manually create your partitions (if dual booting or makign separate /home and swap partions).  And then click install ubuntu.  When you get to the partion editor select the advanced option to manually select your partions, make the first one mount on /, the 2nd (big one) on /home, and the last it automatically selected as swap.  It's way easier than it sounds, and way easier than doing it durng the boot process.

BM

---

### Post by bleepbloop on 2009-12-30
> **blur xc said:**
> How long is forever?  I had some install disks seem like they froze, but they were really taking just that long ot make it work.  The USB stick boots a lot slower that a normal OS.

A long time as in, I will select "Boot from USB'' or whatever it says, and will sit and watch it go through the screen with the ubuntu logo to the spinning gray thingey, and will get up and leave for at least a half an hour and the spinning gray thingey will still be there when I come back.



> **blur xc said:**
> I installed Karmic NBR on two netbooks, on one I used the ubuntu usb dealy, and on another I used unetbootin to create a bootable sd card (left my usb dirve and home, had the netbook at work) with good success. And one was on an EeePC. Dunno which one though, 9", disney princess edition.

Where you used the ubuntu usb dealy, what kind of formatting did you do to the usb stick before putting the .iso or .img file on it?

---

### Post by rad_sci_guy on 2009-12-31
I formatted the usb stick to fat32 in Gparted

---

### Post by blur xc on 2009-12-31
> **bleepbloop said:**
> A long time as in, I will select "Boot from USB'' or whatever it says, and will sit and watch it go through the screen with the ubuntu logo to the spinning gray thingey, and will get up and leave for at least a half an hour and the spinning gray thingey will still be there when I come back.




Where you used the ubuntu usb dealy, what kind of formatting did you do to the usb stick before putting the .iso or .img file on it?


Well, I guess in computer terms that counts as forever...

I didn't do anything ot my usb stick before writing the iso, besides rm -rf * all the files that were already on it.  Didn't do anything for the sd card either.

BM

---

### Post by bleepbloop on 2009-12-31
Hmmm, I think I may just have a finicky flash drive then, I'll try to get my hands on a different one and see how that goes.


_Edit:_  My trouble was definitely due to some issue with the usb stick I was using, because I borrowed a stick from my friend, and did everything **exactly** as I had done before, and it worked perfectly and I was able to install ubuntu on the netbook! :-D

---

### Post by josdomingues on 2010-02-24
I am trying to get the .img of UNR Karmic, but I can not see it anywere. Some one could give me a clue.
 Many thanks in advance

---

### Post by rad_sci_guy on 2010-02-24
They only offer a .iso file now which you can burn to a cd or if you use the USB startup disk creator you can write the files to a usb key.

here is the link to the .iso

[http://www.ubuntu.com/getubuntu/download-netbook](http://www.ubuntu.com/getubuntu/download-netbook)

---

