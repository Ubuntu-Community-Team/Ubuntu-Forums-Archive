---
title: "Creating custom ISO"
date: 2021-01-21
forum: Installation &amp; Upgrades
---

### Post by hamstermandk on 2021-01-21
I am trying to create a custom ISO which I want to modify for unattended installation.

I am able to create the ISO but it seems I cannot make it bootable.
When I use the same procedure for a Window 10 ISO it works just fine. On Windows 10 I am using efisys.bin as bootfile.
And don't hate me - I am creating the custom ISO on a Windows machine using Powershell :)

I have tried using efi.img and that makes it bootable - but into a Grub command line and not starting the normal installer.

I am using this iso file as my base ubuntu-20.04-live-server-amd64.iso (which I have extracted the content and then recreated as my customimage.iso)

My guess is I just need the correct boot file to make it work but I can can't find it anywhere.

---

### Post by yancek on 2021-01-21
>  I am creating the custom ISO on a Windows machine using Powershell 

I think you will have to post a lot more detail if you want help.  Specific steps you took to do this, explain what the 'procedure' is.  Do you want to boot the usb in UEFI mode, Legacy/CSM mode or both?  Live Linux install systems can use Grub or Syslinux/Isolinux.  Which are you using?

---

### Post by hamstermandk on 2021-01-21
At first I "just" want to rebuild [COLOR=#000000]ubuntu-20.04-live-server-amd64.iso.
The official iso boots just fine in my virtual machine - and I want my custom iso to do the same.

I am booting it as UEFI.

My procedure is
1) Mouting [/COLOR][COLOR=#000000]ubuntu-20.04-live-server-amd64.iso
[/COLOR][COLOR=#000000]2) Copy content of mounted drive to a folder
3) Writing the content to a new iso
4) Writing the bootloader with a boot file with [/COLOR]efi.img

[COLOR=#000000]But it seems that [/COLOR]efi.img is the wrong file since it only boots into a command line instead of the regular installer as when you boot &#8203;[COLOR=#000000]ubuntu-20.04-live-server-amd64.iso[/COLOR][COLOR=#000000]

[/COLOR]

---

### Post by yancek on 2021-01-21
What commands did you use for steps 3 and 4.  If you are doing this in a directory (folder) you would then need to create an iso (or img file) of it.  Creating an iso would generally include installing a bootloader and the common tools for this are mkisofs, genisoimage and xorriso.   Some discussion of the last 2 at the Debian site below.  I've always used iso so don't know about img files or what differences there might be.  If you had a usb mounted to the folder on your drive, you could use the first 2 steps but would still have to install a bootloader.i

 [URL="https://wiki.debian.org/genisoimage"]https://wiki.debian.org/genisoimage

[/URL]

---

### Post by hamstermandk on 2021-01-22
It is a iso file I am trying to create.

But have done some more testing and I am a bit closer now.

For some reason my custom iso does not load grub.cfg (which show the install options) when it boots.
So it just show the GRUB command line.

---

### Post by yancek on 2021-01-22
>  So it just show the GRUB command line. 		

To state the obvious, Grub wasn't installed properly and no one can tell you what or if you did something wrong as we don't know what you did?

---

### Post by hamstermandk on 2021-01-22
I am not sure how to make it clearer.

I need the bootloader file that was used to create the original ubuntu-20.04-live-server-amd64.iso.On windows it's included on the dvd. Pretty easy. On Ubuntu not so much.

---

### Post by yancek on 2021-01-22
>  When I use the same procedure for a Window 10 ISO it works just fine. On Windows 10 I am using efisys.bin as bootfile.

The procedure you use for windows is unlikely to work on Linux.   Doubt that efisys.bin will work.  Are you following instructions from a specific web site?  If so, post a link.  I'm not sure you can do this from windows powershell.  I did an online search and everything I found using powershell was to create a bootable windows.

> [COLOR=#000000]Writing the content to a new iso
 Writing the bootloader with a boot file with [/COLOR]efi.img
 

Listing the specific commands you used in the two steps above might help someone to help you.  Also, what did you use to install Grub and also how did you create the iso, what commads.  I've not tried this with windows powershell so doubt I'll be able to help.

---

### Post by hamstermandk on 2021-01-23
I am using this powershell script to create the ISO

[https://gallery.technet.microsoft.com/New-ISOFile-function-a8deeffd](https://gallery.technet.microsoft.com/New-ISOFile-function-a8deeffd)

The script basically takes two inputs a source folder and a bootloader file.
When I use the efi.img bootloeader file from the Ubuntu ISO it does not work as expected.

---

### Post by yancek on 2021-01-23
After reviewing the page  and the script on it which you posted, I don't see any indication that one would expect to be able to use it  for anything other than selected windows versions which are listed at the bottom of the page.  Your unsuccessful efforts would seem to confirm that.  If you are using an Ubuntu install to make your customized iso there are ways to do that.  Do you actually have Ubuntu installed to a hard drive or are you using the iso (extracted and coped)?  If you are just looking for a challenge by using windows powershell, I don't have any ideas or know of any software that would do this.  Good luck.

---

### Post by hamstermandk on 2021-01-23
Thanks a lot yancek - I appreciate your effort.

I will continue to look for a possible way to create the ISO on Windows. I am sure it must be possible :)

---

### Post by yancek on 2021-01-23
>   will continue to look for a possible way to create the ISO on Windows. I am sure it must be possible 

I'm not so sure about that.  Creating an iso on windows or a bootable windows iso isn't difficult.  I did an online search using "how to create a linux iso file on windows 10" and the sites either explained how to create an iso of data, a windows system or the actual reverse, create a windows iso from Linux.  The trick as you have found is not creating the iso but making it bootable and you would need to get Grub or another Linux bootloader in the iso in some manner.  It's difficult enough to boot a Linux system from windows and I'm not sure a windows UEFI system will boot Linux.  I've booted Linux from windows on a Legacy/MBR system that was a pretty convoluted multi-step process.   

I went back through your earlier posts and I see the comment below in your first post.  When you try to boot, what exactly do you see and how are you testing it?  Are you using virtual software such as virtualbox or are you booting it from a USB/DVD?  If you see a grub prompt (grub>) you can get useful information with the command: ls   This should show drive and partitions if you have them.  If you get output from ls, try ls /boot/grub and see if you have any files there.  Should if you created the iso from an installed system.  If it was from an extracted iso, the directories and files will be very different.

>   I have tried using efi.img and that makes it bootable - but into a Grub command line and not starting the normal installer.

If you get this to work, post back as I'm sure others would be interested.  Good luck with it.

---

### Post by hamstermandk on 2021-01-24
It seems I have found a solution.

The thing is when you use the New-IsoFile function the filesystem on the ISO is not compliant with the Ubuntu installation.
By adding this line right after the $Image variable is made it seems to work

$Image.FileSystemsToCreate = 3

[https://docs.microsoft.com/en-us/windows/win32/api/imapi2fs/ne-imapi2fs-fsifilesystems](https://docs.microsoft.com/en-us/windows/win32/api/imapi2fs/ne-imapi2fs-fsifilesystems)

---

