---
title: "How to install windows from ubuntu without an external drive"
date: 2020-09-13
forum: Installation &amp; Upgrades
---

### Post by zakey2 on 2020-09-13
Is there a way to install windows with the iso file directly from ubuntu? It doesn't bother me if it deletes ubuntu in the process since I can reinstall it with a bootable usb and i don't have any data to lose.
Edit: just to clarify what I mean is without the use of a usb stick.

---

### Post by TheFu on 2020-09-13
Sure, you can make a virtual machine and install Windows inside that. This wouldn't harm the Linux install.  Windows will need/want at least 60GB of virtual storage.

Or

you can make some boot media as an optical DVD or boot flash drive using Linux tools, but you'll need to look up how to accomplish that for Windows. As you may guess, this is an Ubuntu-centric forum, so my knowledge about Windows is fairly limited. Last Windows I installed was Win7, though I'm thinking about bringing up a WinXP-Pro system for gaming inside a virtual machine with no networking.

I have a Win7 virtual machine that gets used for tax software. I was installed around 2011-ish and I've moved it from physical machine to physical machine to physical machine as I got faster and faster systems.  No re-install needed. The trick is to ensure the virtual-hardware that Windows sees is exactly the same regardless of the underlying true hardware.  Virtualization is good at that. On $350-ish hardware today, my Win7 system runs REALLY freakin' fast.

---

### Post by zakey2 on 2020-09-13
I already have a windows virtual machine but it doesn't run that good since the hardware I have is prety old and I don't think ubuntu supports it well but thanks anyway :)

---

### Post by TheFu on 2020-09-13
> **zakey2 said:**
> I already have a windows virtual machine but it doesn't run that good since the hardware I have is prety old and I don't think ubuntu supports it well but thanks anyway :)

Or you just need to tune the VM.  The last 12 yrs, I've run Windows inside VMs.  With proper tuning, we can get 90-95% of native performance.  There are lots of articles for how to accomplish that. I've written a few.

---

### Post by SeijiSensei on 2020-09-13
I don't know what "from Ubuntu" means here? Installations involve simply booting of an appropriate medium. The OS on the system doesn't matter.

I made a USB stick from a Windows 10 ISO. Use [Rufus]("https://rufus.ie/") from a Windows installation if possible.

---

### Post by crip720 on 2020-09-13
A fast google search says it is possible, unknown if it can be done from Ubuntu.  Woeusb or mkusb usually good for burning a windows USB from ubuntu.  You do not want Ubuntu deleted during process, because process will stop and you have nothing.

---

### Post by TheFu on 2020-09-13
If you have an ISO and need a bit-for-bit copy somewhere, I'd use **dd** or **ddrescue**.  All the other tools are just training wheels around dd, though I find most too confusing when compared to dd.  Heck, you can use **cp** if you like just get the source and target correct.

I have created a Win7 ISO file using the CDROM as source in this way a few times.  ISO files are handy for installation of virtual machines.

---

### Post by zakey2 on 2020-09-13
What I mean is installing it without a usb, something like creating a partition and somehow make it bootable with the windows iso, I'm not sure if that's even possible just wanted to ask.

---

### Post by sudodus on 2020-09-13
"Everything is possible" but sometimes very difficult.

The easy solution is to get a USB pendrive (size >= 8 GB) and make a Windows installer in it. It does not work to clone from a Windows 10 iso file. You need a tool for it (or do the things necessary manually, again somewhat complicated). I suggest using [mkusb](https://help.ubuntu.com/community/mkusb)

---

### Post by crip720 on 2020-09-13
According to google it is possible to install windows directly from ISO.  How easy or difficult would something to find out.  Google has quite a few hits about it and how to do it.

---

### Post by TheFu on 2020-09-13
> **zakey2 said:**
> What I mean is installing it without a usb, something like creating a partition and somehow make it bootable with the windows iso, I'm not sure if that's even possible just wanted to ask.

MSFT has all sorts of artificial restrictions. Best to ask them.

---

### Post by C.S.Cameron on 2020-09-14
UNetbootin can make a frugal install to a corner of the hard drive.
[https://github.com/unetbootin/unetbootin/wiki/installmodes](https://github.com/unetbootin/unetbootin/wiki/installmodes)
- Select "Disk Image, ISO and the Windows ISO file.  
- Select Type: Hard Disk.
- Select Drive: C:\
- Click OK.

**If** this works you should be able to boot into the Windows installer on the next boot.

This has worked for me in the past installing Ubuntu.
I have never tried it for a Windows 10 install.

There are reports on the internet that it will work for Windows.

I would suggest that the risk level is extremely high.

[B]Edit:
[/B]
I have given this a try, installing UNetbootin on an Ubuntu Persistent install made using **mkusb**.

All the right Windows files were loaded into /writable/upper/.
.
The boot files were put into /EFI/Microsoft/.

It looked promising.

However no Microsoft menuentry was added to grub.cfg, It would only boot to Ubuntu.

I was not able to do an update-grub on the persistent drive.

I will try again with a Ubuntu Full install.

---

