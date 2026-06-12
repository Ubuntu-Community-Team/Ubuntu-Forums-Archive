---
title: "ubuntu wont boot via live cd"
date: 2011-06-25
forum: Installation &amp; Upgrades
---

### Post by louisgonick on 2011-06-25
So i decided to try ubuntu for the first time about 4 days ago, with some help of the people in this forum I figured out how to run ubuntu on a live cd. Everythig was going well and I was planning on installing it after I got used to it, the experience was a bit sluggish but guess that was because I was running it from a CD. So today i booted up my laptop and ubuntu took longer than usual booting up, I got stuck on that purple loading screen for like 15 minutes, and after a while i got this code: 

(intramfs)mount:mounting/dev/loop0 on//filesystem. squashf,falied:Input output error can not mount/dev/loop0(/cdrom/casper)filesystem.squashf)on//filesystem.squashf

udeud[73]:worker[186] unexpectedly returned with statys 0x0100 udeud[73]:worker[186]failed while handling'/devices/virtual/block/loop0

I have 11.04... I am an ubuntu noob so please bear with me.

---

### Post by Quackers on 2011-06-25
If you boot from the cd again, at that first purple screen press any key.On the next screen (after choosing your language) click on "check for errors".

If you haven't done so already you should check the md5sum of the downloaded iso. If that md5sum is correct but the cd has errors you will need to burn the image again using the slowest settings.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Or you could try cleaning the cd and the cd drive's laser eye with a dry cloth.

---

### Post by louisgonick on 2011-06-25
> **Quackers said:**
> If you boot from the cd again, at that first purple screen press any key.On the next screen (after choosing your language) click on "check for errors".

If you haven't done so already you should check the md5sum of the downloaded iso. If that md5sum is correct but the cd has errors you will need to burn the image again using the slowest settings.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Or you could try cleaning the cd and the cd drive's laser eye with a dry cloth.

I've been using ubuntu for more or less 2 or 3 days, I don't know what are you talking about lol. When I boot up I go through 2 purple screens, one has some white icons on the bottom and the other one has the ubuntu logo. I don't get to a screen that asks me to select the language. I will re burn the image tomorrow once I buy a new CD, I don't have many cds laying around here because I rarely use them anymore.

---

### Post by Quackers on 2011-06-25
If you get to the first purple screen (with the little man icon at the bottom) and press any key when it appears you will next choose your language and on the next screen you can choose to check for errors.

---

### Post by louisgonick on 2011-06-25
> **Quackers said:**
> If you get to the first purple screen (with the little man icon at the bottom) and press any key when it appears you will next choose your language and on the next screen you can choose to check for errors.

I tried this, and when I select check disk for errors I get the purple ubuntu loading screen and the same error message. I'm not sure on how ubuntu checks for errors but when windows does it tells me when its doing it, it doesn't just boot up. Any more suggestions?

---

### Post by Quackers on 2011-06-25
It should run a checking process for a few minutes. If it's not running anything I suspect the disc is bad.
Have you checked the md5sum of the originally downloaded iso file?
If that's ok you will just need to burn a new disc, preferrably at slow settings.

---

### Post by louisgonick on 2011-06-25
> **Quackers said:**
> It should run a checking process for a few minutes. If it's not running anything I suspect the disc is bad.
Have you checked the md5sum of the originally downloaded iso file?
If that's ok you will just need to burn a new disc, preferrably at slow settings.

the md5sum file is a notepad file with codes

---

### Post by Quackers on 2011-06-25
Did you take a look at the md5sum link I gave earlier? That explains things for Linux and Windows, I believe.

---

### Post by louisgonick on 2011-06-25
> **Quackers said:**
> Did you take a look at the md5sum link I gave earlier? That explains things for Linux and Windows, I believe.

It tells me MD5 sums are different

---

### Post by Quackers on 2011-06-25
Ok, well if you're sure that you are checking it against the correct checksum for the version you downloaded (ie Ubuntu 11.04 Desktop  x86_64 or i386 etc, etc) then the iso is damaged or incomplete and you will need to download it again I'm afraid.

---

### Post by louisgonick on 2011-06-25
> **Quackers said:**
> Ok, well if you're sure that you are checking it against the correct checksum for the version you downloaded (ie Ubuntu 11.04 Desktop  x86_64 or i386 etc, etc) then the iso is damaged or incomplete and you will need to download it again I'm afraid.

How do I know that I am checking it against 11.04?

---

### Post by YesWeCan on 2011-06-25
```
7de611b50c283c1755b4007a4feb0379 *ubuntu-11.04-desktop-amd64.iso

8b1085bed498b82ef1485ef19074c281 *ubuntu-11.04-desktop-i386.iso

```
It will be one of these two, the top is 64-bit.

---

### Post by louisgonick on 2011-06-25
> **YesWeCan said:**
> ```
7de611b50c283c1755b4007a4feb0379 *ubuntu-11.04-desktop-amd64.iso

8b1085bed498b82ef1485ef19074c281 *ubuntu-11.04-desktop-i386.iso

```
It will be one of these two, the top is 64-bit.

[IMG][[IMG]http://img863.imageshack.us/img863/2558/capturezd.th.png[/IMG]](http://imageshack.us/photo/my-images/863/capturezd.png/) Uploaded with [ImageShack.us](http://imageshack.us)[/IMG]
now I get this, will re burning the image on a new cd help???

---

### Post by YesWeCan on 2011-06-25
If you boot the CD and run "check disk for errors", as Quackers recommends, and it has errors then there's your answer.

---

### Post by louisgonick on 2011-06-25
> **YesWeCan said:**
> If you boot the CD and run "check disk for errors", as Quackers recommends, and it has errors then there's your answer.

it doesent check for errors, it just boots up.

---

### Post by YesWeCan on 2011-06-25
Oh. Yes, it does unless you press a key while you see a sickly purple screen with an anaemic, ambiguous icon at the bottom. :P

---

### Post by louisgonick on 2011-06-25
> **YesWeCan said:**
> Oh. Yes, it does unless you press a key while you see a sickly purple screen with an anaemic, ambiguous icon at the bottom. :P

lol that's what I tried... then I chose language and chose check disk for errors, and after I select that it just boots ;)

---

### Post by YesWeCan on 2011-06-25
That sounds bad. Better re-burn the ISO. Make sure you don't have any other removable drives attached with Ubuntu on them. This threw me for a while when I was trying out Linux Mint - the disk check actually checked a totally different USB stick, or conflicted somehow anyway.

---

### Post by louisgonick on 2011-06-25
> **YesWeCan said:**
> That sounds bad. Better re-burn the ISO. Make sure you don't have any other removable drives attached with Ubuntu on them. This threw me for a while when I was trying out Linux Mint - the disk check actually checked a totally different USB stick, or conflicted somehow anyway.

somebody told me to burn at the slowest speed... will that make any difference?

---

### Post by YesWeCan on 2011-06-25
> somebody told me to burn at the slowest speed... will that make any difference?

> **Quackers said:**
> It should run a checking process for a few minutes. If it's not running anything I suspect the disc is bad.
Have you checked the md5sum of the originally downloaded iso file?
If that's ok you will just need to burn a new disc, [COLOR="Blue"]preferrably at slow settings[/COLOR].
Trust the duck, we share a common ancestor. :)

---

### Post by louisgonick on 2011-06-25
> **YesWeCan said:**
> Trust the duck, we share a common ancestor. :)

Finally I got ubuntu to boot up... But after I clicked try ubuntu nothing happened, I had to try to close that window in order for it to boot. 

I think that I am finally ready to install ubuntu on my machine, should I just click install ubuntu and follow the steps?

---

### Post by Quackers on 2011-06-25
An Ubuntusaurus :-)

---

### Post by louisgonick on 2011-06-26
I just installed Ubuntu and I cant get over it how amazing it is!!!!

---

### Post by Quackers on 2011-06-26
I'm happy to hear that :-)
Have fun!

---

### Post by YesWeCan on 2011-06-26
Congratulations louisgonick, have fun :)

Ubuntusaurus - lmao.

---

### Post by louisgonick on 2011-06-26
> **YesWeCan said:**
> Congratulations louisgonick, have fun :)

Ubuntusaurus - lmao.

the fun did not last for long... I installed compiz and unity apparently got deleted. Tried resetting it on recovery mode and it tells me that unity is not installed.

---

