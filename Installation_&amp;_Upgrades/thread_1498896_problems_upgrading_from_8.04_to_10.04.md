---
title: "problems upgrading from 8.04 to 10.04"
date: 2010-06-01
forum: Installation &amp; Upgrades
---

### Post by stef-l on 2010-06-01
I've been running 8.04 fine for quite a while, initially as dual boot with Win XP, but more recently as the only OS on my desktop.

ubuntu 8.04 linux 2.6.24-27 generic gnome 2.22.3
1GB memory, AMD Ahtlon XP2600+, 132.1GB hard drive
nvidia 6200 graphics card.

I tried first to do upgrade directly to 10.04 via update manager, and this failed, with 10.04 freezing on the splash screen as it booted.

I waited several weeks & obtianed a live install disc of 10.04 & tried to install this over the top of 8.04.  The install went very slowly.  When it completed, the installation was unstable; sometimes it booted and I could use 10.04, sometimes the boot up process froze, either with ubuntu & the 5 red dots, or on the splash screen.  And 10.04 would never shut down, either via the shut down or the restart options; all I could do was turn the power off.

So I gave up, reinstalled 8.04 which works perfectly... and here I am.  

I would like 10.04 for the new features and because I want the support and updates for the next few years.  Any sugggestions, anyone?

stef-l

---

### Post by lemming465 on 2010-06-04
Wait for the 10.04.1 respin in July, and test it with a live CD before trying the upgrade again.

---

### Post by kansasnoob on 2010-06-04
That certainly sounds like a graphics issue so this may (or may not) be helpful:

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Incompatibility%20with%20nVidia%20upstream%20driver%20installer](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Incompatibility%20with%20nVidia%20upstream%20driver%20installer)

> Incompatibility with nVidia upstream driver installer

Ubuntu 10.04 LTS includes improved integration for nVidia binary driver packages. Unfortunately, this comes at the expense of compatibility with the installer provided upstream on the nVidia website. Users who wish to use the nVidia binary video drivers with 10.04 LTS should install them using the Ubuntu packages, as made available under System -> Administration -> Hardware Drivers. 

If you have trouble getting to the Desktop you could try booting in Recovery Mode and when it completes select "failsafeX" which may get you to the Desktop so you can install the drivers, then reboot and keep your fingers crossed :)

---

### Post by stef-l on 2010-06-08
> **lemming465 said:**
> Wait for the 10.04.1 respin in July, and test it with a live CD before trying the upgrade again.

This sounds like a possibility, and I will have time to play with this then.  But how will I know the respin is available?  and do I just download it & burn it to a CD, and then try to install over 8.04?

Thanks for the suggestion.

stef-l

---

### Post by stef-l on 2010-06-08
> **kansasnoob said:**
> That certainly sounds like a graphics issue so this may (or may not) be helpful:

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Incompatibility%20with%20nVidia%20upstream%20driver%20installer](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Incompatibility%20with%20nVidia%20upstream%20driver%20installer)



If you have trouble getting to the Desktop you could try booting in Recovery Mode and when it completes select "failsafeX" which may get you to the Desktop so you can install the drivers, then reboot and keep your fingers crossed :)

Both times when I almost got the 10.04 install completed, I got offered the opportunity via download manager to install nvidia drivers, and did this, but it did not stop the errors I reported in my original post.  Is this relevant to your suggestion?

Thanks for your advice.

stef-l

---

### Post by lemming465 on 2010-06-15
The 10.04.1 respin of the installation CD's will be announced in the usual places: ubuntuforums.org, the main ubuntu.com website, the announcements mailing list, distrowatch, lwn.net, etc.  Still about a month out.  You download the live desktop ISO (32 or 64 bit) corresponding to your 8.04 install from your favorite mirror site or torrent, burn it to a CD-R, and boot it.  The goal is to see if all your hardware works, particularly the video.  If it does, you reboot from the hard drive and try the in-place 8.04 -> 10.04 upgrade again ("sudo update-manager -c").

The live desktop CD should not be installed on top of an existing OS; that messes up the package management, leaving behind a mishmash of improperly migrated configuration files and orphan binaries which will be very hard to unravel.  Generally you only reinstall if you are also reformating the disk partitions (at least the root partition, plus /var and /usr if you made those separate, which is usually only on servers).  If you don't have plentiful internet bandwidth, the alternate install CD's can be registered as package sources to cut down on the number of downloads needed to upgrade.  The live desktop CD's install by cloning; the alternate CD's run a fairly standard debian-style package-based install.  Most people not doing exotic disk layouts (LVM, encrypted root, ...) will prefer the live desktop installs.

Did that answer most of your questions?

---

