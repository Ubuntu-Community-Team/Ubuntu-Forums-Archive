---
title: "Full disk encryption with LVM and dual boot?"
date: 2011-01-15
forum: Installation &amp; Upgrades
---

### Post by johnnyquest on 2011-01-15
Hello all,

So I recently came across this method for doing a full disk encryption install using LVM: [http://readm3.org/os/ubuntu/full-disk-encryption-lvm-luks](http://readm3.org/os/ubuntu/full-disk-encryption-lvm-luks). It looks like this method might have advantages over the Alternate CD setup method, although I'd be interested in hearing peoples' thoughts about the pros and cons of this method.

Anyway, I already have Windows 7 on my machine and want to do a dual boot setup with my encrypted Ubuntu, but the guide above doesn't seem to to address how this would be done (the automatic script posted in the guide doesn't seem to allow this possibility either). I assume it would simply be a matter of setting up everything in partitions outside of the Windows partition, but could anyone, possibly someone who has experience with this method in a dual boot setup, offer some advice on how to go about this?

A few other questions:
[LIST]
[*]Is it best to shrink my Windows 7 partition with the disk manager in Windows, or should I use GParted? Just wondering if GParted would be more flexible than shrinking in Windows.
[*]Will grub be automatically setup so I can select which OS I want to boot when I turn my computer on? Or is there an extra step in this process I need to take to ensure grub is setup properly for dual boot?
[*]I'm doing this all on an SSD; are there any other considerations I'd need to keep in mind for installing and running ubuntu in a dual boot setup on an SSD?
[/LIST]

Big thanks to anyone who can offer any help!

---

### Post by solar george on 2011-01-15
To be honest I don't really see that much of an advantge over the using the alternate cd and just encrypting your home partition (or just encrypting your home directory which is offered by the live installer) assuming that the use case for the encryption is simply to protect your user data if your laptop is stolen.
Sure there are theoretical attacks if you don't have the full system encrypted (for example a keylogger could be installed into the system by a sufficiently skilled attacker) but if you're facing this kind of opponent then they could also compromise the unencrypted boot partition in the setup you linked to.
The most interesting one is allowing hibernation (sleep would work as normal in either setup) since the setup used by the installer wipes the swap partition (which stores the hibernation data) on every boot to prevent possible key or data recovery from the hibernation data.
I would also say that you're more likely to be able to get help with a system setup in the way that the alternate cd does it because that's more familiar to most people using ubuntu, but go ahead and say why you want the encryption since that'll allow people to give you more specific advice.

---

### Post by johnnyquest on 2011-01-15
> **solar george said:**
> To be honest I don't really see that much of an advantge over the using the alternate cd and just encrypting your home partition (or just encrypting your home directory which is offered by the live installer) assuming that the use case for the encryption is simply to protect your user data if your laptop is stolen.
Sure there are theoretical attacks if you don't have the full system encrypted (for example a keylogger could be installed into the system by a sufficiently skilled attacker) but if you're facing this kind of opponent then they could also compromise the unencrypted boot partition in the setup you linked to.
The most interesting one is allowing hibernation (sleep would work as normal in either setup) since the setup used by the installer wipes the swap partition (which stores the hibernation data) on every boot to prevent possible key or data recovery from the hibernation data.
I would also say that you're more likely to be able to get help with a system setup in the way that the alternate cd does it because that's more familiar to most people using ubuntu, but go ahead and say why you want the encryption since that'll allow people to give you more specific advice.

Yeah, I've considered other encryption options but full disk encryption seems to be pretty seemless after you enter the password at the beginning and it's what I'm most used to. I'm doing it to secure my Ubuntu setup while leaving my Windows 7 install for games and other Windows specific programs.

I'm not an expert, though, so if setting this up with the alternate install cd method makes it easier to get help in the future I might just go with that. Do you know of an up to date tutorial that could help me out with that? Thanks

---

### Post by solar george on 2011-01-15
To be honest if you've no specific reason to got for full-disk encryption you may as well use the standard installer and (on the user setup page) select "require my password to login and decrypt my home directory" (or the option with a similar name) which will just encrypt your home directory with your login password and do so entirely seemlessly, its also the officially recommended method for encrypting your data.

---

### Post by johnnyquest on 2011-01-15
You don't know of a good current tutorial for the alternate cd method then?

Also, any thoughts on whether using Windows or GParted to resize my Windows partition would be better?

---

### Post by solar george on 2011-01-16
Take a look here [https://help.ubuntu.com/10.10/installation-guide/i386/module-details.html](https://help.ubuntu.com/10.10/installation-guide/i386/module-details.html) (just scroll down to the section about partitioning) its rather wordy since its based on the debian installer manual. I've not got any experiance of windows 7 but if it supports shrinking its filesystem (and google doesn't come up with lots of horror stories about it) then I'd probably use that since its the file system's official tool (on the other hand I know its many times faster to use linux tools to create an NTFS file system than using XPs tools so YMMV)

---

