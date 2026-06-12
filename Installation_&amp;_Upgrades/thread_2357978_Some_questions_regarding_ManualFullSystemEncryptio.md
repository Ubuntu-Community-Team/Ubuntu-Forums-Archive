---
title: "Some questions regarding ManualFullSystemEncryption guide in Community Wiki"
date: 2017-04-08
forum: Installation &amp; Upgrades
---

### Post by ranloe on 2017-04-08
Dear Paddy,

I've read though your guide ([https://help.ubuntu.com/community/ManualFullSystemEncryption](https://help.ubuntu.com/community/ManualFullSystemEncryption)) and am preparing everything to execute it. However, my situation is slightly different than the one in your example and, since I'm still a beginner at Linux, I thought it would be best to get some directions before I start. I alrdy have Dualboot Ubuntu 16.04LTS and Windows 10 on my PC (Installed Windows first, then Ubuntu. Everything without encryption). However, unlike in your example, I have 3 drives in my laptop.  
 
 
 1 SSD (calling this sda for further reference; 250gb) which has windows (both system and data space) on it,
 
 
 1 SSD(calling this sdb for further reference; 128g) which has ubuntu on it (both system and data space), and  
 
 
 1HDD(2T) with two partitions, one for extra data I acces from windows and one for extra data from linux.  
 
 
 
What I would like to do has changed since I first emailed you, but I will describe both my old (B) and new (A) goal so that more people might be helped by your reply.
 
 
 A:
What I would like to accomplish
 
 a) A fully encrypted Ubuntu (system + data) on sda (250gb)
 b) An encrypted extra data partition on the HDD for Ubuntu to use
 c) A Windows install on sbd (128gb).  
 
 
 My questions:

How do I also encrypt the relevant partition on the HDD, which is not what you call in your example 'a separate data partition' aka home, but rather an extra volume to be used for storage of files that are infrequently accessed. To be clear, I want my home folder to be on the same drive (sda) as the fully encrypted Ubuntu install. To encrypt the HDD partition for ubuntu, can I just repeat the process you described for creating a seperate encrypted data partition and then name that something else than home? Or would this still make it the home directory but just with another name?
 
 
 To accomplish a) will mean erasing the entire windows install. Can I just do that, like boot in a live USB of ubuntu, erase the entire sda & sdb, follow the guide installing everything described in the guide to sda and then install windows onto sdb later? Your guide presupposes that windows is already installed and I'm afraid that installing it afterwards will give problems with being able which OS to boot into later on. I could also erase both sda and sdb, then install windows on sdb first, and then follow the guide. However, this would mean my ESP partition is on sdb and I want it to be on sda, namely the same drive that the fully encrypted Ubuntu install will be on.
 
 
 
 
 B:
This is what I first wanted to do, and put in the email I sent you. I've changed my mind because I want to start using Linux primarily and only use windows for gaming, so I'd rather have the larger (and faster) SDD for my main OS. I'm repeating it here because others might still want to do something similar
 
 
 a) A fully encrypted Ubuntu (system + data) on sdb (128gb)
 b) Fully encrypt the HDD. However, I don't think that would be possible since then Windows won't be able to acces its relevant partition, right?
 c) retain the Windows install
 d) Move the ESP partition from sda a to sdb. Could this be done by just deleting the existing ESP on the windows drive (sda) and then following the guide creating a new one on the Ubuntu drive sdb. I feel this might cause problems with booting into Windows later

Thank you for your time and consideration

---

### Post by oldfred on 2017-04-08
I do not know LVM & encryption.

But grub only installs to the ESP - efi system partition on drive seen as sda. So best to keep an ESP on sda.
Is not Windows already UEFI also? Or do you have mixed UEFI & BIOS/CSM boot?

Drive order is set by UEFI/BIOS. And that usually is set by the port order you plug drives into motherboard. I have skipped ports and had major issues where flash drive as sdf, becomes sdb and every drive changes. While system boots using UUID, some of my terminal commands still used device like /dev/sdf, so had to be careful of which drive was which. 
Best to have drives installed in SATA port order on motherboard starting at SATA0.

Normally I would suggest keeping Windows as sda as it seems to like or maybe assumes it always is the only drive.
UEFI should boot from any drive's ESP, but Ubuntu's grub only installs to sda. So grub major updates may fail if you move ESP. The UEFI entry has the GUID of the ESP partition in it.

You should see same GUID with these two commands:
 to see GUID/partUUID for each device, post with code tags to preserve formatting:
lsblk -o +PARTUUID /dev/sda 
   # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v

---

### Post by Paddy Landau on 2017-04-08
You have some great questions, ranloe.

I shall answer A, not B, because that is what you want.

If you have a fast computer with plenty of RAM (at least 8GB, but preferably more), you can install Ubuntu in the entire machine, and then install Windows under Ubuntu in a virtual machine. That will make your entire machine, even Windows, secure, and you will be able to run Ubuntu and Windows at the same time! I've tried this, and it works well — but, as I say, you need a fast machine with plenty of RAM. If you're a gamer, though, you probably won't want to do this, as it will leave Windows running a little slower; not noticeable for documents and normal browsing, but probably noticeable for gaming.

This answer addresses your requirement to dual-boot.

[INDENT]*Important: My instructions will completely destroy any and every existing installation, which means that all data will go as well. You must ensure that you have a full, confirmed backup, preferably two copies, of everything that you need — both Windows and Ubuntu — before you proceed.*
[/INDENT]

**Some things to bear in mind**

[LIST]
[*]Windows won't be able to take advantage of LVM or to see Ubuntu's storage.
[*]Ubuntu will be able to access and modify files on Windows.
[*]Older versions of Windows were rude and would overwrite any existing system. Windows 10 is more polite, so if you're installing Windows 10, you can do so safely after installing Ubuntu. It's still a little rude in that it stops you from booting into Ubuntu, but we have a fix for that!
[/LIST]
 **Prepare your partitions**

[LIST]
[*]Using Gparted, wipe your partitions. You can do this easily: simply [create a new Partition Table]("https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessPartitionFormatEncrypt#Set_up_the_drive") (type GPT) on each of your three disks. Remember: *This will instantly wipe each one without warning*. (Have you made your backups?!)
[/LIST]
Now, proceed with the installation exactly according to instructions, but with the following changes.

[LIST]
[*][Set up the ESP]("https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessPartitionFormatEncrypt#Set_up_the_ESP") (size 550MB) as [FONT=lucida console]sda1[/FONT].
[*][Create the system partition]("https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessPartitionFormatEncrypt#Create_the_system_partition") as [FONT=lucida console]sda2[/FONT], filling all the remaining space on [FONT=lucida console]sda[/FONT].
[*]Leave [FONT=lucida console]sdb[/FONT] alone (apart from creating the Partition Table as already mentioned).
[*]Create two partitions on [FONT=lucida console]sdc:[/FONT]
[LIST=1]
[*][Create the data partition]("https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessPartitionFormatEncrypt#Create_the_data_partition") on [FONT=lucida console]sdc1[/FONT] for your extra Ubuntu data (even though it won't be for [FONT=lucida console]/home[/FONT] in your case). Remember that Windows will be unable to see it. Make it whatever size you feel is appropriate for your extra Ubuntu data.
[*]Using GParted, fill the remaining space on [FONT=lucida console]sdc[/FONT] as [FONT=lucida console]sdc2[/FONT]. Format it as NTFS; and give the Partition Name and Label whichever names you want (e.g. Windows Extra Data).
[/LIST]

[*][Partition the partition]("https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessSetUpLVM#Partition_the_partition"): Replace [FONT=lucida console]--name=home[/FONT] with [FONT=lucida console]--name=**mydata**[/FONT] (use any name instead of "[FONT=lucida console]mydata[/FONT]", but please don't include spaces; you can use "[FONT=lucida console]home[/FONT]" but this might cause confusion later. Remember that capitalisation is important).
[*][Format the partitions]("https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessSetUpLVM#Format_the_partitions"): Replace:
[FONT=lucida console]sudo mkfs.ext4 -L home /dev/mapper/data-home[/FONT]
with
[FONT=lucida console]sudo mkfs.ext4 -L **mydata** /dev/mapper/data-**mydata**[/FONT]
[*][Select the remaining partitions]("https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessInstallUbuntu#Select_the_remaining_partitions"): skip the step to specify [FONT=lucida console]sdc1[/FONT] as [FONT=lucida console]/home[/FONT].
[*][Mount partitions]("https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessFixBrokenPieces#Mount_partitions"): Skip the part to mount [FONT=lucida console]/home[/FONT], i.e.:
[FONT=lucida console]sudo mount /dev/mapper/data-home /mnt/root/home[/FONT]
[*][Fix fstab]("https://help.ubuntu.com/community/ManualFullSystemEncryption/DetailedProcessFixBrokenPieces#Fix_fstab"): insert this extra line at the end of the file:
[*]```
/dev/mapper/data-mydata    /media/mydata    ext4    defaults    0    2
```
[LIST]
[*]The spacing between terms is unimportant; you can use extra or fewer spaces as you wish.
[*]Replace [FONT=lucida console]mydata[/FONT] with whatever name you chose earlier.
[*]This line will automatically mount your spare partition under the folder [FONT=lucida console]/media/mydata[/FONT], and in the file manager (Nautilus), it will be listed as "[FONT=lucida console]mydata[/FONT]".
[/LIST]
[/LIST]
Finish up and ensure that Ubuntu boots properly. Run all updates, reboot, and if necessary run through the [Troubleshooting guide]("https://help.ubuntu.com/community/ManualFullSystemEncryption/Troubleshooting#Computer_fails_to_boot_after_upgrade_or_new_installation").

**Install Windows**

[LIST]
[*]Ensure that you choose [FONT=lucida console]sdb[/FONT] ("Drive 1" in Windows's parlance) to install Windows, and leave sda and sdc alone.
[*]Once you have successfully installed Windows, run all updates.
[*]Restart your computer. You will notice that it goes straight into Windows without giving you the option to boot into Ubuntu.
[/LIST]
**Allow Ubuntu to boot**

Run through the [Troubleshooting guide]("https://help.ubuntu.com/community/ManualFullSystemEncryption/Troubleshooting#Computer_fails_to_boot_after_upgrade_or_new_installation") to restore Ubuntu's right to boot.

Finally, restore your data.

---

### Post by ranloe on 2017-05-02
Dear Paddy,
Just reporting to say that everything worked exactly as you said. I did run into one unforeseen problem though which was that I entered my password by changing the keyboard settings to azerty in the live USB during setup. However, after setup and the first reboot, there is no option to change the keyboard settings before having to enter the encryption passphrase. I tried everything again and this time set a qwerty friendly password. Then it worked. thank you soooo much for your help once again !

---

### Post by Paddy Landau on 2017-05-02
> **ranloe said:**
> … reporting to say that everything worked exactly as you said. … changing the keyboard settings to azerty in the live USB during setup.
I have only one keyboard — a UK keyboard — so that's all that I was able to test.

I'm glad that you figured it out.

The instructions include a [caveat about which characters are OK]("https://help.ubuntu.com/community/ManualFullSystemEncryption/Overview#Choosing_a_passphrase_and_password"), but I don't know how that works on non-QWERTY keyboards. Unfortunately, I don't know how to find out. Maybe I should post some sort of caveat about different keyboards. For example, how would a Hebrew, Mandarin or Russian keyboard work?

Hmm, I wonder where I could get testers?

---

