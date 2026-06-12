---
title: "Booting from a memory stick"
date: 2011-04-05
forum: Installation &amp; Upgrades
---

### Post by Scunnered on 2011-04-05
I am seeking assistance with loading 10.10 on a Kingston DataTraveler 4GB G2 memory stick as I appear to have done something wrong.

I established that my boot sequence on my system is firstly from :

1. CD/DVD
2. Removable
3. Hard Drive
4. Network.

Having an empty CD/DVD drive I anticipated that I would then boot to the removable drive.  So much for that theory as it totally ignored the pen drive and passed on to my dual boot on the hard drive.

As far as I can see I followed the instructions on the Ubuntu.com page properly and when I click on the pen drive it appears to have downloaded the information to the drive.(see screenshot)

Obviously I have gone wrong somewhere and ask for your kind assistance to resolve matters. I am attempting to prove that my system will boot to a removable drive before I purchase an external HD 

At the moment I would prefer to stick with 10.04 but wish to trial the later versions to see what suits best as I am attempting to persuade another to switch to Ubuntu.

Thanking you in anticipation

---

### Post by Dutch70 on 2011-04-05
Have you tried hitting "esc" when your computer is loading?

---

### Post by Rubi1200 on 2011-04-05
Hi Scunnered,

you need to change the boot sequence in BIOS:

from this:

[COLOR=RoyalBlue]1. CD/DVD
2. Removable[/COLOR]
3. Hard Drive
4. Network

to this:

[COLOR=Red]1. Removable
2. CD/DVD[/COLOR]
3. Hard Drive
4. Network

Then try booting again.

---

### Post by Greyfoxx on 2011-04-05
I tried booting from a Sandisk 4GB pendrive and all it did was pop up a black screen that said Syslinux and all kinds of info across the top of the screen. I really have no idea what is going on with it. I changed the bios so the pendrive was on top and it still didn't work.

---

### Post by Cheezespread on 2011-04-05
@Greyfoxx :

Quick questions :
Which edition of Ubuntu do you have in your usb - server or Desktop ?
The initial syslinux messages are followed by a UI where you should select the type of installation. Did you ever get that screen ? ( Should appear after a few secs of the syslinux messages).

---

### Post by Greyfoxx on 2011-04-05
I was trying to install it on a netbook so I used the Netbook Remix 10.10.

---

### Post by Dutch70 on 2011-04-05
Not to be rude, but if you want to get help... you should start your own thread with a good title. 

It would help, if you read this first...
[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=1422475[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1422475")

---

### Post by Scunnered on 2011-04-05
My thanks for your responses.

**Dutch70**

Would I be right in thinking that your suggestion was to achieve the same result as suggested by **Rubi1200?** if so then I followed his advice and changed the sequence.

Having done so I then restarted the system and noticed that there was activity on the memory stick but the end result was the same. I still ended up with the dual boot display.  Again it brought me into 10.04.

I can't remember what the kernel no was when I cleaned out the large number of them that cluttered my display but currently it displays 2.6.32-30 & 2.6.32-29. In each case they reverted to 10.04 

I had a look at the boot folders on my HD and memory stick and there are large differences which only gets me wondering where I went wrong.  Should I start the whole procedure all over again and do you have any suggestions how I should tackle the matter.

---

### Post by Dutch70 on 2011-04-05
I really don't know, but on my system, hitting the escape key allows me to choose the hard disk, or usb stick. 

You may also want to check the md5sum of your .iso, if you haven't already.
[[COLOR="Red"]HowToMD5SUM[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM")

10.10 has a bug with some usb sticks, but usually you'll see something about libparted 2.3 or something similar if that's the issue.

---

### Post by oldfred on 2011-04-05
Are you setting up the USB flash drive as an installer that you can run, or do you want a full install. Your grub files as from a full install. Your syslinux file is from an installer version.

The 4GB is large for a installer but you can set persistence on and store some data. And 4GB is small for a full install, but can be done if you houseclean regularly and perhaps remove some of the very large apps and use smaller ones.

---

### Post by Scunnered on 2011-04-05
Again my thanks for your prompt reply.

****Dutch70 

I will give your suggestion a try and see if I get lucky.

**oldfred**

I had hoped that it would be a full install as I wished to do two things. Firstly I wanted to prove that I could boot from a USB drive with the intent of buying an external HD if it worked. Secondly I wanted to have the latest version of Shotwell as working photos is the biggest problem of switching my partner over to Ubuntu.

Once again my learning curve is on the up as I was unaware of the installer as against the full install option.

As usual I am open to further guidance.

Again my sincere thanks to you both for your assistance.  Will again look at matters and report back.

---

### Post by rrashkin on 2011-04-05
I had a problem with 10.10 UNR on my ASUS eeePC.  What I did to resolve it was create a clean USB installer, using the "reformat" option to get rid of anything that might have been on the drive before.

---

### Post by oldfred on 2011-04-05
I did a full install to a 16GB flash and installed into a 8GB partition. It works, but is slow particularly on writes. Both USB port speed & flash make it slower than a hard drive, but depending on your expectations it is functional.

Install to flash is just like any install to a second drive except you may need to change a few settings to reduce writes. With install to a second drive you have to use manual install so you get the combo box that lets you choose to install the grub bootloader to the MBR of the second drive.

It does not have to be encrypted:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html]("http://members.iinet.net/%7Eherman546/p19.html")
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

Use ext2 or ext4 without journal:
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

You want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.

Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

If only a 4GB flash, plan on regular housecleaning & consider uninstalling OpenOffice & Firefox as the two larges apps. You can use what lighter weight Versions of Linux use, like Chromium browser as it is lighter than firefox and Gnumeric and AbiWord.

---

