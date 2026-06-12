---
title: "Install hangs at 74% -  storing language"
date: 2010-04-06
forum: Installation &amp; Upgrades
---

### Post by blimkin on 2010-04-06
Hi

I'm trying to install Ubuntu server 9.10 x64 on the following hardware:

Amd 64 2.2 Ghz
Kingston Hyper x 1gb
PATA 160gb HD
DFI Lanparty Motherboard

The issue is that the install gets stuck at 74% - storing language.

I have tried different ISO's and burnt different CD's.

Has anyone else had this issue?

Thanks in advance.

Stephen Turner

---

### Post by dstew on 2010-04-06
Does the Ubuntu Install CD work OK in other computers?

---

### Post by blimkin on 2010-04-06
I don't know to be honest but I have re-downloaded the iso and burnt the CD twice for each Iso now. 
Any ideas?

---

### Post by dstew on 2010-04-06
Did you burn at a slow speed (no more than 4x)? Did you do the CD integrity test (an opening menu option)?

---

### Post by blimkin on 2010-04-06
Yes done both. To be honest I'm getting quite frustated with it. I know the hardware is compatible because I've installed Debian before, I might just go back to that and install the server packages. I only want it as a Vmware host. 

Unless you have any other ideas?

---

### Post by dstew on 2010-04-07
Sorry, I don't have any more ideas at present. You could try other install methods, like [netboot]("http://cdimage.ubuntu.com/netboot/karmic/"). [This document]("https://help.ubuntu.com/community/Installation/Netboot") has information on netboot, and links to other install methods that you might try. It is kind of old, maybe you should look around for other How-Tos. I have done a netboot install on a NAS device that had no disk drives, and it worked OK. You have to set up another computer on your network as a DHCP-netboot-tftp server. [Here]("https://help.ubuntu.com/community/Installation/WindowsServerNetboot") is a document on setting up a Windows computer as the server.

---

