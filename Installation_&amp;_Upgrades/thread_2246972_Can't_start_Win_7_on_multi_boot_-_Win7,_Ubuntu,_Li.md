---
title: "Can't start Win 7 on multi boot - Win7, Ubuntu, Linux Mint"
date: 2014-10-04
forum: Installation &amp; Upgrades
---

### Post by parker-hugh on 2014-10-04
Can't start Windows 7 on multi boot menu, with Ubuntu 14.04.1 and Linux Mint 17 Cinnamon (all 64-bit)

Sony Vaio VGN-AW11Z-B laptop

I've had this problem for a few days now, posted on linuxmint forums but can't get a solution...

I installed windows 7 on a new SSD 224GB, Used 61GB for Windows and created extended partition on the remaining space.

then I installed Ubuntu on part of the extended partition.

Boot menu shows both Ubuntu and Windows 7 and dual boot working fine.

then I installed Linux Mint directly after Ubuntu on same extended partition.

Boot menu now shows Ubuntu, Linux Mint and Windows 7.

I can boot into either Ubuntu or Linux Mint and works fine, but now I can't boot into Windows 7 even though it is shown on the boot menu.

My question is how can I fix this without re-installing everything from the start.

I tried to update grub from Ubuntu with following command....

sudo update-grub

but still can't boot windows 7, not sure if this was a good move to be honest. I'm a bit of a novice on Linux to be honest.

the output from update-grub terminal window is below....

```
hugh@SONY-VAIO-UBUNTU:~$ sudo update-grub
[sudo] password for hugh:
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-36-generic
Found initrd image: /boot/initrd.img-3.13.0-36-generic
Found linux image: /boot/vmlinuz-3.13.0-35-generic
Found initrd image: /boot/initrd.img-3.13.0-35-generic
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
Found Linux Mint 17 Qiana (17) on /dev/sda8
done
hugh@SONY-VAIO-UBUNTU:~$
```

this is what my disk looks like....

```
    
Partition     File System   Mount Point      Label              Size    Flag   Comments
    /dev/sda1     ntfs                       System Reserved    100MB   boot   Windows
    /dev/sda2     ntfs                                           61GB          Windows 7
    /dev/sda3     extended                                       52GB
      /dev/sda5   linux-swap                                    4.8GB          Ubuntu
      /dev/sda6   ext4          /                               7.5GB          Ubuntu
      /dev/sda7   ext4          /home                          15.9GB          Ubuntu
      /dev/sda8   ext4                                          7.5GB          Linux Mint
      /dev/sda9   ext4                                         15.9GB          Linux Mint
    unallocated   unallocated                                   110GB

```



Any help would be appreciated. I am fairly new to linux but I can use the terminal window if I know where to go to fix it. I have done a multi-boot before and didn't have a problem.

Someone suggested that I run the following code in the Ubuntu OS ...

sudo grub-install /dev/sda

output is shown below...

```
hugh@SONY-VAIO-UBUNTU:~$ sudo grub-install /dev/sda
    [sudo] password for hugh:
    Installing for i386-pc platform.
    Installation finished. No error reported.
    hugh@SONY-VAIO-UBUNTU:~$ 
```

I rebooted but still have a problem with Windows 7, it still appears on the boot menu but can't boot into it. I can still boot into both Ubuntu and Linux Mint as before.

I also found this possibility....

[ password for hugh: Generating grub configuration file ... Found linux image: /boot/vmlinuz-3.13.0-36-generic Found initrd image: /boot/initrd.img-3.13.0-36-generic Found linux image: /boot/vmlinuz-3.13.0-35-generic Found initrd image: /boot/initrd.img-3.13.0-35-generic Found linux image: /boot/vmlinuz-3.13.0-32-generic Found initrd image: /boot/initrd.img-3.13.0-32-generic Found memtest86+ image: /boot/memtest86+.elf Found memtest86+ image: /boot/memtest86+.bin Found Windows 7 (loader) on /dev/sda1 Found Linux Mint 17 Qiana (17) on /dev/sda8 done hugh@SONY-VAIO-UBUNTU:~$this is what my disk looks like....Code: Select all Partition File System Mount Point LabelSizeFlagComments /dev/sda1 ntfs System Reserved100MB bootWindows /dev/sda2 ntfs 61GB Windows 7 /dev/sda3 extended 52GB /dev/sda5 linux-swap4.8GB Ubuntu /dev/sda6 ext4/ 7.5GB Ubuntu /dev/sda7 ext4/home15.9GB Ubuntu /dev/sda8 ext47.5GB Linux Mint /dev/sda9 ext4 15.9GB Linux Mint unallocated unallocated 110GBAny help would be appreciated. I am fairly new to linux but I can use the terminal window if I know where to go to fix it. I have done a multi-boot before and didn't have a problem.Someone suggested that I run the following code in the Ubuntu OS ...sudo grub-install /dev/sdaoutput is shown below...Code: Select all hugh@SONY-VAIO-UBUNTU:~$ sudo grub-install /dev/sda [sudo] password for hugh: Installing for i386-pc platform. Installation finished. No error reported. hugh@SONY-VAIO-UBUNTU:~$ I rebooted but still have a problem with Windows 7, it still appears on the boot menu but can't boot into it. I can still boot into both Ubuntu and Linux Mint as before.I also found this possibility....[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)It's called Boot-Repair. Would this be worth a try, also which operating system would I be best to install it to, 1st (Ubuntu) or 2nd (Linux Mint)?I don't want to do it without some guidance as it may make matters worse.Hugh"]https://help.ubuntu.com/community/Boot-Repair]("http://Can't start Windows 7 on multi boot menu, with Ubuntu 14.04.1 and Linux Mint 17 Cinnamon (all 64-bit)Sony Vaio VGN-AW11Z-B laptopI've had this problem for a few days now, posted on linuxmint forums but can't get a solution...I installed windows 7 on a new SSD 224GB, Used 61GB for Windows and created extended partition on the remaining space.then I installed Ubuntu on part of the extended partition.Boot menu shows both Ubuntu and Windows 7 and dual boot working fine.then I installed Linux Mint directly after Ubuntu on same extended partition.Boot menu now shows Ubuntu, Linux Mint and Windows 7.I can boot into either Ubuntu or Linux Mint and works fine, but now I can't boot into Windows 7 even though it is shown on the boot menu.My question is how can I fix this without re-installing everything from the start.I tried to update grub from Ubuntu with following command....sudo update-grubbut still can't boot windows 7, not sure if this was a good move to be honest. I'm a bit of a novice on Linux to be honest.the output from update-grub terminal window is below....hugh@SONY-VAIO-UBUNTU:~$ sudo update-grub [sudo)

It's called Boot-Repair. Would this be worth a try, also which operating system would I be best to install it to, 1st (Ubuntu) or 2nd (Linux Mint)?

I don't want to do it without some guidance as it may make matters worse.

Hugh

---

### Post by Dennis N on 2014-10-04
After running **sudo grub-install /dev/sda**, you need to run **sudo update-grub**

---

### Post by oldfred on 2014-10-04
Both versions of your Linux will install grub by default into the MBR and both will keep settings that when grub has a major update, it will reinstall to MBR. So you need to keep track of which install's grub is in MBR and is the one you are booting. And then you may have to run sudo update-grub in both installs to resync updates and make sure the booting one has the newest kernels from the non-booting one.
Or it can get confusing.

Windows issue sounds separate. Grub only boots Working Windows and it it has boot stanza it at least sees the bootmgr & BCD Windows boot files. You may need to run chkdsk from your Windows repair disk. Boot-Repair can only do minor fixes to Windows like install a Windows boot loader. 

You may need to temporarily install the Windows boot loader and see if f8 gets you to a repair console and run chkdsk until no errors or make other fixes.
If you installed grub into either Windows partition that is a major issue. 

Best to run just the summary report from Boot-Repair so we can see details. Post link it provides.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

      
 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

      
 Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by parker-hugh on 2014-10-05
Thanks oldfred for your reply to my problem. and the links. I tried running following on Ubuntu ...

```
sudo grub-install /dev/sda

sudo update-grub
```


but didn't make any difference, so I ran it again in Linux Mint but still can't boot Windows

I used one of the links which you gave me in your post and it suggested to boot from Winndows 7 disk and try to fix Windows bootloader ....

[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

I first tried repair, but nothing to repair, so I opened command prompt and entered the following....


    ```
bootrec.exe /fixboot                                   # The operation completed successfully.

bootrec.exe /fixmbr                                      # The operation completed successfully.
```


I rebooted and now boots directly into Windows 7. Which is great. But no options for Ubuntu or Linux Mint. I guess the grub menu was over written by Windows.

What is the best method get back the original grub menu? Is it ok to boot from a Ubuntu live CD and open a terminal and run the following commands....

```
sudo grub-install /dev/sda

sudo update-grub
```


Q1. Would this bring back the original boot menu with Ubuntu, Linux Mint and Windows 7 choices?

Or

Q2. Is it best to use the "Boot-Repair" live CD?

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I haven't used it before so would you recommend I use the default settings and go with the "Recommended Repair"?

here is the default settings....

```
Main options
       Reinstall GRUB
       Unhide boot menu: 10 seconds

    GRUB location
       OS to boot by default:  sdb6 (Ubuntu 14.04.1 LTS)                                         # this is my dev/sda6 partition for Ubuntu
       Place GRUB in all disks (except USB disks without OS)

    Other options
       Place the boot flag on:  sdc5                                                               # this is a separate HDD on my laptop used only for Data
       Repair Windows boot files
       Create a Bootinfo summary (to get help by email or forum)
       Participate to statistices of use
       Check internet connection
```


I decided to click "Create a BootInfo Summary", this is what was displayed....

Please write on a paper the following URL:
[http://paste.ubuntu.com/8499706/](http://paste.ubuntu.com/8499706/)
In case you still experience boot problem, indicate this URL to:
[EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL] or to your favorite support forum.

Can you advise which of above two methods is best going forward? Q1 or Q2. thanks again for your help.

P.S. The default settings for boot-repair "GRUB location" suggested "OS to boot by default: sdb6 (Ubuntu 14.04.1 LTS)" It counted the live USB as disk "a" so this is my /dev/sda6 Ubuntu "/" partition so I understand this.

But "Other options" suggest "Place the boot flag on: sdc5" I don't understand what this means as this is a separate HDD on my laptop used only for Data, i.e. it is not bootable as far as I know.

---

### Post by oldfred on 2014-10-05
From a live installer you cannot just do the same commands, you have to mount partition (and separate /boot if you have that and any other sytem partitions except /home) and then install grub or do a full chroot CHange ROOT where you are using the working kernel from the live installer, but change to be the system on the hard drive so all updates are run on installed system. Boot-Repair pretty much automates all that but you do need to choose correct install and correct MBR if you have multiple installs or multiple drives. Do not run auto fix in those cases as it just installs grub everywhere which most do not want.

Only Windows requires a boot flag, grub does not use it. But a few BIOS only boot if a boot flag is on a primary partition. Boot-Repair must see you do not have a boot flag and wants to add it, but better to be on a primary partition.

It looks like you have a system that promotes the flash drive to sda. That often creates issues as grub's default install is sda. You need to keep boot flag on sdb1 or the Windows boot partition.

When booting did you leave flash drive installed and boot from the hard drive or sdb?
Windows configuration does look correct, perhaps the fixes you ran worked and after booting into Linux another sudo update-grub will find it. If not we can manually add aboot stanza.

I would run Boot-Repair. But choose which system you will use the most so it is first in boot menu, other will then be last along with Windows in menu. And do not choose to install grub to all drives. You should use advanced mode, choose an operating system and choose a location or MBR of sdb.

Manual install from Live installer, you really should only need two of the commands, change sda5 in examples to sdb6 if you want Ubuntu first in menu or sdb8 if you want Mint first and change install command to sdb:
 #Comments are anything after the #, enter commands in terminal session
#Install MBR from liveCD/DVD/USB, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5, run next two commands with correct partition and drive
sudo mount /dev/[COLOR=#ff0000]sda5[/COLOR] /mnt
sudo grub-install --root-directory=/mnt/ /dev/[COLOR=#ff0000]sda[/COLOR]
#  The above command should work but they now suggest this command for grub 1.99 with Natty 11.04 or later - uses boot not root.:
sudo grub-install --boot-directory=/mnt/boot /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

---

### Post by parker-hugh on 2014-10-05
Thanks oldfred for your feedback. I wasn't confident about executing the Boot-Repair from live USB. I had some questions in my mind, and one of the default parameters I thought was a bit strange. 

```

Main options 
    Reinstall GRUB = enabled 
    Restore MBR    = NOT enabled      # should this be enabled? 
    Unhide boot menu: 10 seconds 
    Repair file systems: NOT enabled  # should this be enabled? 
 
GRUB location 
    OS to boot by default:  sdb6 (Ubuntu 14.04.1 LTS) # this is my dev/sda6 partition for Ubuntu 
    Separate /boot partition = NOT enabled 
     Place GRUB in all disks = NOT enabled, I changed this and selected option below 
     Place GRUB into = sdb          # this is where Windows, Ubuntu and Mint are located 
 
    GRUB options 
    there are 7 options here and all are not enabled by default 
 
Other options 
    Place the boot flag on:  sdc5        # this is a separate HDD on my laptop used only for Data. 
                                                     # it is formatted NTFS but I never boot from it. 
                                                     # I am not able to change sdc5 to another value. 
                                                     # I don't understand why this is selected. 
    Repair Windows boot files = enabled 
    Create a Bootinfo summary (to get help by email or forum) = enabled 
    Participate to statistices of use = enabled 
    Check internet connection = enabled

```
 
I was a bit unsure about the "Other options" "Place the boot flag on: sdc5" see my comments above. I wasn't confident this was correct, and for some reason I couldn't change it. Only this value sdc5 was allowed. Any idea why this drive was defaulted and no other was available?

So I decided against Boot-Repair for that reason.

Instead, I thought your suggestion about booting Ubuntu from a live USB and entering commands via terminal window.

My main hard drive was showing again as sdb (and not sda, due to my live USB being assigned sda first)

# Check linux partitions, change partition letters accordingly... 
 
```
sudo fdisk -l     
 
sudo mount /dev/sdb6 /mnt    # I chose sdb6 where my Ubuntu OS "/" is installed 
 
sudo grub-install --root-directory=/mnt/ /dev/sdb    # I chose sdb 
 
# The above command should work but they now suggest this command for grub 1.99 with Natty 11.04 or later - uses boot not root.: 
 
sudo grub-install --boot-directory=/mnt/boot /dev/sdb 
 
#If that returns any errors run: 
 
sudo grub-install --recheck --root-directory=/mnt/ /dev/sdb 
 
# If no errors on previous commands reboot into working system and run this: 
 
sudo update-grub 

```

.......output of terminal 

```
mint@mint ~ $ sudo mount /dev/sdb6 /mnt

mint@mint ~ $ sudo grub-install --root-directory=/mnt/ /dev/sdb
grub-probe: error: failed to get canonical path of `/cow'.
Installing for i386-pc platform.
Installation finished. No error reported.

mint@mint ~ $ sudo grub-install --recheck --root-directory=/mnt/ /dev/sdb
grub-probe: error: failed to get canonical path of `/cow'.
Installing for i386-pc platform.
Installation finished. No error reported.

mint@mint ~ $ sudo update-grub
/usr/sbin/grub-probe: error: failed to get canonical path of `/cow'.
mint@mint ~ $ 
```

............ 

Everything is working now even though there was an error as indicated above.  I can now boot into Windows 7, Ubuntu and Linux Mint. I'm very pleased with the result.

Important Note, when I entered..
sudo grub-install --root-directory=/mnt/ /dev/sdb 
You mentioned they now suggest this command for grub 1.99 with Natty 11.04 or later - uses boot not root.:
then I should run...
sudo grub-install --boot-directory=/mnt/boot /dev/sdb

but I forgot to do this, is this something I need do now within the Ubuntu OS? Or is it best to leave it as it's working ok for all three operating systems.

Thanks again for your help on this, it is much appreciated.

Hugh

I booted into the Boot-Repair live USB and clicked "Create a BootInfo Summary" again as it would be different now after the above changes...

Please write on a paper the following URL:
[http://paste.ubuntu.com/8502453/](http://paste.ubuntu.com/8502453/)
In case you still experience boot problem, indicate this URL to:
[EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL] or to your favorite support forum.

The contents are a bit technical for me but I though you might like to see it for information.

---

### Post by oldfred on 2014-10-05
If it is working you should be ok. 

The other option for newer grub was a suggestion only if first option did not work.

Not sure about the /cow error. Not seen that on a grub reinstall. But have seen that in trying to run a grub install from live installer without mounting partition so it tries to reinstall grub to non-existing MBR on DVD or to flash drive.

Not sure why Boot-Repair suggested sdb5. Must be where it saw an install. But boot flag really only applied to Windows and must be on a primary partition. Only with the older Lilo boot loader would that possible be correct. So leave boot flag where it is on NTFS partition.

With several installs and drives, I regularly run the summary report just to document system.

 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

---

