---
title: "Cannot install ubuntu 6.06 in vmware"
date: 2006-07-07
forum: Installation &amp; Upgrades
---

### Post by SlayerMan on 2006-07-07
Hi folks,

I recently wanted to check out the new Ubuntu 6.06 (harddisk install). As I have no spare PC to test it on, I tried to install it inside of a VMware. Unfortunately, the install didn't work, I can't even start the installation program. It also seems to me that the Ubuntu that is started from the install-cd does get slower and slower as time moves on, until it actually freezes completely and I have to switch off the virtual machine.

This is what I already tried:

- kernel boot options ranging from nolapic, noapic, pci=noacpi, ide=nodma to acpi=off
- shutting down hald (as I read somewhere else that hald could cause problems because it constantly tries to access the cd drive)
- checking the md5sum of the iso
- performing a media check (took several hours to finish)

None of the above did change the situation. Can anyone help me?

Kind Regards
Steffen

BTW: Please, don't post things like "use an alternate cd". I want the graphical installer...

---

### Post by rcarring on 2006-07-07
I have successfully installed Dapper 6.06 in vmware. However I found I had better results using the alternate cd. The main difference between the Live CD and the alternate CD is as you say the GUI installer, however to use the Live CD you need to allocate at least 256MB Ram to the virtual machine and use a fixed size disk of at least 8GB so that you have room to add additional packages. With the text based installer, which is very simple and easy to use, you can install on 128MB Ram allocated with no problems.

I had similar results to you running the Live CD and trying to install Dapper into a vmware virtual machine. I understand that you are reluctant to use the text based install, but I would strognly recommend you re-consider as it does actually work.

---

### Post by SlayerMan on 2006-07-07
Hi again,

I followed your suggestions and gave the vm 256mb ram and 8gb disk...

And what can I say... It works like a charm. Even with the graphical installer. Next time, I should RTFSR (Read The ... System Requirements) ;) 

As for Ubuntu: I seem to pretty much like it. Maybe it's the distribution to finally replace my good old mdk 10.1 installation (which also works like a charm). One last question: what's about that "computer is freezing 1 to 2 times a day with ubuntu" that one can read in several threads in this forum? Is that problem already solved?

Kind Regards
Steffen

---

### Post by rcarring on 2006-07-07
I am glad that it worked. So far as the freeze ups you mention reading about, I cannot offer an explanation, but I can speculate that maybe the system ran out of swapped memory after the main system memory was filled or there was some issue with the hardware that Ubuntu was running on. Usually a freeze up is the result of running out of memory, but I don't know how Linux pages to swap.

---

### Post by Gorante on 2006-07-07
I have installed ubuntu 6.06 easily under VMWare Workstation, but i'm having a problem with VMWare ESX.

Actually during the installation it doesn't recognize the ethernet card and asks if i would like to use a firewire port detected instead.

Anyone had this problem, or know how to fix it?

---

### Post by chucksel on 2006-09-22
Has anyone installed it on ESX 3.0 successfully? Do you choose "OTHER Linux" for the guest OS or do you select 64 bit Linux (experimental) ?

---

### Post by BlackNash on 2006-09-22
I have installed on WMWare but I have many troubles with that because It doesn´t works like I want and always is blocked.

---

### Post by arkan over ip on 2006-09-22
Just install one of the images from [cdimage.ubuntu.com]("http://cdimage.ubuntu.com/vmware/")

---

### Post by wolfhard on 2007-06-08
I have downloaded this one: 
ubuntu-6.06.1-server-i386.iso

What is the difference between the one above and the 
ubuntu-6.06.1-server-i386.zip

??

I am not able to install the 
ubuntu-6.06.1-server-i386.iso version 
on an ESX Linux (other) virtual machine.

I boot directly from CD and get an error NET HELPMSG 2158.
The GUI that I am seeing behind is HP ProLiant Essentials Rapid Deployment Pack.

Any ideas?
Kind regards
Wolfhard

---

