---
title: "strange graphical problem on 10.10 amd64 installation"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by utkuozdemir on 2010-10-10
Hello to everyone.

Yesterday I downloaded Ubuntu 10.10 Desktop Edition to install to my Laptop (it's a desktop replacement Laptop). But after boot from cd/dvd (I tried both), while the dots shows progress, I get a strange screen, and nothing happens after that (computer stops reading the cd/dvd). I checked md5 sum and my iso was ok, I burned it two times, to a cd and a dvd, I still got the problem. Here's the funny screen (like a labyrinth):
[[IMG]http://img140.imageshack.us/img140/839/10102010001.th.jpg[/IMG]](http://img140.imageshack.us/i/10102010001.jpg/)

note: I installed 10.04 amd64 Desktop ed. to this laptop without a problem in the past.

Anyone can help?

---

### Post by delphine on 2010-10-11
Hi there

Delurking to say I have the exact same problem. I have never had an issue installing any flavour of Linux before, and this laptop is almost brand new with excellent specs, currently running Linux Mint 9, so should have no issues.

I've tried both 32-bit and 64-bit and burnt three CDs all with the same issue. Googling around hasn't found very much so this doesn't seem very common... which is puzzling.

Edit to add: I have just tried again with a UNetbootin frugal install to hard disk (as I have used up all my spare CDs and do not have a USB stick lying around), and I now hear the bootup sound which is further than I got before, but still the same screen appears and I am unable to interact with it in any way.

---

### Post by cpighin on 2010-10-11
:) Hi!

I wanted to try Ubuntu 10.10 Desktop 64 bit and I had no success as well. 

The system read the installation CD, than showed a coloured screen with a window with two buttons, the trial one and the install one, but after having clicked  the first one, the system became black and nothing  happened after. A white arrow (pointer) was present and I could move it, but no actions were possible. 

Thanks for help

Claudio :)

---

### Post by diebels on 2010-10-11
Hi Guys.  If you figure out which graphics adapter you have, there might be a known problem you can search for.

---

### Post by cpighin on 2010-10-11
:) My graphic adapter is ATI Mobility Radeon HD3650 but I don't think it is relevant since I ran Ubuntu 10.04 without graphic problems.

Claudio :)

---

### Post by delphine on 2010-10-11
I have an NVIDIA graphics card. Happily, I was finally able to solve the issue by:

1. Hitting F6 at the initial LiveCD bootup screen and selecting "nomodeset"
2. Install then proceeded normally. When trying to boot into Ubuntu for the first time, I hit "e" at grub to edit the boot options and changed "quiet splash" to "nomodeset"
3. Booted up ok, installed NVIDIA drivers
4. Reboot, all fine, enjoying Maverick so far

Hope this helps someone out there!

---

### Post by utkuozdemir on 2010-10-11
> **delphine said:**
> I have an NVIDIA graphics card. Happily, I was finally able to solve the issue by:

1. Hitting F6 at the initial LiveCD bootup screen and selecting "nomodeset"
2. Install then proceeded normally. When trying to boot into Ubuntu for the first time, I hit "e" at grub to edit the boot options and changed "quiet splash" to "nomodeset"
3. Booted up ok, installed NVIDIA drivers
4. Reboot, all fine, enjoying Maverick so far

Hope this helps someone out there!

I will try that and retun the result here. My graphics card is NVIDIA Geforge GTS 360M by te way. I thin it isn't the problem.

---

### Post by dino99 on 2010-10-11
as post #6 says, you have to bypass some acpi or irq issues by adding either: nomodeset, irqpoll, noacpi, nolapic, noapic, sometimes you have to add video=vesa

---

### Post by cpighin on 2010-10-11
:) For those interested  I ran the live cd on tral mode by:

[LIST]
[*]Hitting F6 at the initial Live CD bootup screen, 
[*]selecting "nomodeset", 
[*]hitting the ESC key to close the selection window,
[*]hitting the ENTER key
[/LIST]

Claudio :)

---

### Post by utkuozdemir on 2010-10-11
> **cpighin said:**
> :) For those interested  I ran the live cd on tral mode by:

[LIST]
[*]Hitting F6 at the initial Live CD bootup screen, 
[*]selecting "nomodeset", 
[*]hitting the ESC key to close the selection window,
[*]hitting the ENTER key
[/LIST]

Claudio :)

That works. After installation, same problem occurs at boot, after selecting Ubuntu from Grub menu. Like Delphine said, you must use nomodeset here too.

By the way, I'm really disappointed with 10.10. 10.04 was a lot more stable. I did not like the new partitioner in installation too. (I did not like older one too, but it was better). I think major releases (.04 versions) are way better.

---

### Post by utkuozdemir on 2012-07-11
Sorry for reviving a very old thread, but I still have same problem  on 12.04 and had it on every version between 12.04 and 10.10

Is there any solutions except nomodeset or any known causes for this problem?

---

### Post by wildmanne39 on 2012-07-12
Hi, this is an old thread so it has been closed please start a new thread with a descriptive title. 
Thanks

---

