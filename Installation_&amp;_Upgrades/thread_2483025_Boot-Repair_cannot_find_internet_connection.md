---
title: "Boot-Repair cannot find internet connection"
date: 2023-01-18
forum: Installation &amp; Upgrades
---

### Post by luigiwriter2 on 2023-01-18
Dual boot install on brand new tower which came with win11 installed.
Used Gparted to partition for adding Ubuntu Studio.
Install of Ubuntu Studio ended with an error "No EFI system found"
some advice was to create a second boot partition, which I did.
Super Grub2 confused more than helped.
Have tried a boot-repair-disk-64bit ISO USB boot drive using Ventoy
Then Burned boot-repair-disk-64bit to USB boot drive using Rufus 3.21
Both Ventoy and Rufus are the latest downloads as is boot-repair.

Whether the ISO or the burned version after loading boot-repair-disk-64bit it kept asking for me to enable the internet connection.

When I did so the pop up informed me it was enabled and had been used less than 2 minutes before.
When I try to upload the [Boot-Info]("https://help.ubuntu.com/community/Boot-Info") diagnosis reports to the Pastebin site, again I am requested to enable the internet connection.
My internet connection is via Ethernet and I am having no trouble with Win11 connecting as I write this.
I want to upload the two files boot-repair created, but the folders I tried saving them to remain empty and Win11 is not recognizing the boot drive which may be where the file exist.
This has been a long road and tiring. I hope someone has some idea why I am getting simultaneous no internet and yes internet conflicting messages from both the ISO and the burned version.

I will do any procedures  and provide any information requested. I am really hung up until I can boot Ubuntu and reinstall all the apps I use on it.  I only need windows to run two apps that do not run in VBox and WINE or at least did not on my obsolete laptop.

I hope what I have given is useful. please ask for clarification where I have not.
Thank you.

---

### Post by yancek on 2023-01-18
The error you reported "No EFI system found" seems odd to me as windows 11 should certainly be an EFI install.  Can you boot the USB you used to install Ubuntu and run the following command from a terminal:

>  sudo parted -l

Does it show an entry for EFI system partition?  It should and you should boot the Ubuntu install USB from the EFI option in the BIOS firmware boot options.  Also, you do not 'need' a separate boot partition.  Are you installing Ubuntu on the same device as windows 11 and is it connected to the computer during the install?

I don't understand what win 11 has to do with it.  If you are using the boot repair iso, the files would be on the USB drive or rather in memory and if you reboot, they are lost.  These are read-only filesystems.  I would suggest that you use the Ubuntu install USB and go to the boot rep;air site and use the 2nd option described there as that is more current than the iso download.  If you still have problems with the internet, you will need to post more information on the network device.

---

### Post by oldfred on 2023-01-18
Does Windows 11 have bitlocker on and/or fast start up which is hibernation.
Either of those can make it difficult or impossible to see the NTFS partitions and ESP?

Always resize NTFS with Windows tools and reboot as it has to run chkdsk to repair the NTFS partition settings for new size. 

What version of Ubuntu is Ubuntu Studio?

---

### Post by luigiwriter2 on 2023-01-28
Thank you. Your question was right on the ball. In answering I brought up the windows disk management screen the same I used to shrink windows. I found my error there in that the extra empty boot partition I was told I might need was the one set as EFI. 

[LIST]
[*]I did not realize that I guess there can "Only Be One" EFI and had inadvertently removed the EFI designation from the first partition. 
[*]Windows did not give an option to change it, so loaded Gparted and removed all flags from the empty partition beyond the Windows partitions making sure the first now held the EFI moniker. 
[*]Ran Boot-repair again. Looked at the advanced options, ran the boot info summary and from it decided to run Recommended Repair. 
[*]On the next boot, Ubuntu showed up in the UFEI BIOS. Set it first, and Bingo, there was grub. 
[/LIST]
 I am writing this while in installed Ubuntu Studio.
  
All thanks to your suggestion to look at the partitioning again!!=d>

I need to find the way of declaring this Solved since I am not seeing a button or menu for doing so.:confused:

---

### Post by luigiwriter2 on 2023-01-28
Yes made sure that Bitlocker was off. Also Fast start off. Did windows disk manager to to resize its partition. with out touching the EFI partition. It was when I was "gparting" in the Ubuntu installation or more likely later when I was reading possible solutions, one being perhaps needing a second EFI partition with some windows installs. More detail above on that.  
Studio is 22.04 BTW.
Your suggestions helped me narrow down things. Thanks

---

