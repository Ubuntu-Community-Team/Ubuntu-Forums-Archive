---
title: "Wubi download"
date: 2011-11-21
forum: Installation &amp; Upgrades
---

### Post by mikebl on 2011-11-21
I recently completed a new build. I have a 64Gb SSD where Win7 is located. About 9GB of free space is remaining. Along with the SSD, I have 2 other HHD's, one being completely empty. If I DL Ubuntu using the Windows Installer Wubi, I'm guessing that it would install it on one of the HHD's. Am I thinking right along those lines? Is this a pretty straight-forward DL without too much hassle on my part?
One issue that I have is, a day ago I tried to DL Ubuntu using VMPlayer and an .iso version of Ubuntu to create a 'Virtual Machine'. Should I delete any Ubuntu files along with the VMPlayer before I use the Wubi downloader?

Thanks for any advice

---

### Post by bcbc on 2011-11-21
You can choose where to install it. 

It won't be affected by the ubuntu install on vmware.

Why don't you just install ubuntu directly on that empty hard drive?

---

### Post by mikebl on 2011-11-21
That's where I plan to install it.
So, there's no need to worry about the partial install that's on the other HHD?
After I successfully loaded Ubuntu, Will I have an option at initial start-up of which OS I wish to use?

Thanks again for you time

---

### Post by Mark Phelps on 2011-11-21
I'm going with bcbc on this ... and STRONGLY recommending that you install Ubuntu to its own empty drive.

Furthermore, when you do that, ensure that drive is the ONLY drive connected to the PC?

Why?

Several reasons:
1) By disconnecting the SSD and the other drive, you ensure that nothing at all is done to Win7 during the Ubuntu install process.
2) This makes the SSD and the Ubuntu drive both bootable on their own -- which can come in real handy later when you need to do any repairs or updates to either.
3) You can try out Ubuntu on the spare drive without any wear and tear on your SSD.  If it works out well for you, you can later consider reinstalling on the SSD.

---

### Post by bcbc on 2011-11-21
> **mikebl said:**
> That's where I plan to install it.
So, there's no need to worry about the partial install that's on the other HHD?
After I successfully loaded Ubuntu, Will I have an option at initial start-up of which OS I wish to use?

Thanks again for you time

I meant without Wubi. Wubi lets you install anywhere but it uses a virtual partition which is a large file on top of the ntfs/fat32 partition. This actually works very well, but it's mainly of benefit to those who cannot or don't want to partition.

In your case, you have an empty drive so partitioning doesn't seem like a big deal. When you do a normal install Ubuntu will format the partition to be ext4 and this provides better performance and reliability than a wubi virtual disk.


How you install affects how you choose at boot time. With Wubi it adds an entry in the Windows Boot Manager and you get to choose between Windows or Ubuntu. When you select Ubuntu it will load up the grub menu and allow you to boot Ubuntu from there.

With a normal install, it replaces the windows boot loader so that the first menu you see is the grub menu, and from there you can choose Ubuntu or Windows. It's also possible to keep the windows bootloader and have the grub bootloader on a separate drive, and then just select which drive to boot from using your BIOS boot options menu.

---

### Post by mikebl on 2011-11-21
I agree with both of you with what you're suggesting.

So at what point do I physically disconnect the SSD and the other HHD? Then, if I'm understanding your posts' correctly, at initial start-up, I will have the option of OS's.

---

### Post by bcbc on 2011-11-21
> **mikebl said:**
> I agree with both of you with what you're suggesting.

So at what point do I physically disconnect the SSD and the other HHD? Then, if I'm understanding your posts' correctly, at initial start-up, I will have the option of OS's.

I have never had to disconnect drives - I mostly use laptops - so I'll leave that to Mark Phelps to answer. 

I think this is a cautious approach that's not required, but it obviously rules out the possibility of overwriting windows (usually due to user error - although the 10.10 installer was a little confusing and did lead some users to do this).

---

### Post by mikebl on 2011-11-22
I'm a little leery of disconnecting the HD's for now. What I've done now is created Live CD, verified it and loaded it but I did not do the actual install. It booted fine, asked which language I wanted so I'm guessing that I'm good to go with the actual install. 
My question again, sometime in the install process will it ask me where to install it, due to the limited space on my SSD.  If you read my previous post's you will see that I want to put it on an empty HHD. 
Thanks again

---

### Post by bcbc on 2011-11-23
> **mikebl said:**
> I'm a little leery of disconnecting the HD's for now. What I've done now is created Live CD, verified it and loaded it but I did not do the actual install. It booted fine, asked which language I wanted so I'm guessing that I'm good to go with the actual install. 
My question again, sometime in the install process will it ask me where to install it, due to the limited space on my SSD.  If you read my previous post's you will see that I want to put it on an empty HHD. 
Thanks again
Here's a guide to installing in a separate drive. It's written for release 10.10 but should be very similar to the 11.10 install:
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

If you have any questions - feel free to post back.

---

### Post by mikebl on 2011-11-23
I'm pretty good on the link in the previous post up to pg24/042. After that I'm a little confused.
I've got 3 hard drives 
  C/ is where Win7 is located
  D/ is a small partition of C/
  E/ is a CD drive
  F/ is for misc files
  G/ is empty, for install of Ubuntu
  H/ is a CD drive

So, the drive I want to be for my install will be
   /dev/sdc1 
Is that correct?

Now my boot loader will show up as
  /dev/sdc (name of hard drive

Is that it other than my location and name? 

So, if I've done this right, at initial start-up of my computer, I will have an option of which Os I want to load?

Thanks again for your time.

---

### Post by bcbc on 2011-11-23
You cannot assume what the designation will be for the drive. You can figure it out by booting a live CD, running "sudo fdisk -l" and confirming via the size and partitions which is which. Or mounting them and browsing the data.

If you install the bootloader on the specific drive e.g. /dev/sdc you will NOT automatically get the choice of which OS to boot. There is ONE drive that your BIOS is selecting by default and currently it has a windows bootloader, and it will boot windows.

Some BIOSes will allow you to hit a boot options key e.g. F12; and then select which drive to boot from (override at boot time). If you are able to select the ubuntu drive, then it will boot that. If you don't override it will boot the default i.e. Windows.

If you don't want to override then you'll have to change your BIOS default to always boot the Ubuntu drive (grub will then offer you the Windows install as it detects this automatically). OR install the grub bootloader on your default drive (replace windows' bootloader).

---

### Post by mikebl on 2011-11-23
So, it's going to decide where it will install. Not that it matters to me as long as it installs. 
Now, it shouldn't pick my c/ drive due to the lack of free space, right?

---

### Post by bcbc on 2011-11-23
> **mikebl said:**
> So, it's going to decide where it will install. Not that it matters to me as long as it installs. 
Now, it shouldn't pick my c/ drive due to the lack of free space, right?

I was talking about the bootloader, not Ubuntu. You need to take control about where it installs and also take control of where the bootloader installs. Auto is not a good idea.

---

### Post by mikebl on 2011-11-23
Now I got it. Sorry for the misunderstanding on my part.

---

### Post by bcbc on 2011-11-24
> **mikebl said:**
> Now I got it. Sorry for the misunderstanding on my part.

No apology required. I don't intend to sound short - sometimes I am quickly replying while at work. ;)

It's better to ask as many questions as you can upfront.

---

### Post by mikebl on 2011-11-24
I didn't take it that way at all. I'm more than grateful for your advice. 
I haven't pulled the trigger on the install yet. I would imagine that I'll end up booting out of my bios, which doesn't matter to me. I'm  sure that my MB will let me do that. 
What worries me is that I don't want to screw up my Win 7 OS. If worse comes to worse, I can always go back to the BIOS settings that I'm using now.

---

### Post by bcbc on 2011-11-24
Cool. 

So this is what I think you should do...
1. Install on your spare drive
2. Install the bootloader on your spare drive MBR

When the install is completed you'll boot straight into your windows install if you did it right.

Reboot, go into BIOS and change the boot order so that the Ubuntu drive is above the Windows drive.
Then you should get a grub menu, offering the new Ubuntu install (on top) and the Windows install on the bottom.

Note that Grub doesn't always correctly differentiate between the Windows recovery and the actual Windows (on Vista/7). So, the best way to check is to see which partition has the boot flag set. From Ubuntu:
```
sudo fdisk -l
```
If /dev/sda2 has the boot flag set, then that's the real Windows. In the grub menu it will say "Windows xxx (on /dev/sda2)".

If you are careful choosing the right drive and making sure the bootloader goes on it as well, there shouldn't be any issues.

Good luck.

---

