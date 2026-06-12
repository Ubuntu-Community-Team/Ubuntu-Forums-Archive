---
title: "I can't even get to the installer... (Edgy Eft)"
date: 2007-01-18
forum: Installation &amp; Upgrades
---

### Post by MadBrahmin on 2007-01-18
Hello. I'm new here, new to ubuntu and pretty new to linux. While i had no problems installing  ubuntu on a virtual machine, i can't get it to work on a real one.

You will probably laugh at me, but here's the problem: I can't get the installer to work. I insert the cd, boot from it, select the first or second option, the ubuntu logo comes up and hangs there ad infinitum. Booting in non-silent mode didn't tell me much except that it's probably some problem with my hard drives. The message

hda: dma_timer_expiry: dma status == 0xff

keeps appearing onscreen every 10 seconds and continues until I hard-reset the PC. 

My hd configuration is thus: one sata hd with windows on it (the boot drive) and two ide drives, one of which was meant to house linux.

Please help? :(

---

### Post by lhtown on 2007-01-18
Are you using the live CD or the alternate CD or something else?

---

### Post by MadBrahmin on 2007-01-18
ubuntu-6.10-desktop-amd64.iso

I guess that would make it the live cd.

---

### Post by daenyth on 2007-01-18
> **MadBrahmin said:**
> ubuntu-6.10-desktop-amd64.iso

I guess that would make it the live cd.

You should probably get the i386 image (not amd64) unless you know for sure you have a 64bit processor (unlikely)

---

### Post by MadBrahmin on 2007-01-19
No, I'm sure. It's an Athlon 64.

---

### Post by rpradeep on 2007-01-19
This seems regarding your cdrom udma settings. Try to disable DMA for the cdrom and try.

---

### Post by Pobega on 2007-01-19
I would suggest you really try to Alternate CD, it has a thousand times less problems than the LiveCD; The LiveCD is nice, but not practical.

---

### Post by MadBrahmin on 2007-01-19
Okay, I tried both the x86 livecd with the same result as above and the x86 alternate cd. When I try to do anything from the alternate cd i get this:

PCI: device 0000:05:0a.0 has unknown header type 14, ignoring.
PCI: Cannot allocate resource region 4 of device 0000:00:06.0
PCI: Cannot allocate resource region 1 of device 0000:01:00.0
PCI: Error while updating region 0000:00:06.0/4 (00001001 != 0000f001)
ohci_hcd 0000:00:02.0 init 0000:00:02.0 fail, -16
ehci_hcd 0000:00:02.1 init 0000:00:02.1 fail, -16

Then after a while it prints 

Trying to enable the frame buffer...

And that's it. The checksums on the downloaded images are ok.

Any ideas? ](*,)

---

### Post by lhtown on 2007-01-19
Would you care to tell us more about your computer? I don't know what the error messages are referring to, but it seems that there is a piece of hardware that it is stumbling on.

I wouldn't expect it to work, but you might try installing it from a memory stick?

Also, you might try a different linux distribution like Knoppix on a live CD just to see if it works or gives you any more information.

Also, you might try disconnecting any extra hardware to eliminate things.

Can you even boot the live CD? If you can't even run the live CD, it would seem that it is not a disk drive problem.

---

### Post by coakley on 2007-01-19
Does it hang "Mounting Root Partition"?

If so, you will likely be hosed until someone addresses this issue at the kernel level. I just returned 3 Dell systems that would not be installed.

---

### Post by MadBrahmin on 2007-01-19
Certainly. The PC I'm trying to install Ubuntu to is:

Asus K8N4-E Deluxe (nforce 4 chipset)
Athlon 64 2.8
1 gb ram
1 300GB Western Digital SATA drive (boot)
1 200GB Western Digital IDE drive
1 40 GB Samsung drive 
a DVD drive
(sorry for not giving exact model designations of the drives, I don't know them, and it would take me two hours to get them out to see them...)
1 nvidia Gforce 7800GT

It's somewhat dated and pretty standard. I don't own a memory stick (I know, bizzare in this day and age), so I can't really check, but I imagine the effect would be the same. Knoppix works fine, without any trouble whatsoever. Except the screen, mouse and keyboard there isn't any hardware connected. I did disconnect the one hard drive I didn't need for the installation(the 200 GB IDE; I need the 300 gb sata to install grub to and the 40 gb to install linux to, so I couldn't disconnect them), to no avail. 

I can boot the live CD only so far as to see the boot menu and perhaps change some switches, but this didn't help me.

I imagine the part the booting hangs on is indeed part of mounting the root partition, but being new to linux, I'm not sure. How can I tell?

---

### Post by MadBrahmin on 2007-01-20
I gave up on Edgy Eft and tried to install Dapper today... And It's the same. I also tried to disable dma mode for my drives, but it didn't help. :roll: 

I am also now sure the problem occurs while 'mounting root partition'. Is there no way to make ubuntu like my computer? :(

---

### Post by MadBrahmin on 2007-01-20
For whomever may find this thread in the future: the switch

ide=nodma

solved my problem. I don't know why or how it works, but it did.

---

### Post by ecterg42 on 2007-01-20
Hello MadBrahmin,

I am a noob to Linux and seem to have similar problems trying to install Edgy on a HP Pavillion with AMD Athlon 64 X2 DualCore 5000+, 2 GB RAM, NVIDIA GeForce 6150 LE, SATA drive.  I also have a flat panel widescreen monitor.  The install freezes after a line about the PS2 mouse.

Please tell me what I need to do to utilize your solution.  Where exactly do I type "ide=nodma"?  How do I get to that 'place' in the installation?

Thanks, Ecterg.

---

### Post by MadBrahmin on 2007-01-20
If I recall correctly just press F6 in the boot selection screen (the screen with the timer that first pops up after booting the pc with the cd in the drive) and type it at the end of the line that pops up.

---

