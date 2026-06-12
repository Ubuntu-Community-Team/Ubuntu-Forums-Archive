---
title: "New Ubuntu installation: 1st or 2nd hard disk ?"
date: 2016-01-13
forum: Installation &amp; Upgrades
---

### Post by tasos-lists on 2016-01-13
I am about to install in my Desktop machine the Ubuntu 14.04 LTS edition plus the Win7 edition in order to create a dual-boot system. The system consists of 2 seperate hard disks, that means a seperate disk deveted for each O.S.  The question is to know what is the preffered combination method?
1) 1st H.D. for Win7 and 2nd H.D. for Ubuntu ?  or
2) 1st H.D. for Ubuntu and 2nd H.D. for Win7 ?

My concern has to do about where will be the best place ( hard disk) for the boot-loader to be installed, when attempting in the future changes or new installation of any O.S. ?

Thanks for any possible answer.
Tasos

---

### Post by Bashing-om on 2016-01-13
tasos-lists; Hello, Welcome to the forum .

If this were my system I would -
leave Windows well enough alone ,,, do not even touch it .. I expect that the Windows drive to be recognized by the ubuntu installer as device sda, but verify this from the ubuntu installer, as sometimes if using a USB as the install medium the system firmware may assign 'sda' to the usb device .

Now install ubuntu to that 2nd hard drive ... partitioning is  of a personal preference ... how large is the drive ?... what are your use cases ? Do you intend to share data with Windows ? How much space do you want to devote to ubuntu ?  How much space for Windows' data files .... as a 1st time installer, the "easiest" method of install is to let the installer make all the decisions about installing ubuntu .. however this approach will not take into account any space you want to reserve for Windows - that partitioning scheme is " something else " ... You may not be prepared to go there ; but there is nothing to it if you do prior prudent planning and do the homework .

As to the boot code ... leaving Windows alone in the 1st hard drive and installing ubuntu on the 2nd hard drive ... Windows boot code on the 1st hard drive will not be touched . Just insure that ubuntu's boot code is installed to the same hard drive as ubuntu is install to ( most likely 'sdb' ). One would then in ubuntu chainload the Windows boot code to ubunu's boot code  giving you the choice from ubuntu which operating system to boot when this 2nd hard drive is selected as 1st boot priority in the system firmware. Then in the event of any failure of booting with the 2nd hard drive - reselecting the 1st hard drive in the firmware Windows can be booted independent of ubuntu .

So how to tell what drive has what designation ...
Boot the installer -> "try ubuntu" to the desktop -> key combo ctl+alt+t to gain a Command Line Interface .
Here execute terminal command:
```

sudo parted -l

```
all of your drives will be listed with the designation the system has assigned.
All you need to do is insure that you know which drive is the installer, which is Windows and which WILL be ubuntu.

A 1st time install is fraught with concern
But hey
[INDENT][INDENT][INDENT]millions do it -> you can too
[/INDENT][/INDENT][/INDENT]

---

### Post by tasos-lists on 2016-01-13
Well, I have tried several times in the past the configuration that you suggested sda for windows and sdb for Ubuntu.
I was just wondering what it looks like being the reverse configuration, e.g. installing first on the first disk the Ubuntu, and then on the second disk the Win7. 
Since the boot-loader sits always on the first booting disk, wouldn;t it better to be  Ubuntu on the first disk? That means that reinstalling the O.S. in the second disk , that would leave Ubuntu untouched!
Since my prior (main) O.S. is always UBUNTU , not the win7, I trying to think what would be the best choice for me, in any aspect, in the technical aspect,too.
Each of the disks is 500 GB capacity, and at the moment I am going to wipe the entire disk which contains the Win7. That's why I am wondering which O.S. to install first on the 1st disk.


Tasos

---

### Post by Bashing-om on 2016-01-13
tasos-lists; Well ..

Maybe best -- before giving any further advise is to know what we are dealing with here, as you say -
> 
Well, I have tried several times in the past the configuration that you suggested sda for windows and sdb for Ubuntu.

If this is a EFI system .. there is a learning curve to adapt .
Post back to us the output of terminal command:
```

sudo parted -l

```

As to :
> 
Since the boot-loader sits always on the first booting disk, 

untrue ! The boot code sits on whatever drive ( or special use cases the partition ) that the code is installed to.
You tell bios where the boot code to be used is located ( which hard drive ) and bios goes hunting there for the boot code -- then grub goes hunting up the files to boot the selected operating system .

Which hard drive contains which operating system is irrelevant - as you set in bios ( EFI firmware ) where to go looking for the respective boot code . Now if no good boot code is found where you directed the firmware to look, then it defaults down the list ( 2nd hard drive, USB, and DVD - depending on how you have set the list up ).

The choice is utterly your choice - so long as you know what to tell bios ( EFI firmware ) where the desired boot code is located .. and BIOS can find good boot code at that location .
In my scenerio Windows' boot code is on that 1st hard drive, and if you want to boot Windows irrespective of ubuntu . set in bios to boot from that 1st hard drive;
With ubuntu installed to the 2nd hard drive, bios set to boot from that 2nd hard drive AND ubuntu boot code installed to the 2nd hard drive AND AND ubuntu's os-prober has found and added Windows to the booting chain - Then you have the choice from ubuntu's boot menu which system to boot up.

If it aids your thought process to have ubuntu installed to sda ( 1st hard drive) and Windows installed to the 2nd (sdb) hard drive, well more power to you . Windows' boot code on the drive containing the Windows' operating system, ubuntu's boot code installed on the hard drive containing ubuntu. Ubuntu's boot menu can contain the means to boot Windows !

Clear as mud ? It is what you set in bios as the booting device that matters .

[INDENT][INDENT][INDENT]all in the process
[/INDENT][/INDENT][/INDENT]

---

### Post by tasos-lists on 2016-01-13
At the moment, I am posting from  my laptop , so I can not send the output of the above command.
Now, let me make things more easy. 
Let's suppose there is no O.S. already installed in the system, so we are going to decide which O.S. will be installed first, keeping in mind that the favorite  O.S. will be Ubuntu.
One  thing I am thinking , is if , BOOTLOADER AND UBUNTU would be better together on the same disk.

Notice:
My previous installation on another system, was BOOTLOADER + VISTA were on the 1st disk and Ubuntu was alone on the 2nd disk.

---

### Post by tasos-lists on 2016-01-13
At the moment, I am posting from  my laptop , so I can not send the output of the above command.
Now, let me make things more easy. 
Let's suppose there is no O.S. already installed in the system, so we are going to decide which O.S. will be installed first, keeping in mind that the favorite  O.S. will be Ubuntu.
One  thing I am thinking , is if , BOOTLOADER AND UBUNTU would be better together on the same disk.

Notice:
My previous installation on another system, was BOOTLOADER + VISTA were on the 1st disk and Ubuntu was alone on the 2nd disk.

---

### Post by ajgreeny on 2016-01-13
Assuming neither disk has an OS on it, which is what I think you are saying, I would install windows first to the first disk (sda) and as far as I'm aware that means the windows bootloader files will be put on sda.

Now install Ubuntu to the second disk (sdb) but make sure you use the **Something Else** option when partitioning the disk, and tell it to put grub, the linux bootloader used by Ubuntu, on to the root of the second disk, ie /dev/sdb.  Only by choosing Something Else will you get the option of where grub goes

If you do this right you can set sdb as the boot priority device, giving you the option to boot to either Ubuntu or Windows, but you will also have the backup arrangement of the windows bootloader files on sda allowing you to boot straight to windows if grub ever lets you down, by setting sda as first boot device.

If you want to share data files such as documents, music and videos, between the two OSs you should consider making one or more shared ntfs partitions separate from the OS partitions.  Come back and ask again if this sounds right for your situation.

---

### Post by Bashing-om on 2016-01-13
tasos-lists; Well ..

Windows boot code boots Windows Operating system ... Windows has no regard for any other operating system.
ubuntu boot code boots ubuntu and MAY also boot Windows . - GRUB GRand Unified Bootloader.

Windows boot code on the hard drive containing Windows'  operating system
ubuntu boot code on the hard drive containing ubuntu operating system.

If you prefer to "think" the primary should be on the 1st hard drive, go for it . It makes no difference to the hardware what is where. The difference is that you know and have installed the boot code correctly AND you can tell bios what to boot .

To be honest .. my think'n for the "primary" is my work station is on my first hard drive and on that hard drive's 1st partition.
```

sysop@1404mini:~$ sudo blkid
[sudo] password for sysop: 
/dev/sda1: LABEL="1404mroot" UUID="3a47f1f1-ed1f-4134-b6aa-be101a7d97b4" TYPE="ext4" 
/dev/sda2: LABEL="1404mhome" UUID="29a6fc4f-ff12-4cac-8eb1-e98e50f1107f" TYPE="ext4" 
/dev/sda5: UUID="192a4783-56fa-4fd0-a62f-c45a14c08482" TYPE="swap" 
/dev/sda6: LABEL="DATA" UUID="3ad091a1-5036-463b-ba4e-88e98e41b07a" TYPE="ext4" 
/dev/sda7: LABEL="LUBU1404" UUID="4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d" TYPE="ext4" 
/dev/sda8: LABEL="1404mvar" UUID="136af805-5758-4880-acc4-0e1d35e2c266" TYPE="ext4" 
/dev/sdb1: LABEL="my_stuff" UUID="6a24777c-8191-4230-81f1-376f31b321e5" TYPE="ext4" 
/dev/sdc1: LABEL="ubie14.04std" UUID="345cab2e-22e7-4f89-8781-05cc0f7628a2" TYPE="ext4" 
/dev/sdc2: LABEL="ubie1204" UUID="7dd23297-30ea-417a-8f69-3e2df76f3192" TYPE="ext4" 
/dev/sdc3: LABEL="ubie15.10" UUID="2ec4733f-db40-4db0-aef8-5c54e54085ab" TYPE="ext4" 
sysop@1404mini:~$ 

```
where I am booting 5 'buntus and 14.04 minimal - root installed to sda1 - is my work horse .

if it is easy
[INDENT][INDENT]do not make it complicated
[/INDENT][/INDENT]

---

### Post by tasos-lists on 2016-01-13
The reason for this post was to find  out if any difficulty arises when someone tries a different approach to the installation.
Since my first booting device will be the 1st hard disk,  I am going to try the following setup

Installation of Ubuntu on the 1st H.D. Then I will istall Win7 on the 2nd H.D.

Thank you for your support
Tasos -  Crete isl., - Hellas

---

### Post by grahammechanical on 2016-01-13
The Ubuntu installer will default to installing the Linux boot loader to sda whatever drive we are installing Ubuntu to. This is why we advise making sure that the installer is putting the boot loader (Grub) where we want it to go.

For convenience you could install Ubuntu on sda and let the installer do things its way. But here is the problem: If you install Windows after Ubuntu then the Windows installer will most likely install the Windows boot loader on to both disks. I have had this happen to me with the Windows 8 preview edition.

The terms sda & sdb are relative to the sata ports on the motherboard. You could install one OS at a time with only one drive installed at the time. Then you could connect the Ubuntu drive to the sata port that matches sda & the Windows drive to the sata port that matches sdb. Then load into Ubuntu and run

```
sudo update-grub
```

And that will update the Grub configuration files to detect Windows 10 on sdb and put Windows 10 as a boot option in the Grub boot menu. And if you need to reinstall Grub the command would be

```
sudo grub-install /dev/sda
```

Also, if you need to re-install Ubuntu you do not have to worry about where the boot loader is going to be installed. Ubuntu will be on sda and the installer will default to installing grub on sda. It will not over-write the Windows loader on sdb.

Whereas, with Windows on sda there is a chance that a re-install of Ubuntu on sdb will over-write the Windows loader on sda because we failed to change the default location for installing Grub. I have had that happen to me as well.

Regards

---

### Post by tasos-lists on 2016-01-13
I see. Well I was used up to now, to install Ubuntu after the installation of Win, and have had no problems, both installed on the same disk, in different partitions, of course. This the first time I am about to install in seperates hard disks, that's why I am asking these questions. It will be a chance to try this way and see what is going on.

regards

---

### Post by oldfred on 2016-01-13
Just be sure to change default boot device in BIOS to the drive you want to install Windows into.
Otherwise it will install its 100MB boot partition on the drive set as boot in BIOS. It has been known to just overwrite the first 100MB of the boot drive regardless of what is there, since it does not correctly see Linux partitions.
I would keep Windows on first SATA port or as sda. I used to have XP on sda, and on that old system booted sdd or sde as default. And I converted to only using gpt for Linux but for BIOS boot Windows had to have MBR(msdos) partitioning.

---

### Post by tasos-lists on 2016-01-13
I will give it a try tomorrow.

regards

---

