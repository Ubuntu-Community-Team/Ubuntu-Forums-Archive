---
title: "In VBOX with XP install Ubuntu."
date: 2011-08-14
forum: Installation &amp; Upgrades
---

### Post by nichos on 2011-08-14
I Wubi installed Ubuntu 11.04 within XPprf on VBox, I get the menu, select Ubuntu starts loading to normal orange desktop & this comes up:- 
   "....piix4-SMBUS 0000.000-7.0 Smbus Uniniitialised Upgrade Bios or use Force_Addr=dxaddr...."

& then freezes. Which bios is that? the computer works fine with its bios.

Wubi install of 11.04 works fine in my other 2 home computers but they have no VBox.

---

### Post by MG&amp;TL on 2011-08-14
I don't know but on Windows 7 with Lubuntu in Vbox, I get the same message but it boots...:confused:

---

### Post by Old_Grey_Wolf on 2011-08-14
> **nichos said:**
> I Wubi installed Ubuntu 11.04 within XPprf on VBox, I get the menu, select Ubuntu starts loading to normal orange desktop & this comes up:- 
   "....piix4-SMBUS 0000.000-7.0 Smbus Uniniitialised Upgrade Bios or use Force_Addr=dxaddr...."

& then freezes. Which bios is that? the computer works fine with its bios.

Wubi install of 11.04 works fine in my other 2 home computers but they have no VBox.

Why would you install 11.04 using WUBI when you have VirtualBox? Why not just install 11.04 as a its own Virtual Machine in VirtualBox? If you have VirtualBox there is no reason to use WUBI.

:confused:

---

### Post by MG&amp;TL on 2011-08-14
I did think there was something slightly fishy...

---

### Post by Old_Grey_Wolf on 2011-08-14
> **MG&TL said:**
> I did think there was something slightly fishy...

I didn't read anything "fishy" in the post; however, I think there may be a lack of knowledge about what virtualization is or how virtualization works.

---

### Post by nichos on 2011-08-15
Thanx Woolf,

I have a reason to try Wubi here but, will not go in to that. Just wanted to try Wubi in Vbox. Is that asine now.

You are right I have'nt a clue on virtualization, I find it fascinating & am trying to learn, please put me right. Does it not take Wubi? If not OK otherwise I would like to correct the error & get on with it.

---

### Post by MG&amp;TL on 2011-08-15
I see no reason why it shouldn't. Have you tried reinstalling wubi? I'm not entirely sure how wubi works,however.

By slightly fishy, I meant, 'what's the point' :)

---

### Post by nichos on 2011-08-15
SOLVED

I give up.

The point was that VBox is supposed to try various programs.

---

### Post by Old_Grey_Wolf on 2011-08-15
> **nichos said:**
> SOLVED

I give up.

The point was that VBox is supposed to try various programs.

I wish you hadn't given up so quickly. Some of us live in different time zones or have other commitments; such as, family lives, work, or school schedules.

WUBI was intented to allow someone to install Ubuntu within Microsoft Windows for the purpose of trying Ubuntu without the need for an install requiring repartitioning. WUBI was not intended for long term use. The last time I checked, WUBI still had a maximum virtual disk size limit for Ubuntu of 30GB; therefore, I don't think the test before you install it by repartitioning philosophy has changed. I doubt that anyone anticipated that someone would install Microsoft Windows as a VM in Virtualbox, and then use WUBI to install Ubuntu within that Windows VM. I doubt that anyone ever tested WUBI in that configuration or planned for it to be used that way. You are trying do do something very unusual; therefore, I'm not surprised that you are having problems with it.

Most people would have installed Windows as a VM; then, installed Ubuntu 11.04 as another VM. That would allow them to use either VM or use both VMs if they have the memory and cpu resources to support running a host OS, and two guest OSs at the same time. By running two VMs, you don't have to reboot the Microsoft Windows VM to switch OSs as you would with WUBI. As I said, I doubt that anyone ever tested WUBI in that configuration or planned for it to be used that way.

---

