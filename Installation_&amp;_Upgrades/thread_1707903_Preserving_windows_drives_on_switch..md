---
title: "Preserving windows drives on switch."
date: 2011-03-15
forum: Installation &amp; Upgrades
---

### Post by Cyaneus on 2011-03-15
I am switching to Ubuntu soon for security purposes.  I have 3 hard drives, one with my OS, one with nothing, and one with all my junk.  I was wondering if there is anyway that I can only reformat and install Ubuntu onto the drive with windows, reformat the empty drive, and then transfer files from my junk drive onto the empty drive, and then format the junk drive and move all of the files back onto the junk drive?  Or is the junk drive accessible from Ubuntu and not worth trying to switch formats on?

My goal is to really fine-tune my ability to maintain a secure and anonymous computer.

Thanks in advance!

-Cyaneus

---

### Post by Dutch70 on 2011-03-16
> **Cyaneus said:**
> I am switching to Ubuntu soon for security purposes.  I have 3 hard drives, one with my OS, one with nothing, and one with all my junk.  I was wondering if there is anyway that I can only reformat and install Ubuntu onto the drive with windows, reformat the empty drive, and then transfer files from my junk drive onto the empty drive, and then format the junk drive and move all of the files back onto the junk drive?  Or is the junk drive accessible from Ubuntu and not worth trying to switch formats on?

My goal is to really fine-tune my ability to maintain a secure and anonymous computer.

Thanks in advance!

-Cyaneus

Hi, and welcome to UF

Yes you can, although I'm not sure all of it is necessary to get what I think you want. 

First you need to create a live cd or usb stick, the latter being preferred as it is easier, faster, cheaper & kinder to the environment. Then, unplug all your hdd's except the one you want to install Ubuntu on. Proceed with the installation. It is advisable to select "Try Ubuntu" before installing to be sure that it works to your satisfaction on your hardware. 

You also have the option of dual booting windows & Ubuntu, either on the same hdd, or different hdd's & choosing which OS you want to boot into on start up. 

Why do you want to format your hdd with your "junk" on it? It's really not necessary. Ubuntu has read & write access to ntfs file systems by default. So you would be better off not formatting it if you decide to dual boot, as windows doesn't read/write to ext3 or ext4 partitions without some help.

You can download Ubuntu & create you cd/usb from here...
[[COLOR="Blue"]http://www.ubuntu.com/desktop/get-ubuntu/download[/COLOR]]("http://www.ubuntu.com/desktop/get-ubuntu/download")

Alternatively you can create your usb stick from here... 
[[COLOR="Blue"]http://unetbootin.sourceforge.net/[/COLOR]]("http://unetbootin.sourceforge.net/")

_

---

### Post by Cyaneus on 2011-03-16
Dutch,

Thank you much!

And by the way, after Ubuntu is installed, will I be able to format the empty drive.  If so, I'll do that.  I would like to format it because it is inconsistent in it's reliability, that's why I don't hold anything on it currently that is not just a temporary move.

---

### Post by iiiears on 2011-03-16
You might install Ubuntu and the boot loader on a second drive and use bios options to boot Windows and Ubuntu from the second drive. That would leave your windows drive untouched.

---

### Post by Dutch70 on 2011-03-16
> **Cyaneus said:**
> Dutch,

Thank you much!

And by the way, after Ubuntu is installed, will I be able to format the empty drive.  If so, I'll do that.  I would like to format it because it is inconsistent in it's reliability, that's why I don't hold anything on it currently that is not just a temporary move.

Sure, you can actually do that from the live cd/usb if you want.

> iiiears >>You might install Ubuntu and the boot loader on a second drive and use bios options to boot Windows and Ubuntu from the second drive. That would leave your windows drive untouched.

+1 on this.

---

### Post by Cyaneus on 2011-03-16
Cool, thanks again!  I'll do as first suggested.

---

### Post by Dutch70 on 2011-03-20
So, did it work out for you?

---

