---
title: "Preparation for multiple distro installs"
date: 2011-12-12
forum: Installation &amp; Upgrades
---

### Post by Jaybo2179 on 2011-12-12
I'm looking for directions on how to prepare my partitions for multiple linux installations.  I want to have Ubuntu, Cent OS, and an older publishers edition of Redhat 7.2 so that I can follow the exercises in the book.  Can someone tell me the process in concise ordered steps so that I don't mess this up royally.  I have a 160 gig HD to work with.  Please make suggestions for how big I should make the partitions.

---

### Post by RealityMaster on 2011-12-12
Why not just use virtualbox?

---

### Post by fantab on 2011-12-12
> **Jaybo2179 said:**
> I'm looking for **directions on how to prepare my partitions for multiple linux installations**.  I want to have Ubuntu, Cent OS, and an older publishers edition of Redhat 7.2 so that I can follow the exercises in the book.  Can someone tell me the process in concise ordered steps so that I don't mess this up royally.  I have a 160 gig HD to work with.  Please make suggestions for how big I should make the partitions.

Firstly, choose and decide what is going to be your PRIMARY distro installation. You will use GRUB from this distro ONLY.

Suggested Partition Scheme:

/dev/sda1 - Primary - ext4 - 15GB - "/" Main OS
/dev/sda2 - Primary - ext4 - 15GB - "/" Second OS
/dev/sda3 - Primary - ext4 - 15GB - "/" Third OS
/dev/sda4 - EXTENDED - 115GB (approx.)
/dev/sda5 - Logical - ext4 - 111GB (approx.) - Linux Data (NO Mount-Point)
/dev/sda6 - Logical - SWAP - 4GB

(You can create more 15GB Logical Partitions if you need more).

Install GRUB from the MAIN OS to /dev/sda ONLY. 

Do NOT install GRUB from any other Distro. After installing the second and third OS you have to log into Main OS and UPDATE GRUB. And you have to update GRUB every there is a Kernel Update in the second and third OS.

---

### Post by Jaybo2179 on 2011-12-13
Some people suggest installing Redhat/Cent OS first and then Ubuntu so that you can use Grub2 to detect other OS's.  Is this a good thing to do? 

thank u for that partitions example.  It helps tremendously!

---

### Post by Jaybo2179 on 2011-12-13
When Grub pops up in Ubuntu install I tried adding 3 different / mountpoints with 20gigs each.  

When I try to move forward it says:  

Two file systems are assigned the same mount point (/) 
Scsi (0,0,0) partition #1 (sda) and SCSI (0,0,0) partition #2 (sda)

---

### Post by N00b-un-2 on 2011-12-13
the real trick to successful multibooting lies in how you partition.  There's no one right way to do it, but there are infinite wrong ways.  I have OSX Snow Leopard, Windows 7 and Xubuntu on my computer.  At one point I had another partition for a small OS which I tried AndroidX86, Moblin and splashtop on, but OSes like those are more of a novelty than anything useful.  I'll wait the extra 15 seconds to boot a real OS.

---

### Post by Jaybo2179 on 2011-12-13
how do you keep another Linux Distro bootloader from taking over ubuntu?  I installed CentOS after Ubuntu but its bootloader didn't detect my install of Ubuntu.  Not sure what to do at this point.  I need step by step instructions on how to go about this.  Simply want to Dual CentOS and Ubuntu at this point.

---

### Post by fantab on 2011-12-13
> **Jaybo2179 said:**
> how do you keep another Linux Distro bootloader from taking over ubuntu?  I installed CentOS after Ubuntu but its bootloader didn't detect my install of Ubuntu.  Not sure what to do at this point.  I need step by step instructions on how to go about this.  Simply want to Dual CentOS and Ubuntu at this point.

Remember you **ONLY NEED ONE GRUB**. If you have installed UBUNTU with its GRUB then you don't need any other GRUB. **Don't install the Boot-Loader from either CentOS or RedHat**. After installing them when you restart, Boot into Ubuntu and ***sudo update-grub***. The GRUB will detect other OS distros.

CentOS and RedHat (CentOS, Fedora etc are based on Red Hat Linux) doesn't have OS-PROBER pre-installed like in Ubuntu. So the GRUB does not easily recognize other OS, hence it is said that the RedHat based distros must be installed last. 

What I do is, irrespective of whether I install them first or last I Don't Install Grub from these distros. When you install these distros first and don't install Grub don't try to boot into them immediately. You go ahead and install Ubuntu with its GRUB, which WILL find all other distros installed.

---

### Post by N00b-un-2 on 2011-12-13
simply don't install a bootloader.  You only need one to manage your operating systems and Grub works fine and is extremely configurable.  If you install another OS and it automatically installs a bootloader, just uninstall it and reconfigure your original grub.

---

