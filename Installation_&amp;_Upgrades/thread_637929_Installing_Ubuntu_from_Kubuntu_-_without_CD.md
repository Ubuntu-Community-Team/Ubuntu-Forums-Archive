---
title: "Installing Ubuntu from Kubuntu - without CD"
date: 2007-12-11
forum: Installation &amp; Upgrades
---

### Post by Prism on 2007-12-11
Hi there,

I would like to install Ubuntu 7.10 on an ext3 partition, using my existing Kubuntu installation (on a different partition!), so I will have both installed. The catch is, I'd like to do it without using any burned CD.

I've tried to follow the instructions from the wiki article ["Installation/FromLinux"]("https://help.ubuntu.com/community/Installation/FromLinux"), but the installation failed - probably because I had copied the files from the ISO file to the partition to which I had wanted to install. The error message I got was that the installer couldn't format the partition (makes sense - it was mounted and the installation program ran from it).

So how can I install a new shiny ubuntu system using my old kubuntu? (Nope, I don't want to apt-get ubuntu-desktop)

Thanks in advance!

---

### Post by aysiu on 2007-12-11
Try this:
[http://www.psychocats.net/ubuntu/gnome](http://www.psychocats.net/ubuntu/gnome)

---

### Post by Prism on 2007-12-11
I believe you misunderstood me - I don't want to install ubuntu-desktop, but rather have a fresh installation of Ubuntu on a partition other than my Kubuntu partition.

---

### Post by logos34 on 2007-12-11
> **Prism said:**
>  but the installation failed - probably because I had copied the files from the ISO file to the partition to which I had wanted to install. The error message I got was that the installer couldn't format the partition (makes sense - it was mounted and the installation program ran from it).

yes, that is what happened.  You need to create a separate ~750 mb 'holding partition' as it were for the iso files.  It's all in the howto.  If that method doesn't work for you for some reason there's [this approach]("http://ubuntuforums.org/showthread.php?t=316093")--slightly different using the alternate vs. desktop cd and a 'hd-media' directory.  

If you want to continue to use the existing grub on the mbr (poiting to kubuntu) remember to tell the installer to write grub to the bootsector of the ubuntu root partition--i.e. use '/dev/sdax' (where x is the ubuntu root partition #) instead of the default location of '(hd0)', the mbr.  But it will be easier to let ubuntu overwrite the kubuntu one because it will include a kubuntu entry in menu.lst and fstab, so you won;t have to do any editing of those files.

---

### Post by Prism on 2007-12-12
What happens if I create a new folder on my current kubuntu partition (say /dev/sda1/ubuntu_installation), move the cd content into it, and pointing grub to have an "installer" entry from this folder? Can it be done, or I have to make another partition?

(I don't want to partition my h.d., it's already over-partitioned. :P)

---

### Post by logos34 on 2007-12-12
I'm pretty sure you MUST create a separate partition (remember, you are booting the installer).  The only thing you can use root for is the grub entry to boot the installation CD...it has to run from it's own partition.

---

### Post by Prism on 2007-12-13
Well, that is a shame. :(
I'll see what I can do.

---

### Post by xalexbladex on 2007-12-23
i just want to let you know that you cannot copy the iso files to the partition because the files are arranged to start and for the installer to extract the copreesed files and put them where they shoud be. so what you can try and do is, BUT IT ONLY WORKS IF YOU COMPUTER CAN BOOT FROM USB DEVICES, put the iso on a flash drive or camara card (via usb card reader) AND SET YOU BOOT ORDER SO THAT YOUR USB IS ON TOP. REBOOT YOU COMPUTER and then pop in the drive so your computer boots from it. then click install do the wizard and tell it to install ubuntu on the partition you made. good luck.:KS):P):P =P.

---

