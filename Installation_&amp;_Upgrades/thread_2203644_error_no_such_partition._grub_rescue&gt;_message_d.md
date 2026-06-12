---
title: "error: no such partition. grub rescue&gt; message displayed after removing partition"
date: 2014-02-04
forum: Installation &amp; Upgrades
---

### Post by SEKarlos on 2014-02-04
Hi,

I had Ubuntu and a trail version of Windows 8 installed on my laptop. The laptop would dual boot giving option to boot with either operating system. Via Windows 8 admin options I deleted the partition containing Ubuntu and extended the Windows 8 partition into the freed up partition space. Now when the laptop powers up the following message displays: error: no such partition. grub rescue>

Could somebody please advise how to rectify this situation?

I was aiming to have a machine with just Windows 7 reinstalled (I intend to reinstall Ubuntu at a later date )

I feel I must mention I have no Ubuntu or Windows recovery / repair / or installation discs.

Any help would be most appreciated

Many thanks


P.s I'm not technically savy

---

### Post by ubfan1 on 2014-02-04
When you deleted the Ubuntu partition, it contained the grub files (under /boot/grub), so the grub bootloader no longer runs.  If you can borrow some Windows install media, you  could reinstall the Windows bootloader.  Or, you may be able to reinstall grub, with its files put onto a Windows partition.  Best location for the grub files is a FAT (not NTFS) format recovery or tools partition which many machines have.  Make a directory named boot.  From the live media, mount  the FAT partition
sudo mount -tvfat /dev/sda1 /mnt
(or whatever partition you  put the boot directory onto).
 and install grub.
sudo grub-installer --boot-directory=/mnt/boot  /dev/sda
This should allow grub to run, booting Windows.

---

### Post by SEKarlos on 2014-02-04
Hi ,

Thanks for responding. What kind of Windows media are you referring too , would you mind specifying ? Sorry but I'm not to familiar with this stuff and don't want to make matters worse. All data on either OS was backed up before I deleted partition so no worries if solution means overwriting

---

### Post by ubfan1 on 2014-02-05
I was referring to the install media for Windows.  I never had any myself, only the vendor supplied "restore media" which really never offered the capability to repair a boot block.  I have used the grub installed to a FAT partition for years with no problems.  The FAT partitions are typically pretty small, but the grub files are small, and probably will easily   fit if you have any spare space at all on the paritition.  No partitions need to be deleted, just add a boot directory to one that's there.

---

### Post by oldfred on 2014-02-05
Always best to have current version repair tools for every system installed or Ubuntu live installer and Windows repairCD or flash drive.

You can create a Windows repair flash drive from any other Windows system that can restore a MBR with fixMBR command. Any friend, school or work computer with Windows can create a repair disk. Only need to be same 64bit or 32 bit and any version.
Or use Boot-Repair, but need a system to download it and create CD or flash drive.


       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)


 Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
      
 Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by SEKarlos on 2014-02-05
Thanks Oldfred,

I'm now at the end of my tether with this, I've done the following:

Burned the following discs (using another machine obviously):

The Ubuntu Boot Repair disc
Ubuntu Live CD Desktop 64 bit
Repair Disc Windows 7 64 bit


I've set boot priority on the 'broken' laptop so that it boots from the CD/DVD player first.

If I try and boot from either of the above discs i get the following message:

error: no such partition.
grub rescue>

Could you pleeeeeease explain what I should do next?  I'm a complete novice when it comes to administration of Linux or Windoze OS's, all I want is to be able to boot up my laptop and resolve this issue. Data was backed up so I don't mind 'splatting' or whatever the term is.

Any further help would be most appreciated.

---

### Post by oldfred on 2014-02-05
Did you correctly create DVDs? You do not copy ISO to DVD but install it so it extracts all the files from the ISO and makes it a bootable disk. If one large file on DVD that is not correct.

Or you have not selected DVD as boot device, It still is defaulting to hard drive with Broken grub. I used to burn a few coasters, but now use flash drives as they are reuseable.

 Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

        How to create a bootable Ubuntu USB Flash Drive - unetbootin
[http://www.linux-geek.co.nz/2011/04/11/how-to-create-a-bootable-ubuntu-usb-flash-drive/](http://www.linux-geek.co.nz/2011/04/11/how-to-create-a-bootable-ubuntu-usb-flash-drive/)
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)

   Usb installer from Windows
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)

---

### Post by SEKarlos on 2014-02-06
Hi oldfred,

I managed to launch Boot Repair Disc from a usb drive.

After running the repair processes the following url was issed:

[http://paste.ubuntu.com/6886652/](http://paste.ubuntu.com/6886652/)

Now when I reboot the laptop (from hard drive) the following message is displayed:

BOOTMGR is missing
Press Ctrl+Alt+Del to restart

Could you please advise what I should do next?

Many thanks

---

### Post by SEKarlos on 2014-02-06
Raised previous install to the ground and installed Ubuntu from USB drive.

Used the handy exe from this dude [http://rufus.akeo.ie/](http://rufus.akeo.ie/)


Sent from Ubuntu 13.10 :)

---

### Post by oldfred on 2014-02-06
Now sure where you are at now.

But error was from Windows. Its boot loader in MBR goes to partition with boot flag or active partition and looks for bootmgr. Boot flag was on sda3, your main install, but bootmgr was in sda2, but that also is missing BCD which is also needed to boot. But can be recreated with Windows repair tools.

---

### Post by SEKarlos on 2014-02-07
Did a clean install of Ubuntu, all working fine (except some issues with cpu, thiink relates to flash, will refer to forum for related posts). 

Thanks

---

