---
title: "Kubunta and Vista WITHOUT dual-boot?"
date: 2008-04-14
forum: Installation &amp; Upgrades
---

### Post by GBC79 on 2008-04-14
Hi all, this is my first dip into Linux and my first post!

I, like many by the sounds of things, have decided to give Linux a bash and see if it really is worth what many suggest it is. I've used windows for decades so I'm pretty set in my ways and know my way around things, so this venture into Linux is nerve-wracking.

So to help me wean myself off of Windows (Vista currently), I want to install Kubuntu on my computer.

Here's the deal, I have a C: with Vista and a newly purchased external D: that I want to put my linux OS on. What I want to know is can I do this WITHOUT having to go through the whole dual-boot saga. I want the computer to boot to windows, and then if I want to switch to linux, go to the D: and enter a command and have Linux up and running?

Or is the only solution to set up a dual boot?

Sorry if this has been covered before, a search yielded a hundred posts on Dual-boots, but I'm trying to avoid this for now.

---

### Post by kellemes on 2008-04-14
> **GBC79 said:**
> Hi all, this is my first dip into Linux and my first post!

I, like many by the sounds of things, have decided to give Linux a bash and see if it really is worth what many suggest it is. I've used windows for decades so I'm pretty set in my ways and know my way around things, so this venture into Linux is nerve-wracking.

So to help me wean myself off of Windows (Vista currently), I want to install Kubuntu on my computer.

Here's the deal, I have a C: with Vista and a newly purchased external D: that I want to put my linux OS on. What I want to know is can I do this WITHOUT having to go through the whole dual-boot saga. I want the computer to boot to windows, and then if I want to switch to linux, go to the D: and enter a command and have Linux up and running?

Or is the only solution to set up a dual boot?

Sorry if this has been covered before, a search yielded a hundred posts on Dual-boots, but I'm trying to avoid this for now.

You could use a virtual machine like [Virtualbox]("http://www.virtualbox.org/") to run both os's at the same time. I do this all the time.

---

### Post by phidia on 2008-04-14
Is your external drive a usb drive? I have ubuntu set up this way on a laptop. Without the drive plugged in windows (vista) starts; with the drive plugged in at start I get the grub menu. 
You will need to use the alternate cd to do this since the livecd wants to install in a predefined way-the alternare cd allows you to select a drive to install to.
You need to do some [reading on the install]("https://help.ubuntu.com/community/Installation") though, and expect some difficulties.

I just mean that, based on what you've said about your windows experiance. It's almost impossible to learn something new unless you accept you don't know and will have to be a beginner for a while in your chosen pursuit of new knowledge.

You will need to learn about editing grub too since after you have installed to the external drive /boot/grub/menu.lst will require editing. See the link I supplied above.

---

### Post by GBC79 on 2008-04-14
Thanks for the tip. I've just looked briefly(at work!) into VBox and most of the protocols for setting it up describe setting Vista up on a Linux machine, and not the reverse.

Would this cause any compkications?

---

### Post by kellemes on 2008-04-14
> **GBC79 said:**
> Thanks for the tip. I've just looked briefly(at work!) into VBox and most of the protocols for setting it up describe setting Vista up on a Linux machine, and not the reverse.

Would this cause any compkications?

Following link works from XP but it's the same story for Vista.
[http://www.psychocats.net/ubuntu/virtualbox]("http://www.psychocats.net/ubuntu/virtualbox")

---

### Post by GBC79 on 2008-04-14
> **phidia said:**
> Is your external drive a usb drive? I have ubuntu set up this way on a laptop. Without the drive plugged in windows (vista) starts; with the drive plugged in at start I get the grub menu. 
You will need to use the alternate cd to do this since the livecd wants to install in a predefined way-the alternare cd allows you to select a drive to install to.
You need to do some [reading on the install]("https://help.ubuntu.com/community/Installation") though, and expect some difficulties.

I just mean that, based on what you've said about your windows experiance. It's almost impossible to learn something new unless you accept you don't know and will have to be a beginner for a while in your chosen pursuit of new knowledge.

You will need to learn about editing grub too since after you have installed to the external drive /boot/grub/menu.lst will require editing. See the link I supplied above.
Yes, it's a USB drive for my laptop. Thanks for the link...I'll be in my corner doing some reading.

---

### Post by zetetic on 2008-04-14
> **GBC79 said:**
> Hi all, this is my first dip into Linux and my first post!

I, like many by the sounds of things, have decided to give Linux a bash and see if it really is worth what many suggest it is. I've used windows for decades so I'm pretty set in my ways and know my way around things, so this venture into Linux is nerve-wracking.

So to help me wean myself off of Windows (Vista currently), I want to install Kubuntu on my computer.

Here's the deal, I have a C: with Vista and a newly purchased external D: that I want to put my linux OS on. What I want to know is can I do this WITHOUT having to go through the whole dual-boot saga. I want the computer to boot to windows, and then if I want to switch to linux, go to the D: and enter a command and have Linux up and running?

Or is the only solution to set up a dual boot?

Sorry if this has been covered before, a search yielded a hundred posts on Dual-boots, but I'm trying to avoid this for now.

You should be able to choose the booting drive on BIOS.

Please don't refer to disk drives as C: and D:. There is no such thing as C: and D: - only in Windows.

---

### Post by element_G on 2008-04-15
Sounds like virtualization is your only option. If I understand your post, you always want to boot to Vista (for the time being ;-))  and then start Linux from a program (i.e. virtualization software)

When it comes to virtualization it doesn't matter where you have the virtual OS installed so an external drive would work. 

Along with VirtualBox , [VMware]("http://www.vmware.com/") is another good virtualization program, if memory serves me correctly [VMware Server](http://www.vmware.com/products/server/) is the one to try.

---

### Post by kellemes on 2008-04-15
For virtualization there also is [QEMU]("http://fabrice.bellard.free.fr/qemu/").

---

### Post by GBC79 on 2008-04-15
Thanks everyone for their responses. I just came across a program called WUBI which seems to be what I want. Get to load Linux from within windows.

ANyone have any experience with WUBI?

---

### Post by kellemes on 2008-04-15
> **GBC79 said:**
> Thanks everyone for their responses. I just came across a program called WUBI which seems to be what I want. Get to load Linux from within windows.

ANyone have any experience with WUBI?

No experience.. just a link.
[https://wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide")
Good luck.

---

### Post by GBC79 on 2008-04-15
Apparently, from what I read, Wubi allows you to install a Linux OS from Windows as if it were a Windows program. Wubi then does all the install, boot-loading for you, with minimal/no intervention by the *noob* user.

Sounds like a good resource, only thing is that it seems geared toward Ubuntu exclusively...so what if I want to try several Linux desktops?

---

### Post by kellemes on 2008-04-15
> **GBC79 said:**
> Sounds like a good resource, only thing is that it seems geared toward Ubuntu exclusively...so what if I want to try several Linux desktops?

Virtual Machine seems to be the way to go..
I have currently 5 distro's running in a vm for reviewing purposes, all working fine.

---

### Post by GBC79 on 2008-04-15
Kellemes, with Virtual Machine, does the virtual desktop start at startup, are will it only start at your request. Ie. if I have 5 desktops I'm playing with besides my Vista, will all 5 start with every boot? This would seem like a HUGE drain on comp resources?

Secondly, with these virtual desktops, can I access windows files and folders?

Thirdly, if I do make the plunge and decide to do a Linux only PC, how easy is it to transition all my work from the virtual desktop to a permanant desktop?

Sorry if these questions are very elementary, really do appreciate everyones help.

---

### Post by kellemes on 2008-04-15
> **GBC79 said:**
> Kellemes, with Virtual Machine, does the virtual desktop start at startup, are will it only start at your request. Ie. if I have 5 desktops I'm playing with besides my Vista, will all 5 start with every boot? This would seem like a HUGE drain on comp resources?

Secondly, with these virtual desktops, can I access windows files and folders?

Thirdly, if I do make the plunge and decide to do a Linux only PC, how easy is it to transition all my work from the virtual desktop to a permanant desktop?

Sorry if these questions are very elementary, really do appreciate everyones help.

Using Virtualbox I simply bootup one of the virtual machines whenever I want, indeed you're running 2 os's at the same time, I never really use 3+ os's.
See [screenshot of my os-list]("http://img519.imageshack.us/my.php?image=vbrp4.png").

All about sharing folders between host and guest... [http://www.virtualbox.org/download/UserManual.pdf]("http://www.virtualbox.org/download/UserManual.pdf")

The third question I really don't know..
But maybe there are ways to base a "real" install on the package-list of the "virtual" install, something like that seems possible.
Personally I'd go for a fresh install.

---

### Post by GBC79 on 2008-04-15
Thanks Kellemes. So, correct me if I'm wrong. With virtual Box, you can startup on windows, and not have to see any of the other OS's unless I choose to switch one on and play with it?

---

### Post by kellemes on 2008-04-15
> **GBC79 said:**
> Thanks Kellemes. So, correct me if I'm wrong. With virtual Box, you can startup on windows, and not have to see any of the other OS's unless I choose to switch one on and play with it?

Indeed.
It's just an application you startup.. just like your word processor.

---

### Post by GBC79 on 2008-04-15
Nice, I really prefer that to dual-boot setup.

Just went to the Virtualbox website, and apparently it doesnt support all Linux distros: I was hoping to try Sabayon, MEPIS and PClinusOS and compare to Kubuntu. Even though these were not on the list, if they use the Linux 2.4 or 2.6 kernels, could I still use them?

---

### Post by kellemes on 2008-04-15
> **GBC79 said:**
> Nice, I really prefer that to dual-boot setup.

Just went to the Virtualbox website, and apparently it doesnt support all Linux distros: I was hoping to try Sabayon, MEPIS and PClinusOS and compare to Kubuntu. Even though these were not on the list, if they use the Linux 2.4 or 2.6 kernels, could I still use them?

Yes.
It may be that some distro's won't work simply because they can't handle the virtual hardware.
But 9 out of 10 work fine. Just give them a try, you only need to download the iso of a particular distro and boot from it using virtualbox.

---

### Post by GBC79 on 2008-04-15
If I have the LiveCDs on hand...can I set it up from there rather than download the distros?

---

### Post by kellemes on 2008-04-15
> **GBC79 said:**
> If I have the LiveCDs on hand...can I set it up from there rather than download the distros?

Sure.. that's what a lot of people do when installing a distro.. using the LiveCD.

---

### Post by kellemes on 2008-04-15
just mount the cd from virtualbox, and use it as the disk to boot the new virtual machine from.

---

### Post by GBC79 on 2008-04-15
Once I've mounted and installed from the CD, I then no longer have a need to use the CD correct...no need to boot off it?

---

### Post by lespaul_rentals on 2008-04-15
> **GBC79 said:**
> have decided to give Linux a bash

Did anyone else catch this?  :lolflag:

I like this guy already.  Welcome, GBC!  :)

> **GBC79 said:**
> Once I've mounted and installed from the CD, I then no longer have a need to use the CD correct...no need to boot off it?

Once it is fully installed, no.  It will be on the hard drive and you will have no need for the CD any longer.

---

### Post by GBC79 on 2008-04-15
Thanks for the reply! Will be taking the big plunge as soon as my discs arrive. So far have ordered: Ubuntu 7, Kubuntu 7, simplyMEPIS7.0, openSuSE 10.3, Sabayon 3.4, PCLOS 2008, MANDRIVA 2008, Fedora 8 and Linux MINT 4.0.  At $2 a pop, guess there's no harm in trying the bunch and making a direct comparison starting with Ubuntu and Kubuntu to see the differences in gnome vs KDE with the same OS.

---

### Post by lespaul_rentals on 2008-04-16
> **GBC79 said:**
> Thanks for the reply! Will be taking the big plunge as soon as my discs arrive. So far have ordered: Ubuntu 7, Kubuntu 7, simplyMEPIS7.0, openSuSE 10.3, Sabayon 3.4, PCLOS 2008, MANDRIVA 2008, Fedora 8 and Linux MINT 4.0.  At $2 a pop, guess there's no harm in trying the bunch and making a direct comparison starting with Ubuntu and Kubuntu to see the differences in gnome vs KDE with the same OS.

Cool.  Have fun, buddy.

My personal favorites out of the selection you ordered would be OpenSuSE 10.3 and Linux Mint 4.0.  Both fantastic distros.  OpenSuSE has some of the best features out of any distro I've tried.  It's extremely professional and probably the best distro for productivity.  Also, recognizes a lot of hardware out-of-the-box.  Don't let the "deal with the devil" rumors scare you away from OpenSuSE, I think you'll like it.  ;)

I personally like KDE better than Gnome.  Kubuntu is a great distro, and it was my primary distro for almost 8 months.

Post back here if you need anything.  :)

---

### Post by GBC79 on 2008-04-16
Thanks for the suggestions. So far, I've just been playing with PCLOS2008-Gnome...figure I'll give it a full try before trying the others. 

Install went perfect, just having issues setting up my internet access (LAN and Wireless) and adjusting resolution. Wont give me anything more than 1200 x 760 (or something like that). Need to play around with it and do a lot of reading up on the matter. Not sure if this is an OS thing or the setup from VirtualBox (which went flawless!). Also need to figure out how to add drivers for my NVIDIA 8400 GS graphics card.

Lost to learn in linux...this is a BIG change from windows days! Of course I know this is not the forum for help, so please dont feel I'm impinging on the Ubuntu server! if this is inappropriate, my sincerest apologies.

---

### Post by kellemes on 2008-04-17
> **GBC79 said:**
> Thanks for the suggestions. So far, I've just been playing with PCLOS2008-Gnome...figure I'll give it a full try before trying the others. 

Install went perfect, just having issues setting up my internet access (LAN and Wireless) and adjusting resolution. Wont give me anything more than 1200 x 760 (or something like that). Need to play around with it and do a lot of reading up on the matter. Not sure if this is an OS thing or the setup from VirtualBox (which went flawless!). Also need to figure out how to add drivers for my NVIDIA 8400 GS graphics card.


You won't be able to install drivers for your card, you are in a "virtual" machine, so you have a "virtual" videocard.
Search [the forums]("http://forums.virtualbox.org/index.php") for getting to higher resolutions.
Don't forget the install the guest additions.

---

