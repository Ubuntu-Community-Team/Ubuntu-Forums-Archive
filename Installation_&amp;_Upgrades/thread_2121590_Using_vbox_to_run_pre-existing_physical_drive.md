---
title: "Using vbox to run pre-existing physical drive"
date: 2013-03-02
forum: Installation &amp; Upgrades
---

### Post by longwalker on 2013-03-02
Hello all.  I'm new to all this.

I have a new install of Ubuntu 12.04 LTS on a new physical drive (sdb).

I would like to use Linux for most of my tasks while only using VirtualBox to access the existing Win7 loaded onto a different physical drive (sda) *without installing Win7 in VirtualBox.*  Win7 works fine in general and there is no need to tinker with it if un-necessary, except for the fact that I have no need or desire to let MicrosoftAnything connect to the Internet...

Both are loaded into the same tower which holds a late-model MSI motherboard and Intel i7-3770k chipset with 32gb RAM.  It also holds two SATA 1TB HDD units and some random LG optical device reader for spinning coasters.

[INDENT]*The only reason I'm using Win7 at all is due to the fact that I often need the full functionality of Nuance Dragon NatuarallySpeaking 12 Legal, for work and not only is it RAM intensive, but the fruity computer company which competes against the PC world doesn't have a box with enough juice, so I had a PC built instead.*
[/INDENT]

Looking through the GUI for vbox failed to produce a way to simply point the program at the hardware and pass GO to collect my $200. 

Is there a simple setting tweak, or do I have to install Win7 again?
[CENTER][B][I]
Thank you for your attention reading this message.  
No Dodo birds were harmed in the transmission or crafting of this posting.[/I][/B]
[/CENTER]

---

### Post by reedk on 2013-03-02
You have to install Windows 7 as a guest in VirtualBox. It sounds like you want both OS's at the same time, but to access Win7 while booted in Linux. THat does not work, as then Windows does not go through the boot process. This is exactly the sort of case where people generally install a new copy of WIndows within Virtualbox on Ubuntu.

VirtualBox does have a way to import a physical drive into Vbox for access, or even boot, but this is for __experts only__ and there is a pretty good chance you will screw up your Windows install. At the very least, you will force Windows to reconfigure all the hardware to the VirtualBox simulated hardware and not easily be able to reboot back into Windows.

Have you tried running it under Wine? It looks like there is some luck in getting NaturallySpeaking to run within WINE on Linux [http://appdb.winehq.org/objectManager.php?sClass=application&iId=2077](http://appdb.winehq.org/objectManager.php?sClass=application&iId=2077)

I would recommend you investigate reinstalling NaturallySpeaking within WINE, or doing a fresh install of Windows 7 within VirtualBox. I strongly discourage you from trying to reuse your existing Win7 install the way you are thinking (and hoping).

---

### Post by longwalker on 2013-03-02
I have seen the  __experts only__ instruction and, wading through search results found the MEGA Virtualization Thread on page Four (?!?!!!!?????) which points in that direction also.

Hopefully, it will not cause the box to catch fire when Win7 (under Ubuntu) accesses Win7 (on the disk itself).

Thanks for the quick reply.  That disc is around here someplace...

---

### Post by Kow on 2013-03-02
You cannot simply take a hard drive with a Windows install on it and put it into another computer (or virtualbox) and boot that same Windows. During the Windows installation process, Windows is actually installed with computer-specific settings. Linux is completely different and, depending on the distribution, should result in minimal problems when transferred between computers. Caveat: UEFI systems may cause problems, even for Linux.

If you really want to look into moving a Windows install between computers (or from a computer to virtualbox), you will get an idea of just how much work it is by going to this tutorial:
[http://theitbros.com/sysprep-a-windows-7-machine-%E2%80%93-start-to-finish/](http://theitbros.com/sysprep-a-windows-7-machine-%E2%80%93-start-to-finish/)

---

### Post by reedk on 2013-03-02
*> Hopefully, it will not cause the box to catch fire when Win7 (under Ubuntu) accesses Win7 (on the disk itself).*

It won't, because it's not going to access the Win7 part of the disk. It's roughly analogous like a new install and dual-boot. They will be complete unaware of each other. You could import the Win7 physical install as a raw disk to the Win7 virtual install, but I wouldn't for all the reasons you already found :)

---

### Post by haqking on 2013-03-02
You could take a clone using clonezilla of your install and then clone it into a Virtual Machine (I have done this a few times)

You can also convert a physical install into a virtual format such as a vmdk (VMware) and VMWare files can be opened with Virtualbox.

You can do the latter using VMware converter [https://www.vmware.com/products/converter/](https://www.vmware.com/products/converter/)

So pretty straight forward really.

You may get some luck with wine but see here [http://appdb.winehq.org/objectManager.php?sClass=application&iId=2077](http://appdb.winehq.org/objectManager.php?sClass=application&iId=2077)

Personally I would clone it, or the convert is reasonably straight forward also.

neither of these methods will screw with your existing install (unless you do something really stupid)

Peace

---

### Post by sudodus on 2013-03-02
> **longwalker said:**
> 
[INDENT]*The only reason I'm using Win7 at all is due to the fact that I often need the full functionality of Nuance Dragon NatuarallySpeaking 12 Legal, for work and not only is it RAM intensive, but the fruity computer company which competes against the PC world doesn't have a box with enough juice, so I had a PC built instead.*
[/INDENT]

Virtualisation means loss of computing power, so maybe Windows in vbox won't do it's job for you. You can try, but I think the dual boot solution is the best one.

---

### Post by reedk on 2013-03-02
Haqking's ideas are excellent recommendations.

---

### Post by haqking on 2013-03-02
> **sudodus said:**
> Virtualisation means loss of computing power, so maybe Windows in vbox won't do it's job for you. You can try, but I think the dual boot solution is the best one.

The OP has 32GB Ram in his PC and an i7 CPU, there is plenty of performance for Win7 in Vbox.

To the OP, I have Dragon working fine in a Win7 Virtual machine, it is a 32 bit VM as I only ever run 32 bit VM's as i dont see the point for home use in using a x64 bit VM and I have only 2 GB assigned to it.

Peace

---

### Post by longwalker on 2013-03-03
[LIST]
[*]reedk-  Thank you for the WINE suggestion, I started on WINE, but the NatSpeak11 disc isn't readily available, while the upgrade to 12 Legal is...  It is around here someplace, though. 
[*]haqking- Thank you for the clonezilla thought.  I will probably do that next if I can't get vbox to load Win7pro. 
[/LIST]

Win7 likes to hang after the automatic reboot and showing the "Setup is preparing your computer for first use" screen.  It has done this on both 32- and 64-bit versions of Win7pro.

At first I thought maybe Vbox wasn't allocating enough memory for the install, so I gave it 100GB.  Still no go.   More forum research suggests that my version of vbox from the Canonical repository is too far out of date.

Thanks to all for your input.  The physical drive is still in the original tower, with the original motherboard, etc.  I'm just trying to keep it physically separate from my primary OS in the event something goes very wrong; I have spent many hours training it.



[CENTER][B][I]Thank you for your attention reading this message.  
No Dodo birds were harmed in the transmission or crafting of this posting.[/I][/B]
[/CENTER]

---

### Post by haqking on 2013-03-03
> **longwalker said:**
> 
[LIST]
[*]reedk-  Thank you for the WINE suggestion, I started on WINE, but the NatSpeak11 disc isn't readily available, while the upgrade to 12 Legal is...  It is around here someplace, though. 
[*]haqking- Thank you for the clonezilla thought.  I will probably do that next if I can't get vbox to load Win7pro. 
[/LIST]

Win7 likes to hang after the automatic reboot and showing the "Setup is preparing your computer for first use" screen.  It has done this on both 32- and 64-bit versions of Win7pro.

At first I thought maybe Vbox wasn't allocating enough memory for the install, so I gave it 100GB.  Still no go.   More forum research suggests that my version of vbox from the Canonical repository is too far out of date.

Thanks to all for your input.  The physical drive is still in the original tower, with the original motherboard, etc.  I'm just trying to keep it physically separate from my primary OS in the event something goes very wrong; I have spent many hours training it.



[CENTER][B][I]Thank you for your attention reading this message.  
No Dodo birds were harmed in the transmission or crafting of this posting.[/I][/B]
[/CENTER]


yes Ubuntu repos are out of date as far as Vbox is concerned, download the binary from the virtual box website or add its own repo to stay updated, it is currently 4.2.8x and make sure you have the extensions pack also.

Peace

---

