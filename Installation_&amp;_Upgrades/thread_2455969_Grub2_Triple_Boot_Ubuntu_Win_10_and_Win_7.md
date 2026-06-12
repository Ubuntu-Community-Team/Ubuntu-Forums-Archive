---
title: "Grub2 Triple Boot Ubuntu Win 10 and Win 7"
date: 2020-12-31
forum: Installation &amp; Upgrades
---

### Post by mark bower on 2020-12-31
I had a working dual boot system:  Ubuntu 20.04 on a hard drive, and Win7 on another hard drive.

I have now added an additional hard drive to my PC system for a total of 3 hard drives installed, with one OS system on each:  Ubuntu 20.04, Windows 10, Windows 7.  A run of Grub2 does not acquire the 3rd drive, the one with Win10 (plz see image).  So only Ubuntu and Win 7 remain bootable via Grub2.  Both the Win7 and Win10 drives are visible in Places(Gnome classic display).   All of the OS are individually bootable, though I have to manipulate boot order in the BIOS to get Win10 to boot.

I note in the boot menu in the BIOS that the Win10 drive has two entries, one with a line "Windows Boot Manager . . ." .  The Win7 drive does not have a second entry. (plz see image) 

What is wrong and what are options to fix the boot process?  When I installed Win10, I do not recall if there were options for boot loading?  May the only practical option be to reinstall Win10(a bugger compared to installing Ubuntu).

---

### Post by oldfred on 2020-12-31
Are all installs old BIOS with MBR(msdos) partitioning or all newer UEFI with gpt?
Windows 7 usually but not always was BIOS/MBR.
Microsoft has required vendors to install Windows in UEFI mode to gpt drives since 2012, but users could still use BIOS/MBR.
How you boot install media with newer systems UEFI or BIOS boot, it then how it installs.

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 

With multiple drives, do not run any autofix in Boot-Repair. It may want to install grub to MBR of all drives if BIOS/MBR. But you want to keep Windows boot loaders for each system on its own drive. Only use Boot-Repairs advanced mode where you can choose an install and which drive's MBR to install boot loader into.
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by mark bower on 2020-12-31
thanks for reply.  i saw a similar post you made but over my head, as most of your post here is, and i believe the thread was closed.  i will respond tomorrow with questions and edit this post.  

but for starters, i have no idea what "BIOS with MBR(msdos) partitioning or all newer UEFI" was used; i do not recall if there was a choice and/or i made a selection.  i just installed and all worked as intended. unfortunately, i was not cognizant of any choice during today's install of Win 10, and frankly, was irritated the whole time with all the entries required.

---

### Post by ActionParsnip on 2021-01-01
Why Windows 7? It is no longer supported as of 14th January 2020... It's not secure and shouldn't be used by anyone for anything

---

### Post by tea for one on 2021-01-01
> **mark bower said:**
> thanks for reply.  i saw a similar post you made but over my head, as most of your post here is, and i believe the thread was closed.  i will respond tomorrow with questions and edit this post.  

but for starters, i have no idea what "BIOS with MBR(msdos) partitioning or all newer UEFI" was used; i do not recall if there was a choice and/or i made a selection.  i just installed and all worked as intended. unfortunately, i was not cognizant of any choice during today's install of Win 10, and frankly, was irritated the whole time with all the entries required.

UEFI with GPT is superior to BIOS with MBR

Are you familiar with your UEFI set up screens (accessed by a dedicated keystroke at Power On) because that is where you control the boot mode (UEFI or Legacy and/or mixed)?

If you have mixed boot mode set up, then you control the mode with the PC boot menu.
[COLOR="#0000FF"]UEFI:Kingston or other device name[/COLOR] will indicate that the live session will boot and eventually install in UEFI mode.

Each disk with a separate OS is perfect but please heed the comment by [COLOR="#0000FF"]ActionParsnip[/COLOR] and remove Windows 7.

Anyway, please post the boot-repair report as requested by [COLOR="#0000FF"]oldfred[/COLOR] and I'm sure that you will receive good advice/recommendations.

---

### Post by tea for one on 2021-01-01
Why do you have old kernels (4.4.0-97) in the thumbnail of your first post?

The current kernel for Ubuntu 20.04 is 5.4.0-58.

---

### Post by yancek on 2021-01-01
Based on the information in your initial post it is almost certain that you have windows 7 installed in what is referred to as Legacy/CSM mode and Ubuntu the same.  A windows 7 default install will be Legacy which is a boot system that predates the existence of windows (1970's).  A default install of windows 10 on a GPT drive will be UEFI.  If this is the way the systems were installed (boot repair will tell us that) you will be unable to boot windows 10 installed UEFI from a Legacy install of any Linux Grub installed in Legacy mode.  I don't beleive a UEFI install of Linux Grub will boot a Legacy install of windows.

I don't have the unsupported windows 7 installed but I am pretty certain windows 7 bootloader will not boot a UEFI install of windows 10, nor will a windows 10 UEFI boot a Legacy windows 7.

The link below to the Ubuntu documentation gives detailed information on UEFI and mixing modes and its problems (Legacy/UEFI).

[URL="https://help.ubuntu.com/community/UEFI"]https://help.ubuntu.com/community/UEFI

[/URL]

---

### Post by oldfred on 2021-01-01
From the link in my signature below.

Acronyms:
UEFI [https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
ESP/efi -  Efi System Partition  [http://en.wikipedia.org/wiki/EFI_System_partition](http://en.wikipedia.org/wiki/EFI_System_partition)
[https://en.wikipedia.org/wiki/BIOS_boot_partition](https://en.wikipedia.org/wiki/BIOS_boot_partition)
BIOS - Basic Input/Output System [http://en.wikipedia.org/wiki/BIOS](http://en.wikipedia.org/wiki/BIOS)
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.
grub2 [https://wiki.archlinux.org/index.php/GRUB2](https://wiki.archlinux.org/index.php/GRUB2)
gpt(GUID) [http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
MBR(msdos) [http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

---

### Post by mark bower on 2021-01-01
I spent almost two hours preparing a detailed response on my discoveries, how I did it, and addressed everyones' posts, then somehow deleted the post!!!!!  So now a very cryptic response - sorry.  

Disk 1 Ubuntu = Legacy Boot on HHD
Disk 2 Win7 = BIOS
Disk 3 = EFI.

So I have a mix.  I tried messing with the BIOS settings and CSM in particular, but did not effect a change in boot behavior.  I attached screen shots to show CSM settings, and not reflected, I tried OS Type set to "Other", but again, no effect.

So can the problem with Win10 being a UEFI boot loader vs legacy be fixed in the BIOS settings, I gather not?  If not, can I just do a clean install of Win10 again, but pay heed to a possible initial setup choice of setting to Legacy BIOS?

Two side comments:  The Ubuntu OS is 16.04, not 20.04 as I stated.  And I run ACAD2000 and TaxAct on Win7 32bit.  With Win10, I will probably use TaxAct and an app that is only offered in 64bit.

---

### Post by tea for one on 2021-01-02
The solution here is now more apparent.

Leave Windows 10 in [COLOR="#0000FF"]UEFI[/COLOR] mode and install your TaxAct software.
Double check that everything works OK.

Ubuntu 16.04 reaches End of Life in April 2021.
Back up data and install Ubuntu 20.04 in [COLOR="#0000FF"]UEFI[/COLOR] mode.
Run **sudo update-grub** to pick up Windows 10 bootloader. (I would not do this because it's no problem to use the PC boot menu rather than grub)

Remove Windows 7 completely as it is unsupported.

Separate disks for each OS is highly desirable.
If you can, remove, de-activate or isolate your Windows 10 disk when installing Ubuntu 20.04 to eliminate any human error.
Always have backups ready.

---

### Post by yancek on 2021-01-02
If you have some software you need on windows 7, then the setup  you currently have is the best you can do.  Ubuntu in Legacy mode will boot windows 7 but not windows 10.  It is possible to install windows 10 in Legacy mode but NOT on a GPT drive.  You can change the windows 10 drive from GPT to msdos  but that obviously will delete all the data and mean a complete reinstall of windows 10.  So your options are to have Ubuntu Grub boot itself and windows 7 and when you want windows 10, you need to make the change in the BIOS on boot.  If you install Ubuntu UEFI, you will be able to boot windows 10 from Grub but not windows 7.

>  can I just do a clean install of Win10 again, but pay heed to a possible initial setup choice of setting to Legacy BIOS?


That alone won't do it as I indicate above..  If you want windows 10 in Legacy, you need an msdos rather than GPT drive.    If you can use the specific software you currently have on windows 7 on windows 10, that would be the best and simplest option.  Reinsasll Ubuntu UEFI to access windows 10.

---

### Post by mark bower on 2021-01-02
Well, I agree with all that you have said, with one hitch.   The monitor (TV) is 3840 x 2160 pixels and I have tried different combinations of settings to get the ACAD icon sizes increased so I can easily see them. ACAD2000 displays nicely in Win7 32bit, but creates difficulties for me in WINE.  And I tend to panic when I cannot get the WINE 32 prefix set up to run ACAD in Ubuntu.

So I would like to move to 20.04LTS (which I am already using on another computer) with a UEFI install, use Win10 as is, and do a fresh install of Win7 in UEFI mode.  I googled re Win 7 and seems if I set computer BIOS to UEFI mode (believe I have seen how to do this) before a Win7 install to HDD, it will install in UEFI mode.  You noted that PC UEFI might not boot legacy, although I would try this 1st to avoid reinstalling Win7.

To be clear, each OS is on its own HDD and yes, I always disconnect all but the HDD I am installing to.  Developed this habit many many years ago after making a mistake.  I do not believe security is an issue as I have no private information on our computers, with the exception of tax time in which case I may temporarily store a file on HDD while I am doing taxes, but usually try and store all tax info off on USBs.

---

### Post by yancek on 2021-01-02
If you plan to try to install windows 7 UEFI, I would definitely do some research by reading several sites describing the process.  If you want windows 7 in UEFI, disable Legacy/CSM in the BIOS before booting the installer.  Windows 10 in UEFI needs to be on a GPT drive so I imagine it is the same for windows 7.

>   You noted that PC UEFI might not boot legacy,

Not sure what you are referring to but Grub in UEFI definitely won't boot a Legacy windows, tried it in a number of ways and all I have read indicates the same.  If you run sudo update-grub you won't see an entry for windows 7.

>   I do not believe security is an issue as I have no private information  

I think the security issue is less to do with data on your computer and more to do with using an unsupported and insecure system like windows 7.  If you don't use it on the internet, no problem as you won't be exposing the computer to being hacked and causing problems for others.

---

### Post by mark bower on 2021-01-02
I tried to install ACAD in Win10, but Win10 will not accept it.  So I will forge ahead with a 20.04 UEFI install (currently in progress), then try and setup the Win7 on UEFI.  Again, Win7 is targeted to a dedicated HHD so that should reduce complications.  And yes, good idea - I should be able to disable WiFi for Win7 use.

It is very convenient that my top end computer has 4 HDD bays and I have multiple HDDs.  Thus my messing with things, not always sure of what I am doing, is done at low risk.

---

### Post by tea for one on 2021-01-02
I was not familiar with the software ACAD2000 which now seems to be the stumbling block in this thread.

I had a quick search and found a software package produced in 2000 with the last revision in 2002 - is that correct?

---

### Post by mark bower on 2021-01-02
I am not sure of ACAD revision; copyright is 1999.

My 20.04 fresh install did not go well.  I was hoping for choice of UEFI or Legacy, but given those options.  Pls see atch image.  Prior to the install, I chose UEFI BIOS settings:   Boot Device Control:  1) UEFI & Legacy OPROM and 2) Boot from Storage Devices: Ignore.  I do not know what the relevance of the storage devices is and if that refers to the HHDs?  I have include atchs which gives the options in CSM.  Initiating a Grub2 did not pick up the Win10 drive.

So, ready for another advised install?

---

### Post by oldfred on 2021-01-02
If you have UEFI Secure Boot on, it typically does not want to let you boot from any other storage device like a USB port storage drive as that is insecure.
So you have to allow USB boot or full USB support. 

How you boot install media, UEFI or BIOS is how it installs for both Windows & Ubuntu.
Some tools like Rufus make a UEFI only (UEFI/gpt) or BIOS only (CSM/MBR) install flash drive. Most tools make it for both, but then you have two options in UEFI boot menu. One clearly UEFI and other not or the BIOS option. Usually just shows name or label of flash drive.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

UEFI boot settings are then for your installed system. 
On one of my systems, it would only boot in UEFI mode with UEFI only. UEFI or CSM option always booted in BIOS mode.

More info in link in my signature on UEFI boot.

Shows live installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen 20.10 uses grub for both
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

[http://ubuntuforums.org/showthread.php?t=2194280](http://ubuntuforums.org/showthread.php?t=2194280)
Duckhook's suggestions
"Simple", "3D" & "CAD" do not mix. Choose two out of three.
3D + CAD = TurboCAD (not that powerful), AutoCAD (the 800 lb Gorilla of CAD, but only Windows)
Simple + 3D = Blender (awesome), BRL-CAD, FreeCAD (but despite the name, it isn't really CAD&#8212;It's a modeler)
Simple + CAD = LibreCAD, FreeCAD (as above&#8212;primitive CAD functionality), QCad, VariCAD 
[https://ubuntuforums.org/showthread.php?t=2439214](https://ubuntuforums.org/showthread.php?t=2439214)

There is an active project called FreeCAD[1] which has been designed as a kind of CAD platform. It has a built in Python intepreter and everything about it can be altered using Python modules. It's massively extensible and powerful. The GUI frontend only provides access to a tiny tiny subset of what the backend can do.
[http://sourceforge.net/projects/free-cad/](http://sourceforge.net/projects/free-cad/)

---

### Post by tea for one on 2021-01-03
> **mark bower said:**
> I am not sure of ACAD revision; copyright is 1999.

My 20.04 fresh install did not go well.  I was hoping for choice of UEFI or Legacy, but given those options.  Pls see atch image.  Prior to the install, I chose UEFI BIOS settings:   Boot Device Control:  1) [COLOR="#FF0000"]UEFI & Legacy OPROM[/COLOR] and 2) Boot from Storage Devices: Ignore.  I do not know what the relevance of the storage devices is and if that refers to the HHDs?  I have include atchs which gives the options in CSM.  Initiating a Grub2 did not pick up the Win10 drive.

So, ready for another advised install?

Try this option - Boot Device Control > [COLOR="#0000FF"]UEFI only[/COLOR] (your second screenshot)

Each vendor implements their UEFI set up pages to their own recipe so it is difficult to offer perfect individual advice. 
However, I'm sure that the correct option is available somewhere in the UEFI menu.

You can check that you have booted in UEFI mode _before_ installing by opening a terminal:- 
```
[ -d /sys/firmware/efi ] && echo "UEFI mode" || echo "Legacy mode"
```

---

### Post by mark bower on 2021-01-03
o.k., I messed with a number of options for installing the OSes, and below is where I am at.  I would stress that I could find no way to get Win7 to install as UEFI. 

Drive 1 - Ubuntu 20.04, installed with CSM set to UEFI or UEFI, UEFI enabled
Drive 2 - Win10 installed with CSM set to UEFI, UEFI enabled
Drive 3 - Win7, installed with CSM set to UEFI &Legacy OPROM, BIOS enabled

When I installed Win7 with CSM set to UEFI & Legacy OPROM, the BIOS utility sees the Win7 install DVD, but grub2 does not see it.

So I can set CSM to UEFI only or UEFI & Legacy OPROM, and boot either Ubuntu or Win10.  To boot Win7, I must set CSM to Legacy Only - and then the other OSes are not available.  Please see atch which shows these options.

So this may be what I have to live with.  But pure and simple, is there no way to get/trick a Win7 (32bit) to install in UEFI mode?

@oldfred - my CAD drawings are limited to 2D and a bit of a stretch for me to become acquainted with other software other than the ACAD version I continue to use.  But thanks for the effort to outline other possibilities.

---

### Post by oldfred on 2021-01-03
While I still do not recommend Windows 7, its original DVD required you to copy to flash drive & move files around & rename them to make it UEFI bootable.
Supposedly the revised SP1 Windows 7 release included the updates to make it UEFI bootable.

The original 64-bit Win7 DVD did NOT have /EFI/BOOT/BOOTX64.efi.
The /EFI directory only contains /microsoft with a number of different boot manager .efi files.
The 64-bit Win7 DVD with SP1 integrated in DID have /EFI/BOOT/BOOTX64.efi in addition to /EFI/microsoft/<various files>.efi (among others)
So MS apparently figured out EFI booting between Win7 and Win7SP1.

Windows only installs to MBR(msdos) partitioned drives in BIOS mode.
Windows only installs to gpt partitioned drives in UEFI mode.
Conversion for MBR to gpt erases entire drive, so have good backups.
Microsoft suggested partitions including reserved partition for gpt & UEFI:
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions)

[https://ubuntuforums.org/showthread.php?t=2304736](https://ubuntuforums.org/showthread.php?t=2304736)
[https://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx](https://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx)
Convert Windows from BIOS/MBR to UEFI/gpt.
[https://www.windowscentral.com/how-convert-mbr-disk-gpt-move-bios-uefi-windows-10](https://www.windowscentral.com/how-convert-mbr-disk-gpt-move-bios-uefi-windows-10)
[http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx](http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx)

Some have posted that Windows mbr2gpt really only works for data drives, and Linux tools like gdisk work better for data drives anyway.
Best to plan new install.

---

### Post by mark bower on 2021-01-04
I looked at the links you provided; they all seem to point to either Win10 or Win7 64bit conversion to UEFI boot.  I did not see any process given for moving Win7 32bit to a gpt partition, which I now understand is what is needed.  I did some googling and found testimonies of getting Win7 to work with UEFI, but they did not provide step by step discussions on how to do so and seemed "prickly".  For the act, Win7 BIOS to UEFI, I would really need some hand holding.  However, if I were to try something, I believe there is no risk for me since I have each OS on a different drive.

So it looks like I need to close out the thread as solved to the extent of what I would like to do.  Still, I would love to make the alteration so that all drives show in Grub2 - maybe take a crack at it when "snowed in" here in S. California (just kidding).  I will undoubted will try the challenge at at later date when I have an abundant amount of patience.  And in the meantime I will do some more googling for a process that I believe I can follow.

---

### Post by yancek on 2021-01-05
>  I did not see any process given for moving Win7 32bit to a gpt partition, which I now understand is what is needed 

Before you begin that task, I would suggest you go to the link below which is the microsoft site which indicates windows vista and later can be booted from GPT drives.

[https://docs.microsoft.com/en-us/previous-versions/windows/hardware/design/dn640535(v=vs.85)?redirectedfrom=MSDN](https://docs.microsoft.com/en-us/previous-versions/windows/hardware/design/dn640535(v=vs.85)?redirectedfrom=MSDN)

If you scroll about half way down that page, you will see the statements below.

>  Yes, all versions can use GPT partitioned disks for data. Booting is only supported for 64-bit editions on UEFI-based systems.

Similar info at the link below.

[https://superuser.com/questions/642393/how-do-i-install-windows-7-32-bit-on-a-uefi-based-system](https://superuser.com/questions/642393/how-do-i-install-windows-7-32-bit-on-a-uefi-based-system)

---

### Post by tea for one on 2021-01-05
Just to add more fuel to the fire while you are snowed-in in Southern California:-

You could investigate [https://www.rodsbooks.com/refind/](https://www.rodsbooks.com/refind/) 
One of the features mentioned is > rEFInd also supports legacy boots on some UEFI PCs
I've not used [COLOR="#0000FF"]refind[/COLOR], but I've seen it mentioned a few times in these fora.

Secondly, you could also create a VM of Windows 7 (either with Windows host or Ubuntu host) for your CAD software.

---

### Post by mark bower on 2021-01-05
@ yancek
It appears that I was mistaken in a solution.  I thot I had found some posts that said Win 7 32bit could be booted under UEFI - but did a lot of googling and found nothing to support.  The conclusion seems to be what you pointed out in the Microsoft - see attachment.

@ tea for two
Just in case, I have emailed rodsbooks.com re his software, but no response yet.

I am going to gracefully pull out of further pursuit in this thread, and mark this thread as solved.  And in a way it is solved, I learned a bit and it is clear I cannot do what I would like to.  Thanks for hanging in with me.

---

### Post by mark bower on 2021-01-23
@tea for one - you nailed it for me.  Your suggestion of looking into ReFind, a GUI boot manger, is just what I needed.  Now that it is installed, the GUI boot screen gives me three choices to boot from:  Ubuntu 20.04, Win10 and Win7!!!!!!  I do appreciate all who tried to help.

So my quest is _definitely solved_ and I see I have already marked it as such.  But I will return and edit this post with a lot of info on ReFind so that others might want to consider it, althoh I realize there are probably few users of Win7 32bit.

---

### Post by mark bower on 2021-01-24
@tea for one - you nailed it for me.  Your suggestion of looking into rEFInd, a GUI boot manger, is just what I needed.  Now that it is installed, the GUI boot screen gives me three choices to boot from:  Ubuntu 20.04, Win10 and Win7!!!!!!  64bit,64bit,32bit.  Additionally, I do appreciate all who tried to help.

So the key links to obtain the rEFInd boot manager are [https://www.rodsbooks.com/refind/](https://www.rodsbooks.com/refind/) and Rod Smith directly (who was very helpful and responsive) at [email]rodsmith@rodsbooks.com[/email].  Following is my PC GUI boot screen image and the instructions provided by Rod.  On the boot screen going left to right icon, the 1st is Ubuntu, the 2nd is Win10, and the 3rd is Win7.  Added-bolded additions in the instructions are my mine.  I also include some of Rod's options:  1) for keeping Grub2 from returning, which he characterizes as a "coup", and 2) how to remove rEFInd to return to Grub 2.  Bottom line is that rEFInd allows one to easily boot both 64bit and 32bit on an EFI system.

[HTML]1) Set your firmware to its "UEFI and Legacy OPROM" mode.
2) Boot to 64-bit Ubuntu. (It can be done from your 64-bit Windows 10,
   too, but it'll be harder to install that way.)
3) Install rEFInd in whatever way you prefer, as documented at:
   https://www.rodsbooks.com/refind/installing.html
   Installing using a Debian package or the rEFInd PPA is likely to
   be the easiest way to do it.
3a Shutdown and boot to see GUI.  Repeat a 2nd time if GUI does not show.
4) Test that rEFInd works. At this point, it should boot either
   Windows 10 or Ubuntu, but it won't detect your 32-bit Windows 7.
   You'll probably see two Ubuntu options, one of which boots
   through GRUB and the other of which boots the Linux kernel
   directly. If you want only one, you can hide the one you don't
   want later.
5) Boot Ubuntu.
5a Enter "sudo su" privileged
6) Open /boot/efi/EFI/refind/refind.conf in a text editor.
7) Edit the "scanfor" line:  (find scanfor at line 310)
   * Uncomment the line (remove the leading "#").
   * Add "hdbios" to the list of options.
7a) save refind.conf
8) Reboot (two reboots may be necessary). At this point, you should see three
 more boot options, one for each of your hard disks. (Unless you have more than
   those three disks or if one or more of those disks is invisible to
   your firmware, in which case the number of extra options will
   be different.) Test each of these options to learn which one
   boots Windows 7. Make note of this option.
9) Reboot into rEFInd again. This time, select the EFI and/or
   BIOS options (disk icons) you DO NOT want to see and hit the Delete or minus
   ("-") key. This will hide those options. See here for more
   information:
   https://www.rodsbooks.com/refind/configfile.html#hiding
10) You can optionally remove GRUB or otherwise modify it to
    prevent it from taking over as the default boot manager, which
    it's likely to do, sooner or later, if you do nothing about it.
    See here for more information:
    https://www.rodsbooks.com/refind/bootcoup.html
[/HTML]
When you're done, you'll have one Windows 10 entry, one or two Ubuntu
entries, and one entry to boot a disk in BIOS mode. That last entry will
boot Windows 7, but it won't be labeled as such, and there's no way to
give it a "Windows 7" label.

Suggestion Rod Smith makes for keeping Grub2 from taking back control:
$ sudo refind-mkdefault

Suggestion Rod Smith makes for removing rEFInd:
# rm -r /boot/efi/EFI/refind

---

