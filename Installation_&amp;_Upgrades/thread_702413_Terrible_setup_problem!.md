---
title: "Terrible setup problem!"
date: 2008-02-20
forum: Installation &amp; Upgrades
---

### Post by mus,muris on 2008-02-20
Hello everybody! I'm new about linux and about this forum. I decided to abandon windows os because I like linux very much and I like very much the open source. I've an old pc (it sucks :() with this hardware configuration:

CPU:
633 megahertz Intel Celeron
32 kilobyte primary memory cache
128 kilobyte secondary memory cache

Ram:
slot 1: 64 Mb
slot 2: 128 Mb

Hard disk:
20.56 Gb

Video:
Intel(R) 82815 Graphics Controller

I decided to install Xubuntu because it requires not much ram and I like his mascotte :lolflag:. I tried to install the "normal" Xubuntu 7.10 but nothing to do; so I downloaded and burned the xubuntu 7.10 alternate. I started the setup in text mode (the only way on alternates editions) and.... I had this problem: whenever I digit on my keyboard , computer digits as double, example: I digit "test": pc output: "tteesstt". I've this problem when i digit with arrowkeys and enter, too. It isn't a problem of the keyboard because i tried with another one. :( Help me please!
Thanks!

---

### Post by Bruce M. on 2008-02-20
> **mus,muris said:**
> I had this problem: whenever I digit on my keyboard , computer digits as double, example: I digit "test": pc output: "tteesstt". I've this problem when i digit with arrowkeys and enter, too. It isn't a problem of the keyboard because i tried with another one. :( Help me please!
Thanks!

First:  **Welcome to Ubuntu.**

Not sure if this will help or not but you can look at these for a start;

You have two possible choices:
[LIST=1]
[*]When you insert the Alt CD and reboot there are some functions displayed at the bottom of the screen:
[LIST=a]
[*]F2 = Language - choose a language
[*]F3 = Keyboard - choose a layout
[/LIST]
[*]Without doing #1 - continue with setup:
[LIST=a]
[*]Ubuntu will ask you for a language setting
[*]Ubuntu will ask you if you want the keyboard *automatically detected* - **Say NO!**
[*]Select your keyboard and layout
[/LIST]
[/LIST]

My typical way to start is: **1.a, 2.b, 2.c**
**Reasons:**

1.b. - Does not allow for "extra" layout patterns.
2.b. - Saying yes doesn't give me a Spanish language keyboard I have because of my choice of English as my language of preference
2.c. - There are three layouts for a Latin American keyboard, here is where I choose what I have.

Hope this helps.
Bruce

---

### Post by mus,muris on 2008-02-20
No, nothing to do :(. Isn't a keyboard problem, i tried both two ways. Thank you. There's something strange: if I digit in cd's menu is all normal but when i start the text mode setup... Can be a ram or cpu problem?
Help me!
Thanks

---

### Post by Bruce M. on 2008-02-20
> **mus,muris said:**
> No, nothing to do :(. Isn't a keyboard problem, i tried both two ways. Thank you. There's something strange: if I digit in cd's menu is all normal but when i start the text mode setup... Can be a ram or cpu problem?
Help me!
Thanks

I doubt it would be a RAM or CPU problem, you tried another keyboard with the same problem.

You said:
> I decided to abandon windows
Did you have Windows on this old computer?
If yes, I would guess that you used the keyboard you are now using without problems.
Therefore it's not a keyboard problem.

---

### Post by louieb on 2008-02-20
Did you run the media check option?
Just a few twisted bits in the wrong place can lead to strange results.

---

### Post by mus,muris on 2008-02-20
[QUOTE=Bruce M.]Did you have Windows on this old computer?
If yes, I would guess that you used the keyboard you are now using without problems.
Therefore it's not a keyboard problem.[/QUOTE]
Yes I use Windows Millenium, so I wanted to change it.
[QUOTE=louieb]Did you run the media check option?[/QUOTE]
How i can do it?
Thanks.

---

### Post by Bruce M. on 2008-02-20
> **mus,muris said:**
> Yes I use Windows Millenium, so I wanted to change it.

How i can do it?
Thanks.

Boot with the CD in the drive.

One of the main options is something like:

[LIST]
[*]Check integrity of CD
[/LIST]

Do that, it will tell you if the CD is good.
[LIST=1]
[*]If the CD is not good and you still have the original ISO file do a [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") check.
[LIST]
[*]If the ISO is good: burn a new CD at the **lowest** speed you can.
[/LIST]
[*]If **not** good download again and start with Step 1 before burning the CD.
[/LIST]

EDIT:  You will want this page too: [UbuntuHashes]("https://help.ubuntu.com/community/UbuntuHashes")

---

### Post by Bruce M. on 2008-02-20
> **louieb said:**
> Did you run the media check option?
Just a few twisted bits in the wrong place can lead to strange results.

Missed that, I should have thought of it too!  Thanks

---

### Post by mus,muris on 2008-02-20
> **Bruce M. said:**
> Boot with the CD in the drive.

One of the main options is something like:

[LIST]
[*]Check integrity of CD
[/LIST]

Do that, it will tell you if the CD is good.
[LIST=1]
[*]If the CD is not good and you still have the original ISO file do a [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") check.
[LIST]
[*]If the ISO is good: burn a new CD at the **lowest** speed you can.
[/LIST]
[*]If **not** good download again and start with Step 1 before burning the CD.
[/LIST]

EDIT:  You will want this page too: [UbuntuHashes]("https://help.ubuntu.com/community/UbuntuHashes")

Yes thanks a lot! I checked cd for defects and:
at about 30%:
Failed MD5 checksum verification:

./pool/main/g/gimp-help/gimp-help-common-2+0.12-1_all.deb

But... I burned the cd at 8x.
Ok I'll reburn it.
Thanks

---

### Post by Bruce M. on 2008-02-20
> **mus,muris said:**
> Yes thanks a lot! I checked cd for defects and:
at about 30%:
Failed MD5 checksum verification:

./pool/main/g/gimp-help/gimp-help-common-2+0.12-1_all.deb

But... I burned the cd at 8x.
Ok I'll reburn it.
Thanks

If 8x is your lowest try it again, but did you also check the ISO file for errors?
See my post #7

---

### Post by dstew on 2008-02-20
You might have to download the .iso again. Do the md5 checksum test on the original .iso if you still have it, as recommended by Bruce M. The error you got could be because you started out with a bad .iso, and not a burn problem.

---

### Post by mus,muris on 2008-02-20
No, I don't have the original .iso but when I'll download it again, I'll check it.
Thanks

---

### Post by Bruce M. on 2008-02-21
> **mus,muris said:**
> No, I don't have the original .iso but when I'll download it again, I'll check it.
Thanks

Did it clear up your problem?

---

