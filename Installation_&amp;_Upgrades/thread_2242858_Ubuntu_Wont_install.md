---
title: "Ubuntu Wont install"
date: 2014-09-04
forum: Installation &amp; Upgrades
---

### Post by josh84 on 2014-09-04
I am using a live usb and am Installing Ubuntu on a machine. I want it to be the only OS. There are no other OS's. After installing and rebooting it will not boot it says there is no media... I have tried reinstalling multiple times and also using the boot repair from a live version of Ubuntu and no dice. It is set to boot to hard drive first as its priority, I literally have a blank canvas and I just want Ubuntu to install..

Here is my boot summary help link from Ubuntu.. Any help is appreciated.


[http://paste.ubuntu.com/8242138/](http://paste.ubuntu.com/8242138/)

Best,

J

---

### Post by TheFu on 2014-09-04
So - it appears that your system is using UEFI. I think that is the key to solving the problem.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) may help.

I don't have any UEFI systems - sorry.

Way at the bottom of that other link, is a link here: [http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported) with very detailed help.

---

### Post by yancek on 2014-09-04
You have the FAT32 partition (sda1) which is shown as EFI System Partition but none of the necessary files are there.  I don't use UEFI either so reviewing the link posted above would be a good place to start until someone else familiar with UEFI comes along.

---

### Post by josh84 on 2014-09-04
I have tried the basic 1-6 steps but have had no luck.

---

### Post by christopher9 on 2014-09-04
What machine ?  Is UEFI boot option being used ? 
Does the 'Try Without Installing" option work ?

---

### Post by josh84 on 2014-09-04
> **christopher9 said:**
> What machine ?  Is UEFI boot option being used ? 
Does the 'Try Without Installing" option work ?



This is on a laptop. I can go to a try without stalling option but all of the boot repair does not work once I can get in and do it. I have tried going over the boot repair and re-install over 10 times. What is the plain and simple way to install Ubuntu and just Ubuntu on a laptop without the boot. Is there a special process you can link me to? I have never had any issues like this in the past installing Ubuntu on machines. Its a Toshiba laptop, its fairly new.. the live works great but the installs never work and will not boot even if i select the HD it just doesnt find the media .....

---

### Post by Dennis N on 2014-09-04
I installed Ubuntu in UEFI mode on a new hard disk (no Windows OS present) about two weeks ago. I followed the steps in this outline:

[http://ubuntuforums.org/showthread.php?t=1958383&p=11906060#post11906060](http://ubuntuforums.org/showthread.php?t=1958383&p=11906060#post11906060)

Since you say you have a "blank slate", maybe that guide will help. I installed Ubuntu with secure boot enabled and it zipped through the install with no problem.

Note:
I left out the 1mb sector in step 6d, that is set with the "bios_grub" flag in 6f. If needed, I can add it later.

---

### Post by fantab on 2014-09-04
Run boot-repair and go to 'Advanced' settings and choose grub location as 'separate EFI partition' or something of that sort.

---

### Post by christopher9 on 2014-09-04
If you use the USB "Try without installing" option, you can use the Software Center to install Gparted.  You can Gparted to completely delete all the partitions previously created.  You want all the disc space unallocated. Then restart, boot the USB distro and install on a clean HDD.  I have bricked my laptop (Toshiba P-50A) more times than I can count doing Ubuntu installs and this method has always produced a clean install. HTH

---

### Post by josh84 on 2014-09-04
> **christopher9 said:**
> If you use the USB "Try without installing" option, you can use the Software Center to install Gparted.  You can Gparted to completely delete all the partitions previously created.  You want all the disc space unallocated. Then restart, boot the USB distro and install on a clean HDD.  I have bricked my laptop (Toshiba P-50A) more times than I can count doing Ubuntu installs and this method has always produced a clean install. HTH


I tried that and I could delete all but the swap partition that was 8gb and then I tried reinstalling afterwards... no dice just says checking media presence - no media present then reboot or select proper boot device.

Nevermind I got it to delete just had to modify the flag.

:(

---

### Post by josh84 on 2014-09-04
I am currently following this guide and havent had any trouble with them... currently installing fingers crossed... I think specifying the boot partition at step 9 will be key here. We shall see thx for all the help so far guys its very appreciated.

[COLOR=#000000]Here are the Steps I took which have worked. They are similar to the original poster's. You will find screenshots on previous entries I made in this thread.[/COLOR]
[COLOR=#000000]1. Downloaded 12.04 ISO from Ubuntu[/COLOR]
[COLOR=#000000]2. Created bootable USB key using Ubuntu [/COLOR][http://www.ubuntu.com/download/help/...re-you-install]("http://www.ubuntu.com/download/help/try-ubuntu-before-you-install")
[COLOR=#000000]3. Using USB key I booted my computer into Ubuntu Live and selected try Ubuntu[/COLOR]
[COLOR=#000000]4. Selected GParted from Dash and opened it[/COLOR]
[COLOR=#000000]5. Clicked on my SSD drive which was shown as unallocated Space[/COLOR]
[COLOR=#000000]6. Created 5 partitions and one allocated space as so[/COLOR]
[COLOR=#000000]a) First I formatted the drive to GPT[/COLOR]
[COLOR=#000000](Device -> Create Partition Table... -> GPT)[/COLOR]
[COLOR=#000000]b) Right clicked on Unallocated space and chose "new"Then I created a 250 MB FAT 32 partition and labelled it EFI[/COLOR]
[COLOR=#000000]c) I created a 1 MB partition that I left unformatted[/COLOR]
[COLOR=#000000]d) I created and lableled / and HOME partitions and formatted them EXT 4 (32 GB and 40 GB) and labelled them[/COLOR]
[COLOR=#000000]e) I created a 2 GB SWAP and Formatted it LINUX-SWAP[/COLOR]
[COLOR=#000000]f) right clicked on EFI (and 1 MB) partitions and chose Manage Flags for each. I chose boot flag for EFI and bios_grub flag for the 1 MB unformatted partition.[/COLOR]
[COLOR=#000000]7. I rebooted the computer and went into UEFI and set the boot priority to USB 2.0 UEFI as the second choice after the hard drive and exited and saved.[/COLOR]
[COLOR=#000000]8. I then started my install. I chose to install manually -I think it is called "Or Something Else" .Most of the rest is fairly straight forward but I got hung up at the partition table. You have to set the root partition and home partition up. double click on each of these and it will give the option to select / for ROOT from the drop down list or /Home for each. These should be set as EXT 4 partitions.[/COLOR]
[COLOR=#000000]9. Before preceeding choose the bootloader on the bottom of that window to your EFI partition.[/COLOR]
[COLOR=#000000]10. Also I didn't mention this but on an earlier install screen the option to download updates and install 3rd party software is given. I checked these[/COLOR]

[COLOR=#000000]I have to admit that without OldFRed's and Niglas's help I would have been lost[/COLOR]

---

### Post by josh84 on 2014-09-04
Did everything above and it seems to have maybe booted on the first try... it still gave the error message about the media... It is set to boot to HD first... but It booted here on the first go but after a restart it will not boot at all.... I made sure that it is set to boot to the disk first.. So it worked for a few seconds and upon reboot its broken and I cant get back... is the latest version of Ubuntu broken?

Why the hell would it work once but then not again.. 

At this point It would seem there is no solution.

Will any version of Linux work on a UEFI machine..

---

### Post by Dennis N on 2014-09-04
To be clear, the bootloader is installed to the partition you labeled EFI in step 6b. It's going to be sda1 when you follow those steps in order.

---

### Post by josh84 on 2014-09-04
Yep, boot flag for EFI and its 250mb Fat partition.   sda1. I specified this. Did not work. It said checking for media... booted once and I restarted and I am in this terrible loop again.

---

### Post by Dennis N on 2014-09-04
> **josh84 said:**
> Did everything above and it seems to have maybe booted on the first try... it still gave the error message about the media... It is set to boot to HD first... but It booted here on the first go but after a restart it will not boot at all.... I made sure that it is set to boot to the disk first.. So it worked for a few seconds and upon reboot its broken and I cant get back... is the latest version of Ubuntu broken?

Are you selecting the boot choice in the UEFI boot menu? Maybe it is going to another option like the legacy bios option. My boot menu has a number of options, some which don't work. Ubuntu in the mode it was installed should be the top choice in the UEFI boot menu.

---

### Post by josh84 on 2014-09-04
> **fantab said:**
> Run boot-repair and go to 'Advanced' settings and choose grub location as 'separate EFI partition' or something of that sort.

Does not resolve the issue but thanks for suggesting.

---

### Post by josh84 on 2014-09-04
> **Dennis N said:**
> Are you selecting the boot choice in the UEFI boot menu? Maybe it is going to another option like the legacy bios option. My boot menu has a number of options, some which don't work. Ubuntu in the mode it was installed should be the top choice in the UEFI boot menu.


The priority is to boot harddisk first... I have that set.. I can also manually restart and tell it to boot to the hard disk... no dice.. What other options should I be looking for here? It is a Toshiba Satellite S50

Secure boot is disabled... Fast boot Disabled... tried switching these off and on and every which way.. nothing.. 

Should I change the boot mode from UEFI to CSM?

Nevermind its still the same crap telling me to insert boot media...

---

### Post by Dennis N on 2014-09-04
Secure boot should make no difference. Ubuntu is installed in UEFI mode with a signed kernel that will boot with Secure Boot enabled. Mine has Secure Boot enabled no problem. You installed in UEFI mode, so it is not going to boot in any other mode. Try all the options in the UEFI boot menu - in mine, it is not clear how each behaves - - some have identical descriptions! Right now, my menu shows 8 boot choices. I need to take a digital photo to show them. If I don't press F8 on boot up, it automatically boots to the first option without showing any menu - this directly starts Ubuntu since there is only one OS. I can get the grub menu by interrupting that process.

---

### Post by josh84 on 2014-09-04
> **Dennis N said:**
> Secure boot should make no difference. Ubuntu is installed in UEFI mode with a signed kernel that will boot with Secure Boot enabled. Mine has Secure Boot enabled no problem. You installed in UEFI mode, so it is not going to boot in any other mode. Try all the options in the UEFI boot menu - in mine, it is not clear how each behaves - - some have identical descriptions! Right now, my menu shows 8 boot choices. I need to take a digital photo to show them. If I don't press F8 on boot up, it automatically boots to the first option without showing any menu - this directly starts Ubuntu since there is only one OS. I can get the grub menu by interrupting that process.


Guess u are lucky... I am gonna probably flash the BIOS. Or use Fedora

---

### Post by Dennis N on 2014-09-04
This is the Asus boot menu (see attached image). I don't mess with the choices, since the top one has always been the right one. I once tried one of the identical "ubuntu" options just to see, and it failed to boot.

---

### Post by Dennis N on 2014-09-04
Sorry I can't say much more since I am new to UEFI myself, and my total experience right now is one system. I have been doing some reading to learn more. This is a good place to begin:

[http://www.rodsbooks.com/linux-uefi/](http://www.rodsbooks.com/linux-uefi/)

There are more references to related topics throughout the page, and at the bottom of that page.

---

### Post by Dennis N on 2014-09-04
Just thinking you might have better luck with the rEFInd boot manager than grub2. I have no personal experience, but have read some articles about it and some say it solves their boot problems. It installs itself into the UEFI boot menu on top so it gets booted first, then it boots your OS in turn. Do some research and learn more.

[http://www.rodsbooks.com/refind/getting.html](http://www.rodsbooks.com/refind/getting.html)

---

### Post by christopher9 on 2014-09-04
You would be better off to start the install with a completely blank unformatted unallocated HDD like I suggested....the install will  create the correct partitions for the OS without the need for all those other steps...

---

### Post by josh84 on 2014-09-04
> **christopher9 said:**
> You would be better off to start the install with a completely blank unformatted unallocated HDD like I suggested....the install will  create the correct partitions for the OS without the need for all those other steps...

Already tried thanks.

I completely formatted the drive left unallocated - reinstall - nothing
Same as above and made the filetable gpt and reinstall - nothing

Its something with BIOS or firmware perhaps.. I also tried installing other grubs.. nothing yet but still persistent.

---

### Post by josh84 on 2014-09-04
Currently,

[URL="http://paste.ubuntu.com/8255452/"]
http://paste.ubuntu.com/8255452/[/URL]

help?

---

### Post by fantab on 2014-09-04
> **josh84 said:**
> Does not resolve the issue but thanks for suggesting.

Post the Bootinfo Summary url here.

---

### Post by Dennis N on 2014-09-05
Hello josh84, I notice from your boot info script that you don't have a signed kernel. See line 264:

```
linux	/boot/[COLOR="#FF0000"]vmlinuz-3.13.0-32-generic[/COLOR] root=UUID=81b5ad4b-8a69-434b-b6bb-d305a37985a0 ro  quiet splash $vt_handoff
```

Mine looks like this:

```
linux	/boot/[COLOR="#FF0000"]vmlinuz-3.13.0-34-generic.efi.signed[/COLOR] root=UUID=297ecb14-ecb9-4ddb-8331-0f6c6cb9342f ro  quiet splash $vt_handoff
```

What does that mean? For one thing, you can't boot with secure boot enabled. How did that happen? Maybe because the installation media wasn't booted in secure boot mode?

Also I notice that my system has both kernels installed - signed and unsigned. So in the boot menu, that accounts for all the entries I see in my UEFI boot menu (see post #20) as it also has the old kernels on the menu. But they certainly are not well identified. It also accounts for why some entries would not boot - that is because those entries are the unsigned kernels, and my system has secure boot enabled.

Are you making progress?

---

### Post by josh84 on 2014-09-05
> **Dennis N said:**
> Hello josh84, I notice from your boot info script that you don't have a signed kernel. See line 264:

```
linux    /boot/[COLOR=#FF0000]vmlinuz-3.13.0-32-generic[/COLOR] root=UUID=81b5ad4b-8a69-434b-b6bb-d305a37985a0 ro  quiet splash $vt_handoff
```

Mine looks like this:

```
linux    /boot/[COLOR=#FF0000]vmlinuz-3.13.0-34-generic.efi.signed[/COLOR] root=UUID=297ecb14-ecb9-4ddb-8331-0f6c6cb9342f ro  quiet splash $vt_handoff
```

What does that mean? For one thing, you can't boot with secure boot enabled. How did that happen? Maybe because the installation media wasn't booted in secure boot mode?

Also I notice that my system has both kernels installed - signed and unsigned. So in the boot menu, that accounts for all the entries I see in my UEFI boot menu (see post #20) as it also has the old kernels on the menu. But they certainly are not well identified. It also accounts for why some entries would not boot - that is because those entries are the unsigned kernels, and my system has secure boot enabled.

Are you making progress?

No progress I have completely formatted the disk and tried many options with the Ubuntu installation.. The next things I will try are using Ubuntu 12 with all the previous suggestions and then if no dice there... Fedora 20... and if that does not work... I will stomp on this laptop and then cry. :)

---

### Post by Dennis N on 2014-09-05
Well, you don't really have to install in UEFI mode - since Windows 8 is not there. You could partition your disk with MSDos Partition table where you would install Ubuntu in Legacy mode, or whatever it's called on your system. Nothing wrong with that.

---

### Post by fantab on 2014-09-05
```
BootCurrent: 0003
Timeout: 2 seconds
BootOrder: 0003,0005,2003,2001,2002
Boot0001* UEFI: Network Card
Boot0002* UEFI: Network Card
Boot0003* UEFI: SanDisk Cruzer Glide 1.26
Boot2001* EFI USB Device
Boot2002* EFI DVD/CDROM
Boot2003* EFI Network
```

Are you using 'Advanced' option in Boot-Repair to select the Grub location as 'separate efi partition'?

According to the above code there isn't any HDD... unless 'EFI USB Device' is your HDD, however, I don't think so.
But try setting your boot to it and see how it fares... 
Ideally there should an entry 'Ubuntu' or something suggesting your HDD.

Post the output of:
```
sudo gdisk /dev/sda
``` and _exit_ 'gdisk' by typing '**q**'

```
sudo fixparts /dev/sda
```

again 'q' will exit fixparts.

---

### Post by josh84 on 2014-09-05
> **fantab said:**
> ```
BootCurrent: 0003
Timeout: 2 seconds
BootOrder: 0003,0005,2003,2001,2002
Boot0001* UEFI: Network Card
Boot0002* UEFI: Network Card
Boot0003* UEFI: SanDisk Cruzer Glide 1.26
Boot2001* EFI USB Device
Boot2002* EFI DVD/CDROM
Boot2003* EFI Network
```

Are you using 'Advanced' option in Boot-Repair to select the Grub location as 'separate efi partition'?

According to the above code there isn't any HDD... unless 'EFI USB Device' is your HDD, however, I don't think so.
But try setting your boot to it and see how it fares... 
Ideally there should an entry 'Ubuntu' or something suggesting your HDD.

Post the output of:
```
sudo gdisk /dev/sda
``` and _exit_ 'gdisk' by typing '**q**'

```
sudo fixparts /dev/sda
```

again 'q' will exit fixparts.

Hello,

Yes I am using the 'Advanced' option in Boot-Repair to select the Grub location as separate efi partition'? I will try running those commands my suspicion is that the hard disk has errors and ubuntu has been properly installed more than 10 times at this point... After install and removing the flash there is NO boot. Everything is set right in the BIOS but CLEARLY there is an issue with the Hard disk. to add craziness to the situation sometimes after re-installs it will phantomly boot  ONCE - sometimes after saying there is no media...  keep in mind Boot priority is  Hard disk - USB - CDrom - Lan.  So after the phantom boots its back to please insert a bootable media and restart issue. So possible hard disk issues here.

---

### Post by josh84 on 2014-09-05
> **fantab said:**
> ```
BootCurrent: 0003
Timeout: 2 seconds
BootOrder: 0003,0005,2003,2001,2002
Boot0001* UEFI: Network Card
Boot0002* UEFI: Network Card
Boot0003* UEFI: SanDisk Cruzer Glide 1.26
Boot2001* EFI USB Device
Boot2002* EFI DVD/CDROM
Boot2003* EFI Network
```

Are you using 'Advanced' option in Boot-Repair to select the Grub location as 'separate efi partition'?

According to the above code there isn't any HDD... unless 'EFI USB Device' is your HDD, however, I don't think so.
But try setting your boot to it and see how it fares... 
Ideally there should an entry 'Ubuntu' or something suggesting your HDD.

Post the output of:
```
sudo gdisk /dev/sda
``` and _exit_ 'gdisk' by typing '**q**'

```
sudo fixparts /dev/sda
```

again 'q' will exit fixparts.


[FONT=arial]ubuntu@ubuntu:~$ sudo gdisk /dev/sda[/FONT]
[FONT=arial]GPT fdisk (gdisk) version 0.8.8[/FONT]

[FONT=arial]Partition table scan:[/FONT]
[FONT=arial]  MBR: protective[/FONT]
[FONT=arial]  BSD: not present[/FONT]
[FONT=arial]  APM: not present[/FONT]
[FONT=arial]  GPT: present[/FONT]

[FONT=arial]Found valid GPT with protective MBR; using GPT.[/FONT]

[FONT=arial]Command (? for help): q[/FONT]
[FONT=arial]ubuntu@ubuntu:~$ sudo fixparts /dev/sda[/FONT]
[FONT=arial]FixParts 0.8.8[/FONT]

[FONT=arial]Loading MBR data from /dev/sda[/FONT]

[FONT=arial]This disk appears to be a GPT disk. Use GNU Parted or GPT fdisk on it![/FONT]
[FONT=arial]Exiting!


Good stuff huh, I am  starting over again now with some UEFI instructions I found on here... still GPT tho[/FONT]

---

### Post by josh84 on 2014-09-05
> **Dennis N said:**
> Well, you don't really have to install in UEFI mode - since Windows 8 is not there. You could partition your disk with MSDos Partition table where you would install Ubuntu in Legacy mode, or whatever it's called on your system. Nothing wrong with that.


Not sure what legacy mode is on this Toshiba but I know how to format it to MSDos...

---

### Post by christopher9 on 2014-09-05
What he means is toggling from UEFI boot to CSM/Bios in the BIOS configuration...

---

### Post by josh84 on 2014-09-05
> **christopher9 said:**
> What he means is toggling from UEFI boot to CSM/Bios in the BIOS configuration...


I can do that easy peasy. Hopefully that will make this work already... Its day 3 of being bricked.

---

### Post by josh84 on 2014-09-05
> **christopher9 said:**
> What he means is toggling from UEFI boot to CSM/Bios in the BIOS configuration...

Working on installing MSdos is CSM mode... I actually got a boot menu this time! Wow I chose ubuntu but it is just a puprple screen forever... Would a boot repair be a good option here... The boot options are

*Ubuntu
Advanced options for Ubuntu
Memory test 86+
Memory test 86+ serial console 115200
MS-dos on dev/sdb1

After trying to boot and waiting a minute or 5 it said this


Gave up waiting for root device. Common problems.
 - Boot args (cat /proc/cmdline)
- check rootdelay= (did the system wait long enough?)
- check root= ( did the system wait for the right device)

Missing modules (cat /proc/modules; ls /dev)

ALERT! /dev/disk/by-uuid/e5106260-91ed-4a6d-a7ae-7e670f044ea2 does not exist Dropping to shell

Busybox v1.21.1 (Ubuntu 1:1.21.0-1ubuntu1) built - in shell (ash)
Enter 'help' for a list of built-in commands...


Help?

---

### Post by christopher9 on 2014-09-05
Flaky disk drive ?

---

### Post by fantab on 2014-09-05
> ALERT! /dev/disk/by-uuid/e5106260-91ed-4a6d-a7ae-7e670f044ea2 does not exist Dropping to shell
HDD with '/' partition is missing.... its the same problem as explained in my earlier post... 
It doesn't seem to matter whether its UEFI or legacy/csm...
Get that HDD checked. Have you run SMART tests on your HDD with 'Disks' utility?

Also check in UEfI menu for HDD SATA mode or something like that... it should be set to 'AHCI'.

---

### Post by Dennis N on 2014-09-06
Well, this is a better outcome. Looks like a grub menu! There are two things which are odd: The last entry for "MSDos on /dev/sdb1" would not normally be there - what does it do? Second, I wonder why you get a grub menu at all? The computer should not show it if there is only one OS. Maybe you pressed the magic key to get the menu? I would see if the problem repeats if you restart (I suspect you probably already did). Anyway, googling the error "Still waiting for root device" will connect to reports by others with the same error and some causes and fixes. Maybe a solution can be found. Also, you could start a more specific new thread based on that "still waiting for root device" message.

I assume when you installed, you let the installer erase and use the whole disk? Then the creation and the layout of partitions suggested by the installer should be good.

Some implementations of Toshiba UEFI are reportedly not good. Google "Toshiba UEFI Linux" and read some. Could explain the failure of you initial UEFI attempts. These are mostly from 2013. I would stick with an MS DOS partition table and legacy bios mode when installing.

---

### Post by christopher9 on 2014-09-06
If you go to the Toshiba support site and enter your serial number, what BIOS version are they recommending ?

---

