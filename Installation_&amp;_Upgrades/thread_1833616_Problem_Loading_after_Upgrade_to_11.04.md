---
title: "Problem Loading after Upgrade to 11.04"
date: 2011-08-26
forum: Installation &amp; Upgrades
---

### Post by sadssandiford on 2011-08-26
[SIZE=2]Hi All, can anyone help me?  Ive recently upgrade Ubuntu 10.10 to 11.04 using inbuilt software upgrade centre.  Everything downloaded and ran as it should until the system did its initial 11.04 boot when it tried to load and locked up at the UBUNTU title screen (the one with the 5 dots!).  If I press the power button on my laptop, Ubuntu then powers off as it should do!
The odd thing is, if on the GRUB screen I select "Previous Linux Versions" and then select;

"Ubuntu, with Linux 2.6.38-11-generic", 

it loads Ubuntu 11.04 correctly and works correctly!!!

It only locks up if I leave it to automatically select the initial entry on the GRUB screen;

"Ubuntu, with Linux 2.6.38-11-generic-pae"

How can I solve this problem, as I would like it to load the working 11.04 automatically????

Im new to Linux so easy answers please.......!![/SIZE]

---

### Post by dino99 on 2011-08-26
if you have a nvidia card/chipset:

sudo apt-get install dkms
sudo apt-get install nvidia-current

otherwise, at boot line, edit it and remove "splash" to see where the problem is.

---

### Post by slalomchip on 2011-08-26
I'm having the exact same problem as [sadssandiford]("http://ubuntuforums.org/member.php?u=1083981").  (Upgrading from 10.10, hangs on bootup at purple screen with "Ubuntu" in the middle with five red dots under it).  I have a nvidia chipset in the laptop.  How can I do the sudo commands you recommend if it never boots?

---

### Post by MAFoElffen on 2011-08-26
> **slalomchip said:**
> I'm having the exact same problem as [sadssandiford]("http://ubuntuforums.org/member.php?u=1083981").  (Upgrading from 10.10, hangs on bootup at purple screen with "Ubuntu" in the middle with five red dots under it).  I have a nvidia chipset in the laptop.  How can I do the sudo commands you recommend if it never boots?
Please refer to the first 3 posts of this sticky:
**[B]Sticky:**[/B] 			                         [COLOR=#008C00]**[all variants]**[/COLOR] 			 			[Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535")
It will explain how to get to a text console at bootup to diangose and fix graphics issues.  Installing Ubuntu's drivers is at the end of post 1.  Instructions for maunally installing nvidia's own drivers is at post 280.

---

### Post by sadssandiford on 2011-08-27
Thanks for info but is it really a driver problem, as if I load 11.04 through GRUB "load earlier version", it works fine.  Surely if it was a driver problem I wouldnt be able to get 11.04 to work at all!!

Dont forget Im a newbie so dont know anything about manual corrections

---

### Post by grahammechanical on 2011-08-27
This is the bit that I noticed

> "Ubuntu, with Linux 2.6.38-11-generic-pae"

I do not think that a standard upgrade from 10.10 to 11.04 through Update Manager would install the PAE kernel.

When you installed the PAE kernel you may not have installed all the packages needed by it.

Here is a link

[https://help.ubuntu.com/community/EnablingPAE]("https://help.ubuntu.com/community/EnablingPAE")

Regards.

---

### Post by sadssandiford on 2011-08-29
Hi, thanks for info! I think the problem is during upgrade to 11.04 it has installed PAE 64 bit version! When I run the "earlier" non PAE version it works fine! Remembering I'm a newbie how do I get rid of the PAE version and use non PAE version as default? Help please?

---

### Post by sadssandiford on 2011-09-02
Hi All,  I got the problem solved by another posting on this forum!

All I needed to do was book the older NON PAE version of 11.04.

Run Synaptic Package Manager

Search for "linux-generic-pae"

and uninstall the 4 installed items!!

Then re-boot the machine and GRUB gets rid of PAE version and defaults to non PAE version!!

Thanks all for your help!

Sads:P

---

### Post by sadssandiford on 2011-09-02
Sorry, I meant BOOT not BOOK!!!!

---

