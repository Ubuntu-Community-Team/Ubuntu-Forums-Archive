---
title: "Ubuntu partition &gt;100 GB from beginning of disk causing booting errors?"
date: 2013-10-09
forum: Installation &amp; Upgrades
---

### Post by optimusLime on 2013-10-09
Hello,

First, thank you to anyone taking the time to help me out :)

I have an ASUS UX31A computer that I wanted to dual boot Ubuntu on. It came with Windows 7, which I later replaced with Windows 8. I disabled FastStartup on Windows 8, and couldn't find either Quickboot or Intel Smart Response in my BIOS menu, so assumed they weren't there to begin with. I then made a 40 GB partition for Ubuntu using the Disk Management tool in Windows.

After making a live USB of Ubuntu 13.04, I followed the installation steps, manually creating a 4 GB swap partition, and successfully installed Ubuntu to the remaining 36 GB (got a confirmation "Installation Successful"). Upon restarting, however, I booted directly to Windows; no Grub.

I started searching for solutions, and came across this on the Ubuntu help page:
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

I was thinking of making a Boot partition, and then read the part that said "[COLOR=#333333][FONT=Ubuntu]This free space must be located [/FONT][/COLOR]**inside the first 100GB of the disk**[COLOR=#333333][FONT=Ubuntu] (its end must not be located at more than 100GB from the start of the disk). [/FONT][/COLOR]"

When I made my partition for Ubuntu, there was about 190 GB partition that I'm using for Windows in front of it. Could this be why I don't get Grub on start up? Do I need to make sure my Ubuntu parition is within 100 GB of the start of my disk? What is the explanation for the 100 GB rule?

In the mean time, I'll continue searching; I just wanted to elminate this as a possibility.

Thanks again,

-MN

---

### Post by carl4926 on 2013-10-09
The old 100GB related to grub legacy and doesn't apply

If your machine came with windows 8 it's will be EFI and you will likely need a bios_grub partition
You can read about EFI and ubuntu here
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by optimusLime on 2013-10-09
Thanks, Carl.

My computer came with Windows 7; I installed Windows 8 on it later, so maybe it isn't EFI? Regardless, I'll still have a look, and also try with a specific boot partition.

-MN

---

### Post by carl4926 on 2013-10-09
> **optimusLime said:**
> Thanks, Carl.

My computer came with Windows 7; I installed Windows 8 on it later, so maybe it isn't EFI? Regardless, I'll still have a look, and also try with a specific boot partition.

-MN
You might want to let us see it all in Gparted

---

### Post by optimusLime on 2013-10-09
Sure thing:

[IMG]http://i.imgur.com/3NoNUov.png[/IMG]

The "unknown" is part of my Windows system.

---

### Post by optimusLime on 2013-10-09
Hello all,

I ran boot-repair (recommended repair), as per the instructions on the first part of this link:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Things are working now!

For those interested, the URL I got from running boot-repair is:

[http://paste.ubuntu.com/6213956](http://paste.ubuntu.com/6213956)

---

### Post by optimusLime on 2013-10-09
Hello all,

I ran boot-repair (recommended repair), as per the instructions on the first part of this link:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Things are working now!

For those interested, the URL I got from running boot-repair is:

[http://paste.ubuntu.com/6213956](http://paste.ubuntu.com/6213956)

---

### Post by HonorableFool on 2013-10-10
"The Protective MBR protects GPT disks from previously released MBR disk tools such as Microsoft MS-DOS FDISK or Microsoft Windows NT Disk Administrator. These tools are not aware of GPT and do not know how to properly access a GPT disk. Legacy software that does not know about GPT interprets only the Protected MBR when it accesses a GPT disk. These tools will view a GPT disk as having a single encompassing (possibly unrecognized) partition by interpreting the Protected MBR, rather than mistaking the disk for one that is unpartitioned."

I'm only guessing this could be the cause of that

[http://msdn.microsoft.com/en-us/library/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/library/windows/hardware/gg463525.aspx)

---

