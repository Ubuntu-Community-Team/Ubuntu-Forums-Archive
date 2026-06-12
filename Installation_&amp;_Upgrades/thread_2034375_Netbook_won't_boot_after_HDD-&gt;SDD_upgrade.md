---
title: "Netbook won't boot after HDD-&gt;SDD upgrade"
date: 2012-07-28
forum: Installation &amp; Upgrades
---

### Post by DBSLLC on 2012-07-28
Hey guys, I've been trying for weeks to get the HDD in my Netbook upgraded (see [this thread]("http://ubuntuforums.org/showthread.php?t=2022238")) but it's acting funnier and funnier so I decided to forgo figuring out entire-partition encryption, settle on encrypting only the home drive, and press on.

Last night I followed the instructions [here]("http://infidigm.net/articles/ubuntu_hdd_upgrade/") to clone the drive but my machine now hangs during boot.  It appears to find the MBR and Grub lets me select which version of the kernel to boot.  After selecting the kernel version the Ubuntu "ticker" goes through about six little dots, I see the 3-line login prompt very very briefly, and then it seems to just hang.  Won't take keyboard input of any kind.

During the HDD cloning process listed above, things didn't go exactly right.  I was unable to use tune2fs to assign the swap partition on my new drive the UUID of the swap on the old drive so I created a clean partition and used mkswap with the -U option instead.

Additionally, I tried to use "sudo grub-install --root-directory=/media/blahblahblah" to re-install Grub as per the instructions but that didn't work either so I used boot repair instead.  But it didn't work.  Here's the pastebin from my most recent boot repair run, where it reported that everything had been fixed:

[http://paste.ubuntu.com/1115717/](http://paste.ubuntu.com/1115717/)

I'd really like to get things sorted out this weekend if possible.  Are there any other diagnostics I can run to troubleshoot this issue?

TIA
Phil

---

### Post by DBSLLC on 2012-07-29
Last night I tried to fix it again with no luck.  This time I attempted to use dd to clone the old partition but I got an error at the end saying the partition size stated in the superblock did not match the physical partition size.

I started with a Windows box and decided to start dual-booting Ubuntu.  I no longer use the Windows partition so when I upgrade the HDD I only want to have Ubuntu on the new drive.  What's the best way to do this?  Can I just use DD to clone the partition then use Boot Repair to install Grub on it (since Grub is currently on the Windows partition, which I don't want to copy onto the new drive)?

---

### Post by DBSLLC on 2012-08-02
<Bump>

My current HDD is getting worse and worse...  I really need to get this thing swapped out.  What's the recommended method for a forklift HDD migration?

If you look at the first attachment you can see that the MBR is on a Windows partition that I don't use any more.  Is it possible to move only the Linux partitions to the new disk and use Boot Repair or a similar utility to move the MBR/Grub to the Linux partition?

Thanks!

---

### Post by darkod on 2012-08-02
So, what's your problem actually?

Moving the data from your old encrypted /home without knowing the passphrase? I'm not an expert in encryption but I would say forget about it. I don't see a way to enter encrypted partition without the passphrase, that's the point of the encryption right?

So, since you can't move the /home data anyway, ask yourself this: do you have so much programs and settings that it's worth moving them or not?

If you don't, simply install 12.04 LTS on the SSD (I notice it has 10.04 LTS in the bootinfo link you provided) and that's it.

If you do have much programs to move, you can boot the old install, export the packages list to a file and save it on a usb stick.
After that do the new install of 12.04 LTS and import the packages list. I don't have links for the exact procedure right now, but I can look up something if this is what you want to do.

---

### Post by oldfred on 2012-08-02
You are copying an old partition structure onto a new device with dd. You will not take advantage of the SSD as it will not be optimized.

First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays,SSDs, and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment - post 8
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)

If only booting Linux you may want to consider gpt partitioning. It is newer and recommended for SSDs, but you can only boot Windows with gpt partitioned drives if you have the new UEFI not BIOS based system.

[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

I believe in clean installs and then restore data from backups. That way the new install is automatically housecleaned and set up correctly. If you have installed a lot of applications you can export the list, but if installing a new version many default applications have changed and you really do not want the old ones. I found I was still installing python2.5. Now LibreOffice has replaced OO and some others.

---

### Post by DBSLLC on 2012-08-02
Gents, I really appreciate your help.  My HDD is on its last legs and I was really beginning to worry that I was going to lose everything before I could get the data moved over.

Basically, I was just hoping to move my 11.x (10.x? I dunno) install over to the new drive so it would run just like it does now, but on a newer/faster/stable drive.  If simply doing a low-level copy of the data will defeat the purpose of most of the SSD performance increases then I don't mind doing a little more work to get things up and going.

I think I've seen links on recovering encrypted home folders so I'm not too worried about that...  I just guess I'll have to have yet another upgrade marathon this weekend.

Just so I understand the steps,

1)  Export package list to USB
2)  Decrypt home folder
3)  Install Ubuntu 12.x on new SSD
4)  Re-install all previous applications using package list on USB
5)  Move old ~/ to new ~/

Sound about right?

---

### Post by oldfred on 2012-08-02
You may want to review package list for obsolete applications. I was reinstalling python2.5. Now OpenOffice has been replaced by LibreOffice, so you should not reinstall OO. Some others also but I am not current on list.

Step 5 is copy /home whether data or encrypted. I do not know encryption, so cannot help on that.

If SSD is Ubuntu only you may also want to consider gpt partitioning instead of MBR(msdos). Arch recommends gpt. I am using gpt with BIOS boot on one hard drive and my SSD. You do have to create a 1MB unformated bios_grub to get grub2 to install correctly.
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

---

