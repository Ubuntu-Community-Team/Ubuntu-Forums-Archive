---
title: "Can't install Unbuntu but can install other distro"
date: 2019-08-18
forum: Installation &amp; Upgrades
---

### Post by rickseiden on 2019-08-18
Hello,

On my computer (HP Envy M6 P114DX laptop) I can't install Ubuntu.  I've tried various version as far back as 16.04, but none of them work.  Without editing things in the Grub menu, I can't even get the live USB drive to boot. (A while back I was able to get it to boot by adding something along the lines of no-apci, but I don't have my notes on that anymore, and can't remember exactly what I did.)  When it did boot with the live USB drive, it didn't recognize the hard drive at all.  When I don't do any editing, it just hangs.  I don't know how to get any kind of log out of Linux in general or a live USB drive specifically.

The other day I tried the Debian non-free ISO, and that boots to a live session, but won't install on the hard drive.  It gets to 70% and hangs.  I let it go overnight, and it gave me a failed to install error. I didn't write down any details there.

I've been able to get PCLinuxOS to install and boot, but it is based on Mandriva, and doesn't seem to allow for installation of third party RPMs (such as Chromium).

I know that I'm not posting any errors here, so it's not likely that anyone is going to say, "Oh, here's your problem and here's how to solve it."  I'm more hoping that I can start taking steps in the right direction that will eventually lead to that moment.

Please help me figure out what I have to do to get Ubuntu installed and running on my laptop.

Thanks

PS I know that it's possible to get Ubuntu installed and running because HP sold a version of this laptop with Ubuntu pre-installed.  I can't find that version of Ubuntu anywhere, and they will only give you a copy if you are still in warranty (I'm not) and your laptop came with Ubuntu pre-installed (mine didn't).  So that's a complete dead end as far as I can tell.

---

### Post by crip720 on 2019-08-18
This post from Mint might help.  [https://forums.linuxmint.com/viewtopic.php?t=240444](https://forums.linuxmint.com/viewtopic.php?t=240444)

---

### Post by Dennis N on 2019-08-18
You should read this post. It has links to some tips to installing Ubuntu to HP Computers with Windows pre-Installed in UEFI mode. One of those may have a solution.
[https://ubuntuforums.org/showthread.php?t=2392797&p=13770426#post13770426](https://ubuntuforums.org/showthread.php?t=2392797&p=13770426#post13770426)

---

### Post by yancek on 2019-08-19
Based on the information you posted, you have a computer with no operating system on it and you are trying to install Ubuntu.  Or do you still have PCLinuxOS installed.  Is this a newer HP with UEFI or an older machine which is just Legacy/CSM?  Or do you have windows installed and just neglected to mention that?  Makes a big difference.  I have a 2 year old HP laptop with windows 10 pre-installed and was able to install Ubuntu 16.04 and 18.04 as well as sseveral other Linux systms so it is possible.

---

### Post by rickseiden on 2019-08-19
> **crip720 said:**
> This post from Mint might help.  [https://forums.linuxmint.com/viewtopic.php?t=240444](https://forums.linuxmint.com/viewtopic.php?t=240444)

I came across this one a while ago.  I kind of dismissed it at the time, because I wasn't having problems with the wireless card.  I couldn't even boot the live USB drive (no CD to even try on this machine).  And when I did get it to boot playing with grub, it did not see the hard drive.

I've tried the latest Debian with the non-free drivers, and it boots, but won't install.

Thank you

---

### Post by rickseiden on 2019-08-19
> **yancek said:**
> Based on the information you posted, you have a computer with no operating system on it and you are trying to install Ubuntu.  Or do you still have PCLinuxOS installed.  Is this a newer HP with UEFI or an older machine which is just Legacy/CSM?  Or do you have windows installed and just neglected to mention that?  Makes a big difference.  I have a 2 year old HP laptop with windows 10 pre-installed and was able to install Ubuntu 16.04 and 18.04 as well as sseveral other Linux systms so it is possible.

I'm sorry I wasn't clearer.  I have a computer with Windows 10 64 bit (pre-installed) working just fine.  It now dual boots into PCLinux OS, and that works fine, except that I have no wireless drivers, and I can't easily install anything on it because it doesn't support external RPM's.

The fact that PCLinux OS works tells me that it's possible to get Linux working on this laptop, and gives me hope that I'll be able to get Ubuntu installed.

---

### Post by rickseiden on 2019-08-19
> **Dennis N said:**
> You should read this post. It has links to some tips to installing Ubuntu to HP Computers with Windows pre-Installed in UEFI mode. One of those may have a solution.
[https://ubuntuforums.org/showthread.php?t=2392797&p=13770426#post13770426](https://ubuntuforums.org/showthread.php?t=2392797&p=13770426#post13770426)

I looked through those, and I don't believe they apply to my situation.  They are all about either getting Ubuntu to begin the booting process, or about getting dual boot to work.  I can get the live USB drive to start booting, but it freezes half way through the boot process.  If I play with the grub settings (I wish I had the notes to say exactly what I put there--I'll have to look for them again) I can get the live USB drive to boot, but then there is no hard drive to install it to.

I believe that my problem isn't an EFI problem, as I currently have PCLinux OS installed and booting (although I have to go into the computer's boot manager to get it to it's boot menu--something some of the posts you pointed out might help with).

---

