---
title: "Dual boot Win 8, Ubuntu 12.10  Won't boot to windows"
date: 2012-11-20
forum: Installation &amp; Upgrades
---

### Post by claven123 on 2012-11-20
I just installed Ubuntu 12.10.  I shrunk the win 8 partition.  Created a 500gb ext4  /  partition for ubuntu.   I created a 4gb swap partition.

I can still see the OS partition, I chose something else when I installed.

I restart the computer and it boots directly into ubuntu.  I don't see GRUB to make a choice.

When I did get to the install part where it asked if I want to install along side and or something else, it mentioned that there was not an OS installed on the computer, when if fact there was.

Any help....


D

---

### Post by claven123 on 2012-11-20
Here is a screen shot of gparted from the live USB....

---

### Post by claven123 on 2012-11-20
Here is the attachment.

---

### Post by coffeecat on 2012-11-20
You have a UEFI system with a GPT (GUID partition table). One possibility is that you booted the Ubuntu installer in legacy mode and it has installed the wrong version of grub. Have a look here:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Scroll down to:

[https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_or_Legacy_mode](https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_or_Legacy_mode)

And try boot repair:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

That will hopefully fix things, but in any event make sure you take a note of the pastebin URL which Boot Repair will give you. That has details of the boot script output which you can post here if you need any help. 

One thing. Is the Ubuntu you installed 64-bit?

---

### Post by claven123 on 2012-11-20
Yes I do have the uefi....  I have the 64 bit version....   

I guess I will need to do more reading....

This shouldn't be this hard..... conical should update their install directions. 

D

---

### Post by claven123 on 2012-11-20
fstab:
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda7 during installation
UUID=3f5eb512-2a58-4c1e-bea4-d327043b56b3 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=DC36-4675  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda8 during installation
UUID=28d1bb45-842b-4115-8860-8958a0f1e9c2 none            swap    sw              0       0


Also....

dennis@dennis-XPS-8500:~$ dmesg | grep 'EFI: mem' >/dev/null && echo "Installed in EFI mode" || echo "Installed in Legacy mode"
Installed in Legacy mode
dennis@dennis-XPS-8500:~$ 

Thanks

D

---

### Post by claven123 on 2012-11-21
This is the terminal output while I did the instructions.  The message after the boot-repair.
 
However, after all this I got this error...
 
SECURE BOOT VIOLATION
Invalid signature detected.  Check secure boot policy in set-up.
 
I now can only boot into Windows 8, no GRUB or dual boot options...
 
 
Boot successfully repaired.

Please write on a paper the following URL:
[http://paste.ubuntu.com/1374104/](http://paste.ubuntu.com/1374104/)

In case you still experience boot problem, indicate this URL to:
[EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL] or to your favorite support forum.

You can now reboot your computer.
Please do not forget to make your BIOS boot on sda1/EFI/ubuntu/grubx64.efi file!

The boot files of [Ubuntu 12.10] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))


Entire terminal output for boot-repair....





ubuntu@ubuntu:~$ sudo chroot "/mnt/boot-sav/sda7" dpkg --configure -a
ubuntu@ubuntu:~$ sudo chroot "/mnt/boot-sav/sda7" apt-get install -fy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.5.0-17 linux-headers-3.5.0-17-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 119 not upgraded.
ubuntu@ubuntu:~$ sudo chroot "/mnt/boot-sav/sda7" apt-get purge -y --force-yes grub*-commonReading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'grub-common' for regex 'grub*-common'
The following packages were automatically installed and are no longer required:
  linux-headers-3.5.0-17 linux-headers-3.5.0-17-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  grub-common* grub-efi-amd64* grub-efi-amd64-bin* grub-efi-amd64-signed* grub2-common*
0 upgraded, 0 newly installed, 5 to remove and 119 not upgraded.
After this operation, 10.4 MB disk space will be freed.
(Reading database ... 178393 files and directories currently installed.)
Removing grub-efi-amd64-signed ...
Removing grub-efi-amd64 ...
Purging configuration files for grub-efi-amd64 ...
Removing grub2-common ...
Removing grub-efi-amd64-bin ...
Removing grub-common ...
Purging configuration files for grub-common ...
Processing triggers for install-info ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot


ubuntu@ubuntu:~$ sudo chroot "/mnt/boot-sav/sda7" apt-get install -y --force-yes grub-efi

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.5.0-17 linux-headers-3.5.0-17-generic
Use 'apt-get autoremove' to remove them.

The following extra packages will be installed:
  grub-common grub-efi-amd64 grub-efi-amd64-bin grub2-common
Suggested packages:
  multiboot-doc grub-emu xorriso desktop-base
The following NEW packages will be installed:
  grub-common grub-efi grub-efi-amd64 grub-efi-amd64-bin grub2-common

0 upgraded, 5 newly installed, 0 to remove and 119 not upgraded.

Need to get 1,987 kB/1,988 kB of archives.
After this operation, 8,583 kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/main grub-common amd64 2.00-7ubuntu11 [1,280 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/main grub2-common amd64 2.00-7ubuntu11 [116 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/main grub-efi-amd64-bin amd64 2.00-7ubuntu11 [547 kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) quantal/main grub-efi-amd64 amd64 2.00-7ubuntu11 [44.0 kB]
Fetched 1,987 kB in 3s (592 kB/s)        
Preconfiguring packages ...
Selecting previously unselected package grub-common.
(Reading database ... 178075 files and directories currently installed.)
Unpacking grub-common (from .../grub-common_2.00-7ubuntu11_amd64.deb) ...
Selecting previously unselected package grub2-common.
Unpacking grub2-common (from .../grub2-common_2.00-7ubuntu11_amd64.deb) ...
Selecting previously unselected package grub-efi-amd64-bin.
Unpacking grub-efi-amd64-bin (from .../grub-efi-amd64-bin_2.00-7ubuntu11_amd64.deb) ...
Selecting previously unselected package grub-efi-amd64.
Unpacking grub-efi-amd64 (from .../grub-efi-amd64_2.00-7ubuntu11_amd64.deb) ...
Selecting previously unselected package grub-efi.
Unpacking grub-efi (from .../grub-efi_2.00-7ubuntu11_amd64.deb) ...

Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for install-info ...

Setting up grub-common (2.00-7ubuntu11) ...

Processing triggers for ureadahead ...

Setting up grub2-common (2.00-7ubuntu11) ...
Setting up grub-efi-amd64-bin (2.00-7ubuntu11) ...
Setting up grub-efi-amd64 (2.00-7ubuntu11) ...

Creating config file /etc/default/grub with new version
BootCurrent: 0003
Timeout: 2 seconds
BootOrder: 0003
Boot0003* UEFI: USB Flash MemoryPMAP
BootCurrent: 0003
Timeout: 2 seconds
BootOrder: 0000,0003
Boot0003* UEFI: USB Flash MemoryPMAP
Boot0000* ubuntu
Installation finished. No error reported.
Setting up grub-efi (2.00-7ubuntu11) ...
ubuntu@ubuntu:~$

---

### Post by coffeecat on 2012-11-21
> **claven123 said:**
> 
SECURE BOOT VIOLATION
Invalid signature detected.  Check secure boot policy in set-up.
 

I have no experience of secure boot but I understood that Ubuntu 12.10, the version you have installed, included a signed version of the grub bootloader, so in theory you shouldn't be seeing this. You should be able to disable secure boot in the BIOS but someone with secure boot experience might have other ideas.

---

### Post by claven123 on 2012-11-21
Of course I only got that error the first time, now I just boot to windows, no errors.  Just no GRUB.
 
Do I turn off Secure Boot in the BIOS, I can do that.  
 
 
D

---

### Post by YannBuntu on 2012-11-21
Hello

> **claven123 said:**
> Please write on a paper the following URL:
[http://paste.ubuntu.com/1374104/](http://paste.ubuntu.com/1374104/)

Your Ubuntu/GRUB is now correctly setup in UEFI mode, and proposes a signed GRUB file (shimx64.efi).
Please disable "Secure boot" (show us pictures of your BIOS if you are not sure), and tell us what you observe.

EDIT: I added a paragraph about Secure Boot in the wiki: [https://help.ubuntu.com/community/UEFI#Enabling_.2BAC8_disabling_Secure_Boot](https://help.ubuntu.com/community/UEFI#Enabling_.2BAC8_disabling_Secure_Boot)

---

### Post by claven123 on 2012-11-21
I did that.

Now, I only see this:

Reboot adn select proper boot device or insert boot media in selected boot device and pres key.


I went to change the secure boot to enable, but I'm unable to change it.


Any advice...


D

---

### Post by YannBuntu on 2012-11-21
Please could you show us pictures of your BIOS?

---

### Post by claven123 on 2012-11-21
I'm not sure I know how to do that.  I can't take a screenshot, I'll look into it.  Can I do it with the live USB?
 
D

---

### Post by YannBuntu on 2012-11-21
You don't need USB.
Just boot your computer, a screen will appear (generally with the name of the pc vendor), there you need to press a key (F1 or F2, or Esc... it depends on your PC) until you enter your BIOS.

There, just take pictures of all screens via a camera.

---

### Post by claven123 on 2012-11-22
Here are the images...

---

### Post by claven123 on 2012-11-22
another

---

### Post by oldfred on 2012-11-23
You are in legacy mode or booting from BIOS not UEFI. 

Change setting back from legacy to UEFI, but leave secure boot off.

In legacy mode there would be no way to turn secure boot on as BIOS never had that type of setting.

---

### Post by claven123 on 2012-11-23
Ok, so I changed the BIOS to EUFI from legacy.

Now, it boots directly to Win 8., no GRUB

Secure boot is off, unless it resets with the last change?

Any more advice, run boot-repair again?

D

---

### Post by claven123 on 2012-11-23
13. **[COLOR=#800000]Download and Install EasyBCD[/COLOR]:** Download EasyBCD from [here]("http://neosmart.net/EasyBCD/").  Install it as you would any other Windows application. After  installation, start it, if it is not started automatically. The main  window is shown below. To add an entry for Ubuntu, click on the **Add New Entry** tab.
[IMG]http://www.linuxbsdos.com/wp-content/uploads/2012/11/EasyBCDwin8.png[/IMG]
 14. **[COLOR=#800000]And Entry in EasyBCD[/COLOR]:** Then click on the **Linux/BSD** tab. **GRUB 2** is the version of GRUB used by Ubuntu 12.10, so select it from the *Type* menu. For the *Drive* dropdown menu, **Automatically locate and load** always worked for me, but you can select the specific partition, if it makes you happy. Modify the *Name* field to match, then click the **Add Entry** button.
[IMG]http://www.linuxbsdos.com/wp-content/uploads/2012/11/EasyBCDwin8a.png[/IMG]
 15. **[COLOR=#800000]Preview Boot Manager’s Menu[/COLOR]:** To preview what Windows 8&#8242;s boot menu will look like, click the **Edit Boot Menu** tab. You can change the boot order and mess with a few other options from here. **Save Settings**, exit EasyBCD and reboot the computer.
[IMG]http://www.linuxbsdos.com/wp-content/uploads/2012/11/EasyBCDwin8b.png[/IMG]
 That’s it folks! Got any problems or questions, feel free to ask. To  make it easier to help you out, be sure to provide some details about  your [[COLOR=#009900]_hardware_[/COLOR]]("http://www.linuxbsdos.com/2012/11/05/dual-boot-windows-8-and-ubuntu-12-10-on-uefi-hardware/2/#") and partition sizes.






So, I followed these steps.


Now, I load into Windows Boot Loader and I can choose either Win 8 or Ubuntu 12.10.


BUT, When I choose ubuntu, I get an error that there is a missing file to run....  But, I am able to boot into windows from here.




D

---

### Post by claven123 on 2012-11-23
Error screen image.

---

### Post by YannBuntu on 2012-11-23
> **claven123 said:**
> Error screen image.

When does this error appear? with which settings?

---

### Post by claven123 on 2012-11-23
When I choose to load ubuntu.

The other choice is win 8.

D

---

### Post by oldfred on 2012-11-23
That error is from EasyBCD in trying to load the image it created to boot with grub. Not sure if it works with grub's' new UEFI image as it is still calling it .mbr which you do not have. But it could be just the name it uses even with the new version? 

Do not know what info they have on UEFI now.
       [http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

### Post by claven123 on 2012-11-24
I'm real grateful for all the help....

But what do I do now?

Should I just reset my computer to the factory settings and start over?  I'm at a loss for what to do.

D

---

### Post by oldfred on 2012-11-24
If you cannot get grub to work and EasyBCD is the only alternative, then you need to check on their forum.

Usually grub2 installs correctly, and Boot-Repair fixes an incorrect chain load entry to boot Windows.

But some UEFI implementations are just defective. Have you updated your UEFI/BIOS to newest version?
       Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)

---

### Post by coffeecat on 2012-11-24
> **oldfred said:**
> 
But some UEFI implementations are just defective. 

+1. I've been experimenting setting up Ubuntu/Windows 8 UEFI dual-boots with two different motherboards and one of them caused real problems. Out of interest, what make/model is your machine and if a desktop, what is the motherboard?

---

### Post by claven123 on 2012-11-24
Not sure on the MB.
 
Dell XPS 8500, desktop.  Win 8
 
 
D

---

### Post by claven123 on 2012-11-25
Ok, I'm about to give up.

How can I get just Ubuntu 12.10 to boot.  At this point I don't really need windows, I can always use my old machine to run windows vista.  


One thing, a request was made to have the boot record placed closer to the beginning, this was an error message or something I saw once.  Can someone give me advice on how to do this?  Will this help?

Should I somehow reverse the things I did with the EasyBCD?  Looking back, this seems like not the best option, but was advised to do so.


Thank for all the help, I really appreciate it....

D

---

### Post by claven123 on 2012-11-25
> **oldfred said:**
> 

But some UEFI implementations are just defective. Have you updated your UEFI/BIOS to newest version?

Should I have the latest one?  Are you talking about flashing my BIOS?

D

---

### Post by claven123 on 2012-11-25
[http://neosmart.net/forums/showthread.php?t=11135](http://neosmart.net/forums/showthread.php?t=11135)

Interesting...

So, we should not be using the EasyBCD?

D

---

### Post by oldfred on 2012-11-25
I believe that says EasyBCD cannot work with UEFI as Windows does not allow BCD to be customized. 

Grub at least can create a chain entry back to the Windows efi loader to boot Windows or you use UEFI to choose which install to boot from UEFI menu. In BIOS some use f12 or whatever one time boot key to choose what to boot if not using grub2.

Yes on possibility of flashing BIOS, its just it not BIOS anymore but UEFI. :) 
Did you check what version yours is and if a new version has fixes and what those fixes may be. 

We have seen some systems where either very large / (root) partitions like a standard install of just / & swap on a 500GB drive or larger does not work. Also some cases where larger / that is well beyond 100GB point on drive. Boot-Repair uses a standard suggestion of a separate /boot as that can be smaller (300 to 500MB) and possibly easier to fit near front of drive. I usually suggest smaller / (root) of about 25GB and then have rest as /home or just data partitions. 

I have several installs near the end of my 650GB drive and they boot without issue. And problem only exists with some systems. So either a bug in grub that in combination with certain BIOS/UEFI or possibly a setting in BIOS/UEFI that contributes to issues.

---

### Post by claven123 on 2012-11-25
I have posted on the neosmart/EasyBCD forum for advice on how to reverse the changes of that application.

BTW, that site is riddled with similar issues of dual booting Win 8 and Ubuntu 12.10


I will have to look at updating the UEFI/BIOS, not sure how to check that (for current version).

If it will help I am all for moving the boot files to a closer area on the HDD?  Not sure how to do this.  Can someone point me to a tutorial on how this is done?



D

---

### Post by oldfred on 2012-11-25
Rerun BootInfo report and post new link, so we can see where you are at.

From UEFI menu what does it show as bootable devices? Do you have a launch efi shell option?
Use camera if necessary, shrink and post using paperclip icon in edit panel.

---

### Post by claven123 on 2012-12-06
Here is the boot info report....

[http://paste.ubuntu.com/1415492/](http://paste.ubuntu.com/1415492/)


Do I now run this and see what happens?

D

---

### Post by claven123 on 2012-12-06
Scanning all of this and I noticed that my windows is hibernating.  I know this can occur from some of the previous post.  Interestingly this computer has been turned of for a week or more, unplugged and sitting on a shelf.  (I had moved my office the last two weeks).

How do I completely shut down windows?

D

---

### Post by claven123 on 2012-12-06
My gparted info...

---

### Post by oldfred on 2012-12-06
Use paperclip in edit panel above message to attach screen shots.

Some have had issues with very large / (root) partitions. You currently are using 3.4GB of 459GB. :)

> /dev/sda7      ext4       459G  3.4G  432G   1% /mnt/boot-sav/sda7

I often suggest / be 10 to 25GB where only the smaller size is for smaller older systems. And then for the rest of the space you want to allocate for Ubuntu make it /home or data partitions.

Windows is always hibernated, just two levels of hibernation. Much better to have a separate NTFS data partition for any data you may want in both Windows & Uubntu.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by claven123 on 2012-12-07
So, now what do I do.

Do I shrink the partition down to say 10-20gb....

Then create a new partition     /home

How does the current linux know to use that for data vs the /home in the current partition?

Will this solve my issue with no grub2 on boot?


D

---

### Post by claven123 on 2012-12-07
So, I shrunk the linux partition to about 22GiB and added a /home partition of 98GiB.

I then rebooted was given this screen.....  windows boot manager with options for win 8 and ubuntu.  (I think as a result of easyBCD).

Then when I chose Ubuntu I get this error.


NO Grub2.....


D

---

### Post by YannBuntu on 2012-12-07
IMHO reducing the root won't change anything for the boot, because the /boot will remain too far.

What may help is to reduce sda5 in order to create a 1GB free space between sda4 and sda5.
In this free space, create a /boot partition, as described here: [https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition)

But before doing all of this, please indicate your current [BootInfo URL]("https://help.ubuntu.com/community/Boot-Info"), so that we know how you created /home.

---

### Post by claven123 on 2012-12-07
The boot info url is above.  In a previous post....


Thanks for the advice.

D

---

### Post by oldfred on 2012-12-07
I do not see a link since #34 which was before the separate /home. 

I do not disagree with Yann on smaller root may not solve issue. But with UEFI systems we have not see much of the partition not found issue. 
Most issues are related to grub & efi. And then often some issues after grub boot with video or other device drivers. 
Some systems just install without any issue, others not so easy.

---

### Post by claven123 on 2012-12-08
I get the error that EFI has been detected...

[http://paste.ubuntu.com/1419669/](http://paste.ubuntu.com/1419669/)

Thanks,

D

---

### Post by claven123 on 2012-12-08
So, I ran the recommended repairs...

I guess what could it hurt, right?

I guess if this doesn't work, I need to return the computer to factor settings, and start over.  I'm confused as to all that has been done with this install and that would mean most of you all are too.

here is the boot url after the changes...

[http://paste.ubuntu.com/1419687](http://paste.ubuntu.com/1419687)

sda1/EFI/ubuntu/grubx64.efi file.....

D

---

### Post by claven123 on 2012-12-08
Ohhh  myyyy...

I reran boot-repair and it worked!!

I now see the pink grub2 menu and can boot into ubuntu 12.10  

When I choose the windows install it goes into the windows boot loader and I then choose windows 8 and It loads!!

Thanks all...

I'll play with it a bit and see how it works.

D

---

### Post by oldfred on 2012-12-08
So first from UEFI menu, does Windows boot, and then does Ubuntu boot to grub menu?

Then from grub menu does Ubuntu fully boot? And does Windows efi chain entry work (will only work if Windows does boot from UEFI menu).

---

### Post by claven123 on 2012-12-08
When I boot up I first see the Grub2 menu, it's pink.

I can choose either win8  or Ubuntu and some other options (I don't have access now to look).

When I choose ubuntu, it loads up and it appears to be fully functional.

When I choose windows, I get taken to the windows boot manager with options for ubuntu and windows.  I choose windows and it loads and appears to be fully functional.

So, it appears I can dual boot windows 8 and Ubuntu 12.10.....

I would prefer not to have the windows boot manager in there, but if that's all I have to do I'll take it for now.

Thanks for all the help.  I'm not sure what specifically worked.  I bet the Grub was not loaded correctly or something.

D

---

### Post by oldfred on 2012-12-09
Glad it is working. :)

Not sure I understand Pink? Normally you can change lots of settings including colors but its default is not pink.
And I do not understand which menu you are getting to. A Windows boot option should not be also showing an Ubuntu option unless you are really in the UEFI menu.

Please run the BootInfo report one more time just to document what you have that works. If you have a camera you can take photos (and shrink size if not screeenshot) and post those so we all know what menus you have.

---

### Post by claven123 on 2012-12-09
Here is the boot repair url....

[http://paste.ubuntu.com/1421790]("http://paste.ubuntu.com/1419687")


I'll post the images in a minute.

D

---

### Post by claven123 on 2012-12-09
Here is the grub2 image..  I guess it's not pink, but a purple ish color.  :)

The menu options....  I chose the top menu option and ubuntu loads without problems.  This is my defualt.



If I choose the Windows UEFI Loader the third thing on the list, then Windows boot manager loads, the second image.


D

---

### Post by oldfred on 2012-12-09
Boot script looks normal and first purple screen is standard grub. The Windows efi entries were from Boot-Repair.
The other screen is a UEFI menu.

Thanks for posting just to document system.

---

### Post by K. Hendrik on 2013-01-20
Very interesting read here, considering buying an XPS 8500 myself and had to make sure it will work the way I want it to.

After reading this i think your Windows Menu, wich pops up after Grub is still appearing because you entered ubuntu into the menu with BCD Edit perhaps you could just remove it again to get rid of it.

Any problems so far with drivers or heat ... ?

---

### Post by Vesperatus on 2013-03-04
Well, got an XPS 8500 and i'm trying to have the following setup functional :
sda, 2TB - Win 8 pre-installed
sdb, 250 GB - Ubuntu 12.10 64bit

Now, I use boot repair, it says it worked ( [http://paste.ubuntu.com/5585242/](http://paste.ubuntu.com/5585242/) ).

I reboot, I can boot in ubuntu no problem. I boot in windows once, when I reboot, I have no more grub, it tries to directly boot to windows, but no bootable device are found. 
I use an USB key to load ubuntu, do a repair again, boot in ubuntu, launch boot-repair again, same thing. Boot in windows once, reboot and lose the boot. 

Any clues on where i can do the following : "Please do not forget to make your BIOS boot on sda1/EFI/ubuntu/shimx64.efi file!" 
It is the only step I can't seem to properly execute.

---

### Post by oldfred on 2013-03-04
It sounds like Windows is resetting the default back to Windows. Some UEFI only boot the Windows efi folder or the Windows efi file. One of Boot-Repairs work arounds is to rename files. So system thinks you are booting Windows but really booting grub's shim file that has the Windows signed boot key.
       Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot
signed GRUB file shimx64.efi.

But you are not showing any boot files in your sdb efi partitioin. I would at least copy Ubuntu files. I thought Boot-Repair gave the option on which drive to install efi into. Both grub and fstab show the sda1 efi file and if putting grub's boot into sdb1 alows booting from that then both grub & fstab have to be changed from the UUID for sda1 to sdb1.

      
 Installing Ubuntu 12.10 alongside Windows 8 on Asus K95V laptop HD/SSD (EFI) Two drives. Details in post #6
[http://ubuntuforums.org/showthread.php?t=2116610](http://ubuntuforums.org/showthread.php?t=2116610)
UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
UEFI dual boot two drives see #14 on how edit UUID to Windows efi partiton
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)

---

### Post by Vesperatus on 2013-03-04
> **oldfred said:**
> It sounds like Windows is resetting the default back to Windows. Some UEFI only boot the Windows efi folder or the Windows efi file. One of Boot-Repairs work arounds is to rename files. So system thinks you are booting Windows but really booting grub's shim file that has the Windows signed boot key.
       Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot
signed GRUB file shimx64.efi.

But you are not showing any boot files in your sdb efi partitioin. I would at least copy Ubuntu files. I thought Boot-Repair gave the option on which drive to install efi into. Both grub and fstab show the sda1 efi file and if putting grub's boot into sdb1 alows booting from that then both grub & fstab have to be changed from the UUID for sda1 to sdb1.

   
On my rescue usb key, i'm installing boot-repair from the ppa yannubuntu. I guess it is the latest version ?
In Boot-repair, I used the default option, wich is "Sparate /boot/efi partion: sda1"

I still don't understand how I'm supposed to configure the BIOS to load the shim file.

---

### Post by oldfred on 2013-03-04
You only need shim for secure boot, if you want that.
And because some UEFI only boot Windows, Boot-Repair will use shim as Windows boot loader.
Not sure what your UEFI menu looks like and what choices it has.

---

### Post by Vesperatus on 2013-03-04
> **Vesperatus said:**
> On my rescue usb key, i'm installing boot-repair from the ppa yannubuntu. I guess it is the latest version ?
In Boot-repair, I used the default option, wich is "Sparate /boot/efi partion: sda1"

I still don't understand how I'm supposed to configure the BIOS to load the shim file.

This is maddening...

Here is what I did to try to fix the boot. 

[LIST=1]
[*]Boot from rescue usb
[*]Installed boot-repair and went with recommended repairs
[*]Booted in ubuntu and launched boot-repair from the os and purged grub
[*]Reboot many time in Ubuntu with no issues
[/LIST]

I now have the following options in Grub 2.00 before booting windows:
[LIST]
[*]Ubuntu
[*]Advanced options for Ubuntu
[*]Windows UEFI bkpbootmgfw.efi --> Boot Windows once. Then, I will get a no bootable devices error"
[*]Windows Boot UEFI loader --> Boot Windows. I have no more grub, but I can boot windows has much as I want...
[*]EFI/Dell/Boot/bootmgfw.efi --> Boot to some sort of recovery interface.
[*]EFI/Dell/Boot/bootx64.efi --> Same as bootx64.efi
[*]System setup --> Goes to BIOS.
[/LIST]

Any clues on how to fix this or more precision on what to transfer to my sdb1 partition ?

---

### Post by oldfred on 2013-03-04
Did you look at the links in Post #54? Those are probably the best solutions.
You can disconnect the Windows drive and then run Boot-Repair. That will install Ubuntu files to the Ubuntu drive's efi partition and auto edit fstab to be correct. You can manually do the same if you want.

You list of bootable devices looks like a mix of the UEFI menu & grub menu. It also depends on whether Boot-Repair has copies shim to the Windows boot file and somehow Windows then overwrites that. 
Ubuntu's shim file should boot to grub menu and then give the choices of Ubuntu & recover and chain load to the backup Windows file.

---

### Post by Vesperatus on 2013-03-04
> **oldfred said:**
> Did you look at the links in Post #54? Those are probably the best solutions.
You can disconnect the Windows drive and then run Boot-Repair. That will install Ubuntu files to the Ubuntu drive's efi partition and auto edit fstab to be correct. You can manually do the same if you want.

You list of bootable devices looks like a mix of the UEFI menu & grub menu. It also depends on whether Boot-Repair has copies shim to the Windows boot file and somehow Windows then overwrites that. 
Ubuntu's shim file should boot to grub menu and then give the choices of Ubuntu & recover and chain load to the backup Windows file.

Thank you oldfred. I will double check that tomorrow morning.

---

### Post by Vesperatus on 2013-03-08
Allright. I just gave up on dual-booting with grub.

Trying to install to sdb with boot-repair miserably failed. I manually reinstalled my grub on a non efi partition and disabled secure boot in my bios. 

If I need to boot in windows 8, I simply enable secure boot in the bios.

Secure boot and all the rest can burn in hell, where it belongs.

---

