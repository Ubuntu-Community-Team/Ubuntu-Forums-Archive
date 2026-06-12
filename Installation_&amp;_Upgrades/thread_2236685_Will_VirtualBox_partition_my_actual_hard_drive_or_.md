---
title: "Will VirtualBox partition my actual hard drive or just the virtual hard drive?"
date: 2014-07-28
forum: Installation &amp; Upgrades
---

### Post by bulrush2 on 2014-07-28
System: VirtualBox on Win 7
Installing Ubuntu Server 13.10 as a VM

As you can see I'm installing Ubuntu server 13.10 on a PC and I'm new VMs and Ubuntu administration. The Unbuntu install process is asking to partition my hard drive. Is it going to partition only the VM hard drive? 

Also the Ubuntu install program has found no other OS and is asking to install the GRUB boot loader to my master boot record. Should I let the installer do this under my VM? Do I really need GRUB if it's a VM under Windows? 

Thank you for your patience. I know I'm a total sysadmin and VM noob but I'm really trying to learn.

---

### Post by TheFu on 2014-07-28
Unless you go really far out of your way - impossible without lots of extra effort - it is only going to touch hardware that your VM settings provide.  Following the wizard, a virtual-HDD should have been added to the VM settings. This is really a file on the HostOS - but inside the VM, it looks like the entire HDD.

So - no - do not worry - it will not harm the real HDD.

Yes, you need grub inside the VM.  It will not touch the hostOS at all, just the virtual-hdd inside THAT SINGLE VM.

Sometimes I find that watching a youtube video on something new, like creating a new VM in virtualbox, is helpful. It answers many common questions. [https://www.youtube.com/watch?v=nKPA1pdhLwY](https://www.youtube.com/watch?v=nKPA1pdhLwY) is an example.

I would stress again that loading a new system with 13.10 is a bad idea at this point. It is not supported. [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) has the official support information. 14.04 or 12.04 are the best choices for an Ubuntu Server.  A fresh install is much better than an upgrade later.  OTOH, if loading this up just-for-fun, then go ahead with 13.10, provided it will not be placed on the internet or used in any production way.

---

### Post by bulrush2 on 2014-07-28
> I would stress again that loading a new system with 13.10 is a bad idea at this point.

Yes I recall reading that here on the forums. But I don't want a new release like 14.04 full of new bugs, so I figured 13.10 was stable. But you think 12.04 is more stable than 13.10? No one has offered why they prefer 14.04 over an older, more stable version. They just blurt out "14.04". Because everyone knows the newest Windows x.0 never had bugs, right? :)

Right now I'm testing 13.10 but it will later be installed on a real physical server, as a VM, in a production environment.

I'm pretty good with computers, but I'm new to installing and doing admin on linux. I keep following directions for various things and they plain don't work. 

Example: I read 3 unique pages about changing the colors for my directories, using LS_COLORS, and none worked. I even read a page specifically for bash on Ubuntu. I just can't read the dark blue default for directories. And some color numbers from the web pages plain don't work.

---

### Post by Bucky Ball on 2014-07-28
Don't install 13.10. It has reached end-of-life. Use a supported release: 12.04 LTS or 14.04 LTS. Long-term support releases recommended for servers (and both have five years support).

We no longer support EOL release here. Please read this:

EOL release recommendations:
[http://ubuntuforums.org/showthread.php?t=2229730](http://ubuntuforums.org/showthread.php?t=2229730)

Please post a new thread if you have trouble installing a supported release. Good luck.

---

### Post by ian-weisser on 2014-07-28
> **bulrush2 said:**
> Yes I recall reading that here on the forums. But I don't want a new release like 14.04 full of new bugs, so I figured 13.10 was stable. But you think 12.04 is more stable than 13.10? No one has offered why they prefer 14.04 over an older, more stable version.

"Full of new bugs" implies you may be rather a few years behind the times on Ubuntu's development and testing strategies, and the tremendous investment in stability testing since 2012. Your description also suggests misunderstanding how bugs get fixed and stay fixed in future releases of Ubuntu.

You also misunderstand the purpose of LTS releases. They are not magically "more stable" than other releases. They merely update less often, primarily for the benefit of operational servers that need security updates but little else.

I prefer 14.04 over previous versions for two reasons:

1) It includes kernel, system, application, and UI bugfixes that have not been applied to previous versions of Ubuntu (only major bugs get fixed in previous versions).

2) It updates applications without resorting to unsupported, non-Ubuntu PPAs. It also brings major UI improvements (KED, Unity).

I've been using 14.04 on several machines for months. I have found it solid and stable on my various architectures. I have discovered only one bug, which persists from 13.10.

---

### Post by sp40140 on 2014-07-29
@bulrush2:
Could you please tell me how are you actually going about installing Ubuntu on VirtualBox?
Have you created a VM under VirtualBox for Ubuntu? if so, how much disk space have you allocated to it? what installation media are you using? iso file itself, bootable usb, bootable dvd?
When you are trying to install.. are you rebooting the machine?
I think the issues you are having are not dependent on the version of Ubuntu in this case.

---

### Post by bulrush2 on 2014-07-29
[LIST=1]
[*]I installed VirtualBox under Windows 7. 
[*]I downloaded an ISO of Ubuntu. 
[*]In Vbox I created a new VM, where it asks me for the location of an ISO file, which I gave it. 
[*]The ISO file then automatically runs the Ubuntu install program inside Vbox as a terminal window. I gave the VM about 8GB of disk space. 
[*]From there I configure Ubuntu server running as a VM. Sometimes I reboot (it's called "reset" in Vbox terminology) the VM after I change some configurations. 
[/LIST]

---

