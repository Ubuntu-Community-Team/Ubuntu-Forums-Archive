---
title: "Installing Dapper on VMWare machine"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by DanyWu on 2006-06-03
Hi folks,

I successuflly installed and ran Breezy on VMWare machine. Unfortunately Dapper didn't do so well.

The machine has the same basic config, 256 RAM, etc.etc. The installation went smoothly and I was asked to reboot the machine after removing the CD. I did this but then the system hung at "Ok, booting the kernel".

Has anyone else encountered this before?

Cheers,
Dany.

---

### Post by GarlicFish on 2006-06-03
I just tried installing dapper server onto vmware and got the same thing.

Host machine: Dell Lattitude D600, 1GB, 1.6GHz Pentium M
Host O/S: Ubuntu dapper
Host Kernel:  2.6.15-23-686
VMWare Server: 1.0.0 build-24927 (tried on e.x.p-23869 as well)

Tried with bus logic and lsi logic guest scsi controllers, just going to try IDE.

---

### Post by rbalfour on 2006-06-03
Just tried with IDE disk. No go. 
Still hangs on "OK, Booting kernel"

I am using the latest VMWare on Ubuntu (Dapper).

Any ideas?

---

### Post by GarlicFish on 2006-06-03
I didn't get round to trying IDE, guess storage drivers isn't the issue.

I did boot into the rescue system and installed linux-image-2.6.15-23-386 into the failed server install.
With the non-server kernel, it boots nicely into a bash prompt.  :) 

I guess its a clash with something in the 2.6.15-23-server kernel that doesn't like VMWare.

Has anyone tried with the Desktop install CD rather than Server?

I'll give it a go in a bit.

---

### Post by GarlicFish on 2006-06-03
The Desktop Live/Installer CD installs and boots fine in VMware using the "Custom" machine defaults.

I'm gonna try adding in the VMWare tools.

I tried changing the Server kernel to the 2.6.15-23-686 version and that boots fine too.

Wonder what happens if you uninstall the server kernel then re-install it :-k

---

### Post by realmccoy on 2006-06-03
I upgraded from  the previous  version , now I can't even get into  the OS using Vmware

---

### Post by treesize on 2006-06-03
I had the exact same problem running 6.06 server under VMWare Server RC1 (build 24927).

---

### Post by DanyWu on 2006-06-04
I finally managed to install it using the OEM Install in the Alternate CD!

One annoying thing is I can't get VMWare Tools to work. I've installed the correct kernel headers and the tools compiled just fine. I rebooted and nothing happened! There's no sharing of mouse, etc.

---

### Post by rcarring on 2006-06-04
Are you running vmware under linux or xp?

You will need to add vmxnet to the /etc/modules file

You will need to enable the network adapter.

I found that the alternate cd found my nic if I had a floppy disk drive connected! Bizarre.

---

### Post by theaks on 2006-06-16
Has anyone had any luck with this issue?

I am trying to install Dapper server under VMware that is running on my Dapper desktop.

The install gets just stalls after i enter the new name for the server. Is there anyway to debug this and figure out what is going wrong? My vmware logs have nothing useful at all.

---

### Post by theaks on 2006-06-16
I fixed it :mad: it always the way.. post on the forums and then you work it out right after.

The MTU on my hosts eth0 was 1200 but the install was configuring the guest eth0 to 1500. This seemed to freeze the installer up.

---

### Post by Sn3f3ru on 2006-06-26
Can you please detail how you changed the MTU and where? Did you changed a setting in VMWare or in the guest OS?

Thank you.

---

### Post by erk on 2006-08-12
> **DanyWu said:**
> Hi folks,

I successuflly installed and ran Breezy on VMWare machine. Unfortunately Dapper didn't do so well.

The machine has the same basic config, 256 RAM, etc.etc. The installation went smoothly and I was asked to reboot the machine after removing the CD. I did this but then the system hung at "Ok, booting the kernel".

Has anyone else encountered this before?

Cheers,
Dany.

Same problem under Parallels Workstation, there is something screwey in the Ubuntu Server kernel that they both don't like.

What's the easiest way to install a normal Ubuntu kernel whilst installing Ubuntu Server?

---

