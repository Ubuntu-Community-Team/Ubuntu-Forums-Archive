---
title: "Not Booting"
date: 2011-10-19
forum: Installation &amp; Upgrades
---

### Post by gavmoulds on 2011-10-19
ok all I am new here so be easy.

I am very much a novice too.

I decided to download ubuntu 11.10 to try on a usb stick.

Starts booting and then juts stops on the ubuntu screen with the dots underneath.

So I tried it on cd. Boots but then hangs on a multicoloured wierd looking blank screen.

I cant seem to do anything with it.

All answers in laymans terms please.

---

### Post by collisionystm on 2011-10-19
> **gavmoulds said:**
> ok all I am new here so be easy.

I am very much a novice too.

I decided to download ubuntu 11.10 to try on a usb stick.

Starts booting and then juts stops on the ubuntu screen with the dots underneath.

So I tried it on cd. Boots but then hangs on a multicoloured wierd looking blank screen.

I cant seem to do anything with it.

All answers in laymans terms please.

What model computer do you have? 

Any idea what the video card is?

---

### Post by gavmoulds on 2011-10-19
Acer laptop with ATI Radeon graphics

---

### Post by collisionystm on 2011-10-19
> ATI Radeon graphics

Therein lies your problem. There is a bug in 11.10 with Radeon Cards. 

You can reboot your computer with the Live-CD
Keep tapping the up arrow key
You should be presented with the Live-Cd Menu.
Choose Your language
Key down to Install Ubuntu and hit F6 I think and use the spacebar to mark NOMODESET
Esc key
Enter to boot the install

If that fails use the alternative install cd
[http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download)

It is text based and will work.

Either way you choose, you need to do the following when finished.

Reboot your computer, immediately after your ACER bios screen, hold the SHIFT key down until you reach the grub menu
Choose system rescue
At this menu, choose resume normal boot and hold the SHIFT KEY until you reach the text login
Login with your credentials

sudo nano /etc/apt/sources.list

Remove the # from the Ubuntu partners repo's
CTRL + X then Y to save

sudo apt-get update

sudo apt-get install fglrx

reboot like normal

hopefully that works.

---

### Post by gavmoulds on 2011-10-19
Now yu do understand I did say laymans terms

---

### Post by collisionystm on 2011-10-19
> **gavmoulds said:**
> Now yu do understand I did say laymans terms

Buddy,

Thats about as simple as it gets. If you are not willing to try and figure some of this out on your own, then no one can help you. We are on a FORUM not in the same room.

Just follow my directions.

---

### Post by ru2044 on 2011-10-19
@collisionystm, thank you a lot!!!!!!!!!!!!!!!I really apreciate your help. (I 've been trying to install 11.10 for 5 days). 
Method in post #4 works on desktop based on AMD A8-3850 with motherboard ASUS F1A75-M.

One question,
I wasn't quite sure how to prepare partitions in text-mode installer.
I clicked something. Now when I see Grub I have 2 possibilites to run 11.10.
First one is 'normal'
Second one is on dev/sda1

Should I reinstall the sysytem again?

---

### Post by ru2044 on 2011-10-19
post above - solved
The 'normal' run possibility is simply my old 11.10 failed installation. 
Everything is ok!!!

---

### Post by collisionystm on 2011-10-19
> **ru2044 said:**
> @collisionystm, thank you a lot!!!!!!!!!!!!!!!I really apreciate your help. (I 've been trying to install 11.10 for 5 days). 
Method in post #4 works on desktop based on AMD A8-3850 with motherboard ASUS F1A75-M.

One question,
I wasn't quite sure how to prepare partitions in text-mode installer.
I clicked something. Now when I see Grub I have 2 possibilites to run 11.10.
First one is 'normal'
Second one is on dev/sda1

Should I reinstall the sysytem again?

Your Welcome! =)

Glad I could help!

---

### Post by collisionystm on 2011-10-19
> **collisionystm said:**
> Your Welcome! =)

Glad I could help!

> **ru2044 said:**
> post above - solved
The 'normal' run possibility is simply my old 11.10 failed installation. 
Everything is ok!!!

And hey, good job on figuring this out!! I knew you could do it :KS

---

