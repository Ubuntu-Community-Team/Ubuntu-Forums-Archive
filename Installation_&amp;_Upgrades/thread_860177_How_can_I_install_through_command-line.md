---
title: "How can I install through command-line?"
date: 2008-07-15
forum: Installation &amp; Upgrades
---

### Post by xilefian on 2008-07-15
I get the black-screen installation error but I managed to work around it to the command-line, but I am new to linux so I don't know how to install ubuntu using the command-line.
Or if there isn't a way then how can I get past the black screen?
I can't even reach installation step 1.
Safe graphics doesn't work, removing splash doesn't even work, removing quiet mode gets me to the command line and vga lines just change my resolution around and nothing else. The hold F6 options havent changed anything either.
Please help!

---

### Post by overdrank on 2008-07-15
> **xilefian said:**
> I get the black-screen installation error but I managed to work around it to the command-line, but I am new to linux so I don't know how to install ubuntu using the command-line.
Or if there isn't a way then how can I get past the black screen?
I can't even reach installation step 1.
Safe graphics doesn't work, removing splash doesn't even work, removing quiet mode gets me to the command line and vga lines just change my resolution around and nothing else. The hold F6 options havent changed anything either.
Please help!

Hi and welcome, could you give us some system specs?
Also did you check the cd for errors and verified the checksum on the ISO?

---

### Post by xilefian on 2008-07-15
> **overdrank said:**
> Hi and welcome, could you give us some system specs?
Also did you check the cd for errors and verified the checksum on the ISO?
It's an ordered CD so it's no downloaded ISO and I didn't burn it, I figured that an ordered CD would be more reliable.
Also, I checked it over for errors thousands of times and there aren't any.
The laptop is:
256 RAM
20 Gig HDD
VIA Family Graphics Chipset
OS: Mandriva One Free 2008 (I want to go back to Ubuntu)

---

### Post by overdrank on 2008-07-15
> **xilefian said:**
> It's an ordered CD so it's no downloaded ISO and I didn't burn it, I figured that an ordered CD would be more reliable.
Also, I checked it over for errors thousands of times and there aren't any.
The laptop is:
256 RAM
20 Gig HDD
VIA Family Graphics Chipset
OS: Mandriva One Free 2008 (I want to go back to Ubuntu)

Well with the low memory of 256mb you will likely need to use the alternate cd for installation. It is a text based installation therefore requires less memory. You can find it here
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Just be sure to check the box for the alternate cd below the start download.

---

### Post by snowpine on 2008-07-15
256mb is pretty much the minimum ram for Ubuntu, so your system won't be able to run the live CD. You'll need to download the alternate CD (as Overdrank pointed out). I believe you can run the Xubuntu live CD with 256mb ram (haven't personally tried it) and it may be a bit snappier on your machine.

---

### Post by xilefian on 2008-07-15
Okay thanks for the advice. I'll just give away my ubuntu CD to someone else who might use it.
Thanks.

---

### Post by xilefian on 2008-07-18
Oh no, I just tried xubuntu and EXACTLY the same thing has happened. Damn, I thought I was so close. I tried my ubuntu CD on a friend's computer and it's fine on it, I guess my laptop sucks.

---

### Post by overdrank on 2008-07-18
> **xilefian said:**
> Oh no, I just tried xubuntu and EXACTLY the same thing has happened. Damn, I thought I was so close. I tried my ubuntu CD on a friend's computer and it's fine on it, I guess my laptop sucks.

Ok you have the via graphics and what is the the issue now?
 Did it install?
Did you use the alternate cd for the install?
 Is the laptop going black?
If so then boot into recovery mode which is usually the seconded choice on the grub. Then use the xfix option. If Xubuntu is the only OS on the system then when you see the grub loading press the escape key and then you can choose recovery mode.

---

