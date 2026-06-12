---
title: "Problem (Grub ?) installing Ubuntu Studio as 3rd OS"
date: 2021-08-15
forum: Installation &amp; Upgrades
---

### Post by sgalzin on 2021-08-15
Hello,

I have a Dell Inspiron with a number of partitions I do not wish to delete (the original Windows, the recovery partitions and a bunch of things I don't understand, etc.). I have successfully installed, a few months ago, Ubuntu 20.04 on a new partition, and the Grub enabled me to choose between Windows and Ubuntu. I now wish to install Ubuntu Studio 20.04 on a separate partition. I have created an Ext4 partition for that purpose, created a bootable "Live" USB key, and launched the installation from the OS booted on the Live Key.

During the installation process, everything went smoothly, but at the end there was a complaint about not being able to remove a package, I think... It didn't look too serious and the installation said it ended successfully, so I rebooted. A new Grub proposed my previous OSs as well as Ubuntu Studio, but when I tried launching Ubuntu Studio I got the following error:
"file /boot/vmlinuz-5.8.0-43-lowlatency not found". Not being able to solve the problem, I did the installation over, but got that same error message at the end and was again unable to boot.

Looking the error up, it seemed it might be due to a corrupted Grub, so I repaired it using repair-boot. That changed the Grub once again (in terms of looks), but did not solve the problem itself. NB: at that point, I could still boot my previous installations of Windows and Ubuntu. I then proceeded to following the advice from [another thread]("https://askubuntu.com/questions/1199168/grub-error-during-update-syntax-errors-are-detected-in-generated-grub-config-fi") and did "sudo apt-get purge grub-pc grub-common" followed by "sudo apt-get install grub-common grub-pc". Unfortunately, only the first portion worked so I am unsure what the actual status of the Grub is now (I am writing this before a reboot). I tried boot-repair again, but now it fails wit similar errors to what I got during the end of the install process:
```
Adding boot menu entry for UEFI Firmware Settings
error: syntax error.
error: Incorrect command.
error: syntax error.
Syntax error at line 162
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 1
dpkg: error processing package linux-image-5.8.0-43-lowlatency (--remove):
 installed linux-image-5.8.0-43-lowlatency package post-removal script subprocess returned error exit status 1
dpkg: too many errors, stopping
Errors were encountered while processing:
 linux-image-5.8.0-43-lowlatency
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Thanks for any pointers / help, much appreciated if you can help me figure this out!

---

### Post by sgalzin on 2021-08-15
So somewhat miraculously I am able to boot into all 3 OSs now, but the  one I just installed is giving me this error. Not sure if I should start  a new thread since this error is the one I got during installation and  does seem related to my Grub issues from earlier. At boot, an error  window pops up stating "Package operation failed - The installation or  removal of a software package failed." I looked this up and saw the  following [promising thread]("https://askubuntu.com/questions/517857/dpkg-error-processing-package-linux-image-generic-configure-dependency-pro"), hence I tried:
```

sudo apt --fix-broken install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  libreoffice-help-common
The following packages will be REMOVED:
  linux-image-5.8.0-43-lowlatency
The following packages will be upgraded:
  libreoffice-help-common
1 upgraded, 0 newly installed, 1 to remove and 291 not upgraded.
3 not fully installed or removed.
Need to get 0 B/2,355 kB of archives.
After this operation, 982 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 409812 files and directories currently installed.)
Removing linux-image-5.8.0-43-lowlatency (5.8.0-43.49~20.04.1) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-5.8.0-43-lowlatency
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Script `/boot/grub/grub.cfg.new' contains no commands and will do nothing
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 1
dpkg: error processing package linux-image-5.8.0-43-lowlatency (--remove):
 installed linux-image-5.8.0-43-lowlatency package post-removal script subproces
s returned error exit status 1
dpkg: too many errors, stopping
Errors were encountered while processing:
 linux-image-5.8.0-43-lowlatency
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I feel like I am making progress, but not in any deterministic fashion...

---

### Post by sgalzin on 2021-08-15
The situation seems to be the following:
[LIST]
[*]I have 2 different grubs installed: the "old" one from my remaining Ubuntu installation, and the "new" one from Ubuntu Studio.
[*]The new one enables me to launch Windows and Ubuntu, but fails to launch Ubuntu Studio
[*]By doing some attempts at fixing, it turns out I somehow reactivated  the Old grub yesterday: this enabled me to launch all 3 OSs, but when  launching Ubuntu Studio the system failed doing any updates / complained  about Grub
[*]Further attempts today seem to have reactivated the new  Grub, and I still cannot launch Ubuntu Studio from it, though luckily I  can get back to my old Ubuntu...
[/LIST]

One of the problems seems to be in grub:
> Ensure that there are no errors in /etc/default/grub and /etc/grub.d/* 

I looked at the default which seems fine (though I do not know what I'm looking for exactly, it is a short file and no obvious errors stick out). The ones in grub.d/* however are another story: I focused on the one which seems to be associated with the new Ubuntu Studio, but I cannot understand that file, it is quite complex (463 lines...)

Here is the default/grub file which looks OK to me:
```
search.fs_uuid 45e30f03-199f-4956-9501-35ee14755a13 root 
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg
```

And here is a pastebin to the low-latency (the one for Ubuntu Studio, I believe) grub file:
[https://pastebin.com/zmAxsLyX](https://pastebin.com/zmAxsLyX)

---

### Post by yancek on 2021-08-15
> search.fs_uuid 45e30f03-199f-4956-9501-35ee14755a13 root
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg  

The above is a grub.cfg file from your EFI partition.  On a standard Ubuntu instasll, this Grub file would be in /boot/efi/EFI/ubuntu.
If you have both Ubuntu and Ubuntu Studio installed, you should have an entry for both Ubuntu and Ubuntu Studio.  Does Ubuntu Studio create a separate directory in the /boot/efi/EFI directory for itself?

In the grub.cfg file shown above, there is a UUID.  Run the sudo blkid command from a terminal and it will tell you which partition it is pointing to and that partition will have the main grub.cfg files which has all your menuentries.  Also look at the /boot/efi/EFI for directories for both Ubuntu and Ubuntu Studio.

---

### Post by sgalzin on 2021-08-15
In parallel (before seeing the above answer by yancek), I ran boot-repair from a live key and it reinstalled my "old" grub, but with a new entry for Ubuntu Studio. This entry for Ubuntu Studio now works, though an error is reported immediately after logging in (I cannot seem to be able to find the details of the error, I can simply report it without but cannot see the details). Here is the [pastebin for my boot-repair]("https://paste.ubuntu.com/p/QfVFWzq4H3/").

Using Ubuntu Studio, I checked the following to answer yancek's questions:
> **yancek said:**
> Does Ubuntu Studio create a separate directory in the /boot/efi/EFI directory for itself?
It appears not to have created a specific directory for Ubuntu Studio in /boot/efi/EFI:
```
ls /boot/efi/EFI
Boot  dell  Microsoft  ubuntu

```

> **yancek said:**
> Run the sudo blkid command from a terminal and it will tell you which partition it is pointing to
In this case, I get two different results whether I boot into Ubuntu or Ubuntu Studio:
[LIST]
[*]Ubuntu: /dev/nvme0n1p5: UUID="45e30f03-199f-4956-9501-35ee14755a13" TYPE="ext4" PARTUUID="f4ba07f7-0cb0-403e-8893-a4a37795f46f" 
[*]Ubuntu Studio: /dev/nvme0n1p6: UUID="ca17ab3c-82f2-4804-934e-94e684038d5c" TYPE="ext4" PARTUUID="f0250101-fcb6-449a-9830-f68a182a04d6" 
[/LIST]
 
So at this point, it looks as though I can actually boot into Ubuntu Studio, but I am wary that I got there the wrong way and messed things up somehow, hence the errors. When I log into Ubuntu Studio, a short while after login I get "System program problem detected" error which says: Do you want to report the problem now? "cancel" / "Report problem...". Clicking Report seems to do nothing and I cannot get any details on the error...

After that, running apt --fix-broken [aborts as in my earlier attempt]("https://ubuntuforums.org/showthread.php?t=2465919&p=14053714#post14053714") :(

---

### Post by oldfred on 2021-08-15
Do not install grub-pc, that is the version for older BIOS systems. You have UEFI, so use grub-efi-amd64 version.

Ubuntu only installs one UEFI boot entry and one /EFI/ubuntu folder with one grub.cfg which is the 3 line configfile entry to load the full grub.cfg from last install. That install then should offer to boot other installs in same UEFI boot mode.  It will be last install, or if you have other Ubuntu installs & they do a major grub update, the /EFI/ubuntu/grub.cfg may be reset to that version. You can edit  UUID back or reinstall grub from your preferred default boot version. I have multiple installs & have to edit configfile entry regularly to have UUID of my default system.

I once got the grub.cfg.new file. That was from a typo in my 40_custom, but could be an edit error in /etc/default/grub also. In my case it was difficult to find error as it said it was on last line, but actually was a missing } in the middle of my 40_custom boot stanzas. A full reinstall of grub will also fix that, but then you lose any custom changes you have made.

---

### Post by sgalzin on 2021-08-15
> You have UEFI, so use grub-efi-amd64 version.

Unfortunately no dice:
```
sudo apt-get install grub-efi-amd64
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  grub-efi-amd64-bin libreoffice-help-common
Recommended packages:
  grub-efi-amd64-signed
The following packages will be REMOVED:
  grub-gfxpayload-lists grub-pc linux-image-5.8.0-43-lowlatency
The following NEW packages will be installed:
  grub-efi-amd64
The following packages will be upgraded:
  grub-efi-amd64-bin libreoffice-help-common
2 upgraded, 1 newly installed, 3 to remove and 1281 not upgraded.
3 not fully installed or removed.
Need to get 0 B/3,500 kB of archives.
After this operation, 3,456 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Preconfiguring packages ...
(Reading database ... 409812 files and directories currently installed.)
Removing linux-image-5.8.0-43-lowlatency (5.8.0-43.49~20.04.1) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-5.8.0-43-lowlatency
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Script `/boot/grub/grub.cfg.new' contains no commands and will do nothing
Syntax errors are detected in generated GRUB config file.
Ensure that there are no errors in /etc/default/grub
and /etc/grub.d/* files or please file a bug report with
/boot/grub/grub.cfg.new file attached.
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 1
dpkg: error processing package linux-image-5.8.0-43-lowlatency (--remove):
 installed linux-image-5.8.0-43-lowlatency package post-removal script subprocess returned error exit status 1
dpkg: too many errors, stopping
Errors were encountered while processing:
 linux-image-5.8.0-43-lowlatency
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by oldfred on 2021-08-15
> Script `/boot/grub/grub.cfg.new' contains no commands and will do nothing

If it is totally reinstalling grub, you should have a new /etc/default/grub and new folder with grub scripts in /etc/grub.d.

When you ran Boot-Repair which did a UEFI reinstall of grub,  it said this:
Installation finished. No error reported.

But your grub menu seems to have many entries in p5 install, lines 302 and up.
Do you have lots of old kernels?

Boot-Repair typically defaults to first install it sees.
If you want to repair p6 install, you have to use advanced mode & choose p6 partition's install.

---

### Post by sgalzin on 2021-08-15
> **oldfred said:**
> If it is totally reinstalling grub, you should have a new /etc/default/grub and new folder with grub scripts in /etc/grub.d.v
I'm confused. You are correct, the default grub has now changed (still looks clean, but is a bit longer). However I no longer have all the files I used to have /etc/default/grub.d folder ?!? I only have init-selec.cfg, which only contains a few comment lines ... Am I perhaps giving out different bits of info depending on whether I boot in Ubuntu vs Ubuntu Studio ? This is currently in Studio...
  
[QUOTE=oldfred;14053789]But your grub menu seems to have many entries in p5 install, lines 302 and up.
Do you have lots of old kernels?
Not voluntarily, no. My only explanation for all these duplicate lines would be all the attempts I've been making at reinstalling grub or using boot-repair?


> **oldfred said:**
>  Boot-Repair typically defaults to first install it sees.
If you want to repair p6 install, you have to use advanced mode & choose p6 partition's install.
I tried booting on a live-usb key to boot-repair on p6, and it failed. The only way I can get it to work is by doing the default repair. When I do "advanced repair" and select the partition p6, I end up having to copy paste instructions from boot-repair to the command line, and the first command fails due to dpkg not being able to perform its duties (too many errors, etc. as pasted above).

---

### Post by sgalzin on 2021-08-15
So I found some instructions on how to clean up all those kernels and decided I had messed things up enough to warrant a clean reinstall (of the new OS, keeping my existing Windows and Ubuntu intact). So I erased the partition p6 (Ubuntu Studio), updated Grub, used boot-repair (just to be safe), and then ran this bunch of commands (from [this thread]("https://askubuntu.com/questions/176322/removing-old-kernel-entries-in-grub")) to rid the system of any unused kernels:
```
sudo apt-get purge $( dpkg --list | grep -P -o "linux-image-\d\S+" | grep -v $(uname -r | grep -P -o ".+\d") )
```

The things I am changing for this installation are:
1. creating a logical partition rather than a primary one (from what I've read, this does not matter much)
2. for the "device for boot loader installation", I now choose the newly created partition p6 rather than the root of the disk.

Unfortunately, at the end of the install, I again get this error: "Error removing linux-image-5.8.0-43-lowlatency - installed linux-image-5.8.0-43-lowlatency package post-removal script subprocess returned error exit status 1", followed by "error while removing packages: E: Sub-process /usr/bin/dpkg returned an error code (1). The following packages are in a broken state: [<empty list>] This may be due to an old installer image, etc..."

And after this clean reinstall, I get my new Grub from Ubuntu Studio with all 3 options (Windows, Ubuntu, Ubuntu Studio), but starting the latter I again get "error: file /boot/vmlinuz-5.8.0-43-lowlatency not found" ... argh this is so frustrating! Could it be my USB key which is bad? The check at launch of the Live states all checks are OK....

---

### Post by oldfred on 2021-08-15
with gpt partitioning which is required for Windows in UEFI boot mode, there are no logical partitions.
I hope that choosing logical would not convert drive to old MBR configuration as that would break Windows.

For install of boot loader you always choose a drive like sda, not a partition like sda2. Or if NVMe you still choose the nmve0n1.
And with UEFI, it really does not matter as the selection does not work. It just defaults to installing grub to first drive's ESP - efi system partition.

Issue seems to be with low-latency kernel & grub used with that install.
Not familiar with Ubuntu Studio.

Have you tried with the newest version? 21.04
We do normally suggest the LTS and I see you seem to want the same version as your regular Ubuntu. But it may be worth the experiment to see it another version works.

---

### Post by sgalzin on 2021-08-15
Actually I do not mind having a different version of Ubuntu Studio vs Ubuntu, the thing is though that I've read several complaints about the latest version and some people who seem to have expertise advising against it. That being said, this is going to be my next try I think. Or perhaps 20.10...

---

### Post by sgalzin on 2021-08-15
Ok, problem solved. It seems that, for my Dell Inspiron, Ubuntu Studio 20.04 installation does not work well. I just tried 20.10 and it all went smoothly. Thank you both so much for helping out / giving me some advice. I can't say I understood everything going on under the hood but you both definitely helped me understand a bit more about the process :)

---

