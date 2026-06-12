---
title: "Can't get a clean donwload! RRRGGHHH!"
date: 2010-10-27
forum: Installation &amp; Upgrades
---

### Post by cainram on 2010-10-27
I've been using Ubuntu since 8.04 and have never had this kind of trouble. What's worse, I'm trying to get it installed on a friend's computer - she's hot to try Ubuntu and now it's two days into the 'twenty minute install' I was bragging about. Here's the deal.

I started by downloading 10.10 i386 Desktop Live CD from the web-page via HTTP using a wired 30mb down/5mb up wired connection. When I burned to disk (via Windows Vista - yeah, I know, I'll get to that) I got an error. I then booted the disk and ran the Ubuntu Live CD disk check utility and it reported an error in 1 file. Hmmmm. Well, that happens. I first blamed Windows (cause that's how I roll) so, using Vista on the same machine, I downloaded the latest Puppy Linux and burned that. No problem. Booted Puppy and downloaded Ubuntu via a torrent this time. Burned the disk. Still an error in one file. OK, time to try another computer.
I then retried the whole process on my laptop running 10.04. SAME PROBLEM. Hmmm, maybe I've run into a stretch of bad disks halfway through my spindle. Let's try using Unetbootin and a USB stick to Install Ubuntu. Downloaded AGAIN. Ran GTKhash to verify the download. No problems. Expand to USB. Ok. Boot from USB and verify the disk? 'ERRORS FOUND IN 1 FILES'! Ahhhhhhh!!!!!!

Help! I'm not a newb! I know what I'm doing! I've done this a million times! What is going on!?!?

Any advice would be greatly appreciated!

Ramsey

---

### Post by Grenage on 2010-10-27
IT could be bad memory, but I doubt it.  I wonder if the downloads just aren't matching the hashes (Ubuntu bug).

---

### Post by CharlesA on 2010-10-27
Do an md5sum (or sha1sum) to make sure the hashes match.

Shouldn't matter if you are using a torrent, but doesn't hurt to check.

Otherwise burn it at like 4x and try a different brand of media.

---

### Post by cainram on 2010-10-27
Thanks for the immediate help but as I posted, I've checked the sums, they come out perfect. I'd also like to think that this is something the Ubuntu Devs have tried and would have noticed...

---

### Post by Grenage on 2010-10-27
I would probably just install it anyway, but I'm a reckless fool.

---

### Post by cainram on 2010-10-27
I hear, ya - I could just use Clonezilla to get an image of the current M$ install (trying for a dual-boot) but this isn't my computer. I need this user's first experience with Ubuntu to be clean and bug free, dig?

---

### Post by cainram on 2010-10-27
@CharlesA - again, I appreciate the help but as I posted origianally I've run hashes on every download and they're all perfect. As far as using a different brand of media I did - I've tried different KINDS of media altogether. Optical and flash based memory. To no avail.

---

### Post by CharlesA on 2010-10-27
Nothing is 100% bug free.

Just boot off the livecd to let them mess around with it, else install it on a different drive.

---

### Post by beew on 2010-10-27
Why don't you just make a live usb? Fast and easy and you don't have to worry about oddities in burning software, CD rom etc. Installing took me 15, not 20 minutes for 10.10. You can also make the usb persistent to try it out, it is fast and doesn't take up space like CDs.  Forget about disk burning, it is so yesterday, man. :)

Since you are doing this on Vista, check out
[URL="http://www.linuxliveusb.com/"]
http://www.linuxliveusb.com/[/URL]

---

### Post by cainram on 2010-10-27
@beew - Please read my post again and get all the way to the end this time. I appreciate the help and we all rely on forums for help but no one seems to be actually reading my post.

---

### Post by Grenage on 2010-10-27
Considering what you've checked (pretty much everything), it must be a bug on Ubuntu's end.

---

### Post by beew on 2010-10-27
Try a 10.04 iso and see what happens. I am sorry, I was reading people suggesting different burn speed and so on, all these can be avoided if you use a usb instead of a  CD (aside: since most computers now supports booting from usb anyway, I don't know why the first advice given to new users,--I am not saying you,--is always "burn a live CD", it is like saying "make a floppy".)

---

### Post by CharlesA on 2010-10-27
I've got an ISO of 10.10 i386 at home, so I'll check the sums and verify the integrety when I get home.

Is there a problem with just installing it and going from there? It seems that you are hung on the "errors found in 1 file" thing. I don't think I've really bothered with using the "check disk for defects" since I verify the MD5SUM/SHA1SUM before burning.

---

### Post by cainram on 2010-10-27
Well, I appreciate everyone's input but I'd really like to see this bug duplicated - I guess I should post this on launchpad. As far as nothing being 100% bug free, I understand the sentiment but this is a HUGE bug for Canonical's 'Perfect 10' release. Since I can't even get past the Media Verification I wouldn't say it's even 1% bug free. I'm hoping for Canonical's sake that this is a problem that only I'm having and not a problem with the ISO. Don't get me wrong - I'm a HUGE fan of Canonical in general and Ubuntu in particular but c'mon, guys, you're better than this.

---

### Post by Grenage on 2010-10-27
I doubt it's just you.  This could be the first time it's come to light; I can't imagine many people actually check the CD.

---

### Post by oldsoundguy on 2010-10-27
You failed to mention the burning program you are using.  The Roxio program that comes with Windows is garbage.  I use Ashampoo on Windows machines (less obtrusive and not the hog that Nero is.)  But there is the free ImgBurn
[http://www.imgburn.com/](http://www.imgburn.com/)
Works so much better than Roxio.

BOTH programs allow a "verify after burn" option.

---

### Post by CharlesA on 2010-10-27
I use ImgBurn on my Windows machines. The verify after burning part is nice. :)

---

### Post by CharlesA on 2010-10-27
Hi there,

I just checked my ISO in a VM, and it verified fine, no errors.

Burned it to a CD and ran the verify off of it with the same results.

**From Ubuntu.com:**

MD5SUM:
```
[COLOR="Red"]59d15a16ce90c8ee97fa7c211b7673a8[/COLOR] *ubuntu-10.10-desktop-i386.iso
```
SHA1SUM:
```
[COLOR="Blue"]b28bbd742aff85d21b9ad96bb45b67c2d133be99[/COLOR] *ubuntu-10.10-desktop-i386.iso
```

**My hash:**

MD5SUM:
```
[COLOR="Red"]59d15a16ce90c8ee97fa7c211b7673a8[/COLOR] ubuntu-10.10-desktop-i386.iso
```
SHA1SUM:
```
[COLOR="Blue"]b28bbd742aff85d21b9ad96bb45b67c2d133be99[/COLOR]  ubuntu-10.10-desktop-i386.iso
```

---

### Post by oldsoundguy on 2010-10-27
check your memory.

---

### Post by cainram on 2010-10-28
Ok, now I'm getting somewhere. At least I know someone out there can get a good burn from the ISO. Thanks for the help, folks!

---

