---
title: "out of room in /boot, 13.10 upgrade"
date: 2013-11-10
forum: Installation &amp; Upgrades
---

### Post by Norrolith on 2013-11-10
I am trying to uppgrade my 13.04 install to 13.10
but whenever I try do-release-upgrade
I get a lot of scrolling text(normal)
I get a reminder about thirdparty packages
and then I get this.

Calculating the changes

Calculating the changes

Not enough free disk space 

The upgrade has aborted. The upgrade needs a total of 54.8 M free 
space on disk '/boot'. Please free at least an additional 18.4 M of 
disk space on '/boot'. Empty your trash and remove temporary packages 
of former installations using 'sudo apt-get clean'. 


Restoring original system state

Aborting
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
Building data structures... Done 
enduser@Phoenix:~$ ^C
enduser@Phoenix:~$ 

And it goes no farther.
any ideas?
I did install from a live usb on a blank system.

---

### Post by Bucky Ball on 2013-11-10
This:

> The upgrade has aborted. The upgrade needs a total of 54.8 M free
space on disk '/boot'. Please free at least an additional 18.4 M of
disk space on '/boot'. Empty your trash and remove temporary packages
of former installations using 'sudo apt-get clean'.

Empty trash, clear some of the old things out of /boot.

---

### Post by Petro Dawg on 2013-11-10
have you run ```
 sudo apt-get clean 
```?

---

### Post by Norrolith on 2013-11-10
Sorry I did not mention that I had used the sudo apt-get clean
I can find the boot folder and I have no idea what is neccessary in it and what is not.
Looking in the folder I have.
A grub folder.
several versions of abi-3.8.0-[ranges from 19 to 32]-generic.
initrd.img-3.8.0-[varies]-generic
memtest86+.bin
memtest86+_multiboot.bin
config-3.8.0-[varies]-generic
System.map-3.8.0[varies]-generic
vmlinuz-3.8.0-[varies]-generic

---

### Post by ajgreeny on 2013-11-10
can you show us the output of command **df -h** please which will show your mounted partitions and how much space is being used in them all.

---

### Post by Norrolith on 2013-11-10
enduser@Phoenix:~$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root  909G  220G  643G  26% /
none                         4.0K     0  4.0K   0% /sys/fs/cgroup
udev                         3.9G   12K  3.9G   1% /dev
tmpfs                        795M  2.1M  793M   1% /run
none                         5.0M     0  5.0M   0% /run/lock
none                         3.9G  812K  3.9G   1% /run/shm
none                         100M   68K  100M   1% /run/user
/dev/sda1                    228M  181M   35M  84% /boot
/dev/sdb1                     29G   16G   14G  55% /media/enduser/B52C-C294
/dev/sdc1                     30G  9.3G   21G  32% /media/enduser/USB DISK
enduser@Phoenix:~$

---

### Post by SeijiSensei on 2013-11-10
Running "sudo apt-get autoremove" often cleans out older kernels and frees up space in /boot.  Give that a try.

---

### Post by ajgreeny on 2013-11-10
You have a separate /boot partition which is too small for the number of kernels you have installed and I don't think autoremove removes older kernels, I'm afraid.  A separate /boot partition is not normally recommended on a desktop machine, partly for the reason you have just seen, ie, it is too easy to run out of space, but if you make sure you only keep two kernels you should be fine until you next install the system, at which point I suggest you get rid of the /boot partition and leave it in / as is more normal.

I always remove extra kernels with synaptic, which you may have to install. I then search for the kernel numbers that are installed with command ```
grep "menuentry " /boot/grub/grub.cfg | cut -c 1-100
``` and remove all except the two most recent; autoremove will then remove the unneeded header packages related to your now removed kernel versions.

---

### Post by Norrolith on 2013-11-10
So I would enter
 	Code:

 	grep "menuentry " /boot/grub/grub.cfg | cut -c 1-100
in a terminal?
I am not finding a codebox in synaptic.

---

### Post by hamishmb on 2013-11-10
I'd agree with ajgreeny: You've got a lot of old kernels in /boot. Make sure you remove them with either synaptic, or ubuntu tweak (or something similar), just make sure you don't remove the current running kernel!

---

### Post by Norrolith on 2013-11-10
> **hamishmb said:**
> I'd agree with ajgreeny: You've got a lot of old kernels in /boot. Make sure you remove them with either synaptic, or ubuntu tweak (or something similar), just make sure you don't remove the current running kernel!

I agree that would not end well.
but how do I tell which one is the currently running one?
the file with the highest number? what?

---

### Post by Petro Dawg on 2013-11-10
run...

```
uname -a
```

in terminal to see which you are currently running.  You should see something like "3.5.0-42-generic" in the output, which is the kernel version number.

---

### Post by Norrolith on 2013-11-10
SO it is safe to delete any files in there that don't have 3.8.0-31-generic at the end of their titles?

---

### Post by Dennis N on 2013-11-10
> **Norrolith said:**
> I agree that would not end well.
but how do I tell which one is the currently running one?
the file with the highest number? what?

To remove unneeded kernels and headers, try the easy method described here using Synaptic Package Manager:

[http://liam-on-linux.livejournal.com/20347.html](http://liam-on-linux.livejournal.com/20347.html)

---

### Post by Dennis N on 2013-11-10
There can be more than three packages to remove for each kernel. In the attachment, they are sorted by installed version after sorting by installed status, and there are four packages for each kernel. The top four are for the current kernel. Usually you keep one more set of 4, and can remove the rest.

---

### Post by Norrolith on 2013-11-10
The guide seems out of date i can't follow using the version of synaptic I have installed.
you ninja'ed me checking if it makes sense now.

---

### Post by Norrolith on 2013-11-10
Okay, Dawg's command tells me I am using3.8.0-31
but synaptic puts 3.8.0-32.47 at the top of it's list.
could it be that I have partial packages from the aborted installs?

---

### Post by ajgreeny on 2013-11-10
> **Norrolith said:**
> So I would enter
     Code:

     grep "menuentry " /boot/grub/grub.cfg | cut -c 1-100
in a terminal?
I am not finding a codebox in synaptic.

Sorry if I confused you.

That command is entered in a terminal and the output shows a list of all kernels installed, all of which except the top two in the list can be removed.  You will be running the top listed kernel by default, but check with command **uname -a** as suggested by Petro Dawg.

---

### Post by Petro Dawg on 2013-11-10
Either way you should be safe deleting anything than ends in -30 or less.

---

### Post by Norrolith on 2013-11-10
they seem to be dissagreeing

enduser@Phoenix:~$ uname -a
Linux Phoenix 3.8.0-31-generic #46-Ubuntu SMP Tue Sep 10 20:03:44 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
enduser@Phoenix:~$ grep "menuentry " /boot/grub/grub.cfg | cut -c 1-100
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnu
    menuentry 'Ubuntu, with Linux 3.8.0-32-generic' --class ubuntu --class gnu-linux --class gnu --clas
    menuentry 'Ubuntu, with Linux 3.8.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux --
    menuentry 'Ubuntu, with Linux 3.8.0-31-generic' --class ubuntu --class gnu-linux --class gnu --clas
    menuentry 'Ubuntu, with Linux 3.8.0-31-generic (recovery mode)' --class ubuntu --class gnu-linux --
    menuentry 'Ubuntu, with Linux 3.8.0-30-generic' --class ubuntu --class gnu-linux --class gnu --clas
    menuentry 'Ubuntu, with Linux 3.8.0-30-generic (recovery mode)' --class ubuntu --class gnu-linux --
    menuentry 'Ubuntu, with Linux 3.8.0-27-generic' --class ubuntu --class gnu-linux --class gnu --clas
    menuentry 'Ubuntu, with Linux 3.8.0-27-generic (recovery mode)' --class ubuntu --class gnu-linux --
    menuentry 'Ubuntu, with Linux 3.8.0-26-generic' --class ubuntu --class gnu-linux --class gnu --clas
    menuentry 'Ubuntu, with Linux 3.8.0-26-generic (recovery mode)' --class ubuntu --class gnu-linux --
    menuentry 'Ubuntu, with Linux 3.8.0-25-generic' --class ubuntu --class gnu-linux --class gnu --clas
    menuentry 'Ubuntu, with Linux 3.8.0-25-generic (recovery mode)' --class ubuntu --class gnu-linux --
    menuentry 'Ubuntu, with Linux 3.8.0-19-generic' --class ubuntu --class gnu-linux --class gnu --clas
    menuentry 'Ubuntu, with Linux 3.8.0-19-generic (recovery mode)' --class ubuntu --class gnu-linux --
menuentry "Memory test (memtest86+)" {
menuentry "Memory test (memtest86+, serial console 115200)" {

---

### Post by Dennis N on 2013-11-10
> **Norrolith said:**
> The guide seems out of date i can't follow using the version of synaptic I have installed.
you ninja'ed me checking if it makes sense now.

My output is from Xubuntu 12.10. I also have 13.10 installed and it is exactly the same procedure for both.

---

### Post by Norrolith on 2013-11-10
the picture cleared the procedure up for me.
except every technique you guys suggest gives contradictory results.
uname -a gives  3.8.0-_31_-generic
ajgreeny gives me
enduser@Phoenix:~$ grep "menuentry " /boot/grub/grub.cfg | cut -c 1-100
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnu
    menuentry 'Ubuntu, with Linux 3.8.0-32-generic' --class ubuntu --class gnu-linux --class gnu --clas
    menuentry 'Ubuntu, with Linux 3.8.0-32-generic (recovery mode)' --class 
which is 3.8.0-_32_
synaptic tell me I am running _32.47_
This is all very confusing.
unless anybody screams stop, I will delete all my under 20's
edit: I have one under twenty, make that all my under 25's

---

### Post by Petro Dawg on 2013-11-10
Pause!!!  oh, I mean STOP!!!

I was just thinking, do you only have 1 Linux Distro Installed?   If so, you can go ahead. Otherwise if you are dual booting Ubuntu and Xubuntu, or Lubuntu or something you might have other linux kernels being used by them.

---

### Post by Norrolith on 2013-11-10
It should be only Ubuntu.
while trying to make it boot, we tried a bunch of stuff but Ubuntu 13.04 was what eventually ran.

---

### Post by Petro Dawg on 2013-11-10
Then you should be ok deleting anything under -30 then.

---

### Post by Norrolith on 2013-11-10
Okay, then.
here we go.
(if you don't here back from me. I lived a full life with no regrets)

---

### Post by Dennis N on 2013-11-10
This may explain:

**uname -a** gives the kernel you are using now.

```
dn@Sydney:~$ uname -a
Linux Sydney 3.5.0-43-generic #66-Ubuntu SMP Wed Oct 23 17:33:43 UTC 2013 i686 athlon i686 GNU/Linux

```

But, my attachment shows latest installed version as 3.5.0-43.66 from Synaptic.  The 66 is a minor revision number and that is never included with uname output. The 'package' column of Synaptic  shows 3.5.0-43 which does agree with uname -a. 

Also, if you just installed a kernel, uname will not give the newly installed kernel number until you reboot and it is in use.

---

### Post by Norrolith on 2013-11-11
Okay, the advice worked to a point.
I deleted two old kernels. and the upgrade ran for a long time.
until it gave a fatal error message, and some paths to error logs.
unfortunately launching firefox caused a boatload of new messages to float by.
I went to find the files myself and discovered that I can't launch my file browser.
I can launch software center, and apport has a new blue splatter logo. my dash has the question mark icon.
any ideas?

---

### Post by Petro Dawg on 2013-11-11
In my honest opinion, since you are having upgrading issues I would recommend backing up your home folder data and just doing a fresh install of 13.10 instead of trying the update route.  I find dealing with just 1 partition for both home and root is less problematic, and I don't mind doing the fresh installs, they typically are less of a hassle in the long run.  

Taking from what I've seen posted on the forums before, I too am thoroughly amazed that upgrades from old Ubuntu versions to new Ubuntu versions work at all, ever.

---

### Post by Norrolith on 2013-11-11
How would I go about setting up a clean install?
I had my stuff backed up from the very start of this.

---

### Post by Bucky Ball on 2013-11-11
Download the ISO, make a disk, boot from it, install.

---

### Post by ajgreeny on 2013-11-11
And _do not_ use a separate /boot partition this time; it is not normally needed and can, as you've seen, cause more problems for you, particularly when using a desktop system as opposed to a server install.

---

### Post by Norrolith on 2013-11-11
I had to boot from a usb last time. and I still can't launch my file browser.
It had repeatedly failed to boot from disk, repeatedly over the course of several days.
I am unsure how I got the separate boot partition. Where in the install process does it ask me whether I want it?
(I did partition off a segment in case Ubuntu didn't work for me so I could install windows in parallel. is that the cause of separate boot partition?)

---

### Post by ajgreeny on 2013-11-11
> **Norrolith said:**
> I had to boot from a usb last time. and I still can't launch my file browser.
It had repeatedly failed to boot from disk, repeatedly over the course of several days.
I am unsure how I got the separate boot partition. Where in the install process does it ask me whether I want it?
(I did partition off a segment in case Ubuntu didn't work for me so I could install windows in parallel. is that the cause of separate boot partition?)

No, I don't see how that would make a separate /boot partition, which I think you must have manually made at some point, as somehow or other it was made and then the mountpoint was chosen.

As far as I'm aware there is no way for a separate /boot partition to be made by the system without any personal input from you as you install.

---

### Post by Bucky Ball on 2013-11-12
> **ajgreeny said:**
> 
As far as I'm aware there is no way for a separate /boot partition to be made by the system without any personal input from you as you install.

No, not aware that it can. The /boot partition, though, is needed for UEFI boots or some form of boot I'm not familiar with as far as I know. I noticed oldfred discussing it in a thread the other day. Perhaps that is why it's there. Get into the BIOS and check the details of how the machine is booting (look for EFI and other boot options) and that might job the memory. 

Windows 8? Think Ubuntu needs a boot partition to trick it into letting it install.

---

### Post by ajgreeny on 2013-11-12
> **Bucky Ball said:**
> No, not aware that it can. The /boot partition, though, is needed for UEFI boots or some form of boot I'm not familiar with as far as I know. I noticed oldfred discussing it in a thread the other day. Perhaps that is why it's there. Get into the BIOS and check the details of how the machine is booting (look for EFI and other boot options) and that might job the memory. 

Windows 8? Think Ubuntu needs a boot partition to trick it into letting it install.

Perhaps you are right.  This is info I gleaned from an oldfred post; he knows a lot more about grub/boot/UEFI etc than I have ever known or am likely to know, so may thanks to odfred!  Some of this is a bit old now and things are moving very fast in UEFI so treat with a little caution and be prepared to make changes.  However, the BIOS_boot partition mentioned here is not the same as a normal /boot partition as it does not contain all the kernels, just grub itself, which requires a very tiny space.
                                             
> Some more info on bios_grub gpt partition, since it is gpt it can be anywhere on drive:[INDENT] 
grub2 & GPT info
[http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition)
[http://kubuntuforums.net/forums/inde...opic=3106368.0]("http://kubuntuforums.net/forums/index.php?topic=3106368.0")
In a GPT partition map, the 31 kiB area after Master Boot Record where  GRUB is usually embedded to, does not exist. When GRUB can't be  embedded, its only option is to use blocklists, which are unreliable and  discouraged.

If you have gpt you need another small (8-32mb) partition for grub. Are you using efi or BIOS compatible mode?
[http://grub.enbug.org/BIOS_Boot_Partition](http://grub.enbug.org/BIOS_Boot_Partition)
"unknown" filesystem! may be shown
However, in the GPT setup, there is no space following the 512-byte MBR  for embedding the "second stage" core.img. Thus, you must make a  separate "BIOS boot partition" to hold core.img. Make it 128 kiB as  recommended in the following link. Actually, using ext2 for example, and  GParted Live CD, the minimum partition size is 8 MB, or 32 MB for  FAT32. You can set bios_grub flag in gparted or with command line: In  GPT fdisk (gdisk), give it a type code of EF02.
sudo parted /dev/sda set <partition_number> bios_grub on

It only needs to be about 32 KiB in size, although in most cases make it 1 MiB because of partition alignment issues

This link says they just installed grub2 to the drive and it found the BIOS boot partition.
[http://www.mail-archive.com/grub-dev.../msg12109.html]("http://www.mail-archive.com/grub-devel@gnu.org/msg12109.html")
Legacy BIOS issues with gpt
[http://www.rodsbooks.com/gdisk/bios.html](http://www.rodsbooks.com/gdisk/bios.html)                         
[/INDENT]
[INDENT]
[/INDENT]
>                     
                                       
             [INDENT][COLOR=Navy]For info on UEFI boot install & repair:
[/COLOR] [http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

[/INDENT]
 

---

### Post by Norrolith on 2013-11-13
Okay guys,
need help again. I got my ubuntu file downloaded, and I open up brasero, put a blank dvd in.
and I get this.
[IMG]http://i.imgur.com/TG3AH3r.png[/IMG]
I want to know what people think these windows are, and what buttons I should press.
I admit I don't want to have to go through downloading It again on a different computer.

---

### Post by ajgreeny on 2013-11-13
First thing to do is check the md5sum of your downloaded .iso file against the list at [UbuntuHashes - MD5sum]("https://help.ubuntu.com/community/UbuntuHashes")

If it does not match exactly you will have to download again; if it does match, I have no idea what is going on, unless you have some sort of graphics display glitch.

---

### Post by Petro Dawg on 2013-11-13
Not sure what is going on with your Brasero burner program, perhaps try downloading and using the K3b disk burner to make the disk.

---

### Post by SeijiSensei on 2013-11-13
> I don't think autoremove removes older kernels, I'm afraid.

Running apt-get today resulted in this suggestion:

The following packages were automatically installed and are no longer required:
  linux-image-3.8.0-30-generic linux-image-extra-3.8.0-30-generic
Use 'apt-get autoremove' to remove them.

---

### Post by Norrolith on 2013-11-14
I think its a graphics glitch related to the partial install, Like I said, it not the only glitch my dash home is now the unknown program icon.
and Apport got a new image. I think that right now, a bunch of the file replaces during the OS upgrade wasn't undone  when the upgrade crashed.

---

### Post by ajgreeny on 2013-11-14
> **SeijiSensei said:**
> Running apt-get today resulted in this suggestion:

The following packages were automatically installed and are no longer required:
  linux-image-3.8.0-30-generic linux-image-extra-3.8.0-30-generic
Use 'apt-get autoremove' to remove them.

That's a new one for me to see; perhaps it's a change with the newer versions of apt-get in *ubuntu 12.10 and later as I have never seen apt-get autoremove managing to remove old kernels.

I would be interested to see your current full list of installed kernels.

---

### Post by SeijiSensei on 2013-11-14
After I ran autoremove I was left with 3-11.0-12.  I don't have any other kernels on this system.

Personally I would prefer that only the (n-2)th and older kernels be automatically removed, leaving the current and one prior kernel in /boot in case of emergencies.

---

### Post by Norrolith on 2013-11-17
Okay, every one problems over as far as I can tell.
I rebooted after making a bootable usb on a different machine.
and when I cam back up I had some initial weird stuff, and I had to reset my display.
but I am now in 13.10, as far as I can tell.
uname -a doesn't say 13.10 anywhere but my boot screen did, I can launch files,
and My error messages show 13.10(yay?)
thank you all for your help and goodnight.

---

### Post by ajgreeny on 2013-11-18
```
lsb_release -dc
``` will tell you exactly what version you're running.

---

