---
title: "Ubuntu Istall/Live CD wont install"
date: 2006-12-28
forum: Installation &amp; Upgrades
---

### Post by new2ubun2 on 2006-12-28
Issue: Ubuntu Istall / Live CD for  ver 6.06 wont complete installation

Hardware;
Compaq Presario SR 1000
CPU: Intel Celeron 2.66GHz
RAM: 256MB DIMM
HD 0:Win XP (SP2) -installed on Partition 1
         70 GB on Partition 2 with 40 GB Free spacee.
       (I have defragmented Partition 2, format: NFTS)

HD 1: SATA Hitachi Drive with 80GB HD. Formated NFTS.
         Split into two partitions of 40GB each. For backup of WinXP files.
Antivirus Programs: Removed 
USB peripherals    : Removed

Installation Versions /Source:

Live:
1. Pressed Live CD  / Rickford Grant's Book on Ubuntu Linux for Non-Geeks
2. Download Image ISO / Burn after confirming Mdsum on a DVD-RW
3. Pressed Live CD (This one was Fedora Linux ) from Linux for Dummies -ed. 5

Install CD:
4. ISO for Ubuntu 6.06 was burned on CD-RW at 4X, CD test is OK

Boot Set up:
1. Boot from CD

What happens:
Goes to the Ubuntu screen. Otption to 1. Start or Install 2. Start in graphics mode etc.. is displayed. When I press enter, it shows me the compaq orange screen with following options in the bottom - F1 boot set up  F6.. (dont remember this one) F10 Recovery. Then a black screen flashes for a couple of seconds ..it has something like "Decompressing Ok..booting Linux Kernel (?)", Then I hear the CD ROM stop spinning and coming to halt. It brings back to the Ubuntu screen described at the top of this paragraph.

Let me know if I am missing some details to describe the symptoms.

I cannot try to install this in any other computer meeting the minimum requirements.

I did look around on the forum and tried a few things like F3. VGA setting and a couple of different boot options via F6 at the initial Ununtu screen.

Thank you in advance for your help.]

---

### Post by janosz on 2006-12-28
how well, i ve got exactly the same problem...

i tried (using the 6.10 build of kubuntu) the live cd, installation cd and even the dvd-version; i just get a black screen saying : Decompressing Ok... booting Linux Kernel

i first thought that it is my x1950xtx, since this card is not natively 100% supported by linux!!! but now i guess its something else...

need help!!!

thx in advance


------------------------------------------

my hardware:
MB: Asus A8n32sli-deluxe
CPU: A64 4000+
GRA: Ati Radeon X1950XTX
MEM: 1GB ocz RAM

---

### Post by new2ubun2 on 2006-12-30
It appears like the problem was due to some conflict on the Hardware side. I got an older HP Desktop and just erased the HD and using same CD ubuntu desktop installed fine. I am actually posting this from my desktop running ubuntu.

Very pleased with the appearance of desktop  and stability of the OS.

Running on :

HP pavillion a300n
40GB HD
2.6GHz Intel Celeron
CR-RW
246MB DDR SRRAM

Ethernet port for getting online.

In next couple of months I am retiring a XP laptop and putting Ubuntu on it. :)
Have fun...If there are others reading the post who are frustrated with the installation:

i) Hang in, it is worth it
ii) Go for an older PC on which you can erase the HD and put Ubuntu with XP
  (dual boot was giving me a lot of trouble)
iii)If you are going with dual boot and dont know what you are doing when it asks for
   partitioning the HD...just dont do it.

   I almost eneded up getting on the second PC here because I messed up the partitioning.
   Then I said, what the heck, let us just erase XP and put Ubuntu only.

   Anyway, there was not much to lose on this older PC in terms of data.

   I am very pleased with the result.

   Cheers!!!

---

### Post by Sef on 2006-12-31
If the live cd fails to install due to graphics problems, then try the alternate cd.  It can install where the live cd can't.

---

### Post by zionykl on 2007-01-05
I was quite happy today when I just got my Ubuntu 6.06 Live CD from ShipIt but you know what, I have got the exactly same problem as described above when installing it.

It hanged at something like "Decompressing Ok..booting Linux Kernel", and yes the CD ROM stop spinning and coming to halt.

My PC is a Core 2 Duo 1.86GHz, 1 GB Ram, 250GB Harddisk and a HIS ATI X1600 Graphic Card and I have already Windows XP installed and thinking of making it dual boot.

Somehow, I feel the Linux OS has quite a long way to go. I am definitely tired of Windows and would want something new, it appears that Linux is actually quite advanced for people who know little about computer, I am a computer student and does not even have any clues what went wrong here and imagine a novice who just come into the Linux world.

---

### Post by qphone on 2007-01-05
This is really getting frustrating now! I'm helping my friend (non-techie type) install Ubuntu on his old HP.

Specs:
AMD K6 550 Mhz
256MB SDRAM
20 GB Hard Drive (Formatted/Empty no Partition - just like new)
CD-RW 
8MB onboard video

Here's the scoop. Firstly I burned perfect copies on Memorex cd-r's at max. I burned copies of 6.10, 6.06.1 and 6.06.1 alternate. Installed first one...hung after the blinking cursor and blank screen. Tried the second...hung after installing live CD user "Uncompressing Linux blah blah blah...". Tried the 3rd and we thought heck...I think we've got it. It started loading some drivers, it checked and mounted cd-rom and then on the 3rd item...it started to move (loading bar) then it got stuck at SOME ITEMS CAN'T BE RETRIEVED FROM THE CD ROM.

WTF????? I let it to check CD for errors....NO ERRORS WHAT SO EVER!

So for the benefit of the doubt, maybe my discs might be the culprit. So I go back to my computer and burn all iso files (roughly 700mb each) again this time on brand new (very expensive) verbatim cd-r's recorded at half speed. (24x instead of 52x)
Result...same damn thing on every disc.

What gives...I've even formatted his original hard drive to be completely blank. I checked once again cd rom integrity and all have passed.

The alternate disc installed the most things instead of being left hanging or a blinking cursor but...again, it stopped by saying some items can not be retrieved from the cd-rom. (Third or fourth process from installing from text) How can that be when you just tested the cd-rom with no checksum errors????

Roughly 3 days trying to do this...what a complete waste of time. Don't think its the optical drive because this thing was installing a running fine with XP SP2. I'm the one advocating LINUX and now I'm starting to look bad in front of my buddy.

Is installing Linux this hard?

---

### Post by NMeyne on 2007-01-05
Linux is great...  but Ubuntu install seems pretty hard to sort out if it doesn't work first time.   Try DSL-N instead? ([www.damnsmalllinux.org)](www.damnsmalllinux.org)).  Works great on this 500Mhz Celeron.

---

### Post by qphone on 2007-01-05
> **NMeyne said:**
> Linux is great...  but Ubuntu install seems pretty hard to sort out if it doesn't work first time.   Try DSL-N instead? ([www.damnsmalllinux.org)](www.damnsmalllinux.org)).  Works great on this 500Mhz Celeron.

I'm going to my office and download all (5) Fedora Core 6 iso files and try that one. Hopefully I can get some flavor of Linux up and running before the weekend. It's too bad because I really like Ubuntu. I first came across it using my brother in-law's toshiba latop (dual booted).

---

### Post by Rebellion on 2007-02-14
I've got the exact same problem, except that when I tried to install 6.10 nothing but the memtest worked. I got as "far" as the "Booting the kernel" text. On everything. And that's kind of odd, because I've already used 6.06 and that worked just fine, but when I decided to try the 6.10 and that didn't work I wanted to try the 6.06 (just to check) again, but now that didn't work either...  And that's sad, because linux, and ubuntu especially, is very handy and tidy.  Thanks for any response!:)


Edit: Have tried the alternate ISO-file too. And the previous 6.06 version I've used is a shipit CD:)

---

### Post by dubuisson on 2007-02-21
Same problem with me the CD stop when veryfying the X... and computer freeze.

---

