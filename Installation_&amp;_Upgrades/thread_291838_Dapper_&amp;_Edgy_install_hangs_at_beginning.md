---
title: "Dapper &amp; Edgy install hangs at beginning"
date: 2006-11-03
forum: Installation &amp; Upgrades
---

### Post by noldguy on 2006-11-03
Trying to install on a brand new system: Intel DG965WH motherboard, Intel G965 Express chipsite, Core 2 duo processor. Screen shows: Uncompressing Linux...OK, booting the Kernal then it hangs.

Tried Edgy then Dapper, Live CD and alternate CD. Same thing each time. FWIW XP works fine. The PC is a marvel except it Ubuntu doesn't like it. 

Any ideas. If not, I'm selling my beautiful new baby and buying a Mac.

---

### Post by K.Mandla on 2006-11-03
You might give the K/Xubuntu discs a whirl. Or maybe a server CD and install ubuntu-desktop once the server is in place.

Have you tried any other distros? See if something like DSL or Arch linux will boot. That might give you an idea where the problem is occurring. 

Good luck! :)

---

### Post by noldguy on 2006-11-03
Try K and server edition? Why not, it's only 2 more downloads bringing total to 5 downloads. :) 

Haven't tried any other distro. Everything I've read indicates Ubuntu is the right one for me.

---

### Post by K.Mandla on 2006-11-03
It would be more of a troubleshooting process than anything. If it's strictly hardware-related, you might see a similar issue with other distros.

Arch linux is only about 120Mb, if I recall correctly. And DSL is only 50Mb. Saves bandwidth, anyways.

---

### Post by rsambuca on 2006-11-03
You might want to try a few different boot options at startup (F6) if I recall correctly.  

Many have had to add "noapic nolapic" as a boot option.  I had to insert "ide=nodma" in order to get the cd to boot.  You can then turn on the dma after ubuntu loads.

Anyways, they are a couple of things that will just take a couple of seconds to try before you burn more CD's.

---

### Post by noldguy on 2006-11-03
First...I tried installing DSL. It hung too. Then tried booting the embedded version within windows and qemu errored out at what looks to be the  same point as Ubuntu.

Second...tried boot option combinations of noapic nolapic and ide=nodma. With these I get one or both errors:

No expicit IRQ entries, using default mptable
Local APIC #0 not detected

Also, sometimes the pc just stops responding when I am entering boot options (espcially long ones or if I make a typo and have to backspace).

I'm assuming there is some conflict with the Intel 965 chipset but dammed if I know what it might be. All in all a very frustrating experience. I figured that with brand new hardware there'd be no problem installing Linux.

Any other ideas I might try before giving up?

---

### Post by seraph47 on 2006-11-03
I have the same problem on my machine, its running an AMD Opteron 165. Tried both 6.06 and 6.10 server, and it hangs right after it says its booting the kernel. The weird thing is that I was running the 6.10 live cd just before with no problems.

Edit: I changed one of my BIOS settings to enable ACPI or something like that, and I got further in the install, but well see if it finishes...

Edit: Still nothing...

---

### Post by xp_newbie on 2006-11-03
> **seraph47 said:**
> Edit: I changed one of my BIOS settings to enable ACPI or something like that, and I got further in the install, but well see if it finishes...

Edit: Still nothing...

See [my comment here to a similar problem]("http://ubuntuforums.org/showpost.php?p=1711560&postcount=5"). You may be able to boot and install using one of those kernel boot options, but your system hardware will not be used efficiently.

Alex

---

### Post by noldguy on 2006-11-04
Thanks for the info Alex. Follwed the link and links in that thread. Looks like I'm SOL. Am now downloading SUSE 10.2 beta. At the speed that's going it will be 26+ hours before I know whether it with the 2.6.18 kernel will boot on my machine.

In the meantime, rather than twiddle my thumbs, think I'll try to make some room on my older Athalon server and try to load Ubuntu on it.

---

### Post by seraph47 on 2006-11-04
Heh I think I know what could be a problem, I was installing Ubuntu over a NTFS hard drive, that could account for some problems.

---

### Post by noldguy on 2006-11-04
I've given up trying to get Linux installed on this machine. Maybe I'll try again a year or so from now.

It's a crying shame that my old copy of XP (SP2 vintage) installs without a hitch on this new hardware but new versions of Linux distros don't.

I stumbled on this info in the wiki: [wiki.ubuntu.com/Core_2_Duo_Support]("https://wiki.ubuntu.com/Core_2_Duo_Support"). May help somebody else. But I'm not into that much effort to get it installed (and still not have a working ethernet connection afterwands). I just want a system that basically works out of the box.

---

### Post by procco on 2006-11-14
I have the same problem - during boot:
Uncompressing Linux... Ok, booting the kernel.

And it hangs there.  I am running a VIA EPIA SP13000 mini-ITX with 1GB RAM and an 80GB SATA HDD.  This problem happened when I tried to install 6.06.1LTS-SERVER.  I was running 6.06.1LTS-DESKTOP on this same machine and it works great.  I downloaded two different images of the server CD and it's the same thing each time.  I wanted to set up a LAMP server and not have to go through the process manually but it looks like I'm going back to the desktop version and manual LAMP install.  At least it works.  Sure wish someone could tell me why the SERVER version won't boot.[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

Paul.

EDIT: I was using 6.06.1-desktop-i386 (worked great) and 6.06.1-server-i386 (hangs when booting kernel)

EDIT:  I solved the problem using the info in this link:  [https://launchpad.net/distros/ubuntu/+source/initramfs-tools/+bug/47197](https://launchpad.net/distros/ubuntu/+source/initramfs-tools/+bug/47197)

I did not have an it821x module but here is what i did.

1.  boot from CD and open terminal
2.  sudo mount /dev/sda1 /mnt      (or whatever your partition is)
3.  sudo chroot /mnt
4.  cd /etc/mkinitramfs/
5.  cat modules 
this command said :
# List of modules that you want to include in your initramfs.
.
.
.
# This might be good choices:
# 
#raid1
#sd_mod

6.  echo raid1 >> modules
7.  echo sd_mod >> modules
8.  dpkg-reconfigure linux-image-`uname -r`
 - I did not have the linux-image loaded so I had to get it using: apt-get install linux-image-`uname -r`
9.  reboot and viola - works great.

Hope this help someone.

Paul.

---

