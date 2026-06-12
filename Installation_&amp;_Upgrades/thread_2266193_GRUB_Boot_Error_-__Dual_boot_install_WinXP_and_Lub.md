---
title: "GRUB Boot Error -  Dual boot install WinXP and Lubuntu 14.01"
date: 2015-02-20
forum: Installation &amp; Upgrades
---

### Post by Jwilso on 2015-02-20
Like Shane36 I am new to Ubuntu and am trying to install but keep getting a boot error.

System  is Dell Pentium 4 1.7GHz with 1 Gig RAM and two IDE drives - HD0 with  40 GB and HD1 with 80GB and WinXP installed and working.  I want ubuntu  only on the 40GB HDD.  Have tried preformatting dev0 from XP for root,  swap and home partitions and always got hung up before install  finished.  Then I thought my system was too old for the version (11) I  was installing...I know not supported now...so I went back to Lubunu  14.01 and did the install that does all the partitioning and formatting  for you. All seemed to work well until I rebooted and selected Ubuntu  from the dual boot screen.   This is what I get (same error I had trying  to install Ubuntu 11 previously):

Try (hd0,0) :NTFS5: error: "prefix" is not set.
error: no such device: /ubuntu/disks/root.disk
error: no such device: /ubuntu/install/boot/grub/grub.cfg

Then some other info that scrolls by too fast to pause on

Then it starts GNU GRUB and I get 
GRUB> 

Is this happening because the HD0 has no label:  i.e. in WinXP it does not show up because it has no device name like D: or E:

Did  I miss something...I thought the Lubuntu installer would take care of  this.  And I don't know where the NTFS5 thing comes from because I  formatted the HD0 drive as FAT32 and ran chkdsk to confirm it is OK  because I know of issues with ubuntu and NTFS.

Like Shane my head is swimming with the stuff I've read trying to solve this myself after 3 days!
Any help will be greatly appreciated.
Jeff

---

### Post by oldfred on 2015-02-20
Boot live Installer CD or flash drive and install Boot-Repair.

 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by grahammechanical on 2015-02-20
> [COLOR=#000000]Have tried preformatting dev0 from XP for root, swap and home partitions[/COLOR]

We do not do that. Linux has its own file system format. The present default is Ext4.

What options install are you choosing?

Install Ubuntu alongside
Erase disk and install Ubuntu
Encrypt the new Ubuntu installation for security
Use LVM with the new Ubuntu installation
Something Else.

You could try disconnecting the second hard disk with XP on it and the select the Erase disk and install Ubuntu option. Once the installation is finished and Ubuntu is loading set the BIOS to boot from the Ubuntu hard disk, connect the XP hard disk and load into Ubuntu and run

```
sudo update-grub
```

That should give you a Grub boot menu with XP listed.

> [COLOR=#000000]error: no such device: /ubuntu/disks/root.disk[/COLOR]
[COLOR=#000000]error: no such device: /ubuntu/install/boot/grub/grub.cfg[/COLOR]

these folder or directories /ubuntu/disks/ and /ubuntu/install/boot/grub/ do not exist. That is why you are getting a "no such device" error message. The file grub.cfg does exist in a normal Ubuntu installation but not at /ubuntu/install/boot/grub/. And the file root.disk does not exist at all in a normal Ubuntu installation neither does the /ubuntu/ folder.

I wonder if you are trying to install Ubuntu from inside XP using wubi.exe. Are you? If so, please read this

[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

EDIT: It is a wubi install. That NTFS5 prefix not set error is typical of a wubi install using Ubuntu 11.04 or 11.10

[https://answers.launchpad.net/wubi/+question/171739](https://answers.launchpad.net/wubi/+question/171739)

Regards.

---

### Post by Jwilso on 2015-02-21
I solved the problem.
By changing to boot order of the hard drives.  HD1 had XP and HH0 had Lubuntu.  I was booting as CD-ROM - HD1 - HD0.  With no disk in the CD-ROM the BIOS gave me and option of Boot to Windows XP or Ubuntu.  Worked for XP but not for Ubuntu - got the GRUB error.  Saw that is was using wubi and the NTFS5 etc.  When I switched the drive order to CD-ROM - HD0 I got the GRUB boot with the option for Ubuntu and WinXP and all work fine.  I must have switched the drive order by accident when I had the drives out to make sure they were both set as CS drives.
Thanks for your replies - they were helpful....now to post this as solved....?
Cheers
Jeff

---

