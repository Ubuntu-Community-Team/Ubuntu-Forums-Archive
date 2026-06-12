---
title: "want to install Ubuntu on Vista computer"
date: 2007-12-04
forum: Installation &amp; Upgrades
---

### Post by t2000kw on 2007-12-04
Are there any issues with a dual boot Ubuntu/Vista that are different from using Ubuntu/XP? This new laptop came with Vista and I would like to add Ubuntu for a dual boot. Wiping Vista in this case and installing XP is not a great idea since Acer is not supporting XP (with drivers, etc.) for this computer.

Does GRUB work well for booting to either OS or does Vista re-take control of the boot partition once I boot to Vista?

---

### Post by Pumalite on 2007-12-04
The only thing you have to worry about is to allocate space for Ubuntu with Vista partitioner first. Then install Ubuntu, let Grub install to MBR and you'll have a dual boot system.

---

### Post by t2000kw on 2007-12-04
> **Pumalite said:**
> The only thing you have to worry about is to allocate space for Ubuntu with Vista partitioner first. Then install Ubuntu, let Grub install to MBR and you'll have a dual boot system.

I'm new to VIsta. Been with XP for a long time.

Does it have its own partitioner, or did you mean a Windows compatible partitioner like Partition Magic?

I have PM 8.0 but I'm not sure if it will work with Vista or not. I also have to watch out for the hidden 10 GB partition Acer set up for a recovery partition, but I can just leave it wherever it is, I think, and work around it.

Thanks for the reply!

---

### Post by sethvath on 2007-12-04
There is a disk management tool in vista, follow this guide [http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

There are probably a thousand other dual boot guide on this forum alone, do a search if you want a second opinion/method.

---

### Post by t2000kw on 2007-12-04
Thank you very much. I was looking for something closer to what I was doing. There were plenty on using XP, and I already knew there were few problems with that from my own experience. 

There were a few that showed up for Vista but did not answer my questions. 

I have found the Ubuntu search engine sadly lacking as it returns many threads not relevant at all to what I am looking for. It seems that if the word is used somewhere in a post, that thread gets returned as a relevant thread. 

This is exactly what I was looking for. And it looks as if I can just use the provided 69.5 GB partition and slice it and dice it to my content, though I won't have it as a backup partition, which was probably the intent of the manufacturer.

So I might not need the info about using the disk manager, though I want to know more about it just in case I'll need it for some other reason later on.

---

### Post by Pumalite on 2007-12-05
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

---

### Post by t2000kw on 2007-12-05
Thanks. Looks like it's no different than with XP. 

I wonder if I ever want to go back to the original Vista only drive if I can restore the boot sector, maybe using FDISK /MBR or another way of doing it?

Anyway, it looks like this will go smoothly. I burned a system restore disk just in case something goes wrong. I'll only lose a few things this early in the gams as I just got this thing (Acer 5630) a couple of days ago.

Donald

---

### Post by stlcoptony on 2007-12-05
I had vista and ubuntu set to dual boot not long ago. If you search for "super grub disk" on google, go to the site and you can download a bootable iso. I burned it and used it to return vista's MBR to normal. I think you could use a factory restore disc, but no one sells them with the computers anymore.... Anyway, this worked perfectly to restore my computer to normal

---

### Post by t2000kw on 2007-12-08
Thanks. Acer has a setup where you can burn a factory restore disk onto two DVDs or 8 CDs. It automatically assumes that you have the 4.7 GB (?) "regular" DVDs, though, so when I tried to burn one on a dual layer DVD, it oly filled it to 4.7 GB and asked for the second DVD. Still, it's worth knowing that I can go back to square one if I want to. 

I'll look into the super GRUB disk. Does it have a specific option to restore the MBR or do you have to figure things out for yourself? I might find a program that can backup the MBR also, if one exists. 

> **stlcoptony said:**
> I had vista and ubuntu set to dual boot not long ago. If you search for "super grub disk" on google, go to the site and you can download a bootable iso. I burned it and used it to return vista's MBR to normal. I think you could use a factory restore disc, but no one sells them with the computers anymore.... Anyway, this worked perfectly to restore my computer to normal

---

### Post by tgalati4 on 2007-12-08
Be wary that some manufacturer's install chips that lock the machine to a particular operating system.  The fact that ACER doesn't provide XP drivers for it's hardware is an indication that it's designed to run Vista (and perhaps paid fees to only support Vista).  

So if you find reduced functionality in Ubuntu on your laptop, keep that in mind.  Look at the efforts to lock down the iPod and the Zune.  It's bound to happen to laptops as well.

---

### Post by Pumalite on 2007-12-08
+1

---

### Post by stlcoptony on 2007-12-08
> **t2000kw said:**
> Thanks. Acer has a setup where you can burn a factory restore disk onto two DVDs or 8 CDs. It automatically assumes that you have the 4.7 GB (?) "regular" DVDs, though, so when I tried to burn one on a dual layer DVD, it oly filled it to 4.7 GB and asked for the second DVD. Still, it's worth knowing that I can go back to square one if I want to. 

I'll look into the super GRUB disk. Does it have a specific option to restore the MBR or do you have to figure things out for yourself? I might find a program that can backup the MBR also, if one exists.

It's kind of confusing, but i figured it out, so you should be good ;) Basically just follow the text directions for windows (just ignore the fact that it doesn't mention vista). It's a bootable cd, just like a linux distro

---

### Post by t2000kw on 2007-12-09
> **stlcoptony said:**
> It's kind of confusing, but i figured it out, so you should be good ;) Basically just follow the text directions for windows (just ignore the fact that it doesn't mention vista). It's a bootable cd, just like a linux distro

Hopefully I won't need to figure it out, but I have the Super Grub Disk made and ready just in case.

I installed Ubuntu Gutsy on this laptop and it went smoothly, using 3 partitions (/, /swap, and /home). Then I made changes to /etc/x11/xorg.conf and got syndaemon working (to disable the touchpad while typing) and installed Gsynaptics. I then installed Crossover Office and my Agent email (windows-based) program and I think I'm all set for now. A few more programs, like K3B, and I'll be done.

---

