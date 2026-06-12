---
title: "Multipartition, multi-hard drive GRUB issue"
date: 2007-03-06
forum: Installation &amp; Upgrades
---

### Post by 8-bitDesigner on 2007-03-06
Okay, this one should be simple enough! I borked my system while trying to install Fiesty Herd 5, and managed to bugger up GRUB in the process. I've got three OSes on here, Windows, a borked Fiesty Fawn install, and a healthy Edgy install

I've got two harddrives (hda, hdb). hda has one partition with Windows XP on it, and GRUB stage  1 installed to its MBR. hdb has 6 partitions:

[LIST]
[*]hbd1 = Windows storage partition
[*]hdb2 = borked Fiesty install
[*]hdb3 = borked Fiesty swap partition
[*]hdb4 = (Extended partition:)
[*]hdb5 = Healthy Edgy Eft install
[*]hdb6 = Healthy Edgy Eft swap partition
[/LIST]

Now, it looks like the GRUB menu I'm receiving on boot is actually from the borked Fiesty install, and a quick "file /boot/grub/stage1" from the grub command line shows that it's reading a stage1 file from (hd1,1) and (hd1,4) which correspond to the Fiesty and Edgy installs respectively.

So, long story short, does anyone know how I'd tell grub to ignore (hd1,1) and just go straight to (hd1,4)?

I believe it's something along the lines of going into grub and typing:
grub> setup (hd0)

...but I'm a bit at a loss as to how I'd tell it to read the stage2 file from (hd1,4). Any ideas?

---

### Post by bhupeshrawal on 2007-03-06
try following:

grub>root (hd1,4)   <press return>

and then set kernel image path and root file system path.

You may require to set initrd too.


**example:**

grub>root (hd1,4)
grub>kernel /boot/vmlinuz-2.6.17-11-generic root=/dev/sdb3 ro single
grub>initrd /boot/initrd.img-2.6.17-11-generic

grub>boot


make sure you select right filesystem path for root :)

---

### Post by Herman on 2007-03-06
8-bitDesigner, 
I agree with bhupeshrawal, that is correct.

Here are some links for you with illustrations to show you what bhupeshrawal means exactly,  
Here is a picture of [Grub's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli")

This is how to boot any Linux OS with it,                                                               [How To Boot Linux from GRUB's CLI]("http://users.bigpond.net.au/hermanzone/p15.htm#How_To_Boot_Linux_from_GRUBs_CLI")

This is how to restore Grub from any grub shell,                                                        [Re-install Grub with a GRUB shell eg; with Live CD]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD")
Actually, if you want to take a shortcut, you can just re-install grub from the command line before you even boot an operating system, because the command line is a special type of grub shell.
Here is an example of that, [**Chainloader Boot**]("http://users.bigpond.net.au/hermanzone/p15.htm#Third_method_chainloader_boot"). However, you do not need to follow that exactly, where that shows how to install grub to a partition, you can modify that command a little to install grub to your MBR instead.

I hope I didn't confuse you with an excessive amount of information.

Regards, Herman :)

---

### Post by 8-bitDesigner on 2007-03-07
bhupeshrawal and Herman, major thanks, and I'm a good deal further down the line now. I managed to fix things up by doing:

grub> root(hd1,4)
grub> setup (hd0)

Now, this points grub back to my Ubuntu partition just fine, and I'm good to go after that. Herman, the information overload was well appreciated and the grub pages you pointed me to were perfect. :)

However, the more astute of you in the audience might be thinking, "But isn't that where your Windows bootloader lives?", and the answer is yes.

Oops.

So I overwrote the bootloader on my WinXP partition, and thankfully since anything of importance is stored on (hd1,0) I'm doing peachy keen. However, on the off chance that I *do* want to boot back into Windows at any point, does anyone have any idea on how exactly I'd repair the WinXP boot loader, and how exactly Grub should be installed then?

Cheers

---

### Post by Herman on 2007-03-07
```
 grub> setup (hd0)
```> However, the more astute of you in the audience might be thinking, "But isn't that where your Windows bootloader lives?", and the answer is yes. No, 
you are _not_ correct. 
(hd0) refers to the MBR, or Master Boot Record of the hard disk. Each hard disk has a Master Boot Record, which is in the first sector of the hard disk.

WIndows bootloader does not live in the Master Boot Record at all, because the Master Boot Record is only one sector or 512 bytes. There can be code for a bootloader in the first 446 bytes, and then room needs to be reserved for the partition table, which consists of four, sixteen byte entries. (one for each of the four primary partitions). At last there is the two byte aa55 signature, which tells the BIOS that this is a bootable device.

The code for the bootloader which is written in the first 446 bytres of the MBR, is very small and roughly speaking, it only severs as a 'pointer', to point to a bootloader in a filesystem (partition).

The rest of the first track of the hard disk is empty, one track is 63 sectors. Windows filesystem begins with the Windows bootsector and if Windows happens to be located in the first physical partition on the disk, then normally that will be sector 63. You can prove that by running 'sudo fdisk -lu' in a terminal and examining the output. The Windows bootloader files are inside the Windows filesystem, the main ones are NTLDR, NTdetect, and boot.ini.
If you open your hda1 icon you can take a look right now at the root of your Windows filesystem and verify that those files are stil, in fact, untouched, and so is Windows bootsector. [**            A Birds's eye view of Windows XP **(showing the bootloaderfiles)]("http://users.bigpond.net.au/hermanzone/p6.htm#A_Birdss_eye_view_of_Windows_XP")

This command will show you what your Master Boot Record looks like, This has the stage1 code for the Grub bootloader written to it now, in the first 446 bytes. ```
sudo dd if=/dev/hda count=1 | hexdump -C
```And this command will show you what your WIndows bootsector looks like, this has code for the Windows bootloader, doesn't it?  ```
sudo dd if=/dev/hda1 count=1 | hexdump -C
```When the MBR points to Grub's stage2 files in the Ubuntu partition, when you select Windows from your Grub menu, Grub 'chainloads' Windows by the Windows bootsector.

If you want, you can write Windows bootloader's stage1 code to MBR again, and overwrite grub's stage1. There are many ways of doing this but the most popular way is to run A Windows  [recovery console]("http://www.kellys-korner-xp.com/win_xp_rec.htm") and apply the FIXMBR command. Don't worry if you don't have the right klind of Windows CD, you can also rewrite the Windows bootloader's stage1 code to MBR with many other utilities. See this link, [Un-install Page]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

The MBR is made of the same material as the rest of the hard disk, and it can have grub's stage1 restored again afterwards, and you can change it as many times as you like, it will never wear out. I know because I do a lot of testing of all kinds of bootloaders, grub, GAG, LiLo, Windows, Grub for Windows, you name it and I've written it to MBR many times and then overwritten it with something else. My MBRs are all still okay.

Windows does not own the MBR, they have never purchased any of my MBRs. I buy hard disks new and install any operating systems to them I like, but regardless of what system I have installed at any time, I regard the MBR as mine, because I paid for the hard disk. Any bootloader I choose may have its first stage written to one of my MBRs, but only for as long as I want it to be there.
> So I overwrote the bootloader on my WinXP partition, and thankfully since anything of importance is stored on (hd1,0) I'm doing peachy keen. However, on the off chance that I *do* want to boot back into Windows at any point, does anyone have any idea on how exactly I'd repair the WinXP boot loader.Well if you overwrote the code in your Windows XP partition, which is designated (hd0,1) usually, that is a different matter. Grub is not supposed to be installed to the Windows bootsector. You can fix that in several ways, but the most popular is again, to use a Windows [recovery console]("http://www.kellys-korner-xp.com/win_xp_rec.htm") but this time you use the FIXBOOT command.
If the Windows filessytem is FAT32, you can also easily replace the Windows bootsector with its backup with a linux command if you can;t get a recovery console for some reason.
(hd1,0) is the first partition of hard disk number 2, so you are saying that you have a data partition there eh? Okay, that;s fine. 
> and how exactly Grub should be installed then?Most of us install Grub to MBR, or (hd0). ```
setup (hd0)
```Meaning, we install the stage1 code of grub to the first 446 bytes fo the MBR. This is just to make the MBR point to the Ubuntu filesystem where the grub bootloader really lives. 

So now I hope you know the difference between a MBR and a bootsector, and how to restore the bootloader's code to either one. I hope that helps you, please let me know if there is anything else you want. :) 
Did I understand your question right?
Could there perhaps be some other reason why you are unable to boot into Windows that we need to investigate? Have you a line in your Grub menu that allows you to select Windows and try to boot it?

Regards, Herman   :)

---

### Post by 8-bitDesigner on 2007-03-07
You know, I've been working with these things for years, and I've never quite understood the difference between a bootloader and a boot record, apparently! So, the problem, a little more precisely, is that when I select "Windows XP" from the grub boot menu, Grub goes to load the OS, and then drops me back down into the menu. 

Additionally, in Linux, the disc won't mount, whereas hdb1 (another NTFS disc) mounts perfectly. 

To recap, I installed grub by doing:
grub> setup (hd0)

Now, I think I've at least found the problem, and in that this appears in dmesg when I try to mount hda1:

[34500.227513] NTFS-fs warning (device hda1): is_boot_sector_ntfs(): Invalid boot sector checksum.
[34500.227527] NTFS-fs error (device hda1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[34500.227537] NTFS-fs error (device hda1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[34500.227546] NTFS-fs error (device hda1): ntfs_fill_super(): Not an NTFS volume.

So, it looks like running FIXBOOT from a handy dandy WinXP install CD might just do the trick. I'll give this a shot when I get back home, and keep everyone posted.

Thanks for the help!

---

### Post by Herman on 2007-03-07
Hello 8-bitDesigner,
Okay, I can see now from the new information that you have indeed, (or someone has) installed grub to (hd0,1) in your computer. Grub's stage1 is installed in your Windows bootsector, which is not useful for booting Windows.

That is a problem, but it can easily be corrected with your Windows Xp install CD and running FIXBOOT in [recovery console]("http://www.kellys-korner-xp.com/win_xp_rec.htm"), that is correct.

You can "install grub to MBR", (hd0) or to the first sector of any Linux partition (hdx,y), but it is generally not a good idea to install grub to (hd0,1), which is commonly the first sector of Windows.
Even when preparing to install grub to a Linux partition, we always check to make sure which partitions are which, because it is possible to install Windows in a non-first partition. That's not common, and normally the owner of the computer is aware of that if that's the case. However, that's why the procedure for installing grub from a grub shell begins with the test command 'find /grub/boot/stage1'. That is a test to confirm which partitions contain grub already and therefore are Linux partitions, and are okay to install grub to.

Just run the FIXBOOT command and your computer, (Windows), will be fine.

Regards, Herman :)

---

### Post by 8-bitDesigner on 2007-03-08
Well, a quick FIXBOOT via the XP recovery console seemed to do the trick just right! Oddly enough, I'm good to go again without having to re-setup Grub, so I'm now booting all OSes properly!

Thanks for all the help, Herman!

---

### Post by Herman on 2007-03-08
You are welcome 8-bitDesigner, and thanks for the good feedback too, good luck with all you do.
Regards, Herman :)

---

