---
title: "Grub-EFI, 2 drives, dual-boot, general confusion"
date: 2015-12-10
forum: Installation &amp; Upgrades
---

### Post by Xpinguin on 2015-12-10
Hello, this is my situation:

drives:
1st: 120 MB SSD, GPT partitioned
-> Windows7 Home Premium x64, System on sda2
2nd: 1 TB HDD, GPT partitioned
-> Xubuntu 14.04 x64, boot on sdb2, root on sdb3

There is a fat32 formatted EFI System Partition on each drive:
sda1 and sdb1.

What I also have to boot with:
1.  4GB flash drive with Live Xubuntu 12.04 (no persistence)
2.  Xubuntu 14.04.2 Installation DVD (used to install my current OS)
3.  Windows7 Installation DVD

I just re-installed Windows7 (UEFI mode, 64bit) on my first drive because it would no longer
boot.  I forget exactly why.  Something about a BIOS update and/or a sequence of procedures
I did to repair Xubuntu 14.04 after trying to install a package from Debian Repos and making
a mess.  Just to be safe I unplugged my HDD (2nd drive) before I installed Windows.

I have spent countless hours researching, trying to learn about the UEFI boot process,
GRUB-2, efibootmgr, cdbedit, rEFit, rEFInd, os-prober, "Boot Repair", CSM/Legacy mode/
functions, NVRAM, chroot, etc.  I tried a bunch of small steps making sure I would not
add to the problem(s), but eventually I gave up (for my first drive), wiped it clean and
managed to re-install Windows and get it to boot.

Now I'm trying to get Linux to boot.  It WAS booting before I re-installed Windows, but no more.
I am quite surprised at this because I even took the precaution of disconnecting my 2nd drive
before re-installing Windows.  So now before I do this I would like to clarify some things.
That's why I'm here.

My motherboard is the GA-Z77X-UD3H rev 1.0.  BIOS ver F18. Its manual is not very verbose
about the various options.  It basically only re-states what is already on the screen.

Windows7 is now booting fine, but for it to work I have to select "Always Allow CSM" instead
of "Never", those are the only two main options in the UEFI screen.  That is clearly NOT what
I would have expected for a UEFI mode OS.  Under that main selection (CSM Support) I have
selected the following:

1. Boot Mode Selection  [UEFI Only]
2. PXE Boot Option Control  [Disabled]
3. Storage Boot Option Control [UEFI First]
4. Display Boot Option Control [UEFI First]

Now, when I want to boot from some REMOVABLE media in UEFI mode I have to change the
setting of "CSM Support" to [Never].  If I don't I get the black screen with message:
 
Windows failed to start...

1. Insert Windows Installation disc and restart ...
2. Chose language ...
3. Select "Repair your computer".

File: \EFI\Microsoft\Boot\BCD Status: 0xc000000d

Info: An error has occurred while attempting to read the boot configuration data.

This is also the result when I try to boot Windows with CSM=Never.

I never got past step 1. because the Windows Install Disc hangs right before the logo gets
formed.   I have tried this more than once, always with the same result.

QUESTION 1: Why is it that I can't just leave everything in UEFI mode (CSM=Never) since I
only have/want UEFI hdd, sdd, flash drive(s), installation CD/DVDs ?  I'm trying to keep
things as simple as possible.

QUESTION 2: 
a) How could my "boot configuration data" be wrong?  I haven't touched
it since installing Windows, haven't used bcdedit.  All I did with Widows is to install the
drivers that were on the motherboard's CD/DVD, and install the Widnows updates.
b) Could it be that simply plugging in my 2nd drive alters something in the boot config.
even if both drives have their own separate ESP?

QUESTION 3: I wanted to include a "bootinfoscript" output here but I think I have to
chroot into my unbootable system in order to provide useful info.  Am I correct in
assuming this ?


Boot Repair output: [http://paste.ubuntu.com/13910976/](http://paste.ubuntu.com/13910976/) 

Thanks in advance for any answers or comments.

---

### Post by oldfred on 2015-12-10
You can run the Boot-Repair report from just about any Linux live installer and post the link to the report.
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

If you changed to boot Windows 7 installer in CSM/BIOS mode it will install in BIOS mode. And if ESP - efi system partition still has the old Windows UEFI boot, it will not work. 
When you disconnect a drive, the UEFI NVRAM entries are erased. But you can use efibootmgr to reinstall grub to UEFI. Boot-Repair on a grub reinstall will also do that as grub on reinstall will also add a new entry to UEFI.
Or if install is UEFI, and system is booting in CSM mode it will not boot correctly.

Windows in UEFI mode must have MBR(msdos) partitions. And Windows in UEFI mode must have gpt partitioned drive. I think Windows 7 default is BIOS, but you copy to flash drive and move around the files required for UEFI boot to make it also an UEFI installer. And then how you boot is how it installs.

---

### Post by Xpinguin on 2015-12-10
Sorry for the delay.  I'm not used to working in a live environment + Internet, reduced access
to lots of my info, passwords, etc.  Plus I'm trying to keep notes about what I do, messages, 
background info, cause I forget stuff like that.  Never was able to make a live usb with "persistence",
but that was back in the Precise days, haven't tried more recently.  Anyway there's the Boot Repair
report.  Thanks for the help.

---

### Post by Xpinguin on 2015-12-10
> **oldfred said:**
> If you changed to boot Windows 7 installer in CSM/BIOS mode it will install in BIOS mode. And if ESP - efi system partition still has the old Windows UEFI boot, it will not work.

I made sure I installed in UEFI mode, and I verified a couple of times just to make sure.  Unless I'm loosing my mind (the longer this thing goes on, the more I think it's possible), everything is UEFI.
That's why I can't understand the option the motherboard is forcing me to use for Windows7.

> **oldfred said:**
> But you can use efibootmgr to reinstall grub to UEFI.

I've done that already.  Can it hurt to do it again?  If you suggest I do it again, do I have to be in chroot environment to do it?  That's how I did it before.

> **oldfred said:**
> Or if install is UEFI, and system is booting in CSM mode it will not boot correctly.

Yes, that's one of the things I've known for a while.  When chosing (forced to) [CSM support: Always], there is a sub option where I have always made sure that UEFI is selected and that the system cannot boot using BIOS/MBR: 

1. Boot Mode Selection: UEFI Only
2. ...
3. ...
4. ...
(see original message, near the middle of it)

I looked in my notes and in the Manual but I can't find the exact wording but essentially there are three (3) other possibilies for this feature: "UEFI First", "Legacy/BIOS First",  "Legacy/BIOS Only".  There may have been a fourth one like "both" but I'm not sure anymore.  Anyway when forced to pick CSM: Always, I made sure every time I selected UEFI Only right underneath it, in the sub-option. 

I've tried to make it as clear as possible in my first message/question. 

The CSM implementation, or at least the way Gigabyte's displays it in the UEFI screen, throws me off completely.  Maybe I should have spent more time searching the web for info on Gigabyte's UEFI implementation.  I don't know.  The problem is from what I've seen it's often difficult to know exactly what the options are on other models, if they are identical to mine or not, and minute details in the terms used can make a big difference.  My own motherboard's manual is pretty but is missing a lot of important info.  Their web site isn't much better.

---

### Post by oldfred on 2015-12-10
I do not see Windows in MBR, so assume it is in UEFI boot mode.
But it normally would have its system reserved before first NTFS partition. Did you manually partition?
You also have Windows boot files in both the sda & sdb ESP - efi system partition.

I have an Asus system and it also has many UEFI settings. I had to change a lot. I did turn off CSM, but kept UEFI only on. And kept secure boot off. Windows 7 will not work with secure boot on anyway. Some UEFI just call UEFI Secure boot Windows mode, but you cannot use that with Windows 7, if yours is that way change to "other".

Some Gigabyte boards have issues with iommu. That also needs changing in UEFI, but that changes how USB ports work not booting.
       Gigabyte GA-X79-UD3 with I7-3820
Needed F6 (BIOS boot) to set ACPI=Off and nomodeset, add to grub if UEFI boot.
Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.
Gigabyte Z97-HD3 Intel Z97 Motherboard
[http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1](http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1)
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU GRUB_CMDLINE_LINUX="iommu=soft"
[http://ubuntuforums.org/showthread.php?t=2292025](http://ubuntuforums.org/showthread.php?t=2292025)

    
You have Windows efi boot files in both ESP. But entry in grub only shows one. My UEFI seems to noy want to let me directly boot from first ESP or sda. I copy files & use efibootmgr to add entries for sdb's ESP but my UEFI does not correctly show them. I have tried several experiments, but none worked yet.

So can you boot Windows directly from UEFI.
Is drive that is sdb, set as first in boot? 
Or have you changed drive order?
Windows just seems to work better if it is on sda. 
And grub just likes to install the ubuntu folder in the sda drive's ESP.

Your grub entry has the UUID for neither of the ESP partitions.
```
 menuentry "Windows UEFI bootmgfw.efi" {
search --fs-uuid --no-floppy --set=root [COLOR=#ff0000]6A2D-CF9D[/COLOR]
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
}
/dev/sda1        [COLOR=#ff0000]33C2-3C9C[/COLOR]                              vfat       EFI_SYSTEM
/dev/sdb1        [COLOR=#ff0000]6047-DBE8[/COLOR]                              vfat       EFI_system

  
```

I think your grub has not been updated since Windows install.
If you can get to grub menu, you can use e for edit can change to one or the other efi partition's UUID.
That will test if Windows boots.

 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

---

### Post by Xpinguin on 2015-12-11
> **oldfred said:**
> But it normally would have its system reserved before first NTFS partition. Did you manually partition?[INDENT]Yes:
part-1: 560 MB, fat32 (for UEFI System Partition)
part-2: 45 GB, ntfs (for Windows System)
part-3: 55 GB, ntfs (for my own files & everything I can move out of C:\ )[/INDENT]

> **oldfred said:**
> You also have Windows boot files in both the sda & sdb ESP - efi system partition.

Yes, that makes sense.  The ones on sda are from the new installation I just made, after deleting all the old partitions and creating the new ones mentioned above.  The ones on sdb are from the old installation.  Both old and new installations on 1st drive (SSD).

> **oldfred said:**
> I have an Asus system and it also has many UEFI settings. I had to change a lot. I did turn off CSM, but kept UEFI only on. And kept secure boot off. Windows 7 will not work with secure boot on anyway. Some UEFI just call UEFI Secure boot Windows mode, but you cannot use that with Windows 7, if yours is that way change to "other".

I have disabled from the start everything that could create conflicts, like Secure Boot, Fast Boot, Intel's Rapid Start Technology.  When I say from the start I mean two years ago, when I first installed Windows7 and then Xubuntu Precise (12.04).  Both were booting fine until about three months ago when I flushed "Precise" (formatted partitions) and replaced it with a fresh "Trusty". And then also I think a BIOS update, and all kinds of problems related to trying to get programs to work properly, installing newer (bug free) versions of a few buggy programs, and generally messing things up by playing with non standard repositories, Debian in particular.  I didn't know better.

> **oldfred said:**
> Some Gigabyte boards have issues with iommu. That also needs changing in UEFI, but that changes how USB ports work not booting.

I haven't seen the term "iommu" in my motherboard's options, and I don't know what it is ... Ok, I just verified with a software search in the online manual and the term is not there, neither is it in the board's specs on the Gigabyte's web page.

 > **oldfred said:**
> Gigabyte GA-X79-UD3 with I7-3820
Needed F6 (BIOS boot) to set ACPI=Off and nomodeset, add to grub if UEFI boot.

Ok, maybe I'll look into that later.

> **oldfred said:**
> Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.
Gigabyte Z97-HD3 Intel Z97 Motherboard
[http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1](http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1)
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU GRUB_CMDLINE_LINUX="iommu=soft"
[http://ubuntuforums.org/showthread.php?t=2292025](http://ubuntuforums.org/showthread.php?t=2292025)

    Well, what you put together above makes it look like "iommu" has something to do with the size of the partition holding the OS installation file(s) or of the usb drive (flash) used to install an OS.  In my case both Windows and Xubuntu were installed via CD/DVD, so I don't think it applies here.

> **oldfred said:**
> So can you boot Windows directly from UEFI.

Yes, I can boot Windows, and I do not see a Grub menu before I do, therefore I think I am booting directly from UEFI.  That's one of the things I'm trying to clarify.

> **oldfred said:**
> Is drive that is sdb, set as first in boot? Or have you changed drive order?

Trying to understand all this stuff I've been constantly changing the boot order.  I am experimenting.  I've been having all kinds of problems booting from usb keys, my keyboard (usb) sometimes not working: F10, F12, Del, End, Esc; depending on various motherboard's options.  At least now I know to keep everything UEFI, or at least try to.  Like I said in my first post, Windows is booting now, since I re-installed it.  It is Xubuntu that is not booting, no matter what options I select.  I was trying to get a clear picture of the situation, and maybe clean things up, BEFORE I try to either FIX or RE-INSTALL Xubuntu.  I just don't want to make things worse.  I think that my motherboard's UEFI implementation, and even more its documentation, or lack thereof, has been making this more laborious than it should be.

> **oldfred said:**
> Windows just seems to work better if it is on sda.

It is.  Has always been on this machine.

> **oldfred said:**
> And grub just likes to install the ubuntu folder in the sda drive's ESP.

AH, AH !  Now that's news to me.  I was not aware of that and it seems a very important fact.  Ok so I don't mean to be facetious but is that just part of Grub's personality or is it the result of a rule, a specification or an algorithm ?  Does anybody know ?

So I guess the thing to do is to put Grub only in sda1 (ESP on 1st drive, Windows' drive) and at boot time chose between:

a) selecting either Windows or Xubuntu in Grub (on sda1)
or
b) selecting either Windows or Xubuntu in UEFI by pressing [Del], no Using Grub at all, delete all its files

I would probably go for a) because I'm pretty certain I will eventually try other Linux distros, but I can't explain why it would be better or necessary to use Grub instead of simply selecting any of a number of OSes directly from the UEFI boot screen.  I haven't found the feature in my mobo's configuration for controlling the time before the default/pre-selected value (OS/boot-manager/chainload) is triggered.  With Grub I think this is easy to set and you can even instruct Grub to do nothing forever, until the user presses a key.  I'm sure there are other more important differences.I did read a couple of papers on not using any boot manager (boot loaders) but they were a bit too much for me.

> **oldfred said:**
> Your grub entry has the UUID for neither of the ESP partitions.
```
 menuentry "Windows UEFI bootmgfw.efi" {
search --fs-uuid --no-floppy --set=root [COLOR=#ff0000]6A2D-CF9D[/COLOR]
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
}
/dev/sda1        [COLOR=#ff0000]33C2-3C9C[/COLOR]                              vfat       EFI_SYSTEM
/dev/sdb1        [COLOR=#ff0000]6047-DBE8[/COLOR]                              vfat       EFI_system


```

I think your grub has not been updated since Windows install.

I just did it very recently, yesterday I think, inside a chroot.  I guess I did something wrong then.

HERE'S AN IMPORTANT QUESTION:  Since I cannot boot into Linux, must I update (or --reinstall?)
Grub in a "chroot" via a live environment ?

> **oldfred said:**
> If you can get to grub menu, you can use e for edit can change to one or the other efi partition's UUID.
That will test if Windows boots.

I haven't seen a Grub menu for a while on this machine.  Maybe after updating or reinstalling Grub
I will.

 > **oldfred said:**
> Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)


Well, oldfred, thank you very much for your help.  I will work with what you gave me.

---

### Post by oldfred on 2015-12-11
If you update UEFI/BIOS from vendor it resets everything back to defaults. With my old BIOS system I ended up taking photos of every screen where I changed settings.
My new Asus posts what I am changing before I press save. And it also allows screenshots but have to have space on flash drive to save them.

Boot-Repair has a full uninstall/reinstall of grub. It needs Internet working as it is downloading anew copy of grub from repository. I have not used it, but I think it walks you thru a chroot.

Some systems do not like to boot the Ubuntu entry. They violate UEFI spec that says not to use description as part of boot. But all motherboards we have seen seem to be ok, but do have lots of settings.

Grub is a boot manager, UEFI is also a boot manager. So you can use either. My UEFI has settings for fast boot on/off and if on a time delay, so I have a chance to press a key to get into UEFI or one time boot key. And I set normal boot after power off, so it always goes thru hardware check & update of devices. But that gives me time to press keys if needed.

---

### Post by Xpinguin on 2015-12-11
Yes, after all I had done not only a Grub Update in chroot, but a "--reinstall".  That was three days ago, definitely AFTER I had reinstalled Windows.  These are the steps I took to get Xubuntu to boot, or at least show up in the Grub menu:

Note:
Windows system:  sda2
          Xubuntu /boot:     sdb2 
          Xubuntu / (root):  sdb3
[SIZE=2]
[/SIZE]
[LIST=1]
[*][SIZE=2]1.```
~$ sudo mount /dev/sdb3 /mnt
~$ sudo mount --bind /dev /mnt/dev
~$ sudo mount --bind /sys /mnt/sys
~$ sudo mount --bind /proc /mnt/proc
~$ sudo mount /dev/sdb2 /mnt/boot
```
[SIZE=2]
[/SIZE]2.```
/# cd /boot/grub
/boot/grub# ls -l
total 2388
drwxr-xr-x 2     root root    4096 Jun 23 12:25 fonts  
-r--r--r-- 1     root root   10114 Dec  2 17:57 grub.cfg  
-rw-r--r-- 1     root root    1024 Dec  2 19:14 grubenv
drwxr-xr-x 2     root root    4096 Nov 18 11:36 locale
-rw-r--r-- 1     root root 2405285 Nov 18 11:36 unicode.pf2 
drwxr-xr-x 2     root root   12288 Nov 18 11:36 x86_64-efi
```

3.```
root@xubuntu:/# dpkg -l | grep grub
  ii  grub-common                     2.02~beta2-9ubuntu1.4  (...)
  ii  grub-efi-amd64                  2.02~beta2-9ubuntu1.4  (...)
  ii  grub-efi-amd64-bin              2.02~beta2-9ubuntu1.4  (...)
  ii  grub-efi-amd64-signed  1.34.5+  2.02~beta2-9ubuntu1.4  (...)
  ii  grub2-common                    2.02~beta2-9ubuntu1.4  (...)
```

4.```
root@xubuntu:/# modprobe efivars
modprobe: ERROR: ../libkmod/libkmod.c:556 kmod_search_moddep() 
could not open moddep file '/lib/modules/3.2.0-85-generic/modules.dep.bin'

``` 
5.
```
root@xubuntu:/# sudo apt-get update
sudo: unable to resolve host xubuntu
(... LONG LIST HERE, NOT USEFUL, LOOKS NORMAL ...)
Fetched 4,537 kB in 25s (180 kB/s)    
Reading package lists... Done

``` 
6.
```
root@xubuntu:/# sudo update-grub
sudo: unable to resolve host xubuntu
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.16.0-55-generic
Found initrd image: /boot/initrd.img-3.16.0-55-generic
Found linux image: /boot/vmlinuz-3.16.0-53-generic
Found initrd image: /boot/initrd.img-3.16.0-53-generic
done

``` 
7.
```
root@xubuntu:/# apt-get install --reinstall grub-efi-amd64
Reading package lists... Done
(... REGULAR STUFF ...)
Preconfiguring packages ...
E: Can not write log (Is /dev/pts mounted?) - openpty (2: No such file or directory)
(Reading database ... 361818 files and directories currently installed.)
Preparing to unpack ...
/grub-efi-amd64_2.02~beta2-9ubuntu1.4_amd64.deb ...
Unpacking grub-efi-amd64 (2.02~beta2-9ubuntu1.4) over (2.02~beta2-9ubuntu1.4) ...
Setting up grub-efi-amd64 (2.02~beta2-9ubuntu1.4) ...
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.16.0-55-generic
Found initrd image: /boot/initrd.img-3.16.0-55-generic
Found linux image: /boot/vmlinuz-3.16.0-53-generic
Found initrd image: /boot/initrd.img-3.16.0-53-generic
done

```
8.
```
root@xubuntu:/# update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.16.0-55-generic
Found initrd image: /boot/initrd.img-3.16.0-55-generic
Found linux image: /boot/vmlinuz-3.16.0-53-generic
Found initrd image: /boot/initrd.img-3.16.0-53-generic
done

```

 I noted three (3) things that seemed irregular, which may be part of my problem, but I would clearly need some confirmation on this:[/SIZE]
[/LIST]
[SIZE=2]A.[/SIZE]
[SIZE=2]modprobe efivars generated an error because (at least partly) it was using/looking at the old kernel from the Live Xubuntu usb Key.  I should have done it after 6. or 7. or 8.   [/SIZE][SIZE=3][SIZE=2]I don't know if it was necessary to do it at all.  The docs I read about it went too much in depth I drowned in it.  All I know is it's for looking at EFI variables.  I don't know what uses them or at what point in the booting process they are read and used.  If someone could shed some light on this, for this particular case, that would be nice.

B.
I don't know what caused the "unable to resolve host xubuntu" in 5. and 6. but it apparently did not prevent the actions to take place and complete.

C.
"E: Can not write log..." in 7., the message is clear, I did not mount [SIZE=2]/dev/pts[/SIZE] at step 1.  I don't think it matters here.  If that log would have been useful someone can say so here.


I know I could just re-install Xubuntu, but I'd rather learn something.  I don't want to just start over every time I have a problem.  In the long run I don't think it would be more productive.

Again please fell free to comment on anything in here.[/SIZE][/SIZE]

---

### Post by oldfred on 2015-12-11
I do not know if any of those issues are vital or not. Since update worked, I do not know why it had issues with it. I think once you have chrooted you do not need sudo, so that may be the one error.

And on my 14.04 trying to list efivars, just does nothing. I thought I saw somewhere the command changed or got moved, but have not used it.
This does show something with my 14.04:
 ls /sys/firmware/efi/vars

I think what is important is that you boot live installer or any repair CD/DVD/flash in UEFI to repair UEFI.

---

### Post by Xpinguin on 2015-12-11
> **oldfred said:**
> I do not know if any of those issues are vital or not. Since update worked, I do not know why it had issues with it. I think once you have chrooted you do not need sudo, so that may be the one error.

Yes, that makes sense...  Once in a while, something does make sense.

> **oldfred said:**
> ls /sys/firmware/efi/vars

Ok, will look at it.

> **oldfred said:**
> 
I think what is important is that you boot live installer or any repair CD/DVD/flash in UEFI to repair UEFI.

Ok, will do.  I'll be back when I get something important.

Thanks again.

---

### Post by Xpinguin on 2015-12-11
From O.P.:

> **Xpinguin said:**
> QUESTION 2:  (near bottom of #1)
a) How could my "boot configuration data" be wrong?  I haven't touched
it since installing Windows, haven't used bcdedit.  All I did with Widows is to install the
drivers that were on the motherboard's CD/DVD, and install the Widnows updates.

I'm sorry while re-reading I just realized the above statement is false: see post #8.
Technically something was not working, and after doing X to it the problem was still
there.  We can't conclude that X had no effect.  It may have compounded the problem.
I doubt it but it's possible.

> **Xpinguin said:**
> 
b) Could it be that simply plugging in my 2nd drive alters something in the boot config.
even if both drives have their own separate ESP?

The question above still holds.  I will do a quick search on the web for this question/answer, and
if I don't find it I will post this as a new question here or in Ask Ubuntu or Supersuer.

---

### Post by oldfred on 2015-12-11
Windows on installs, major updates and with Windows 10 just about anything will update settings in UEFI. 
I think that is why Boot-Repair's suggested fix is to add Ubuntu to Windows BCD, so when Windows resyncs UEFI & BCD, that ubuntu entry can stay.

---

