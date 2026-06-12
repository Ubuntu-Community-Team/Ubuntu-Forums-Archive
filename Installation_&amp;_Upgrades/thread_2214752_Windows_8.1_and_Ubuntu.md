---
title: "Windows 8.1 and Ubuntu"
date: 2014-04-02
forum: Installation &amp; Upgrades
---

### Post by jeff49 on 2014-04-02
So I do a lot of folding and I heard that Linux is better for doing the folding. I don't want to get rid of my Windows 8.1 so I was thing of double boot. I think that is what is called. Anyway I do no that I can't run them together and the stuff I am folding with Linux can't be folded with windows. 

Now I have been told that I can do this and I have also been told that I can't. I need someone anyone to tell me if it can be or can't be. 

Plus I see that Ubuntu 1 is not going to be available soon should I wait for next one to come out.

---

### Post by QIII on 2014-04-02
Hello!

Folding depends...

Are you using the CPU client or the GPU client?  I don't know if the GPU client is any further along in the last year or so, but it wasn't available for ATI GPUs on Linux in about 2012. 

I don't think they had a Linux NVIDIA client either.

 I used the ATI GPU client with 4 HD 5870s on a Windows machine for a while.  Sounded like a jet taking off!

If you want to use the GPU client, first check to see if the one for Linux is even available yet.  If it's not, it's probably not worth changing just for that.

But you could still run Ubuntu in a dual boot, of course!

Cheers.

---

### Post by jeff49 on 2014-04-02
Yeah I just built a system and have a EVGA Geforce Gtx 760 and using it and 8 core cpu for folding. I no someone was saying you could use the GPU on Linux for folding. 

How hard is it to run dual boot with Windows 8.1 and Ubuntu. I no with Windows XP system I had it was just intall it and it worked no doing anything with partitions. I don't care if I have to play around with partitions. But is it just install and go.

I guess what I am trying to say is there anything special I need to do to install Ubuntu beside Windows 8.1

---

### Post by oldfred on 2014-04-02
Is your Windows pre-installed or booting with UEFI and secure boot?

And with nVidia you will need nomodeset until you install the nVidia proprietary driver.

       Backup efi partition and Windows partition before Install of Ubuntu.
Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

More info in link in my signature, depending on model of computer you may need some of those links.

---

### Post by QIII on 2014-04-02
From Folding@Home's site:

> GPU folding is supported only in Microsoft Windows for now. Native support for Linux and OX-X may be a possibility in the future, and it’s something we’re looking into.

So, I'd say you won't be able to use the GPU with Ubuntu.

As for dual-booting with Win 8, I have no experience.  I stopped dual-booting some time ago and connect to my Windows machine remotely.  I don't use Win 8.

---

