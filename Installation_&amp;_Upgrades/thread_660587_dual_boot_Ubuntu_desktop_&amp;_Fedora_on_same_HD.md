---
title: "dual boot Ubuntu desktop &amp; Fedora on same HD?"
date: 2008-01-06
forum: Installation &amp; Upgrades
---

### Post by picard12 on 2008-01-06
can I install dual boot Ubuntu desktop and Redhad Fedora server on same HD?

I already did search on dual boot topic but no one posted a thread about my topic.

---

### Post by logos34 on 2008-01-06
I don't know why not.  Not aware of any issues preventing you.  Install ubuntu second and grub will detect and add fedora to menu.lst so you have a choice at boot.  (Fedora uses grub too so you could just as well do it the other way.)

---

### Post by picard12 on 2008-01-07
> **logos34 said:**
> I don't know why not.  Not aware of any issues preventing you.  Install ubuntu second and grub will detect and add fedora to menu.lst so you have a choice at boot.  (Fedora uses grub too so you could just as well do it the other way.)

ok thanks. which Fedora should I download?

There are different versions:  Install media, KDE Live Media, and GNOME live media. :confused:

---

### Post by logos34 on 2008-01-07
hmm, they don't have a separate server version?  

The install media version has everything I suppose (~3.2 GB)--probably overkill with a lot of stuff you don't need (it looks like the DVD equivalent of the 5-cd set).

Maybe just go with one of the other desktop environment versions (~697 MB CD), depending on whether you like gnome or KDE. From there you can download just the server pkgs you need

---

### Post by picard12 on 2008-01-08
> **logos34 said:**
> hmm, they don't have a separate server version?  

The install media version has everything I suppose (~3.2 GB)--probably overkill with a lot of stuff you don't need (it looks like the DVD equivalent of the 5-cd set).

Maybe just go with one of the other desktop environment versions (~697 MB CD), depending on whether you like gnome or KDE. From there you can download just the server pkgs you need

what are Gnome & KDE ?

---

### Post by picard12 on 2008-01-09
I was unable to install Ubuntu dual boot with Fedora.
The Ubuntu Live CD disc boots up but it looks for logical drives on HD. It lists a bunch of logical sectors on HD in text format then it just stop. there was no error message.

I reboot PC over 5 times but the installation went through the same steps as above. 

I am really frustrated here. 
Can some one tell me why I can't get Ubuntu to setup dual boot. I can't even get to the GPart software to partition the HD.

---

### Post by DonnieP on 2008-01-20
If you installed fedora first, it probably made your entire hard disk (except for one small boot partition) into one large lvm (Linux logical volume).  This I think the Ubuntu installer doesn't appreciate.  If my diagnosis is correct you can shrink the logical volume in Fedora so it doesn't take up your entire hard drive which will then leave unallocated space that gparted can see.  The Ubuntu installer should then be able to do its thing with that unallocated space.  Alternatively, if reinstalling Fedora is an option, you could reinstall it and force it not to use up your entire hard disk.

---

### Post by sandysandy on 2008-01-20
> **picard12 said:**
> can I install dual boot Ubuntu desktop and Redhad Fedora server on same HD?

I already did search on dual boot topic but no one posted a thread about my topic.

i have dual booted (or Penta booted) with Ubuntu 7.10, Open SUSE 10.3, Mandriva 2008 and Fedora 8 in addition to Win XP. In my case i had installed Fedora 8 last. I had to manually edit the menu.lst of fedora to make sure that the correct partitions were mentioned against each OS entry. otherwise it was a breeze.

though each OS setup has partitioning software, u may also consider using GParted initially to partition ur HDD and then install the OS into the selected partition so that there is no confusion and loss of data. 

regards

---

### Post by DonnieP on 2008-01-20
Agreed - partition prepping is definitely preferred.  I actually triple boot Vista (which the laptop came with), Ubuntu (my 'home' distro) and (for now) Fedora.  Much safer to do any shrinking first before you go installing a new OS.  In my case I installed Fedora last but didn't let it install a boot loader.  I then went back to Ubuntu's menu.lst and added the stanza for Fedora.  This of course is after a previous install of the paldo distro which I accidentally allowed to take over my MBR.  So then I got to learn how to use the grub command to point MBR back to my Ubuntu menu.lst.

Anyway, for picard's benefit, the server install of Fedora (if you want to think about it that way) is called Red Hat Enterprise Linux 5 Server.

---

### Post by conradinsf on 2008-01-21
> **sandysandy said:**
> i have dual booted (or Penta booted) with Ubuntu 7.10, Open SUSE 10.3, Mandriva 2008 and Fedora 8 in addition to Win XP. In my case i had installed Fedora 8 last. I had to manually edit the menu.lst of fedora to make sure that the correct partitions were mentioned against each OS entry. otherwise it was a breeze.

though each OS setup has partitioning software, u may also consider using GParted initially to partition ur HDD and then install the OS into the selected partition so that there is no confusion and loss of data. 

regards

Hi sandysandy

I currently have my comp setup as ubuntu xp dual boot.  It was initially only XP, then I added another HD, partitioned it with GParted to have 4 ext3 partitions, 1 linux-swap, and 1 NTFS partition for data storage (mainly data storage for XP boot).  Ubuntu /root is installed on one ext3 partition, and the /home is setup on another ext3 partition.  So, it is a dual boot dual HD system now.  I have two more free (and available) ext3 partitions to play with and was thinking of installing Fedora on one ext3 partition.  I will be installing Fedora 8 (or at least attempt to) or maybe Open SUSE or Mint. 

You mentioned you installed Fedora 8 last.  How much work is required for editing the menu.lst of Fedora, and do I need to change the menu.lst for Ubuntu as well?  I may need your assistance with this.

---

### Post by sandysandy on 2008-01-22
> **conradinsf said:**
> Hi sandysandy

I currently have my comp setup as ubuntu xp dual boot.  It was initially only XP, then I added another HD, partitioned it with GParted to have 4 ext3 partitions, 1 linux-swap, and 1 NTFS partition for data storage (mainly data storage for XP boot).  Ubuntu /root is installed on one ext3 partition, and the /home is setup on another ext3 partition.  So, it is a dual boot dual HD system now.  I have two more free (and available) ext3 partitions to play with and was thinking of installing Fedora on one ext3 partition.  I will be installing Fedora 8 (or at least attempt to) or maybe Open SUSE or Mint. 

You mentioned you installed Fedora 8 last.  How much work is required for editing the menu.lst of Fedora, and do I need to change the menu.lst for Ubuntu as well?  I may need your assistance with this.


when u install another linux OS it is supposed to detect other Linux OS and Win OS by default and add the correct entries to its menu.lst file. But in practice this may not always be the case. after u have installed Fedora and have loaded its grub on the MBR, the IPL will point to its menu.lst file. So u will have to make sure that entries of your Win XP and Ubuntu in Fedora&#347; menu.lst file is OK. there are different ways of ascertaining the partition number [(0,1) or (0,2) etc] of your Win Xp and Ubuntu as well as Fedora. One is by using SGD, u can see the different partitions which u can then compare with Fedora&#347; menu.lst to see whether each OS has been tagged correctly to its respective partition. before u change the menu.lst file please take its backup. U may not need to change the menu.lst file of Ubuntu unless u want to use it for booting.

as far as Mint is concerned it is but a derivative of Ubuntu and u can change ur existing Ubuntu to Mint by adding some repositories.

regards

---

### Post by conradinsf on 2008-01-22
> **sandysandy said:**
> when u install another linux OS it is supposed to detect other Linux OS and Win OS by default and add the correct entries to its menu.lst file. But in practice this may not always be the case. after u have installed Fedora and have loaded its grub on the MBR, the IPL will point to its menu.lst file. So u will have to make sure that entries of your Win XP and Ubuntu in Fedora&#347; menu.lst file is OK. there are different ways of ascertaining the partition number [(0,1) or (0,2) etc] of your Win Xp and Ubuntu as well as Fedora. One is by using SGD, u can see the different partitions which u can then compare with Fedora&#347; menu.lst to see whether each OS has been tagged correctly to its respective partition. before u change the menu.lst file please take its backup. U may not need to change the menu.lst file of Ubuntu unless u want to use it for booting.

as far as Mint is concerned it is but a derivative of Ubuntu and u can change ur existing Ubuntu to Mint by adding some repositories.

regards

I will be installing OpenSUSE on my current dual boot Ubuntu/XP system.  Hopefully, it will go smoothly.  The only problem I have so far is that I am trying to boot up with the DVD, but it skips the install window and goes straight to GRUB.  The LiveCD for OpenSUSE works fine.  Maybe it has to do with having a dual optical drive (CDR as master, and DVDR as slave), and the boot sequence only gives me the option of booting to CD (I should be able to boot up with the DVD drive, shouldn't I?).  Now that I typed this, I will try to put the LiveCD (which works in the CDR drive) in the DVDR drive, to see if that is the case.  Wish me luck!  

I do have a question regarding the /home directory.  Do you recommend having a separate /home directory?  Others have mentioned they were able to use the same one for all their linux/ubuntu distros.  I currently have Ubuntu /root on one ext3 partition, and its corresponding /home directory on another ext3 partition.  I have two more ext3 partitions available, and I was thinking of installing OpenSUSE on one and Fedora on the other (and all sharing the /home from Ubuntu).  But if this will give me grief, then I guess I will just install OpenSUSE on one ext3 and its /home on the other ext3.  

Any suggestions and/or comments will be greatly appreciated.  :)

---

