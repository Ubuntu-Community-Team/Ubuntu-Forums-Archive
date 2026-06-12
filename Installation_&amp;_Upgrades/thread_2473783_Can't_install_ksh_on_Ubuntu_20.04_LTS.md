---
title: "Can't install ksh on Ubuntu 20.04 LTS"
date: 2022-04-13
forum: Installation &amp; Upgrades
---

### Post by the-scourge on 2022-04-13
Hello,

Having a heck of a time. Every time I try to install ksh, I get the following error:
"E: Unable to locate package ksh"

I use both "sudo apt-get install ksh" and "sudo apt install ksh" (and have also run "sudo apt-get update")

I was able to install "libc6" (using apt-get) successfully.
I should note that I'm "trying" Ubuntu so am running it currently from my flash drive - haven't installed it yet...
but I've run Ubuntu before on older laptop.

Please - any help would be appreciated. Not sure if I'm in the right discussion as I'm not having issue installing Ubuntu?

Thx,
JakeT

---

### Post by TheFu on 2022-04-13
Did you run **sudo apt update && sudo apt upgrade** first?
Which package does **apt search ksh** say to install?

Other Linux distros do the *update* automatically. Ubuntu does not.  Running it once a day should be sufficient if you are installing a bunch.  I only run it weekly, since I patch weekly.

BTW, bash is very much like ksh and is the Linux standard shell.  I was a tcsh user for far too long before changing to bash. Bash is the best of tcsh + ksh + lots of other shells.  Best of all, with bash, we don't need expr anymore. Math is built into the shell, finally.

---

### Post by the-scourge on 2022-04-13
After the update and upgrade, the **sudo apt install ksh **now outputs "E: Unable to locate package ksh"
A **apt search ksh **output I'll post in a minute (have to get it sent to the machine I'm on right now), but
it says something about Bourne shell and zsh.

BTW, the update/upgrade I did is writing all this to the flash drive, right? I'm in the process of setting up a dual boot
with W11 and Ubuntu and don't want this writing onto the SSD that I haven't setup for sharing yet.

Does any of this help? Why isn't it finding the ksh package?

---

### Post by TheFu on 2022-04-13
My 20.04 install found ksh and MirBSD Korn Shell.  Seems something could be wrong with the repos or DNS on the system?

---

### Post by the-scourge on 2022-04-13
Here is the output of **apt search ksh**

Sorting...
Full Text Search...
bash/focal-updates,now 5.0-6ubuntu1.1 amd64 [installed,automatic]
  GNU Bourne Again SHell

bash-doc/focal-updates 5.0-6ubuntu1.1 all
  Documentation and examples for the GNU Bourne Again SHell

shtool/focal 2.0.8-10 all
  portable shell tool from the GNU project

zsh/focal-security,focal-updates 5.8-3ubuntu1.1 amd64
  shell with lots of features

zsh-common/focal-security,focal-updates 5.8-3ubuntu1.1 all
  architecture independent files for Zsh

zsh-dev/focal-security,focal-updates 5.8-3ubuntu1.1 amd64
  shell with lots of features (development files)

zsh-doc/focal-security,focal-updates 5.8-3ubuntu1.1 all
  zsh documentation - info/HTML format

Thx so much for looking at this

---

### Post by ubfan1 on 2022-04-13
Unless you created your install media with persistence, there is probably no writable place to actually download and install a package.  mkusb gives you the option, then you can write some permanent changes into the install media, like new packages, wireless config, etc.

---

### Post by the-scourge on 2022-04-13
I just downloaded the ISO from ubuntu.com and used **USBimager **to create the image on the flash drive.
So, you're saying I might've written onto my existing SSD (that Windows 11 is currently residing on)? I
guess I'll find out if that hoses up my Windows. 
However, my flash drive should be writable, correct?

---

### Post by the-scourge on 2022-04-13
TheFU: Can you please send me your DNS setup and the other? What "repos" are you referring to?

---

### Post by ubfan1 on 2022-04-14
I'm not familiar with USBimager, but different tools may handle the Ubuntu ISO in different ways.  Simply doing a byte for byte copy of the ISO to a USB flash (using dd fro instance), will create a bootable media, with with the ISO9660 filesystem, which is read-only. There may be some ramdisk(s) created, so some things may be written, but they will disappear at shutdown. Other tools may break up the ISO a bit, into multiple partitions, some of which are writeable, and overlay the base (read only) filesystem.  This allows you to make some changes to the install media, like setting up your wireless config, so it is available the next time you boot the media.  Additional things may be added, like ksh too.  mkusb is the tool I last used for this.  Without a Linux to run mkusb, there may be other Windows tools (maybe Rufus?) which allow you to select persistence, but I don't know.  Or, just use the USB you created in try mode to mount another USB, and install to that.  That will then be a full install, and you can add (space permitting) the packages you want, before you commit to installing to the SSD.

---

### Post by deadflowr on 2022-04-14
ksh is in the universe repository, sometimes it is not enabled on new installs (for whatever reason).
```
sudo add-apt-repository universe
sudo apt update
sudo apt install ksh
```

---

### Post by the-scourge on 2022-04-14
deadflower - You are the man (or woman)! That was it. You are a life saver! Was ready to give it up.
Thanks so much! You made my day.

---

### Post by ActionParsnip on 2022-04-14
Please remember to mark as solved if all is well

---

### Post by TheFu on 2022-04-14
> **the-scourge said:**
> TheFU: Can you please send me your DNS setup and the other? What "repos" are you referring to?

My setup isn't good for non-experts. Sorry.  I gut the DNS setup from all my ubuntu systems, because my network has a DNS server for all client machines to use - including IoT devices.
As for repos, there's nothing special on my systems. Appears that the default focal repos have both versions of ksh.

```
ksh/focal 2020.0.0-5 amd64
  2020 version of the AT&T Korn Shell

mksh/focal 58-1 amd64
  MirBSD Korn Shell

```

I'm guessing the issue is that the system doesn't have enough virtual storage (in RAM) to allow it to behave as a regular system. Few people here run their systems from a read-only media like an Ubuntu Install environment except in emergencies.  I've done it after a HDD for a few days with limited stuff added. At each reboot, everything previously setup was lost.

There are ways to make a persistent storage area for a "Try Ubuntu/Install" setup based around the .iso file.  I've barely played with that situation.  A few friends run that way all the time, but I don't.  I know that mkusb and Ventoy both can create persistent setups able to run from Flash storage.

Don't worry about touching your SSD.  That won't happen unless you explicitly tell the installer to do that  ... or you use a file manager to access the internal SSD.

In a Try Ubuntu environment, can't you just get by with bash?

---

### Post by the-scourge on 2022-04-14
TheFu: The issue has been resolved (see post by **deadflowr**) - I had to explicitly add a repository.
But, thanks anyway for sending that info. As for bash/Try Ubuntu - I didn't plan on staying in the _Try Ubuntu _environment forever.
I'm doing a dual-boot thing with W11 and was only trying to see if the basic items I wanted (like ksh) were there and obtainable.

I am curious about one thing: in this "Try" environment, where are files you created or modified and downloaded packages stored?
Some temp/scratch area on the local drive or, indeed, on the inserted flash drive. After finally able to install ksh I then rebooted and
it was not there, so it would seem where ever the mods were done was cleaned up/deleted?

---

### Post by TheFu on 2022-04-14
> **the-scourge said:**
>  
I am curious about one thing: in this "Try" environment, where are files you created or modified and downloaded packages stored?
Some temp/scratch area on the local drive or, indeed, on the inserted flash drive.  

RAM. Nothing touched storage in a Try Ubuntu environment. That's part of the reason it is used only for emergencies and doesn't replace a regular install to disk/ssd.  

If you want more details, read up on overlay file systems.  I use this when using certain web browsers, so the files it touches doesn't actually touch any storage, ever. I'm not very trusting, sad to say.

---

