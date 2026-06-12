---
title: "Ubuntu, XP, a Dell 8400 and fixmbr"
date: 2006-07-22
forum: Installation &amp; Upgrades
---

### Post by s13_mills on 2006-07-22
I apologise in advance for the length of this post, I thought I would write a post about this situation since I just finished a long ordeal working out the best way to repair my windows XP Pro install - I am VERY new to linux, having only really been introduced by my university this semester! I like Ubuntu though, and look forward to developing my knowledge.

My problem was this - I had installed Ubuntu 5.10 and used GRUB to boot either XP or Ubuntu, this was working fine, except I could not get my wireless card to work (tried ndiswrapper... etc). Being a windows user, I decided to reinstall Ubuntu, seeing as that solves most windows problems ](*,) 

But upon rebooting my computer, I got grub error 17 - this would normally be ok to fix with the XP install cd and fixmbr, but I own a Dell (this applies to all modern Dells using the factory partition system), and they have a 'different' partitioning system due to their system restore feature. I was unsure what to do, so I searched for an article telling me what was best... nothing, so I decided to write this now that I fixed it.

use the windows recovery console and fixmbr - it throws up an error message about a 'non-standard' partition system - I just hit yes, and it worked fine. My XP is back with no new issues.

Please note, however, that the Dell System restore feature is no longer available to me - I may or may not reinstall it later using DSRfix (google it).

I chose to use fixmbr because the Dell System restore facility returns the computer to the state it was in from the factory, and I have new hardware etc that could potentially have collided with this. Also, because of the early stage in boot that I got the GRUB error, I did not have the opportunity to automate the Dell process - I would have had to do it manually (google for how).

---

### Post by DetroitBaseball on 2006-07-22
Dell is made for Windows, it doesn't officially support Linux, and discourages the use of it on a Dell computer, so dont be surprised if you run into problems with Linux on a Dell.

---

### Post by Buffalo Soldier on 2006-07-22
s13_mills,

There is no need to apologise, you post was not very lenghty . In fact it was an informative post. I too am using a DELL computer (laptop), Inspiron 510m. When I first got my hands on that laptop, I used the DELL CDs to repartition, reformat and reinstall Windows XP. But I avoid installing the DELL "systems" applications / add-on software, especially things like their system restore feature. That seems to avoid any "incompatibility" with the laptop when I'm running Ubuntu or any other distro

DetroitBaseball,

DELL is one of the brand that I would recommend to anyone wanting to buy a laptop for Ubuntu. It's because most of the time they used tried and tested hardware especially those from Intel. Hardware from Intel have a nice support in Linux because it is well documented and some Intel hardware even have Linux drivers (but not under free/gpl licence).

---

### Post by s13_mills on 2006-07-23
Alright - so you reckon I'm best off just using the remade mbr and leaving the DELL system restore alone? It does seem that things like the DELL system restore and GRUB might 'tend' to collide for one reason or another!!!

---

