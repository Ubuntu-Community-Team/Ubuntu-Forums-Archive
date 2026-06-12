---
title: "Upgrade crashed, what now?"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by twygly on 2007-04-23
Almost at the end, just prior to clean-up and the upgrader stopped responding, keyboard did nothing and no response to mouse clicks.

Forced reboot but doesn't get past the first logo.

Have Live CD but not sure what to do.

Any ideas for a newbie non-techie...

---

### Post by az on 2007-04-23
Hmm.

Can you boot the live cd, and chroot into your Ubuntu install and run

sudo apt-get -f install

---

### Post by twygly on 2007-04-23
After a few reboots I get into a screen that starts "BusyBox v1.1.3..." with a command promt "(initramfs)"

---

### Post by twygly on 2007-04-23
Please explain "chroot into your Ubuntu install" - I can boot off the CD so this sounds like an options I just don't know how.

---

### Post by az on 2007-04-23
Boot the live cd.

Open a terminal and mount your installed linux partition somewhere.  If it is hda5, then it would be

sudo mount /dev/hda5 /mnt

then 

sudo chroot /mnt

That will put your terminal in that filesystem.   It's as if you are running from that partition except your net connection and kernel are already loaded into memory.

---

### Post by twygly on 2007-04-23
Ok, managed the chroot part, thanks for the explaination.

But the install/upgrade says there's nothing to be done.

What now? Can the upgrade be reversed?

---

### Post by az on 2007-04-23
> **twygly said:**
> Ok, managed the chroot part, thanks for the explaination.

But the install/upgrade says there's nothing to be done.

What now? Can the upgrade be reversed?

What about running

sudo apt-get istall ubuntu-desktop

and 

sudo apt-get dist-upgrade

If that does not work, can you try booting an older kernel?

---

### Post by twygly on 2007-04-23
Nothing :-(

Wouldn't know how to boot boder kernel.

The order of events is:
1. GRUB loading...
2. Starting up.
3. Please wait

and then just a cursor!

There must be a broken file or something? What's supposed to happen next?

---

### Post by twygly on 2007-04-23
After about 10min of cursor I then get the "BusyBox" prompt...

---

### Post by twygly on 2007-04-23
sorry, what it also says is something about 'tty job control" being off (which generates an error)

Found an article that suggests the following - would these be ok to do? Applicable to Feisty?

> sudo mkinitramfs -o /boot/initrd.img-2.6.17-10-generic 2.6.17-10-generic

sudo update-grub

sudo aptitude reinstall linux-restricted-modules-2.6.17-10-generic



---

### Post by twygly on 2007-04-23
> **az said:**
> 
sudo chroot /mnt

I'm starting to suspect I did this wrong... I tried again to chroot and it tells me I do not have permission  to run /bin/bash

---

### Post by twygly on 2007-04-23
Ok, this is like a running commentry (in the hope that someone is listening).

I've now managed to correctly chroot and I get a message that dpkg was interupted.

I evently go to /var/lib/dpkg/updates and find that 0028 and 0029 just have "#padding" repeated endlessly...

And ideas? Anyone?

---

### Post by az on 2007-04-23
> **twygly said:**
> 
And ideas? Anyone?

Run 
sudo apt-get -f install

and it may prompt you to run

sudo dpkg --config -a

That will configure packages that were not finished installing.

---

### Post by John Jason Jordan on 2007-04-23
> **az said:**
> What about running
sudo apt-get istall ubuntu-desktop
and 
sudo apt-get dist-upgrade
If that does not work, can you try booting an older kernel?
I had exactly the sasme problem as twygly upgrading Edgy amd64. Upgrading from Update Manager hung. I was watching the Details and it hung at "installing new version of config file /etc/apt/apt.copnfig.d/01ubuntu..." It didn't say nit was hung, just nothing further was happening. I waited a while, then discovered the mouse and keyboard were dead. I had no chopice but to hit the power button.

When I rebooted the old Grub boot menu came up and I let it continue. It hung with a cursor blinking in the upper left corner of the screen. After a while I get a BusyBox message:

/bin/sh: can't access tty; job control turned off
(initramfs)

Typing 'help' gives a list of commands, but none looked very useful. I did navigate to /etc/apt/apt.conf and idscovered that the requested file is not there.

At that point I used my other computer to get on the net and found this thread. I booted the Feisty live CD, then made a folder /media/hda2 and mounted the boot partition (hda2) on it. Then I chrooted to it (learned something -- didn't know you could do that!) and tried apt-get -f install. Sure enough it said I needed to do dpkg --configure -a, which I did. (After mounting hda2 I noticed in /etc/apt/apt.conf.d/ there was a file labeled "50 unfinished updates.") Dpkg woked for quite a while, but finally ended saying there were too many errors. Just in case it fisxed enough things to get the computer to boot I shut down and restarted, buty it still hangs with the error message and the (intramfs) prompt. I tried the live CD again, repeating the process, but it dpkg still won't  fix everything. 

I really don't want to reinstall from scratch. I do have a full backup of ~/ made last night before the upgrade (I'm not totally stupid), but I have a zillion programs installed and each has tons of personal configurations. Does anyone have any further suggestions for how to fix a broken upgrade?

---

### Post by John Jason Jordan on 2007-04-23
bump

---

### Post by az on 2007-04-24
> **John Jason Jordan said:**
>  repeating the process, but it dpkg still won't  fix everything. 

I really don't want to reinstall from scratch. I do have a full backup of ~/ made last night before the upgrade (I'm not totally stupid), but I have a zillion programs installed and each has tons of personal configurations. Does anyone have any further suggestions for how to fix a broken upgrade?

Keep running 
sudo apt-get -f install

and dpkg --config -a

Over and over until no new packages get fixed.  Most of the time, dpkg will be able to gain a little more ground each time.  Whe it sticks, you may be able to single out a particular package that is causing problems.  Usually, these packages come from third-party sources.

You can try to remove the package by hand

sudo dpkg -r package

and then try again.

That's basically how you get the package manager out of a knot.  Is this the reason it crashed?  I dunno.

---

### Post by John Jason Jordan on 2007-04-24
> **az said:**
> Keep running 
sudo apt-get -f install
and dpkg --config -a
Over and over until no new packages get fixed.  Most of the time, dpkg will be able to gain a little more ground each time.  Whe it sticks, you may be able to single out a particular package that is causing problems.  Usually, these packages come from third-party sources.
You can try to remove the package by hand
sudo dpkg -r package
and then try again.
That's basically how you get the package manager out of a knot.  Is this the reason it crashed?  I dunno.
I kept trying, but couldn't get it to finish the upgrade. But I belong to a local Linux user group with an e-list, so I posted there about my problem. Another user told me how to fix it. First, boot to the live/install CD, then open a terminal. Then create a folder for a mount point and mount the partition where your borked Ubuntu is installed. In my case that is hda2 (throughout the following change "hda2" to whatever your partition is):

sudo mkdir /media/hda2
sudo mount /dev/hda2 /media/hda2

Then do:

sudo mount -o bind /dev /media/hda2/dev
sudo mount -o bind /proc /media/hda2/proc

The purpose is to mount bind the /dev and /proc folders on the borked installation to the live CD copy that is running. Otherwise a lot of the apt-get and dpkg commands will not complete correctly. And then chroot yourself into the borked installation:

sudo chroot /media/hda2

That will put you at a root prompt, so the sudo's are no longer necessary. Now just do

apt-get -install -f
and
dpkg --configure -a

And you should have much better luck getting the borked installation fixed. You may have to run them over a few times, alternating each time.

In my case after apt-get install -f and then dpkg --configure -a at the end it said it couldn't fix acpi-support, powermanagement-interface, gnome-power-manager, and gnome-session. I tried to remove them with dpkg -r <package> and then reinstall, but stopped after the first one. That is, I successfully rremoved acpi-support, but then couldn't reinstall it. After that I decided to leave well enough alone and try to boot.

When I rebooted it came up to a command line with error messages. Reading the errors I had a hunch the problem was that damn Grub menu.lst file (I have NEVER had an upgrade fix that thing properly). So after doing nano /boot/grub/menu.lst I quickly realized that the UUID might be wrong. I changed it to /dev/hda2, wrote out the file, and suddenly the boot process continued. I didn't even have to restart. And then there was my beloved Ubuntu desktop!!!! Happy dance! Happy dance! Happy dance!!!

There are a few glitches yet to run down. Gnome announced that some of the gdesklets couldn't be launched. And uname -a says I am running 2.6.17-11-generic #2 SMP. That is wrong -- for one thing this is a single-core CPU. But more importantly, the new kernel for Feisty is 2.6.20-15-generic, so I must have still booted to the old kernel. Maybe it's really there and the menu.lst file wasn't updated to show it (it's not in the list). Yet I launched OpenOffice.org and found that it is 2.2, which means that I must be running Feisty. I can fix these things, now that it's finally running.

Thanks for the help. I hope the tips about mount bind and chrooting into the old installation will help someone else patch up a hung upgrade.

---

### Post by roboa1983 on 2007-05-09
> **az said:**
> Run 
sudo apt-get -f install

and it may prompt you to run

sudo dpkg --config -a

That will configure packages that were not finished installing.

Hi
I had this problem too by upgrading. After searching endlessly for a solution, this has been the one that got me out of the trouble. I could access into Feisty (fitting name by the way :) ) Fawn and did all the other updates from the inside.

Thanks for the support!

---

