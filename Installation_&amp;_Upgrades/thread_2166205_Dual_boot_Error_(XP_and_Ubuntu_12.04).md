---
title: "Dual boot Error (XP and Ubuntu 12.04)"
date: 2013-08-08
forum: Installation &amp; Upgrades
---

### Post by cpplin2 on 2013-08-08
Hi,
I have a dual boot (XP and Ubuntu 12.04) installation on my laptop. 2 days back my screen went black, the system was starting but I couldn't see anything.
I got it repaired actually my RAM went bust. 
BUT
Now I see the GRUB, I see the OS options but when I click on XP , the XP screen starts then the blue screen and again the GRUB. Then the system hangs.

If I select Ubuntu then it works perfectly fine.
How wanted to know has my XP been corrupted or repairing the GRUB will work or do I need to reinstall XP.
But reinstalling XP will put XP's grub in the MBR , so How do I replace it with Linux's grub later on ?

---

### Post by lukeiamyourfather on 2013-08-08
You can install either GRUB or the Windows boot loader after the fact from the install discs. Depending on what you're using Windows for you might consider running a virtual machine in Ubuntu.

---

### Post by cpplin2 on 2013-08-08
You mean to say I reinstall and update the grub.
I use windows for Visual Studio..!!!

---

### Post by sudodus on 2013-08-08
Before reinstalling Windows, you can try to repair it, which is possible with Bart PE, Win PE or Win 7 PE. The idea is to boot Windows from another drive, and run ```
chkdsk /f
```

Another alternative is to take out the HDD from the computer and connect it to another computer with Windows and run chkdsk. Do what is simplest for you.

If there is some slight error in the file system, that happened when your RAM broke, chkdsk might fix it for you.

When running Ubuntu: can you read your personal files (documents, picture files etc) in the Windows partition?

If you reinstall Windows, and it overwrites the grub bootloader, it is easy to reinstall it. See this link

[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by cpplin2 on 2013-08-09
Yes , I am able to see my Windows Partitions on Ubuntu , and able check my personal files, pictures, documents which I had saved on Windows.

I guess then simple windows repair might work.. ??

---

### Post by sudodus on 2013-08-09
> **cpplin2 said:**
> Yes , I am able to see my Windows Partitions on Ubuntu , and able check my personal files, pictures, documents which I had saved on Windows.

I guess then simple windows repair might work.. ??

Yes, good luck :-)

---

### Post by cpplin2 on 2013-08-09
Thanks mate..
Will try and let you know :)

---

### Post by oldfred on 2013-08-09
To install a boot loader:
 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

Also 
      
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)

---

### Post by lukeiamyourfather on 2013-08-12
> **cpplin2 said:**
> 
I use windows for Visual Studio..!!!

If the stuff you're developing doesn't use 3D accelerated graphics and isn't heavy memory or I/O wise then I'd use a virtual machine like VirtualBox instead of dual booting.

---

### Post by cpplin2 on 2014-03-14
Hi,

Finally I decided to totally shift to Ubuntu.. 

So what I did is I Formatted my xp drives to ext4 from ubuntu...!!
But then now my drives just auto mount as external hard drive..

But what I wanted is instead the root file system's size should have got increased..
How can I integrate the new hard drive portions into the root filesystem  ???

---

### Post by sudodus on 2014-03-14
It is rather complicated to increase a file system by merging several disks. RAID is a technology for doing that. But in your case, I'd suggest something else, exactly what depends on the layout (including the sizes of the partitions in your system as it is now.

So ***please describe*** it

1. generally with words

2. post the output of the following commands

```
sudo parted -l
```

```
df
```

---

