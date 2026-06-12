---
title: "GUIDE: (U)EFI installation"
date: 2012-04-14
forum: Installation &amp; Upgrades
---

### Post by niglas on 2012-04-14
BACKGROUND[INDENT]EFI is a replacement of the older BIOS. If your motherboard supports EFI, this is how you use it.
I have read a bunch of different guides/howtos, but i thought none of them were easy enough, or they where outdated. Here comes my version...
[/INDENT]INSTRUCTIONS[INDENT]EFI uses a whole partition (ESP=EFI System Partition) instead of the first 512B at the first sector as MBR does. A partition has to be reserved for that (see below).
First you need a EFI bootable device with your favorite distro on. Use a USB memory, because most (?) CD/DVD readers does not seem to boot the OS into EFI mode, and will therefore not be able to automatically install EFI.


[LIST]
[*]Create a bootable USB live "CD".
[LIST]
[*][usb-creator-gtk]("https://launchpad.net/usb-creator/") in linux
[*][unetbootin]("http://unetbootin.sourceforge.net/") in win
[/LIST]
 
[*]Boot into the live CD (USB).
[*]Format the disk with a GPT partition table with for example *gparted* [screenshot 1].
[FONT=Courier New](Device -> Create Partition Table... -> GPT)[/FONT]
[*]Start installation, create the desired partitions and make one of them the ESP [screenshot 2-3].
(The EFI partition choice will not appear unless the live CD is booted into EFI mode.)
The ESP does not necessarily have to be the first one in the partition table.
I choose a 16MB ESP as the last partition in the table.
[*]In the UEFI BIOS settings make sure all EFI bootable devices are ahead of the MBR devices in the boot order [screenshot 4].
(Otherwise the empty DVD reader can rule out the EFI compatible hd, that you've put after the DVD in the boot order and the boot will stall.)
[/LIST]
[/INDENT]NOTES[INDENT]
[LIST]
[*]If you want to be able to dualboot with MS Win, then the ESP has to be FAT32. Most linux distros choose FAT16 as default (but handles FAT32), you can either preformat the ESP with FAT32 or covert it to FAT32 later on.
[*]Be sure to download the 64-bit version of the OS if you have a 64-bit CPU, otherwise it won't boot using EFI.
[/LIST]
[/INDENT]SCREENSHOTS

[LIST=1]
[*]    [IMG]http://i.imgur.com/Y9wEi.png[/IMG]
[*]    [IMG]http://i.imgur.com/0HHnY.png?2[/IMG]
[*]    [IMG]http://i.imgur.com/Fslg3.png[/IMG]
[*]    [IMG]http://i.imgur.com/2mmM5.png[/IMG]
[/LIST]

---

### Post by pulpo69 on 2012-04-15
hi niglas,

thank you for your efi-guide, it's very well done.
I'll try to make an ubuntu-efi-install alongside with windows depending on your guide)when 12.04 is finally out.
Please keep on with your fine guide.
I believe for a lot of people it will be helpful.

---

### Post by vasa1 on 2012-04-15
> **pulpo69 said:**
> hi niglas,

thank you for your efi-guide, it's very well done.
I'll try to make an ubuntu-efi-install alongside with windows depending on your guide)when 12.04 is finally out.
Please keep on with your fine guide.
I believe for a lot of people it will be helpful.
**A big +1**.
There's virtually no easily understandable how-to for installing Ubuntu (as a dual boot) onto a UEFI PC that already has Windows installed.

---

### Post by kolinab on 2012-04-15
Thank you for this guide. On my UEFI capable system, I set up a dual boot by first disabling UEFI in the BIOS and selecting 'legacy' mode instead. When I upgrade to 12.04, I might try to do a UEFI installation.

Are there any clear advantages to a UEFI boot over the legacy mode?

---

### Post by niglas on 2012-04-15
Some of the advantages:

[LIST]
[*]Faster boot time
[*]Support for boot disks >2TB
[*]Improved graphics
[*]IPv6 support
[/LIST]

---

### Post by pulpo69 on 2012-04-15
> **vasa1 said:**
> **A big +1**.
There's virtually no easily understandable how-to for installing Ubuntu (as a dual boot) onto a UEFI PC that already has Windows installed.

I agree. And more and more efi-boards are on the market.

---

### Post by Yahoé on 2012-04-15
Hi niglas,

Thanks for the explanation. I'm trying to follow your steps but using Gparted 0.12.1 (the latest) I'm not offered the "EFI start partition" option as an available format as you have in screenshot 2. Any idea why?

Regards,

---

### Post by oldfred on 2012-04-15
You format to FAT32 although the Ubuntu installer uses FAT16 which is allowed but really for older external devices like floppy disks not hard drives.

Then in gparted you set boot flag.

In GPT fdisk, ESPs have a type code of EF00. In libparted-based tools, you mark the ESP as such by setting its "boot flag." Note that the libparted "boot flag" means something entirely different under MBR, and you should not set the "boot flag" on any OS partition under GPT!

Use can use gdisk to see type codes.

Although niglas was able to put efi partition anywhere on his drive, the specification says it should be the first partition. It may have to do with it being FAT32 and the software will not read beyond a certain point on the hard drive and it is easier just to specify it to be first and not very large (~100 to -256MiB, FAT32). I would not try to put it at the end of a 1 or 2TB drive and expect it to work.

---

### Post by niglas on 2012-04-15
> **Yahoé said:**
> I'm not offered the "EFI start partition" option as an available format as you have in screenshot 2. Any idea why?

It all depends on if the live CD (USB) is booted in UEFI mode. Check in UEFI  BIOS boot prio if the (blue) flag "UEFI" is detected [screenshot 4] on the USB memory, otherwise you'll not be offered the "EFI start partition".

If not there try with a  newer version of the OS or another USB memory.

The only thing you need to do in gparted is to set the partition table type to GPT. The partitioning can be done during the installation and when you choose one of the partitions as "EFI start partition" the GPT boot flag will automatically be added. (Choose *configure partiton table manually* during the installation.)

Good luck Yahoé! :)

---

### Post by Yahoé on 2012-04-15
Thanks guys.

Right now on a brand new Lenovo G770, after install (all new partitioning as I would usually do), on reboot the laptop stays mostly completely dead, just the power light is on, no display, so no access to the bios
Very odd. I can't believe that installing 12.04 would just result in a non-functioning PC just because of UEFI. Thousands of newbies, or even more experimented users that did not expect the issue will be left stranded...

---

### Post by medic2000 on 2012-04-16
Hi niglas, i just need an confirmation. Is this a guide for a GPT UEFI system with a dual-boot Linux + Windows 7 installation?:

[https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB](https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB)

Are you configuring everything in the USB thumb and when you are installing you are not doing any more configuration if you use that guide?

Is it like that?

---

### Post by Yahoé on 2012-04-16
Hi had a bit of a battery problem that I fixed. Now back to trying to install on a GPT HD.
I have a brand new Lenovo G770 with a InsydeH2O bios V3.08 which is UEFI.
When booting from the latest 12.04 daily live (USB), Gparted doesn't  offer me to format the ESP as a EFI start partition (fat32 with the boot  flag), which would mean that I'm not booting into EFI mode. This kind  of Bios doesn't offer any option even mentioning UEFI.
I'll try to move along with the installation process and shall post the results.

---

### Post by jruden on 2012-04-17
> **niglas said:**
> It all depends on if the live CD (USB) is booted in UEFI mode. Check in UEFI  BIOS boot prio if the (blue) flag "UEFI" is detected [screenshot 4] on the USB memory, otherwise you'll not be offered the "EFI start partition".
I use a 16gb Sandisk USB stick to install from. It is detected in Asus EFI BIOS which displays two devices for my USB stick ("Sandisk" and "UEFI Sandisk").

The problem for me is that it never boots if I choose the UEFI version.

I built my stick in win using "Universal USB Installer" as mentioned on the Ubuntu home page.

Question: Does unetbootin do something special to the USB stick to allow it to be booted as UEFI?

Question: Which Ubuntu version did you succeed installing with this? I am trying 32bit 12.04...

EDIT: Question: Did you use some special version of unetbootin?

---

### Post by oldfred on 2012-04-17
If you look at ISO/CD/Flash you will see this:
/efi/BOOT/bootx64.efi

That is the file the UEFI menu on your system should find to boot in UEFI mode.

But when installed on a hard drive it is 
/boot/efi/EFI/BOOT/bootx64.efi

Some UEFI system may only look in one place? It is known that the UEFI implementations are not all the same as the standard is not totally clear or allow some interpretation.

---

### Post by jruden on 2012-04-17
I have checked now and i386 version of 12.04 does not even contain an /efi folder on the ISO. Thus it seems(?) amd64 is the way to go. So I downloaded that and "burned" it to the USB with unetbootin.

Yay! It does start when I boot the stick with UEFI! And Yay #2 it does allow me to set type EFI on a partition.

After installation though, it behaves oddly. Sometimes it does not start. Sometimes it comes to a grub menu, but I get errors when I choose ubuntu, memtest or my windows7 (which is on a completely different drive).

Will try with daily build and see if that works better...

---

### Post by Yahoé on 2012-04-17
Installation completed on the  the Lenovo G770 with InsydeH2O Bios. It was successful.
Here are the steps I followed:
The drive partition table is GPT. I created a fat32 partition in first position and set the flag to boot (partition type is EFI, checked with gdisk type ef00). Then an ext4 / , an ext4 /home and a swap. 
The installer warned me that with this partition table format in use I should normally have a separate partition for the boot loader code, also it nay still be possible to install the boot loader to a partition. I ignored that,  did not create one and went one the installation process.
It completed nicely.  I then installed grub-efi-amd64 and all is working perfectly on this laptop, the system now works just fine.

---

### Post by jruden on 2012-04-18
The following came with updates today on my other computer (already running 12.04)...maybe they are improving my chances(?) 
[IMG]https://lh3.googleusercontent.com/-pHRn1kWgvaY/T46nYbsXClI/AAAAAAAACX4/z_ikqnIni40/s400/IMAGE_1E854E86-938C-459B-9BEA-23B5C8DCEFD4.JPG[/IMG]

---

### Post by kolinab on 2012-04-18
Thanks for this guide! UEFI install today went almost perfectly - with one small hiccup.

When specifying the size of the EFI partition, I selected 16MB, as the OP suggested. Due (I think) to the block sizes on my HD, this was automatically rounded to something like 15.7MB. The partitioner halted and gave me an error that it could not create the EFI partition. I think 16MB is the minimum size for this type of partition and the partitioner fails if you make it too small.

When I increased the size to around 20MB or so everything went perfectly.

---

### Post by apprayo on 2012-04-19
Thanks Niglas..
This thread really saved me and my team..

---

### Post by niglas on 2012-04-23
> **medic2000 said:**
> Hi niglas, i just need an confirmation. Is this a guide for a GPT UEFI system with a dual-boot Linux + Windows 7 installation?:

[https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB](https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB)


I have not had any reason of messing with Microsofts OS yet, but if I will some day, I will post it here. But my general experience says install Windows first, then Linux, 'cause Microsoft tend to do all kinds of funky stuff to your system...

> **medic2000 said:**
> 
Are you configuring everything in the USB thumb and when you are  installing you are not doing any more configuration if you use that  guide?

Is it like that?

Nothing tweaked with the USB memory, just use *usb-creator-gtk* or *unetbootin* as the guide says, and it will all be set up for you. Remember to download the correct version of the system thou, 64-bit if you have a 64-bit processor.

---

### Post by niglas on 2012-04-23
Good to hear that it worked out for you jruden. The essence of installing the matching OS with the system arcitecture appears to be even more clear here, thanks!

I'm happy it worked out for you too guys kolinab & apprayo.

---

### Post by SuperFreak on 2012-04-28
Hi,

I am building a computer with an Asrock Motherboard ( Z77 Extreme4-M) and intel 520 SSD for root and home  and Regular 2 TB Hard Drive for data. Reading your previous post niglas, it appears I don't have to do much more than set partition table to GPT in GParted, the installation USB does the rest.

> The only thing you need to do in gparted is to set the partition table type to GPT. The partitioning can be done during the installation and when you choose one of the partitions as "EFI start partition" the GPT boot flag will automatically be added. (Choose configure partiton table manually during the installation.)



My question is, do I set both the SSD and the mechanical HD as GPT in GParted?

---

### Post by niglas on 2012-04-28
The GPT partition table is only critical for the boot partition, in other words you can choose what ever partition table you'd like for the other disk.

---

### Post by Lancro on 2012-04-28
Hi, I have EFI on my computer, and ubuntu installer doesnt detects my windows 7 installation, so I cant continue, I have looked your guide, and I dont know if its my bad english or my lack of experience but I dont understand it... Is there any chance of installing ubuntu alongside windows from the installer, wich is the simplest way?.

Thanks.

---

### Post by oldfred on 2012-04-28
@Lancro
Just because you have UEFI, you may still be in BIOS mode. Most Windows installs are BIOS/MBR and then you are into the 4 partition limit or other issues.

May be best to start your own thread and post the Boot info

 Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or Create BootInfo report & post the link to a run of boot info script so we can see your exact configuration.

---

### Post by SuperFreak on 2012-04-28
> **niglas said:**
> The GPT partition table is only critical for the boot partition, in other words you can choose what ever partition table you'd like for the other disk.

Just so I am clear on this, I would boot into the live usb of 12.04 and set up EFI, Root and Home partitions on the SSD using GPT as the format type? I am afraid I am a novice at this and your instructions seem to be the best available, but I still need a little clarification. Am I correct that setting up GPT as the partition table is the same as formating the partitions?

edit: I see by looking at your screenshots that it is only one partition EFI that gets formated GPT. It was a little confusing because the screenshots were in a foreign language to English

When I start to install Ubuntu that boot partition will be recognized by the install program and automatically fill the partition?

---

### Post by oldfred on 2012-04-28
gpt is the partitioning scheme instead of the default ancient MBR(msdos). I just use gparted or you can use gdisk if you like command line, sometimes good to have anyway.

I have BIOS but use gpt. I have created my gpt partitions with gparted. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning. My partitioning shows a bios_grub but if just UEFI you do not need that.

gdisk is in the repository so you can easily download it
GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

Some useful links:
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

---

### Post by SuperFreak on 2012-04-28
Much clearer. Thanks to both of you OldFred and niglas

---

### Post by SuperFreak on 2012-05-02
OK,

I set partition table to GPT and clicked apply. Nothing happened and it said 0 operations pending. Forgive my ignorance but the disk is unallocated does it have to be formatted to FAT 16 first for the GPT to take effect?

---

### Post by oldfred on 2012-05-02
gpt or MBR(msdos) are just the type of partitioning used. You still should create partitions in advance.

Some have only gotten efi to work by first installing in BIOS mode, so I usually suggest both efi & bios_grub partition. Let grub decide, but if you boot USB in UEFI mode it should install in UEFI mode. If also installing Windows you need to review what partitions they may want.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
If gpt(not MBR) partitioning include these first - all partitions with gpt are primary
    250 MB efi FAT32
    1 MB bios_grub  no format 
Ubuntu partitions - smaller root only where hard drive space is limited
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

I like to leave some unallocated, so you can add test installs or experiment with other systems. I also have separate data partitions.

---

### Post by SuperFreak on 2012-05-02
Thank you Fred,

One difficulty is I can't seem to make Root or Home logical partitions as the choice is greyed out. The partition are still pending I haven't set them yet but I have followed more or less your scheme with 250 MB Fat 32 EFI, 1 MB unformatted,48.83 GB Root EXT4 (I install a lot of programs), 39 GB Home EXT4 and 23.65 unallocated. Presently all partitions pending are marked Primary-do I change that after I apply the settings? And do I then create a partition table in GPT for all partitions?
Oh and I have 16 GB of RAM so I have not created a SWAP partition but it is not too late

edit-Is it necessary to set any flags?

---

### Post by oldfred on 2012-05-02
efi needs boot flag, bios_grub unformated need bios_grub flag.

In gdisk the gpt code for efi is ef00 and for bios_grub is ef02.

One advantage of gpt is that all 128 (or more) partitions are primary, so no logical partitions.

Some swap is recommended. If you really want to hibernate you would need 16GiB or 17 or 18 in GB. Only if editing many videos or some other massive task will you every use that much memory. I find with 4GB of RAM I never use swap. Supposedly it boots a tad faster with some swap as it goes and looks for it and has to time out if not found. I normally would suggest 2GB of swap.

---

### Post by SuperFreak on 2012-05-03
I am going to reduce my ROOT down to 30-35 GB and add the 2 GB SWAP as you suggested.

I have read a number of good articles (ie[https://wiki.archlinux.org/index.php/Solid_State_Drives#Intelligent_Partition_Scheme]("https://wiki.archlinux.org/index.php/Solid_State_Drives#Intelligent_Partition_Scheme")) and [http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/]("http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/") about optimizing the SSD after install and I will follow up on that. One thing that is not mentioned is whether email (ie Thunderbird in my case) should be on the SSD or not as it is rewritten daily. Would it make sense to put the Thunderbird folder which is normally in HOME on the mechanical drive and put a symlink to it on the SSD?

---

### Post by oldfred on 2012-05-03
I have both Thunderbird & Firefox profiles in my NTFS shared data partition which is a rotating drive. That is from when I used it with XP also, but I did not sym-link them but used the profile.ini to show the new location. I also move a few other hidden folders that are data to my ext3 data partition, but for example, kmymoney lets me just save to my linked folder and remembers that location.

[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

My /home on the SSD is really just the hidden user settings and very little data. I move data to my data partition on my rotating drive as soon as it starts to consume any space. The only thing I have not moved (yet?) is .wine. I understand that is a bit more difficult than just a sym-link,

---

### Post by SuperFreak on 2012-05-03
Moving the Profile is a much better way than symlinks. Thanks for your suggestion

---

### Post by SuperFreak on 2012-05-03
OK, I have created all the partitions and set the two flags and have 33 GB unallocated space. Do I now set each and every partition(including the unformatted partition) except unallocated space as GPT as per the earlier instructions?
Thanks for your help by the way I am finding this much harder than building the computer itself.

edit: I tried to set the Boot partition to GPT in Gparted (Live USB) and it deleted all the partitions. I am back to unallocated space for the entire drive again. I get the feeling that I am suposed to set GPT right from the start before making the partitions but it doesn't seem to work

---

### Post by oldfred on 2012-05-03
The very first thing you choose is the partitioning scheme or MBR(msdos) or gpt(GUID). That is not a partition but the type of partitioning table/records/system used to keep track of partitions on the drive.

Then you create partitions. With gpt you need a few extra partitions but since they all are primary it is easier.

[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

---

### Post by SuperFreak on 2012-05-03
I had tried setting the partition scheme first before but it didn't work for some reason. However I set it again and this time it seems to have worked (see screenshot) . I just have to set the flags now. Do I have to do anything else to make the Efi partition work?

---

### Post by oldfred on 2012-05-03
Use the screenshot app in Ubuntu and use the paperclip icon to upload.

I do not see the flags, and to install in UEFI, you have to boot LiveCD or USB in UEFI mode from the UEFI menu. If you boot from BIOS then it is in old standard BIOS mode.

I do not have efi but created the partition as I may move SSD to new system, I hope to get soon.

---

### Post by SuperFreak on 2012-05-03
OldFred I appreciate your patience with my fumblings. I have attached a screenshot and Flags are set. Am I ready to install now; Anything I need to know other than to make sure I am in UEFI mode not BIOS mode?


I notice that about a GB is marked as used in Home and ROT but I haven't installed anything, is that normal?


I think I must be in EFI mode as when I boot up and press DEL to go into BIOS it goes into a graphical interface with mouse control

---

### Post by oldfred on 2012-05-03
When you partition with ext4, it has a journal which helps with file recovery. But journal takes space. Also Ubuntu typically reserves 5% that you do not really see unless you start calculating sizes, so system will not run out of space and crash.

What I have not seen anyone post is how to add nomodeset for nVidia or other video issues with UEFI. With BIOS it is hit any key, then f6 and choose.

Someone posted this, but each vendor's UEFI may be different, I think it is after an install to add grub to the UEFI menu, if it did not install correctly:

> Enter your UEFI menu, select "Boot maintenance manager", then "Boot options", then "Add boot option", then "NO VOLUME LABEL,....Primary,Slave...1, GPT,..", then browse the /EFI/ubuntu/ folder via the UEFI boot menu, and select the grubx64.efi . Give it the name you want (eg "Precise"), then "Commit Changes and exit", then Enter. 
 

---

### Post by Bartender on 2012-05-03
Man, this sucks.  I finally had old-school BIOS figgered out, and now I gotta start all over again?

If [this]("https://help.ubuntu.com/community/UEFIBooting") is the best that Ubuntu Docs has to offer, we're in trouble.  

Well, I'm in trouble anyway.  :(

---

### Post by SuperFreak on 2012-05-03
> Enter your UEFI menu, select "Boot maintenance manager", then "Boot options", then "Add boot option", then "NO VOLUME LABEL,....Primary,Slave...1, GPT,..", then browse the /EFI/ubuntu/ folder via the UEFI boot menu, and select the grubx64.efi . Give it the name you want (eg "Precise"), then "Commit Changes and exit", then Enter. 

Not seeing these options in my boot menu. It gives me the option of booting to either USB 2.0 Corsair or USB 2.0 UEFI Corsair so I have set the latter and I will try installing now.

---

### Post by SuperFreak on 2012-05-03
OK started install it is asking me for device for bootloader install, Am I correct this would be the 250 MB partion in FAT 32?

or is it the 1 mb Bios_Grub partition?

Or do I want the ROOT partition?

Seemed a lot easier when I installed 10.10

---

### Post by oldfred on 2012-05-03
With UEFI, it has to be the efi partition. 

It was the old BIOS installs that you chose the MBR of the drive. 

You should not really be using the bios_grub, it is more a just in case as it is only 1MB, so having it does not really cost any space.

---

### Post by SuperFreak on 2012-05-03
Thanks, I will try the install tomorrow morning

---

### Post by SuperFreak on 2012-05-04
The reason I had asked you about the choice of bootloader is that when I choose the 250MB partition I get an error and can't proceed. See screenshot

---

### Post by oldfred on 2012-05-04
That is not the boot loader but the system.

Even though you partitioned in advance & you know which partition is which the installer does not. You have to choose the partition you want for / (root), and what format you want ext4 (or ext3). First time you also choose swap, and if separate partition for  /home and its format. If a reinstall when you choose /home you DO NOT format it.

Then the combo box below specifies where to install the grub2 bootloader. That is designed for BIOS/MBR and I am not sure what it does for UEFI, try the efi partition. gpt partitions have a protective MBR and if grub2's boot loader is installed to it, it will not cause any issue but then grub probably will not boot in efi mode, but may in BIOS? and then you can fix the UEFI boot if necessary.

---

### Post by SuperFreak on 2012-05-04
Thanks so much for guiding me. I have Ubuntu installed and I checked Gparted and it seems in order. I skipped grub2bootloader .

---

### Post by oldfred on 2012-05-04
@   	SuperFreak

Is it working? If so document what you did, so others that look at this thread can also learn.

---

### Post by SuperFreak on 2012-05-04
I am running 12.04 now with only one issue. Should I start a separate thread to describe how I got to this point or add it here? I am afraid any screenshots are lost unless there is a way of retrieving them off of previous posts.
I started a new thread with my present issue which is here [http://ubuntuforums.org/showthread.php?p=11905630#post11905630]("http://ubuntuforums.org/showthread.php?p=11905630#post11905630")

---

### Post by SuperFreak on 2012-05-04
Here are the Steps I took which have worked. They are similar to the original poster's. You will find screenshots on previous entries I made in this thread.
1. Downloaded 12.04 ISO from Ubuntu
2. Created bootable USB key using Ubuntu [http://www.ubuntu.com/download/help/try-ubuntu-before-you-install](http://www.ubuntu.com/download/help/try-ubuntu-before-you-install)
3. Using USB key I booted my computer into Ubuntu Live and selected try Ubuntu
4. Selected GParted from Dash and opened it
5. Clicked on my SSD drive which was shown as unallocated Space
6. Created 5 partitions and one allocated space as so
   a) First I formatted the drive to GPT
          (Device -> Create Partition Table... -> GPT)
   b) Right clicked on Unallocated space and chose "new"Then I created a 250 MB FAT 32 partition and labelled it EFI
   c) I created a 1 MB partition that I left unformatted
   d) I created and lableled / and HOME partitions and formatted them EXT 4 (32 GB and 40 GB) and labelled them
   e) I created a 2 GB SWAP and Formatted it LINUX-SWAP
   f) right clicked on EFI (and 1 MB) partitions and chose Manage Flags for each. I chose boot flag for EFI and bios_grub flag for the 1 MB unformatted partition.
7. I rebooted the computer and went into UEFI and set the boot priority to USB 2.0 UEFI as the second choice after the hard drive and exited and saved.
8. I then started my install. I chose to install manually -I think it is called "Or Something Else" .Most of the rest is fairly straight forward but I got hung up at the partition table. You have to set the root partition and home partition up. double click on each of these and it will give the option to select / for ROOT from the drop down list or /Home for each. These should be set as EXT 4 partitions.
9. Before preceeding choose the bootloader on the bottom of that window to your EFI partition.
10. Also I didn't mention this but on an earlier install screen the option to download updates and install 3rd party software is given. I checked these

I have to admit that without OldFRed's and Niglas's help I would have been lost

---

### Post by YannBuntu on 2012-05-04
**@SuperFreak:** good job, and thanks for the summary! Please could you also indicate your [BootInfo URL]("http://ubuntuforums.org/showpost.php?p=11136267&postcount=1"), so that we get a detailed view of your current situation ?

---

### Post by SuperFreak on 2012-05-04
I can't post it now as I am doing data transfers to the new computer but will later

---

### Post by tamashumi on 2012-05-06
Hi Guys!

I've been trying to install 12.04 x64 in UEFI mode on a GPT drive. 

Problem is I cannot boot Ubuntu USB stick with UEFI. No matter the stick created with *Startup Disk Creator* nor simply iso extracted (the creator's one works fine when booted in BIOS mode).

My problem is the exact same as described [in this thread, post 8]("http://ubuntuforums.org/showthread.php?t=1945850#8")
btw. I really wonder why this thread is closed as it seems more common problem and no solution have appeared :confused:

To add some details, I'm on new Asus B23E notebook. I prepared SSD partition table (GPT) and partitions layout with gparted (12.04 live USB booted in BIOS MODE).
I have of course 1st partition FAT32 200MiB as ESP

I'm also 100% sure that my system support UEFI and that it's enabled in BIOS (f.e. USB stick with Ubuntu appears twice at boot device selection menu, one name is with UEFI prefix).
Moreover I succeeded with UEFI Windows 7 installation and it works (boots fine). Just to mention, I didn't let Windows to change anything with partitions layout. Only pointed installer to which it should deploy OS.

After lot of tries I gave up and installed Ubuntu in BIOS mode. Now I can select through notebook's boot device startup menu (available under ESC key) to boot from:
[LIST]
[*]"SSD disk" - falls to legacy BIOS and boots Ubuntu
[*]Windows Boot Manager - boots Windows 7 with UEFI
[*]...
[/LIST]

This is almost fine, but I would feel much better if both systems boot through UEFI.


I had tried also to migrate the BIOS installed Ubuntu to UEFI but only screwed Ubuntu. So I had to reinstall Ubuntu (i installed grub-efi package, so it stopped to boot).

One more thing which can be helpful in my case. Under BIOS settings I can create custom UEFI boot menu items and point each to .efi file path.
I compiled grub2, and installed on ESP partition, then I created item "GRUB2" under BIOS and pointed it to the proper EFI file. It kind of worked. I got even to the menu I specified in grub.cfg, but then only couple of errors and blank screen again. Probably wrong grub.cfg or hardware compatibility issue (in matter of fact I'm not totally sure what I was doing :rolleyes:).


Short version is:
How to overcome 'blank screen problem' and successfully boot Ubuntu installer in UEFI mode?
or
How to migrate already installed Ubuntu in BIOS mode to UEFI?

I will appreciate any advice, please :)

---

### Post by oldfred on 2012-05-06
@tamashumi
You probably had grub.efi and UEFI working, but have a video issue after grub loads. There also was a bug which I think they fixed that shift key did no work to get to grub menu. 
With newer versions of grub2 you do not need to download and compile it. I think that was only 11.04 or before did not work well and you need the newer code that is now standard.
You need to see if the nomodeset parameter or possibly other boot parameters are required.

 How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode), install nVidia driver suggested my Ubuntu

---

### Post by tamashumi on 2012-05-06
@oldfred
Thanks for reply.

I also think that this can be some hardware issue like you mentioned, video maybe.

I'll check your links later as now is late.

I'm not sure how changing grub options for Ubuntu instance already installed in BIOS mode can help me?

The installed Ubuntu instance works fine when booted with BIOS.

You mean to try boot with grub.efi and then try nomodeset under GRUB menu?

Just to mention I don't have nvidia GPU, just Intel's integrated HD 3000.

---

### Post by oldfred on 2012-05-06
Are you then able to boot Windows in UEFI and Ubuntu in BIOS?

With gpt partition and BIOS boot, grub really wants a 1MB bios_grub partition that is unformated to hold grub code. I am recommending both efi partition and bios_grub for most installs and let grub sort it out.

But if you boot the installer in UEFI most it should install in UEFI mode.

If you do not have video issues in BIOS mode, I would not think that is different in UEFI mode. But there are many settings in BIOS/UEFI and some may make a difference.

Someone posted this:
[SOLVED] UEFI Boot Problems 
quiet splash vt.handoff=7 rootdelay=90 reboot=a,w
[http://ubuntuforums.org/showthread.php?t=1857639](http://ubuntuforums.org/showthread.php?t=1857639)

Post results.txt from this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

### Post by tamashumi on 2012-05-07
Just quick reply for now.

> **oldfred said:**
> Are you then able to boot Windows in UEFI and Ubuntu in BIOS?
Yup, this is the exact case I have. And I don't have 1mb grub_bios partition.

> **oldfred said:**
> But if you boot the installer in UEFI most it should install in UEFI mode.
But the main problem is that the _Ubuntu installer doesn't work in UEFI mode_. I'm getting to the try/install/check Live CD menu. After any option is selected USB stick flashes with a led for couple of seconds, then notebook freezes with a blank screen and nothing else happens.
It's the exact same behaviour like posted in closed thread I linked in my 1st post here (seems to be more common).
I tried with three different USB sticks.
It's also the main reason why I can't install and test properly Ubuntu in UEFI mode :/ For the same reason I went with BIOS install (and tried to convert into UEFI then).

Best thing would be to figure out why installer freezes. I understand that I can try this 'e' trick with modifying grub2 options during Live USB boot too. Is it good way to try?

---

### Post by GerMulvey on 2012-05-07
Having followed the advice and info I still get no further than grub fails. I followed exactly SuperFreaks method but it never boots. I can install opensuse on gpt with no issue at all yet ubuntu seems to make it harder than hell. So I'm kinda stuck.
opensuse 12.1 just booted fine from gpt disk :)

---

### Post by oldfred on 2012-05-07
@tamashumi
Are you starting CD or USB flash from UEFI menu not from BIOS boot?

@GerMulvey
It may just be better to start a new thread. Too many different questions with possibly different solutions starts to get confusing.

---

### Post by tamashumi on 2012-05-20
> **oldfred said:**
> @tamashumi
Are you starting CD or USB flash from UEFI menu not from BIOS boot?


I'm booting USB flash. The notebook has not any optical drive.
Installing in BIOS mode from the same stick works fine. EFI files are also loaded as I'm getting to the GRUB menu (UEFI's menu as it's black-and-white).
Then when any option selected screen goes blank and USB led (depends on stick used) flashes/glows for some time then stops and nothing more happens.

---

### Post by oldfred on 2012-05-20
If you can get to grub then you have a boot issue. Often video, sometimes other options.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by Vidar30 on 2012-05-23
Sony Vaio E

In UEFI-mode, it will _only_ boot the pre-installed windows7 or a DVD with Windows8.

These media will boot in BIOS-mode, but not UEFI: 

- DVD with windows7
- Live DVD Ubuntu12
- Ubuntu USB installation

I apologize in advance if the answer to my question is to be found in this thread: 

Any tips on how I can install Ubuntu in UEFI-mode? It puzzles me since the installation DVD won't boot unless I switch to BIOS -mode.

Thanks in advance  - Windows is slowly killing me.

---

### Post by YannBuntu on 2012-05-23
Hello Vidar30,

i am not a EFI expert, but if i were you, i would:
1) backup my documents
2) backup the current EFI partition, and make sure you have a Windows CD in case you need to reinstall it
3) use the [latest Gparted CD]("http://sourceforge.net/projects/gparted/files/gparted-live-stable/") to create another EFI partition (FAT32, >200Mo, close from the beginning of the disk for example just after the Windows EFI partition), without deleting the Windows EFI partition, and move the boot flag from the Windows EFI partition to the new one. Also create a BIOS_boot partition (>1Mo, bios_grub flag, unformatted) just in case. And partitions that will contain Ubuntu  (SWAP= size of your RAM  +  system / in ext4, >15Go).
4) boot a Ubuntu CD in BIOS mode (as you can't boot in EFI mode), install Ubuntu in your previously prepared partitions. If you have a GPT disk this will install GRUB in MBR+BIOS_boot partition. If not, this will not use the BIOS_boot partition. Reboot and check if this works (=if you have access to both Windows and Ubuntu or not)
5) If not, purge grub-pc and install grub-efi. This can be done via the "Separate /boot/efi" option of Boot-Repair for example. This will create a grub(..).efi file in your new EFI partition. You may then need to setup your BIOS to add this file as an entry in your BIOS menu (but i have doubts as you said you don't have EFI mode in your BIOS).

---

### Post by Spudgun79 on 2012-07-07
Hi all,

I'm trying to follow this guide, but the Ubuntu 12.04 live usb stick I've created does not appear to want to boot if I pick UEFI mode.  All I get is a grub> prompt.

Everything seems to fire up okay if I choose BIOS mode, and looking on the contents of the usb stick the efi folders with the 'bootx64' is present.  I've googled for an hour with no success before posting here.

Have I missed something?

For info my motherboard is an Asus P8P67 LE

---

### Post by YannBuntu on 2012-07-09
**@Spudgun79:** please indicate your [BootInfo URL]("http://ubuntuforums.org/showpost.php?p=11136267&postcount=1").

---

