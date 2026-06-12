---
title: "Troubleshoot auto boot after using boot-repair"
date: 2015-08-24
forum: Installation &amp; Upgrades
---

### Post by Alfonce_Derp on 2015-08-24
Hi everyone,

I've been having many difficulties to get an ubuntu 15.04 working on my dell xps 13 2015.
During the process I may have "broken" my grub, but thanks to a live cd and boot-repair, I now have a functional ubuntu.

But when I boot it goes to the "splash" page (GNU grub ubuntu page) where I can select booting on ubuntu, advanced options, and so on...
I would like my computer to automatically boot on ubuntu, as it has usually be performed when I received it (ubuntu 14.04)

---

### Post by oldfred on 2015-08-24
If you are not getting a normal shut down, then grub sees a flag & boots to grub menu so you can see if you need to use recovery mode or not.

I do not know details any more but post this:
cat /etc/default/grub

I prefer to have grub show, just in case, but I set it to 3 sec so it is not there for long.

---

### Post by Alfonce_Derp on 2015-08-25
Hi again,

Here is the output of the command-line **cat /etc/default/grub**

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

I have another little question, I have tried to reinstall my ubuntu with a manual partitioning, 
And after the installation, I have faced with the same problem I described in my previous post, my computer couldn't resolve how to boot. Did I miss something during the installation, grub is already present in /boot so if I select from the ubuntu partition tool installer the format ESP it should work, shoudn't it ? 
I went to the live CD again and run the boot-repair tool in order to boot from my new installation.

Here is a screenshot from the installer, and how I manage partitioning :

[IMG]https://scontent-fra3-1.xx.fbcdn.net/hphotos-xlp1/v/t34.0-12/11938912_10153561687864464_1476338427_n.jpg?oh=54853ab8283922b1a281127696425905&oe=55DE6092[/IMG]

And here is my schema after running boot-repair and booting from my new ubuntu:

```
Disk /dev/sda: 238,5 GiB, 256060514304 bytes, 500118192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 41757CE6-3C78-45CF-9D61-F0CC246E4E7E

Device         Start       End  Sectors  Size Type
/dev/sda1       2048   1050623  1048576  512M EFI System
/dev/sda2    1050624  30347263 29296640   14G Linux filesystem
/dev/sda3   30347264  88940543 58593280   28G Linux filesystem
/dev/sda4   88940544 104564735 15624192  7,5G Linux filesystem
/dev/sda5  104564736 120188927 15624192  7,5G Linux filesystem
/dev/sda6  120188928 136189951 16001024  7,6G Linux swap

```

Thanks in advance.

---

### Post by oldfred on 2015-08-25
I do not recommend separate system partition like /boot, /var or even /tmp. I consider /home worthwhile for a newer user, but more advanced users may be better with a /mnt/data partition which is what I and many others use.

Boot-Repair will work with a separate /boot, but not with the other system partition. Any chroot requires them to be mounted.

It looks like you have an UEFI system as the sda1 is the ESP - efi system partition. But you still specify grub to be installed into sda and it is smart enough to install the efi boot files into the ESP.

You should then be booting installer in UEFI mode not BIOS mode.

If you only have Ubuntu, you should not normally be getting grub menu. Again is it not shutting down correctly?

---

### Post by Alfonce_Derp on 2015-08-26
At the moment, there is only ubuntu but the space I let free would be use for another linux in the future. But only with ubuntu installed and the partitionning you've seen I can't get into booting without the boot-repair.
About the ESP, I think during my first unsuccessful installation I have wiped out my entire hard drive, so I thought I had to create another ESP. I also always boot in UEFI mode, but nothing shows up as bootable (until I run the boot-repair).

Thank you for the link, I will try some of these procedures today.

---

### Post by Bucky Ball on 2015-08-26
I suggest starting a new thread regarding the second issue. It has nothing to do with the first and the title of this thread and that can only get confusing and lessen your chances of support, although you are in good hands with that issue with oldfred. Sure he'll follow. :) 

I would normally move your second issue to its own thread myself, but as the two are in the same post a bit tricky. Good luck.

---

### Post by oldfred on 2015-08-26
When you say you cannot boot without Boot-Repair what are you doing? Do you have to use Boot-Repair to repair it every time, and then when you boot it works, but then does not work next time? That may just be going into UEFI and setting ubuntu entry as default.

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

    I just changed this from 10 to 3 in /etc/default/grub, so menu does not show for long. But still gives me enough time to press escape to get to menu. If later dual booting you will need to get to menu anyway.
GRUB_TIMEOUT=3

And if later using another Linux, a shared data partition lets you have data available for both systems. I originally had XP & Ubuntu and a shared NTFS for photos, and profiles for Firefox & Thunderbird. Then I added a shared ext4 partition. Now retired NTFS shared as no more XP.

If UEFI booting you do have to have the ESP, but only one per device. I believe UEFI spec says you can have more than one, but yet to see a system that will work with more than one. Some laptops have a second FAT32 with efi files from vendor. But it is not flagged as Boot, so not sure if they then change flag or can just use them when you want vendor recovery or other features that are unique to that vendor's pc.

---

### Post by Alfonce_Derp on 2015-08-26
Before running boot-repair, my computer in legacy or UEFI mode didn't see anything he could boot on. After boot-repair, my ubuntu works "fine" he can now boot every time without any trouble with the grub installed by the boot-repair (i guess).
But if I understood what you said I would not be able to run with the grub installed from the boot-repair, another linux instance. 
Futhermore, I would like to understand how to create and manage ESP correctly without every time I want to format, the need of running the boot-repair..

Thanks you so far for your help and advices about partitioning oldfred.

---

### Post by oldfred on 2015-08-26
You should not need Boot-Repair normally. I do run it just to document my system. Or run the bootinfoscript which is really part of the Summary report that is command line only.

I backup efi partition separately.
I run 14.04 as my main working install. And in fstab it mounts the efi partition with defaults. But newer versions are now mounting with 0077 which is read only. And just changing it to defaults in fstab and remounting did not work. I had to reboot, then I could edit efi partition from inside my install. Otherwise you now have to edit from a live installer or other install.

The installer should be adding an ubuntu entry into UEFI boot. And you may have to go into UEFI and choose that and make it first or default boot entry, even though installer should have made it first. Sometimes a reboot or two reset UEFI entries?

---

### Post by Alfonce_Derp on 2015-08-26
I don't know how but I finally made a ubuntu without any boot-repair, he boots directly on it. I don't know if it is due to the fact that I have flash my BIOS to the last update found on dell website. 
I have made my partition schema looks like the older one without /home, /var and /tmp.

Thanks again

---

### Post by Bucky Ball on 2015-08-26
Excellent news. Enjoy and thanks for marking as solved. :)

---

