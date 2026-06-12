---
title: "Third time in a year that kernel update clobbered the system."
date: 2022-02-12
forum: Installation &amp; Upgrades
---

### Post by Draciron on 2022-02-12
What's going on with the kernel upgrades. Yesterday was the third time a kernel update left my system unbootable.  The machine in particular was an older Toshiba Satellite running 18.04 LTS. I had same thing happen on  2 other machines, one a desktop the other a laptop running different versions of Ubuntu. The hardware is fine. I have plenty of disk space on /. No kernel mods. I use the software updater for updates. The installation was uninterrupted. Software updater says a system reboot needs to happen, I click OK and next thing I know I'm having to boot into a USB drive, backup anything not already backed up and doing a wipe and load. 

I've been using Linux since the mid 90s. I've used most the distros out there at one time and been using Ubuntu for about a decade as my main distro. I once had a Redhat update clobber my RAID drivers on a high profile production server around 2001. I had a Fedora update go badly around 2004. Other than that I've never had a problem until this year with any distro or version. 

There are no odd drivers. The install on all of these machines was effortless and stock drivers. All of the machines were older machines. That's all I can afford. 2 of these machines were given too me or I inherited. The Toshiba that just crumbled is probably about 7 years old. About the same age as the HP I am typing on. The Dell that got clobbered about a year ago was about 9 or 10 years old. The other Toshiba that got clobbered is about the same age as the one that got clobbered yesterday. 4 gigs of RAM on the Toshibas, 2 gigs on the Dell desktop.  I'm able to reinstall, but then comes the 40 hours of installing the software I use and configurations. That's with having /home on a separate partition and thus saving a lot of configuration that way as well as not needing to back up my files.  

2 of the bad upgrades were 18.04 LTS, the other was 19.04 LTS. 

I had no USB devices of note plugged in at the time. Just mouse and keyboard and a hub. Nothing plugged into the hub at the time of the install. Hub is good, using it on this machine without a problem. Same with mouse and keyboard. ` On all the machines in question I've had Ubuntu running on them for at least a year prior to the update killing the system.  Hardware checks out fine. No corrupt disks or bad RAM. Runs fine once reinstalled on the 2 previous problem machines. I suspect I'll find the same on this one. I ran a disk check and it came back fine. I haven't tested the RAM yet but booting from USB gave me no issues. 

I use LTS versions to AVOID having to spend days reinstalling and configuring my system. I prefer to install, configure, and run it till the hardware dies. One of the things I love about Linux is the ability to do that. So I'm working WITH my system not ON it. 

TDE is my default DM. KDE and Gnome are way too bloated to use anymore on a system with only 4 gigs of RAM. XFCE was my DM on one of the three machines that got clobbered. So it's not DM related. 

What's going on?  Is the problem with Software updater?  One of the updates being installed was software updater ironically. 

It's getting to where I feel like I should do a complete backup every time I reboot the system after an upgrade.

---

### Post by webaake on 2022-02-12
Ubuntus default is to always boot to the newest installed kernel. Which can be a bummer sometimes. I've changed the default a long time ago, to boot instead from the last saved kernel . 
Add two lines to /etc/default/grub

> GRUB_SAVEDEFAULT=true
GRUB_DEFAULT=saved


And then sudo update-grub

More here:

[https://unix.stackexchange.com/questions/198003/set-default-kernel-in-grub](https://unix.stackexchange.com/questions/198003/set-default-kernel-in-grub)

I know, I know; "You should always use the newest kernel because of security issues"! Well, how can you be politically correct if your computer does not start?

---

### Post by mikewhatever on 2022-02-12
This is a bit light on details. At least tell the kernel version that caused problems.
Why did you have to reinstall? Just select an older kernel at Grub, something an old timer should know.

---

### Post by webaake on 2022-02-12
Kernels comes and goes, sometimes they work sometimes not. Sometimes sound disappears, sometimes you can't boot. So I've found it safer to boot from a known kernel that works, and then test the new kernel when I decide to do so. I do not like Ubuntu to push new kernels on me and make surprises. Oldtimers as well as newcomers can profit from using grub "saved" kernel, instead of the newest kernel. As long as it works, Ubuntus default kernel handling is user friendly. But when it doesn't work, you're in for surprises. 

So, there's not much use in dissecting one kernel and its problems. Just go back to an older working kernel and wait for the next working kernel to pop up.

---

### Post by grahammechanical on 2022-02-12
> It's getting to where I feel like I should do a complete backup every time I reboot the system after an upgrade.

Better to do the backup before rebooting. Kernel upgrades are not the only reason for rebooting to start using updated packages. There is nothing in the original post to indicate that a kernel upgrade caused the problem or even what the problem was. Rebooting to a Grub rescue prompt? Grub loading the kernel which did not progress to a graphical login screen?

The original post is not a help request but a complaint.

Regards

---

### Post by linux-sysop on 2022-02-12
You have been using Linux OS longer than I, but I have a methodology I use to prevent screwing up my system.  Recently I started using Timeshift and before that I used Bodhibuilder for backups.

1. I always lag 2 years behind on LTS.  I still have my 18.04 on one SSD and building and tweaking 20.04 on the current SSD. When I get done I will be running 20.04 for 2 years while improvements are made to 22.04.
2. I always keep the OS on its own partition. So far, Ubuntu never chews up space, my 18.04 has been on the 100 GB partition and is only using about 30 GB.
[LIST]
[*]I always replace the file folders in my home with soft links to another drive, thus (document, downloads, music, pictures, and videos) are shared by both the OS while I am doing my upgrades and tweaks.
[*]Should something, for whatever reason, go horribly wrong, I can boot the other OS and make repairs.
[/LIST]
3. Once I am done tweaking the system, I will remove the 18.04 and replace it with the next LTS 22.04.
4. Where possible, I will **apt-mark hold** some applications I don't want to change.  

However I don't think apt-mark hold will work for the kernel.  Instead I would simply remove both "linux-image and linux-image-generic" packages and reinstall them when or if needed.

I do not believe I can place a hold or remove the kernel image on my system, as I have Nvidia proprietary drivers, and when the driver upgrades, it needs to rebuild the kernel.  I suppose could place a hold on both the driver and the kernel.  
The methods I deploy have prevented major data loss and a lot of wasted time starting over from scratch.

---

### Post by TheFu on 2022-02-13
I patch weekly and only reboot when there is a /var/run/reboot-required created.
I've not seen the kernel issues that you claim across any of my 20-ish systems.
/ having plenty of space isn't the entire answer.
What about /boot and /boot/efi?  Do those have plenty of space?

You claim the hardware is all fine, but didn't provide a list of what you validated as proof.  Could the storage be failing where the boot files are placed?  What does the SMART data on the boot device show?

Do you really do a reinstall over a boot issue?  I'd boot into a Try Ubuntu disk, do a chroot (setup the links/mounts first), then update-grub.  I don't need to do this very often, perhaps once every 4 yrs and usually because I did something dumb like not keeping /boot/ with sufficient space or perhaps I added LUKS and forgot to include the dm-crypt stuff in the mkinitramfs config.  Only when I have a storage failure, would I start with a fresh install ... or perhaps if a new storage device was added where I want the OS installed.

---

### Post by webaake on 2022-02-14
None of you get my point! Ubuntus default by always booting the latest installed, the newest standard kernel in the repo and that is NOT always the smart thing. You can however, change that default behavior by making some simple changes in grub.

Take control yourself. And don't bother to analyze the kernels too much. If the previous kernel worked - use that. And wait for the next new working kernel. Canonical can not promise that all kernels will work on all hardware. 

Over the years I've had kernels crash, I've had kernels without sound. No biggie - just use an older kernel. Or the next new one that works.

---

