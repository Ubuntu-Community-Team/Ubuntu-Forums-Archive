---
title: "Installing VMWARE tools with Ubuntu as Guest?"
date: 2007-06-14
forum: Installation &amp; Upgrades
---

### Post by tigerplug on 2007-06-14
Hi everyone,

I am at work running Windows XP professional with VMWARE Server installed running Ubuntu as the guest OS.

I can't install VMWARE tools at all. I have searched the forums and in particular I have been following this guide: [http://blog.sirkevi.com/2006/08/17/i...-ubuntu-guest/](http://blog.sirkevi.com/2006/08/17/i...-ubuntu-guest/)

Im having no luck, for example after I enter this command into the terminal:

*sudo apt-get update*

I am getting a long reply, the end of which is:

[I].....................................Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/...rce/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/...rce/Sources.gz) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied. )
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/...rce/Sources.gz](http://ie.archive.ubuntu.com/ubuntu/...rce/Sources.gz) 407 Proxy Authentication Required ( The ISA Server requires authorization to fulfill the request. Access to the Web Proxy service is denied. )
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
shane@shane-desktop:~$[/I]

Can anyone advise me? I have already set up the static IP for the machine and entered the Subnet Mask, DNS and Gateway by going to *System-> Administrator->Network* from the GUI. Is there anywhere else that I have to enter settings or is it an issue with ports?

---

