---
title: "EZ(lol)BOOK PC Doesn't work"
date: 2012-04-09
forum: Installation &amp; Upgrades
---

### Post by dmackay on 2012-04-09
I swapped some golf clubs for this EZBOOK PC, Model:EZ-72A.
On the back it says Windows Embedded CE 6.0 Pro
00039-460-141-302
X13-12055
(pink sticker)002302
(White Sticker)JH08041472A000302 (Perhaps Serial NO.)
 
Anyway, when I start it up, I get the "loading device drivers", then it says EZBOOK PC (with an "E" in dots above it, like a registered TM 
 
And that's as far as I get. I tried the reset button on the back, but that made no difference.
 
So I'm wondering, Do I have to install a Program/ Is it locked?
 
If I need to install something, What is it, and Where do I find it, and How do I install it?
 
The person I got it from,wasn't able to use it, and doesn't know what's wrong with it!
 
He didn't have the manual. From some research I found, it uses this Ubuntu???
 
Please, be kind in explainging what to do, If this is the forum for HELP:confused::mrgreen:If you can provide a link, specific instruction, navigating instructions, it will help me immensly.
 
Thanking you all in advance,
<email removed>
P.S. I'm new here

---

### Post by prshah on 2012-04-10
> **dmackay said:**
>  EZBOOK PC, Model:EZ-72A.
On the back it says Windows Embedded CE 6.0 Pro
00039-460-141-302

Hi and welcome to the forums.

Unfortunately, there is no easy way to do this.

The "PC" that you have is not really a PC (Eg, IBM-compatible x86). It uses an ARM processor, and has no "BIOS".

Installing either the original or an alternate OS on this will require modification to the boot loader (usually in "flash memory"), and possibly requires a proprietary tool for this. Your best bet will be to head over to xdadevelopers forums for this device.

Further, you cannot install just any Ubuntu on it. You have to get the ARM build; however, I do not have any more information about this.

If you would like to go ahead with this anyhow, take a look at this rather huge thread: [http://ubuntuforums.org/showthread.php?t=1349626](http://ubuntuforums.org/showthread.php?t=1349626)

Hope this helps.

---

### Post by dmackay on 2012-04-10
I just traded some golf clubs for this EZBOOK PC. Some details on the back are:
Model:EZ-72A
(grey sticker)Windows Embedded CE 6.0 Pro / 00039-460-141-302 / X13-12055
(Pink Sticker) 002302
(White Sticker) JH08041472A000302 (Perhaps the Serial No.)
 
When I start this up, I get "loading device drivers"
Then the screen, "EZBOOK PC" with an E in dots above like a RTM
But that's it. I don't see anything else. I tried the reset button on the back, but still the same.
 
So, I'm wondering, Do I have to install a program on it, or does a lock have to be taken off?
 
If I have to load a program, what do I load and where do I find it? and how do I load it?
 
It doesn't have a CD/DVD Device. It does have a SD Card Slot, 2 USB Ports, a USB Disk Port (not sure what that's used for), and mouse and keyboard slots.
 
Please, can someone steer me in the right direction? 
 
If you could Please Provide detailed help, and links if possible, I would be Very Greatful. If you need more details, I'll try my best to provide them, but I didn't get an Owner's Manual with it, but the person is looking for one. The person who gave it to me rec'd it as a bonus for buying an Infared Heater, and he was not able to use it.
 
Thanking Everyone in Advance,

---

### Post by haqking on 2012-04-10
> **dmackay said:**
> I just traded some golf clubs for this EZBOOK PC. Some details on the back are:
Model:EZ-72A
(grey sticker)Windows Embedded CE 6.0 Pro / 00039-460-141-302 / X13-12055
(Pink Sticker) 002302
(White Sticker) JH08041472A000302 (Perhaps the Serial No.)
 
When I start this up, I get "loading device drivers"
Then the screen, "EZBOOK PC" with an E in dots above like a RTM
But that's it. I don't see anything else. I tried the reset button on the back, but still the same.
 
So, I'm wondering, Do I have to install a program on it, or does a lock have to be taken off?
 
If I have to load a program, what do I load and where do I find it? and how do I load it?
 
It doesn't have a CD/DVD Device. It does have a SD Card Slot, 2 USB Ports, a USB Disk Port (not sure what that's used for), and mouse and keyboard slots.
 
Please, can someone steer me in the right direction? 
 
If you could Please Provide detailed help, and links if possible, I would be Very Greatful. If you need more details, I'll try my best to provide them, but I didn't get an Owner's Manual with it, but the person is looking for one. The person who gave it to me rec'd it as a bonus for buying an Infared Heater, and he was not able to use it.
 
Thanking Everyone in Advance,
[EMAIL="Darrendmmackay@hotmail.com"][COLOR=#000000]Darren[/COLOR][/EMAIL]
[EMAIL="dmmackay@hotmail.com"]dmmackay@hotmail.com[/EMAIL]


depending on the specs (which i havent looked up) you could download Ubuntu and put it on a USB key and boot to that and install, after all it is a Ubuntu Forum, however it depends on the specs i expect something a bit more legacy friendly may be better such as puppy linux or tiny linux etc.

Or a minimal install.

here is a link [http://askubuntu.com/questions/14440/installing-ubuntu-on-a-windows-ce-6-0-ezbook-pc-ez-72a](http://askubuntu.com/questions/14440/installing-ubuntu-on-a-windows-ce-6-0-ezbook-pc-ez-72a) which also links to other stuff down the page

And not a good idea to have email address in signature unless you want loads of spam.

Peace

---

### Post by nothingspecial on 2012-04-10
Hi, welcome to the forums

I have removed your email address from your post. Not a good idea to leave it there because it will lead to spam.

:D

---

### Post by snowpine on 2012-04-10
I think it is the seller's responsibility to make this right with you.

These forums are for discussing the Ubuntu operating system, and your computer runs Windows, so you'll probably get a better answer on a Windows forum (or from the person who sold it to you).

---

### Post by coffeecat on 2012-04-10
@dmackay, I've merged your two threads together as they seem to be asking the same thing. Please do not post the same question in separate threads. This dilutes community effort.

I've also removed your email address from your older post for the same reason that nothingspecial cites. Besides, this is a forum and questions and answers are for the benefit of all, not just the person who first posts the question. Answers in pm's and emails disadvantage those who come here looking for a solution to a similar problem from a google or forum search.

---

### Post by arpanaut on 2012-04-10
I know nothing about this product but this may help you.

[http://askubuntu.com/questions/14440/installing-ubuntu-on-a-windows-ce-6-0-ezbook-pc-ez-72a](http://askubuntu.com/questions/14440/installing-ubuntu-on-a-windows-ce-6-0-ezbook-pc-ez-72a)

---

### Post by dmackay on 2012-04-10
I was on another forum, and someone had suggested Ubuntu.  I believe because of the Windows Embedded CE 6.0.  
 
It's quite hard to find support for this PC.  A support no. on the back is no longer available.
 
As for the retailer making it right.  I didn't buy it, nor was I given it, and the person who was has had it for some time, and they may have bought it in another country.
 
So, I have to try to figure this thing out, but certainly not with HELP:confused:
 
Thanks for the replies so far.

---

### Post by snowpine on 2012-04-10
I recommend you get your golf clubs back (you were scammed) and purchase a computer that meets the following [minimum hardware requirements]("https://help.ubuntu.com/community/Installation/SystemRequirements") for a fun, easy introduction to the wonderful world of Ubuntu:

> 1 GHz CPU (x86 processor (Pentium 4 or better))
1 GiB RAM (system memory)
15 GB of hard-drive space (or USB stick, memory card or external drive but see LiveCD for an alternative approach)
800 by 600 screen resolution
Either a CD/DVD drive or a USB port for the installer media
Internet access is helpful 

Installing Ubuntu on your EZBook is not a beginner's task (if it's even possible at all, I have my doubts).

Here is a list of computers that are certified to run Ubuntu flawlessly: [http://www.ubuntu.com/certification/](http://www.ubuntu.com/certification/)

An Asus EEE PC, for example, is a superior machine to the EZBook and will run Ubuntu very well, for less than US$300.

---

