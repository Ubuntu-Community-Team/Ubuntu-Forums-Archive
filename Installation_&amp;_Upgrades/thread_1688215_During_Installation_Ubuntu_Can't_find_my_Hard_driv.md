---
title: "During Installation Ubuntu Can't find my Hard drive"
date: 2011-02-15
forum: Installation &amp; Upgrades
---

### Post by Reduced_Oxygen on 2011-02-15
im using unetbootin to install using my c drive from windows, when I get to the partitioning bit there are no options

---

### Post by Quackers on 2011-02-15
Welcome to UF.
WHat is your current system layout? How many primary partitions do you currently have in use? You can see in Windows by using the disk management screen. If you are unsure post a screenshot of that screen.

---

### Post by Reduced_Oxygen on 2011-02-15
where can i find the above mentioned menu?

---

### Post by Quackers on 2011-02-15
In Windows Start > right-click Computer and select Manage > in the left pane select Disk Management

---

### Post by Reduced_Oxygen on 2011-02-15
Vloume: (c:) Layout: partition Type: Basic Filesystem: NTFS Status: Healthy CCapacity: 55.70 GB

btw i want to replace windows with ubuntu

---

### Post by Quackers on 2011-02-15
Are you using the Windows Ubuntu installer (wubi)? Or are you trying to completely over-write Windows? If so, are you sure you won't need Windows again? It is possible to dual boot both Windows and Ubuntu, if you want to.
Which version of Windows are you running and which version of Ubuntu are you installing?

---

### Post by Reduced_Oxygen on 2011-02-15
iv tryed dual boot befor and wasnt a fan so i decided to wipe everything and install 11.04

im not using wubi (hate it)

no matter wich version i try has the same problem (just befor u comment on how unstable 11.04 is)

---

### Post by Quackers on 2011-02-15
Which version of 11-04 are you trying to install (alpha1/alpha2)?
Have you checked the md5sum of the downloaded iso file?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If that checks out ok, boot from the live usb and at the first purple screen (the one with the little man icon at the bottom) press any key. Then choose your language and on the next screen choose the option that checks the cd for errors. (It doesn't matter that you are using a usb - the check is the same).

---

### Post by Reduced_Oxygen on 2011-02-15
i believe im using alpha 1 but all that is fine becuz i have the same problem with other versions

---

### Post by Reduced_Oxygen on 2011-02-15
Yup ok did all of that checked out fine

---

### Post by Quackers on 2011-02-15
Ok, next question :-)
Are you using a raid array, or has the hard drive ever been used as part of a raid array?
Was the disk partitioned as GPT at some time (maybe by a Mac)?

When the installer gets to the partitioning stage, what is happening, exactly?

---

### Post by srs5694 on 2011-02-15
Please boot into live CD mode (the "try without installing" option), open a Terminal, and type the following command:

```

sudo fdisk -lu

```

Post the results here, between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings. That will let us see what your partition table looks like, since many problems with symptoms like you report can be traced to bad partition tables.

---

### Post by dabl on 2011-02-15
If your hard drive is a SATA drive, you can go into BIOS and change the mode from AHCI to "legacy" or "compatibility" or "IDE" or whatever is not AHCI.

If that solves the problem of the ubiquity installer not seeing the drive, then after you finish installing and have your Ubuntu running satisfactorily, during a reboot you can go back into BIOS and change the SATA mode back to AHCI and it should still work correctly.

---

### Post by Reduced_Oxygen on 2011-02-15
Help?!

---

### Post by glene77is on 2011-02-15
> **Reduced_Oxygen said:**
> 
Help?!


Help, 
Looks like you feel you are in over your head!
Been there before.  
Stay with it.  
There is No Magic, 
just a little mystery that has not shown its head yet !
Every time I try to upgrade an old "mysterious" computer 
I run into this same type of thing.  
Somebody before me Did Something !
:)

I am fascinated by the skills that these software-engineering / geeks have, 
and how willing they are to share. 

To show you that mysteries can be solved. 

My 'other' computer has 12 partitions, with Ubuntu 10.04, 
Puppy 5.11, Knoppix 6.2, WATT R2, Knoppix 6.4, Puppy 5.12 running. 
This is a multi-boot via Grub2.  
I had to get help from this forum 
in order to repoint the MBR to my preferred partition. 
Having been through that, I find MBR and BootLoaders interesting. 

My 'fast' computer is Win-XP and Ubuntu 10.04, dual boot. 
I did a MS Restore to Win-XP, and then resized the partition to make more room for Ubuntu, then used CloneZilla for Ghost Imaging.  

Hope to hear from you again.  :)

---

### Post by Reduced_Oxygen on 2011-02-16
thanks, but does anyone know if i need to creat the partitions first?

---

### Post by Reduced_Oxygen on 2011-02-16
> **Quackers said:**
> Ok, next question :-)
Are you using a raid array, or has the hard drive ever been used as part of a raid array?
Was the disk partitioned as GPT at some time (maybe by a Mac)?

When the installer gets to the partitioning stage, what is happening, exactly?

nope neva used a raid array

and ill take a photo

---

### Post by Reduced_Oxygen on 2011-02-16
> **dabl said:**
> If your hard drive is a SATA drive, you can go into BIOS and change the mode from AHCI to "legacy" or "compatibility" or "IDE" or whatever is not AHCI.

If that solves the problem of the ubiquity installer not seeing the drive, then after you finish installing and have your Ubuntu running satisfactorily, during a reboot you can go back into BIOS and change the SATA mode back to AHCI and it should still work correctly.

im using a laptop so its not sata

---

### Post by Reduced_Oxygen on 2011-02-16
[QUOTE=srs5694;10461096]Please boot into live CD mode (the "try without installing" option), open a Terminal, and type the following command:

```

sudo fdisk -lu

```

 ```
Disk /dev/sda: 59.8GB,59814236160 bytes
225 heads, 63 sectors/track, 7272 cylinders, total 116824680 sectors
Units = sectors of 1* 512 = 512 bytes
Sector size (logical/physical): 512 bytes /512 bytes
Disk identifier: 0x089c4586
 
   Device Boot     Start       End    Blocks   Id System
/dev/sda1   *         63 116808614  58404276    7 HPFS/NTFS 
```

---

### Post by Reduced_Oxygen on 2011-02-16
[IMG]http://img820.imageshack.us/i/pict0064d.jpg/[/IMG]
[IMG]http://img412.imageshack.us/i/pict0065ap.jpg/[/IMG]
[IMG]http://img401.imageshack.us/i/pict0066zo.jpg/[/IMG]
[IMG]http://img141.imageshack.us/i/pict0067i.jpg/[/IMG]

---

### Post by Reduced_Oxygen on 2011-02-16
anyone there?

---

### Post by Reduced_Oxygen on 2011-02-16
Ok figured it out ubuntu has decided my hard drive is a 55GB cdrom but heres the big problem i havent bean able to boot from cd or usb

---

### Post by srs5694 on 2011-02-16
I have no definite solution, but I do have some observations:


[list]
[*]Your partition table (revealed by "sudo fdisk -lu") looks OK to me. That eliminates a large number of possible causes.
[*]Your claim that you're using a laptop so the disk can't be SATA is incorrect. Modern laptops use SATA disks, and AFAIK laptop BIOSes have the same types of options for hard disk access modes as do desktop BIOSes. Of course, your specific laptop could be old enough that it uses a PATA disk, or your BIOS may lack the mode options that dabl suggested you check, but you shouldn't dismiss the suggestion to check those options, at least not for the reason you gave.
[*]Your claim that "ubuntu has decided my hard drive is a 55GB cdrom" is odd. I see no evidence of such a mistake. What makes you think that's the case? If Ubuntu is making such a mistake, providing the details to the people who are trying to help you is vital. If you're mistaken, providing the details will enable us to steer you out of a dead end.
[/list]


Given the evidence you've presented thus far, my suspicion is that you've got some leftover or incorrect RAID data on the drive. I'm not an expert on this topic, but uninstalling the RAID software (the mdadm package, as in "dpkg -P mdadm") from the live CD and then proceeding with the installation may enable you to proceed with the installation.

---

### Post by Reduced_Oxygen on 2011-02-17
> **srs5694 said:**
> I have no definite solution, but I do have some observations:
 

[LIST]
[*]Your partition table (revealed by "sudo fdisk -lu") looks OK to me. That eliminates a large number of possible causes.
[*]Your claim that you're using a laptop so the disk can't be SATA is incorrect. Modern laptops use SATA disks, and AFAIK laptop BIOSes have the same types of options for hard disk access modes as do desktop BIOSes. Of course, your specific laptop could be old enough that it uses a PATA disk, or your BIOS may lack the mode options that dabl suggested you check, but you shouldn't dismiss the suggestion to check those options, at least not for the reason you gave.
[*]Your claim that "ubuntu has decided my hard drive is a 55GB cdrom" is odd. I see no evidence of such a mistake. What makes you think that's the case? If Ubuntu is making such a mistake, providing the details to the people who are trying to help you is vital. If you're mistaken, providing the details will enable us to steer you out of a dead end.
[/LIST]
 
Given the evidence you've presented thus far, my suspicion is that you've got some leftover or incorrect RAID data on the drive. I'm not an expert on this topic, but uninstalling the RAID software (the mdadm package, as in "dpkg -P mdadm") from the live CD and then proceeding with the installation may enable you to proceed with the installation.
 
the laptop is PATA also im usinf unetbootin so as to boot from my hard disk, if i then goto gparted it shown the only partition as 55GB CDROM so there for i see the only solution to my problem is to boot from disk witch iv found some handy tips from else where in the forum

---

### Post by srs5694 on 2011-02-18
> **Reduced_Oxygen said:**
> the laptop is PATA also im usinf unetbootin so as to boot from my hard disk, if i then goto gparted it shown the only partition as 55GB CDROM

I've never seen GParted show optical discs, so this sounds very peculiar to me. Could you please post a screen shot?

Perhaps unetbootin is doing something strange with the BIOS drive mappings, which could then have continuing effects once Linux is booted. (I'm not familiar with unetbootin, so I don't know precisely what it does or what unintended or undesirable consequences it might have.)

---

### Post by Reduced_Oxygen on 2011-02-21
as it turns out i was right, i simply made a live cd using high quality disk on lowest burn speed and it worked :) thanks for your help guys

---

