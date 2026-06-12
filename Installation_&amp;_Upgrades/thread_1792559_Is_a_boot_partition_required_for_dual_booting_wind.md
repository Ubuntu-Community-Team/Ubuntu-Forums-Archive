---
title: "Is a /boot partition required for dual booting windows 7 with ubuntu"
date: 2011-06-28
forum: Installation &amp; Upgrades
---

### Post by ktp.kti on 2011-06-28
Is a /boot partition required for dual booting windows with ubuntu? 

I am quite confused after googling this. 

Some say 2 partitions are enough. A '/' partition at beginning and a 'swap' partition at the end.

(Some say a single / partition is enough. see [here]("http://blog.sudobits.com/2011/04/23/how-to-install-ubuntu-11-04-from-usb-or-cd/"))

Others ask to create 4. 
/boot (for programs critical for booting)
swap (space for virtual memory)
/ (root directory, for installing programs used for running the system)
/home (for saving your files)
I understand that /home is optional, but is /boot required?
There is 100 MB of space in front of my windows partition. I think that that is my boot partition.

Can i proceed with installation of only the / partition or should i use both / and swap partitions?

---

### Post by SoFl W on 2011-06-28
If you let Ubuntu handle the install it will set up everything automatically for you.  If you wanted a separate "/home" partition then you have to do it manually.  No a "/boot" partition is not necessary.

---

### Post by ktp.kti on 2011-06-28
> **SoFl W said:**
> If you let Ubuntu handle the install it will set up everything automatically for you.  If you wanted a separate "/home" partition then you have to do it manually.  No a "/boot" partition is not necessary.

I would have gladly let ubuntu handle these stuff. Bu it did not do so the way i wanted. 

Actually i had already partitioned a 20GB drive for ubuntu. But there was no option in ubuntu to install here. By default it went to the C drive with windows. So i had to take the harder route.

Thanks for the reply!

---

### Post by ktp.kti on 2011-06-28
If i create only a / partition, will the swap partition be automatically created? (I am asking this just out of curiosity. I have started the installation after creating a / and a swap partition which is running smoothly now)

---

### Post by ktp.kti on 2011-06-28
> **ktp.kti said:**
> If i create only a / partition, will the swap partition be automatically created? (I am asking this just out of curiosity. I have started the installation after creating a / and a swap partition which is running smoothly now)
 
I tried this in another installation. I recieved a notification saying that if i proceed without creating swap partition the performance will be severely affected. So i went back and created a swap partition.

So finally i learnt these for a windows 7 dual boot with ubuntu in a separate partition,
1)you first have to create free space by deleting/resizing partitions.
2)Then create a swap area partition (ext4) (logical) first of 2048 MB (for a 2GB RAM) located at 'the end'.
3)Then create / (root partition)(primary) (also ext4 file system) with the rest of the free space located at 'the beginning'.

That's all! (Phew!)

---

### Post by YesWeCan on 2011-06-28
The Ubuntu installer is not very clear, is it?
> **ktp.kti said:**
> I tried this in another installation. I recieved a notification saying that if i proceed without creating swap partition the performance will be severely affected. So i went back and created a swap partition.
Actually, you don't *have* to install a swap partition. You can easily add one later.
> So finally i learnt these for a windows 7 dual boot with ubuntu in a separate partition,
1)you first have to create free space by deleting/resizing partitions.
Use Windows to create one free, primary partition for all Ubuntu stuff.
> 2)Then create a swap area partition (ext4) (logical) first of 2048 MB (for a 2GB RAM) located at 'the end'.
3)Then create / (root partition)(primary) (also ext4 file system) with the rest of the free space located at 'the beginning'.
Using the Ubuntu installer, first make the free partition an extended partition. Then add logical partitions for / and swap and any others. Where they are placed is of little importance.

It is best to install the boot code to a different disk than the Windows disk since it breaks the MBR.

Glad you wrestled it into submission. ;)

---

### Post by oldfred on 2011-06-28
Do not mix up windows /boot 100MB boot/recovery partition with a /boot in Ubuntu. The windows partition has to have windows in it and nothing else.

Only if you have a older computer circa 2002 BIOS that limited booting from the first 137GB or a server will you possibly need a Ubuntu /boot partition under MBR(msdos) partitioning.

---

### Post by ktp.kti on 2011-06-28
Thanks YesWeCan for the clear explanation! I'll try your method next time!

---

