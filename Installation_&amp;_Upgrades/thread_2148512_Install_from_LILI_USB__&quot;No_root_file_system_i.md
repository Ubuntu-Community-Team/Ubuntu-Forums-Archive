---
title: "Install from LILI USB / &quot;No root file system is defined&quot; &amp; no device listed"
date: 2013-05-25
forum: Installation &amp; Upgrades
---

### Post by LLAA on 2013-05-25
I am attempting to run linux in a virtual window from USB so my xp remains unchanged. The distro is zorin but the issue is generic, not limited to zorin. 

Issues: 

1. Error: "No root file system is defined. Please correct this from the partitioning menu."
and
2. There is no device listed in "Installation type". 
and
NOtes:  I don't know even the vocabulary involved 
        I tried Wubi and ran into problems so am trying to run linux-zorin from USB 
        I tried searching forums for answers but have two problems: a) some solutions talk about running commands and making partitions, but the terminology is over my head, and b) when I see solutions for other people, I don't know if they are for my case, my situation (eg. running from USB). 

How trying to install: 

- I downloaded and ran Linux Live USB creator (Lili), selecting Zorin 
- clicked icon 'virtualize this key' 
- selected choice 1 (boot in the live system, but not sure the meaning of this choice),

result: virtualization opens (oracle vm virtualBox)

- I opened icon that says 'instal zorin'

I see box that says "Installation type" with these columns "device, type, mount point format, size".  I haven't the slightest clue what most of those are.  How can I learn what those are?  Important!  Sorry, when I attempt to take a screen shot, I get "failed to execute screen process". 

There are no items (no devices) at all on the list.  Why?  Important!  The unclickable table options low on the table include "new partition table, add, change, delete".  

Below that is drop down "Device for book loader installation".  And the device automatically listed is:  /dev/sda

The drop-down arrow does not list produce other choices or allow any text entry. 

Are there videos or a help manual to explain? 

Theories: 

Is my problem cause by not doing some complicated procedure that was supposed to be done prior to making my USB live-USB?  Is it caused by having tried to install using Wubi then deleting it in add/remove programs?   Or caused by having downloaded and uninstalled oracle on my hard drive?  

Finally: 

I don't know even some the vocabulary that is used when I undertake this process.  In addition, I feel uncomfortable in getting involved in petitioning before knowing what hazards to watch out for, and without knowing how much many manuals be involved.  What forums and video tutorials should I avail myself of to know what I am getting into?

---

### Post by gordintoronto on 2013-05-26
Simplify your life: go to pendrivelinux.com, install their software, use it to put Linux on a 4/8 GB flash drive. If possible, specify the maximum possible "persistent" space. Boot from the flash drive. You can run Linux without making any changes to your Windows system. It will be a little slower than if it were on the hard drive.

Virtualization requires a lot of knowledge which you do not have yet.

You might find it easier to get answers to questions if you use Ubuntu 13.04 or Linux Mint 14.

---

### Post by LLAA on 2013-05-27
That seems wise. 

Thanks!!!

---

