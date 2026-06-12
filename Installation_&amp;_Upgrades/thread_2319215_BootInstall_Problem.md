---
title: "Boot/Install Problem"
date: 2016-04-02
forum: Installation &amp; Upgrades
---

### Post by rouxster2 on 2016-04-02
I am new to this, please bear with me. So I was trying to breath new life into one of my old devices, a Toshiba running on Windows XP, with Ubuntu. Followed all of the steps up to running the demo and installing the full version, where I ran into a problem. I clicked install, and a message came up telling me that I should reboot my device before going any further. So I did. In the past, on Windows XP, I had set a password that I would have to type in before logging in to my Windows account. As usual, I was asked to put in a password, and when I did this happened:
[IMG]http://i.imgur.com/Ucts1Dq.jpg[/IMG]
It has been stuck on this screen for three hours now, and nothing has been able to change it so far. This is with version 14.04.4. I would really appreciate some help. Thanks!

---

### Post by mörgæs on 2016-04-02
Hi, welcome to the fora.
If the computer is from the XP era I recommend Lubuntu, not Ubuntu.

---

### Post by rouxster2 on 2016-04-02
Thank you! Now, how do I get Ubuntu off the computer, since I can't access it past the password?

---

### Post by mörgæs on 2016-04-02
Where is the password created? In BIOS?

---

### Post by Bucky Ball on 2016-04-02
*Thread moved to **Installation and Upgrades**.*

Welcome. You don't need to yet. You can just forget about the installed Ubuntu and run Lubuntu or Xubuntu from live media. If you like it and it works, install right over what you already have. In fact, if you choose 'Something Else' at the partitioning section, you can use the existing /swap partition and manually partition how you like it. Use the existing / partition as your new / partition for the new install and tick the partition to 'Format' in that column. ;)

I advise you 'Try *buntu' from the live media prior to attempting to install. Check what works and what doesn't.

It helps us help you if you give as much info as possible when posting. Which Toshiba model exactly and CPU, GPU and amount of RAM if you could. ;)

---

### Post by rouxster2 on 2016-04-02
Well, me being a newbie, I would be grateful if you could explain to me how to run Lubuntu from live media. Am I supposed to do all this on a separate device? And if I like everything once I do it in "live media," how do I transfer the files over? USB I would guess?
---
I created the password by holding F8 on XP and going to the options while the laptop was booting.

---

### Post by Bucky Ball on 2016-04-02
> **rouxster2 said:**
> Well, me being a newbie, I would be grateful if you could explain to me how to run Lubuntu from live media. And if I like everything once I do it in "live media," how do I transfer the files over? USB I would guess?

Yep. Download either Xubuntu or Lubuntu ISO (as no idea of the details of your machine hard to say what's best), create a USB using UNetbootin or your weapon of choice, boot from it, 'Try *buntu' (replace *buntu with the flavour you're trying). ;)

It is a good idea to rewrite the partition table on the USB to wipe all data then create one FAT32 partition that uses all space. Just creating the partition should work fine, though.

(Running Ubuntu from install media is called a 'live' session. Install media is DVD, CD, USB, whatever you're booting from to install/try.)

---

### Post by rouxster2 on 2016-04-02
Thanks. I need to get some sleep. Will post results tomorrow after I have tried everything.

---

### Post by Bucky Ball on 2016-04-02
Yep. Sleep will help consolidate new ideas. ;)

---

### Post by rouxster2 on 2016-04-02
Here are the full specs of my laptop, a Toshiba Potege M700:

[LIST]
[*]Core 2 Duo 2.2GHz T7500 processor
[*]160GB hard drive
[*]2GB RAM
[*]12.1&#8221; WXGA (1280×800) LED backlit LCD display with both touchscreen and pen/ink capabilities
[*]802.11a/g/n, Gigabit Ethernet
[*]Full Suite of Toshiba 3rd Generation EasyGuard Technology
[*]Shock absorbing design
[*]DVD Super Multi Drive
[*]2x Sleep and Charge USB ports
[*]1x USB port
[*]PC Card Slot
[*]SD Card slot
[*]RGB (monitor) output port
[*]Headphone and Microphone ports
[*]RJ-11 and RJ-45
[*]IEEE 1394
[*]Integrated webcam
[*]Fingerprint reader
[*]Windows XP
[*]Dimensions: 12" x 9.41" x 1.47"
[*]Weight: 4.76 lbs
[*]6-cell Lithium-Ion battery
[/LIST]
[FONT=inherit]Which flavour should I go with? Can I use a DVD+R instead of UNetBootin?
Yes, I created the password in BIOS.

---

**EDIT:**
I was able to remove the BIOS password by using the ESC Key BIOS removing procedure. Standby for results on next startup.

---

**Edit 2:**
Now I when I boot my laptop, this screen pops up and gets stuck.
[/FONT][IMG]http://i.imgur.com/VC3BnpE.jpg[/IMG]
*The white underscore is blinking on my screen.
What can I do to fix this?

---

### Post by rouxster2 on 2016-04-02
I fixed this black screen by simply booting my laptop from the DVD+R that Ubuntu was burned on. I am currently in the demo of Ubuntu. My laptop's specs are in my previous post. Should I continue with the installation of Ubuntu 14.04.4 or use a different flavour?

---

### Post by Bucky Ball on 2016-04-02
How is 14.04 LTS running now? If you're happy, install. If not, try a lighter flavour, Xubuntu or Lubuntu. Xubuntu or Xubuntu-core should fly along on that machine. 

You're issue with Ubuntu may be the 3D graphics. It also may be a bit sluggish. One of the other two will be faster and more lightweight.

---

### Post by rouxster2 on 2016-04-02
I went ahead and installed Ubuntu. I don't plan on gaming much, so I don't think speed will be too problematic. If I come across any major sluggishness, I can just change flavors. Thank you.

---

