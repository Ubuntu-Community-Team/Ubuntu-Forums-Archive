---
title: "Upgrading 14.04 to 16.04 over 24hrs. still upgrading? ? ?"
date: 2016-09-14
forum: Installation &amp; Upgrades
---

### Post by JustJazz on 2016-09-14
I'm new to Ubuntu so I wanted to upgrade after notification of upgrade available but Distribution Upgrade has been going on for over 24hrs. I'm sure this is NOT normal? ? ?

---

### Post by howefield on 2016-09-14
No, it is very much abnormal.

How are you upgrading, what process have you gone through to get to where you are now ?

Possibly a dialogue window hiding somewhere needing input ?

---

### Post by JustJazz on 2016-09-14
> **howefield said:**
> No, it is very much abnormal.

How are you upgrading, what process have you gone through to get to where you are now ?

Possibly a dialogue window hiding somewhere needing input ?

As soon as I turned on my desktop I was prompt to upgrade or upgrade was available. . . I think I made the mistake of not making sure 14.04 was up to date.

This is where it's been after packages were downloaded:

---

### Post by JustJazz on 2016-09-14
Sorry for DOUBLE posting. . . just got off work and still NO change :confused:

---

### Post by howefield on 2016-09-15
Pretty clear that the upgrade has stalled and won't go any further without input or instruction from you. Can you scroll down in the terminal window shown in the screenshot or resize to see more of it ?

PS. You are correct, prior to the upgrade it would be good practice to ensure that you start from a fully up to date system. Too late for that now though, just have to deal with what yo have.

---

### Post by JustJazz on 2016-09-15
> **howefield said:**
> Pretty clear that the upgrade has stalled and won't go any further without input or instruction from you. Can you scroll down in the terminal window shown in the screenshot or resize to see more of it ?

PS. You are correct, prior to the upgrade it would be good practice to ensure that you start from a fully up to date system. Too late for that now though, just have to deal with what yo have.

Thanks. The upgrade window was full-size. I clicked terminal to read the configuration message below then it shrank to what you see now. It was some type of Microsoft font agreement with ok at the bottom, no directive. . .

---

### Post by howefield on 2016-09-15
> **JustJazz said:**
> Thanks. The upgrade window was full-size. I click terminal to read the configuration message, it was some type of Microsoft font agreement with ok at the bottom, no directive. . .

Cool, try using the tab button to highlight the ok button and press the enter key. If you get a further licence agreement dialogue after that, use tab and or the arrow keys to move between options.

---

### Post by JustJazz on 2016-09-15
> **howefield said:**
> Cool, try using the tab button to highlight the ok button and press the enter key. If you get a further licence agreement dialogue after that, use tab and or the arrow keys to move between options.

I tried like hell, clicking terminal but the licensing dialogue box or the upgrade window will full size again. . .

---

### Post by howefield on 2016-09-15
> **JustJazz said:**
> I tried like hell, clicking terminal but the licensing dialogue box or the upgrade window will full size again. . .

Not really sure what you mean here.

> **howefield said:**
> Cool, try using the tab button to highlight the ok button and press the enter key. If you get a further licence agreement dialogue after that, use tab and or the arrow keys to move between options.

PS. Just to clarify I meant use the tab key on the keyboard, not the "tab button"

---

### Post by JustJazz on 2016-09-15
> **howefield said:**
> Not really sure what you mean here.



PS. Just to clarify I meant use the tab key on the keyboard, not the "tab button"
Tab key allowed me to continue installing the upgrades as we speak.

---

### Post by howefield on 2016-09-15
> **JustJazz said:**
> Tab key allowed me to continue installing the upgrades as we speak.

Great, good luck :)

---

### Post by JustJazz on 2016-09-15
> **howefield said:**
> Great, good luck :)
Thanks for helping, I'm going to keep my fingers crossed! ! !

---

### Post by JustJazz on 2016-09-15
After upgrade completed I rebooted the system and now I have a BLACK screen. I have Nvidia graphics card, I've read a few post regarding black screen issues and Nvidia graphic card drivers but don't know exactly how to fix by issue(s) without breaking something else?

---

### Post by howefield on 2016-09-16
> **JustJazz said:**
> After upgrade completed I rebooted the system and now I have a BLACK screen. I have Nvidia graphics card, I've read a few post regarding black screen issues and Nvidia graphic card drivers but don't know exactly how to fix by issue(s) without breaking something else?

Did you remove the nvidia proprietary drivers before the upgrade, assuming that you are using them ?

If you didn't, I'd suggest booting into recovery mode and purging all nvidia packages to get the system using the nouveau drivers. The nvidia drivers can then be put back once the machine is booting properly.

---

### Post by JustJazz on 2016-09-18
> **howefield said:**
> Did you remove the nvidia proprietary drivers before the upgrade, assuming that you are using them ?

If you didn't, I'd suggest booting into recovery mode and purging all nvidia packages to get the system using the nouveau drivers. The nvidia drivers can then be put back once the machine is booting properly.
I wasn't aware I had to do anything prior to upgrading so no I did not. 

How do I purge all nvidia packages to get my system using the nouveau drivers?

I'm assuming via terminal but what command lines?

---

### Post by oldfred on 2016-09-19
# Shows standard repository versions
ubuntu-drivers devices

# only reason to purge is there are several versions, if you know you have different nVidia use that:
Also must make sure parts of old install or persistence issue are not preserved as they are in use.
#To see available versions:
dpkg -l | grep -i nvidia*
#see details for version installed
sudo apt-cache policy nvidia*
Lists installed version, in/with your kernel:
dkms status

# Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
# [ using the correct names] for each driver, before running:
sudo apt-get purge nvidia*
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 

This should install the same as recommended driver in System Settings, Software & Updates, additional drivers tab.

 sudo ubuntu-drivers autoinstall 

You can check which nVidia driver is correct from nVidia also:

 Legacy drivers by GPU model 
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)
Updated driver search by nVidia model, do not download, just check correct driver version
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)

---

### Post by JustJazz on 2016-09-19
> **oldfred said:**
> # Shows standard repository versions
ubuntu-drivers devices

# only reason to purge is there are several versions, if you know you have different nVidia use that:
Also must make sure parts of old install or persistence issue are not preserved as they are in use.
#To see available versions:
dpkg -l | grep -i nvidia*
#see details for version installed
sudo apt-cache policy nvidia*
Lists installed version, in/with your kernel:
dkms status

# Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
# [ using the correct names] for each driver, before running:
sudo apt-get purge nvidia*
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 

This should install the same as recommended driver in System Settings, Software & Updates, additional drivers tab.

 sudo ubuntu-drivers autoinstall 

You can check which nVidia driver is correct from nVidia also:

 Legacy drivers by GPU model 
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)
Updated driver search by nVidia model, do not download, just check correct driver version
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)

Thanks for the help but I'm still blacked out? ? ?

---

### Post by oldfred on 2016-09-19
Can you boot Recovery mode to get to command line? 
Second entry in grub menu under Advanced options.

Do you get grub menu?
If not with UEFI you need to press escape perhaps more than once, with BIOS press left shift until menu appears.

Or have you tried nomodeset?
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by JustJazz on 2016-09-21
> **oldfred said:**
> Can you boot Recovery mode to get to command line? 
Second entry in grub menu under Advanced options.

Do you get grub menu?
If not with UEFI you need to press escape perhaps more than once, with BIOS press left shift until menu appears.

Or have you tried nomodeset?
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
I have grub menu. I can boot to recovery/advanced options/command lines.

I also tried replacing quiet splash with nomodeset in the linux line, rebooted to black screen. . .

---

### Post by oldfred on 2016-09-21
Recovery mode also uses nomodeset, but just to terminal. Where standard boot with nomodeset tries to load gui/desktop.

Using recovery mode & terminal with Internet working, I would try the commands posted above to purge nVidia(may not be requied) and install nVidia driver.

---

### Post by JustJazz on 2016-09-22
After sudo apt-cache policy nvidia*

Unable to locate package nvidia-bug-report. log.gz
Couldn't find any packages by glob ' nvidia-bug-report. log.gz' 
Couldn't find any packages by regex ' nvidia-bug-report . log.gz'

---

### Post by oldfred on 2016-09-22
Both of these can give errors if already erased:
sudo apt-get purge nvidia*
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup 

This should install the same as recommended driver in System Settings, Software & Updates, additional drivers tab.

 sudo ubuntu-drivers autoinstall

---

### Post by JustJazz on 2016-09-22
I booted grub ubuntu/advanced options/recovery menu/network/root/drop to root shell prompt(filesystem state: read/write then ran 'sudo ubuntu-drivers autoinstall'

0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

exit then Resume normal boot, still have black screen.

---

### Post by oldfred on 2016-09-22
Then it did not see nVidia hardware to install a nVidia driver.

Post this:
       #To see video:
sudo lshw -c display
sudo lshw | grep -A 11 display
lspci | grep VGA 

 #What is installed
dkms status

---

### Post by JustJazz on 2016-09-23
> **oldfred said:**
> Then it did not see nVidia hardware to install a nVidia driver.Post this:       #To see video:sudo lshw -c displaysudo lshw | grep -A 11 displaylspci | grep VGA  #What is installeddkms statusI hope these screens help:

---

### Post by oldfred on 2016-09-23
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)
That says you need 304.xx and you have installed 304 per dkms.

Please do not use screen shots on text or teminal output. If long also use code tags to preserve formatting.

---

### Post by JustJazz on 2016-09-29
> **oldfred said:**
> [http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)
That says you need 304.xx and you have installed 304 per dkms.

Please do not use screen shots on text or teminal output. If long also use code tags to preserve formatting.

Unfortunately nothing worked out for me so before I pull out anymore hair I decided I'd just do a fresh install of 16.04. The fresh install of 16.04 runs great, I navigated to setting/software & updates/additional drivers and changed Using X.Org X server --Noveau. . . to Using Nvidia legacy binary version 304.134 from nvidia-304-updates. No problems so far. Now I'm sitting on a quadruple boot system in grub2 and would like to remove:

1. linux mint.
2. ubuntu with graphic issue. 

while keeping:

3. Windows 7.
4. ubuntu 16.04(working).

```
Sector size (logical/physical): 512 bytes / 4096 bytesI/O size (minimum/optimal): 4096 bytes / 4096 bytes




Disk /dev/sda: 149.1 GiB, 160041885696 bytes, 312581808 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x6f06ecd2


Device     Boot     Start       End   Sectors  Size Id Type
/dev/sda1  *         2048    206847    204800  100M  7 HPFS/NTFS/exFAT
/dev/sda2          206848 164158359 163951512 78.2G  7 HPFS/NTFS/exFAT
/dev/sda3       164159486 312580095 148420610 70.8G  5 Extended
/dev/sda5       164159488 203404079  39244592 18.7G 83 Linux
/dev/sda6       308654080 312580095   3926016  1.9G 82 Linux swap / Solaris
/dev/sda7       247971840 308641791  60669952   29G 83 Linux
/dev/sda8       203405312 247963647  44558336 21.3G 83 Linux


Partition table entries are not in disk order.



```

.

---

### Post by oldfred on 2016-09-29
Normally last install is the grub in MBR. But you want to make sure.
And you can run this to confirm what is installed in which partition.

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by JustJazz on 2016-09-30
> **oldfred said:**
> Normally last install is the grub in MBR. But you want to make sure.
And you can run this to confirm what is installed in which partition.

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Thanks, will get it posted when I get in later.

---

### Post by JustJazz on 2016-09-30
Here's my BootInfo summary report:

[http://paste2.org/HzLbY7XH](http://paste2.org/HzLbY7XH)

---

### Post by oldfred on 2016-09-30
That says you are booting from sda8, one of two 16.04 installs.

Which 16.04 do you want to keep?

---

### Post by JustJazz on 2016-10-01
I wish to keep the newer 16.04 of the two if it shows the latest/last date used. I last used 16.04 last night. [B]

I want to keep[/B]: 

Windows 7(84 gb)
Ubuntu 16.04(23 gb) LTS

**I want to remove**:

Linux Mint Xfce(20 gb)
Ubuntu 14.04/16.04(31 gb) LTS which was supposed to be overwritten by Ubuntu 16.04 but encountered graphics upgrade fail.

---

### Post by oldfred on 2016-10-01
If you are booting by default or first grub entry then it is the one in sda8.

Of course you should do backups of any data or lists of installed applications or configuration files you have in other partitions.

---

### Post by JustJazz on 2016-10-01
> **oldfred said:**
> If you are booting by default or first grub entry then it is the one in sda8.

Of course you should do backups of any data or lists of installed applications or configuration files you have in other partitions.

I kinda figured the first entry in grub2 is my default/16.04 and the last entry is 16.04 I had graphic issues with. . . so what's the easiest way to remove the OS's I no longer want, I backed up what I intend keep?

---

### Post by oldfred on 2016-10-01
What do you want to do with the space?
You can just use gparted to remove partitions or reformat them. Then run sudo update-grub to remove boot entries in grub menu.

But I like to have several 25GB / (root) partitions so I can do another install and test things without potentially creating problems in my main working installs. And I have a large /mnt/data partition that I use in every install, so same Firefox book marks & Thunderbird email as well as all my files.

---

### Post by JustJazz on 2016-10-01
> **oldfred said:**
> What do you want to do with the space?
You can just use gparted to remove partitions or reformat them. Then run sudo update-grub to remove boot entries in grub menu.

But I like to have several 25GB / (root) partitions so I can do another install and test things without potentially creating problems in my main working installs. And I have a large /mnt/data partition that I use in every install, so same Firefox book marks & Thunderbird email as well as all my files.

For right now I'd like to keep Windows 7 and Ubuntu 16.04, maybe add gnome shell. . . but I would like to keep enough space available to try another install flavor down the road. . .

I want to remove:

Linux Mint Xfce(20 gb)
Ubuntu 14.04/16.04(31 gb) LTS which was supposed to be overwritten by Ubuntu 16.04 but encountered graphics upgrade fail.

---

### Post by JustJazz on 2016-10-03
Ok so I. . .


[LIST=1]
[*]I booted gparted with live cd.
[*]I turned swap to off.
[*]I selected /dev/sda5 as first partition to delete.
[/LIST]

As soon as I select sda5 or sda7, sda8 which is default disappears. Is this normal as I do NOT want to lose sda8?

Once a partition has been deleted will I be prompt to do something with that partitions memory?

How can I create another / root partition and where?

I noticed now I have unallocated memory but I figure this can, in some way be cleaned-up later?

Sorry I'm still learning(noob) all this as I go but some of it I find very confusing.

[ATTACH=CONFIG]271483[/ATTACH]

---

### Post by oldfred on 2016-10-03
Your gparted post, shows you running gparted from your install, not live installer. 
It shows swap & your ext4 partition, and then extended partition mounted.

I would not expect deleting sda5 or sda7 to also delete sda8. 
But choosing sda3 as the extended partition may delete all logical partitions, not sure if it lets you do that or not.

---

### Post by JustJazz on 2016-10-03
I posted image from my install just to show my set-up.

So is it safe, from within iso CD gparted to delete either sda5 or sda7 partitions then add that unallocated memory to a new / root partition and the rest to sda8?

Do a create this new / root partition within sda3?

---

### Post by oldfred on 2016-10-03
You can extend sda8 right into unallocated space, if sda7 is deleted. That works relatively quick & easy.
But if you want to move sda8 left where sda5 was & then expand right, the move left has to copy all data and it will take a while. And any interruption totally corrupts it. So have good backups and do not stop process if you move it.

---

