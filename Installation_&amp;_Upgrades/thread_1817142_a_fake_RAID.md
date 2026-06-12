---
title: "a fake RAID"
date: 2011-08-02
forum: Installation &amp; Upgrades
---

### Post by sarpedun on 2011-08-02
I was trying to install Ubuntu 11.04 today and after the installation GRUB would not let me boot up it was giving a file not found error. I am running off of a HP board and hard drives which are in some RAID set up that isn't software based but not really hardware either. I would prefer to not have to completely format both drives if possible, and would like to keep it in the RAID set up it has currently. has anyone encountered a similar issue? it is a HPE-175z board / hard drives from HP.

---

### Post by FormatSeize on 2011-08-02
Yes. I am having this issue right now as I type.
My thread here is called "Installing Grub still fails". Here's what I've done so far:

1. Tried to install 11.10 on the RAID 5. Nothing.
2. Tried 11.04 on the RAID 5. Still get the same error. 
3. Dismantled the RAID, and tried to install on only one hard disk. Nothing.
4. I realized that the disk I was installing on was called "/dev/sdc". Grub seems to be looking for a "/dev/sda". So I rebooted and picked the disk that the installer is calling "/dev/sda", and I am almost to the point where the installation fails right now.

I'll keep you posted.

EDIT: For me, installing on a single disk that the installer calls "/dev/sda" works with no problem. It got past that, ran update grub, and seems to be going well. 

In my RAID, there was nothing called /dev/sda", so installing grub there is going to endlessly fail. I find it odd that "/dev/sda" seems to be hard coded into the installation script. Why? What about those of us that want RAIDs?

---

### Post by EkuquoL on 2011-08-02
Can you still logon to tht system ? .. 

I had that problem installing the server edition of Ubuntu... Seems the dingus like to write " Installing Grub" But only install Terminal.
Just no graphic interface/GUI? 
Just run the 
# apt-get install gnome
An you will have a desktop.
You will have to install Unity and everything else manually.

Your system  should have a swap and a main partition.
Nothing more... If you isolate your usr folder too  its own partition... You will get indexing errors and other small annoying things. Such as file location not being found.

---

### Post by FormatSeize on 2011-08-02
> **EkuquoL said:**
> Can you still logon to tht system ? .. 
If I could, I couldn't figure out how. I did also notice that after the failed grub installation, that the installer, during the next try, did acknowledge that there was a filesystem and swap space filling the drive. The failed grub installations actually happen after the system is installed, but without a boot loader, there was no booting, and as far as I could tell, no logging on.

---

### Post by sarpedun on 2011-08-02
Same issue here, it installs fine just the bootloader doesn't know where to look for the filesystem I assume.

---

### Post by FormatSeize on 2011-08-02
The disks with the failed installation are bootable once you have an installation of Grub on a device named sda. I tried it after the installation while rebooting when I saw that sdc and sdb were showing up in the grub menu. I'm using sdc right now. It has a full GUI and everything, but I'm not sure what's missing since the install stopped once the grub-install failed. So what I'm going to try tomorrow is to set up a RAID 0, have an installation fail on those disks, then see what the show up as in the Grub menu, then try to log in. That is, assuming that updates will install and fix anything that happens during the installation after the grub-install stage.

---

### Post by Hakunka-Matata on 2011-08-03
In case you haven't checked this out, it might be worth while:
the alternate install CD has provisions for installation with a RAID array.  

[http://releases.ubuntu.com/natty/](http://releases.ubuntu.com/natty/)

---

### Post by YesWeCan on 2011-08-03
Are you folks all using fakeRAID here? That is, the RAID that you switch on in your bios?
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

AKAIK you cannot install the Grub boot program to a fakeRAID disk. You can install the Grub program to any other disk MBR (except GPT format), but the Ubuntu installer (which is a PITA) won't let you choose the disk unless you choose "manual" or "other" or whatever it calls it.

Unless you are dual-booting with Windows RAID, there is no need to use fakeRAID. I would disable it in the bios and remove the RAID metadata blocks from the disks:
sudo dmraid -E -r /dev/sdx   (x= a,b,c,d as appropriate)
Then install Ubuntu using the alternate install CD which allows you to create linux RAID and LVM etc.

---

### Post by YesWeCan on 2011-08-10
Someone has installed Grub2 to a fakeRAID: [http://www.techspot.com/vb/topic153346.html](http://www.techspot.com/vb/topic153346.html)

---

### Post by MooPi on 2011-08-10
I'm setting up a new computer for gaming and Windows 7 install and considered using raid 0 as you say in a fake raid. If I choose to install Linux will I have trouble getting grub to load on this drive config ? Will Windows 7 function in raid 0 from a raid config'd via Linux partitioning tools ?

---

### Post by YesWeCan on 2011-08-10
> **MooPi said:**
> I'm setting up a new computer for gaming and Windows 7 install and considered using raid 0 as you say in a fake raid. If I choose to install Linux will I have trouble getting grub to load on this drive config ? Will Windows 7 function in raid 0 from a raid config'd via Linux partitioning tools ?
I have no experience in this area. As ever with linux you can do anything you want; it is just a matter of how much "crafting" is required. My impression is that if you set up the RAID0 using Windows and then install Ubuntu to the array and then follow that link, it will work. I imagine you would need to use the alternate install CD which, I heard, has the dmraid drivers and will recognize the Windows RAID for what it is.
Try searching for "Installing Ubuntu to Windows RAID0" or similar.
I'd start another thread on this if you want to lure some experts.

---

