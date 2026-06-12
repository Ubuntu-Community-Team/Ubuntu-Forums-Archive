---
title: "Cannot Instal on Lenovo 3000 C200"
date: 2008-07-19
forum: Installation &amp; Upgrades
---

### Post by ShiNki on 2008-07-19
I've been trying all night now, and I still can't install it.

I've downloaded the recent version, burned it on a DVD, it didn't work. I then burned it on a CD and the install menu came up this time, however when I press enter on the "Install Ubuntu", nothing happens. It just stays at that screen and my DVD/CD drive keeps on flashing and on flashing.

I've ran that checksum program and it says everything matches, so why is it causing problems? Is it because of the specs?

My Lenovo specs..

Intel Celeron-M 430 (1.63 Ghz)
512MB DDR2-667MHz
40GB SATA Hard Drive

---

### Post by overdrank on 2008-07-19
> **ShiNki said:**
> I've been trying all night now, and I still can't install it.

I've downloaded the recent version, burned it on a DVD, it didn't work. I then burned it on a CD and the install menu came up this time, however when I press enter on the "Install Ubuntu", nothing happens. It just stays at that screen and my DVD/CD drive keeps on flashing and on flashing.

I've ran that checksum program and it says everything matches, so why is it causing problems? Is it because of the specs?

My Lenovo specs..

Intel Celeron-M 430 (1.63 Ghz)
512MB DDR2-667MHz
40GB SATA Hard Drive

Hi and welcome, Have and when you say "I've ran that checksum program and it says everything matches" do you mean you checked the cd for errors or you have checked the iso with [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM). 
Whichever you have not done the you may try, and also burn the cd at the slowest speed. 
What is the model of the grpahics card?
 as you may want to try the alternate cd as it is a text base installer.

---

### Post by ShiNki on 2008-07-19
It's a Mobile Intel 945GM Express Chipset Family.

I did use that program. I believe I burned my CD at 16x. I'll try to burn a new one at 2x now. Oh and can I get a link to the text based installer? 

Much appreciated, thanks.

---

### Post by ugm6hr on 2008-07-19
> **ShiNki said:**
> Oh and can I get a link to the text based installer? 

[http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)

Follow one of these, go to the 8.04.1 link within whichever mirror, then select the appropriate "Alternate" CD (i386 / 32-bit).

Did you try running the Check CD for errors when you boot the CD?

PS: Try reading some of the links in the Start here thread linked in my signature below.

---

### Post by oilchangeguy on 2008-07-19
> **ShiNki said:**
> I've been trying all night now, and I still can't install it.

I've downloaded the recent version, burned it on a DVD, it didn't work. I then burned it on a CD and the install menu came up this time, however when I press enter on the "Install Ubuntu", nothing happens. It just stays at that screen and my DVD/CD drive keeps on flashing and on flashing.

I've ran that checksum program and it says everything matches, so why is it causing problems? Is it because of the specs?

My Lenovo specs..

Intel Celeron-M 430 (1.63 Ghz)
512MB DDR2-667MHz
40GB SATA Hard Drive

may just be the computer. i've got a toshiba satellite 1805 s-177 with a 800mhz. celeron cpu, 512mb of ram, and a 40gb hard drive. and it will not run anything newer than version 7.04.(and yes the cd's are ok) i even tried mandriva one spring 2008. it got to the desktop, but no background. and would not see my pcmcia wireless card.

---

### Post by ShiNki on 2008-07-19
Alright, the installation went fine with the alternate installer. 

But I have another problem..

I've installed everything for the windows wireless driver, the NDISWrapper Common, NDISWrapper Utilities, and the NDISGTK. However, I can't find the .inf driver anywhere.. I tried the Intel site since it's a Intel PRO/Wireless 3945ABG, but whenever I click the link to download it, the site just dies on me. Anyone have another download link for it?

---

### Post by ugm6hr on 2008-07-19
> Intel PRO/Wireless 3945ABG

Lots of people seem to have difficulties with this chipset, and yet it is supposed to be one of the best supported in Linux.

You should not need ndiswrapper at all (in theory).

---

### Post by ShiNki on 2008-07-19
> **ugm6hr said:**
> Lots of people seem to have difficulties with this chipset, and yet it is supposed to be one of the best supported in Linux.

You should not need ndiswrapper at all (in theory).


Then how do I get my wireless to work?

EDIT:

Ahh it seems that my wireless interface is disabled.. How do I enable it?

---

### Post by ugm6hr on 2008-07-20
> **ShiNki said:**
> Ahh it seems that my wireless interface is disabled.. How do I enable it?

Depends on what you have done to try and install it.

It should have just worked out-of-the-box with a few clicks.

But having installed ndiswrapper, you will have to undo any changes you made with ndiswrapper first.

Can you turn the wifi on and off with a switch or from the BIOS?  Other possibility is that Windows has a power save option which turns it off at shutdown, and will not allow it to be turned back on.

---

