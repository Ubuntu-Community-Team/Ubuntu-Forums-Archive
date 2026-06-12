---
title: "GRUB2 no longer boots any operating system"
date: 2021-06-20
forum: Installation &amp; Upgrades
---

### Post by fr33boot3r on 2021-06-20
Greetings to the community. :)

On an old laptop (Samsung NP300E5X-A04IT with 4 GB of RAM and Intel Core i3-2310M processor) I had to replace the hard drive - due to failure - with a new SSD (Crucial BX500 480 GB).
Partitioning the hdd I chose, as it was for the old one, the ms-dos partition table (MBR) and not GPT; the machine has the old BIOS.
As my custom, I installed a Debian-based distro (BunsenLabs) by letting the installer install Grub2 into the disk MBR and immediately after that I installed Lubuntu 21.04 letting the installer install Grub2 into the disk MBR.
Everything worked fine and Lubuntu's Grub2 allowed me - of course - to start both Lubuntu and BunsenLabs. 

Later I decided to install Sparky Linux (in addition to Lubuntu and BunsenLabs) and I followed the same procedure, letting the installer install Grub2 in the MBR.
And here come the problems: on reboot, a BIOS screen detects the CD player and hard drive, but does not allow me to boot any operating system, as if it did not detect the presence of a boot loader.

I used a USB stick with the SuperGrub2Disk live: the Grub2 on the stick detected the presence of the distros and allowed me to start the one I wanted, in the specific case Lubuntu.
Started Lubuntu, reinstalled Grub2 and updated the OS list: 

```

# grub-install /dev/sda

```

```

# update-grub

```

The terminal replied that the Grub2 installation was successful.
I restarted the machine, and the situation has not changed: the PC does not start, if not using the USB stick with SuperGrub2Disk.

I tried to reinstall Grub2 through the other distros too, with the same result.

-------------------

Moreover, with the command:

```

sudo dpkg-reconfigure grub-pc

```

I installed Grub2 in the first sector of each root partition of the installed distros, and lastly I did the operation with Lubuntu, installing Grub2 also in the disk MBR (sda).
I never got any error messages, and each time the command updated the grub configuration file.
I rebooted (without the USB stick with SuperGrub2Disk) and the situation has not changed: the BIOS screen always appears which detects the CD player and the HDD but does not allow me to start any operating system.

I can't explain what happened and why reinstalling Grub2 doesn't fix the problem.
For now, I can still use the PC and start any distro, thanks to SuperGrub2Disk, but I would like to fix it permanently.

Is there any other attempt to make?

Thanks for the help and suggestions. 

.

---

### Post by ajgreeny on 2021-06-20
It will be very helpful to see more details of the current situation with all the information that can be obtained from running the Boot-Info script.
See Boot-Repair in my signature below and follow the instructions there.
**Do not run any repair just yet** but simply copy back here the pastebin link you are given when running the boot-info script which will tell us a lot more.

---

### Post by tea for one on 2021-06-20
I have also been in a similar position where [highlight]grub-install /dev/sda[/highlight] failed to produce the desired result.
No matter what I tried, Grub2 would not install at all, even though, as you mentioned, there were no error messages.
My situation was slightly different with a restore of a Clonezilla image in UEFI mode with GPT.
I managed to boot the image via the UEFI shell by navigating to [COLOR="#0000FF"]shimx64.efi[/COLOR] to boot.
However, all attempts to repair grub while in a booted session failed.

If a repair fails and I've spent more than a couple of hours on it, I simply re-install.

It looks like you want Lubuntu to control Grub, therefore two suggestions:-
[LIST]
[*]
[*]You could consider this oldish tutorial [COLOR="#0000FF"]Grub2 Recovery Hard way: Manual fix from live CD[/COLOR] [https://www.dedoimedo.com/computers/grub-2.html#mozTocId842078](https://www.dedoimedo.com/computers/grub-2.html#mozTocId842078)
[*]Try and re-install Lubuntu (having backed up first)
[*]
[/LIST]

---

### Post by fr33boot3r on 2021-06-20
tea for one, thanks for the tips.

I reinstalled Lubuntu 21.04 in the same partition (after formatting) and letting Grub2 install itself in the hard drive MBR, but nothing has changed.
I again formatted the partition (SDA3) and installed LXLE (a derivative of Lubuntu 18.04 LTS) hoping things would change, but it didn't.

I will read the article from dedoimedo.com, hoping it will be useful.

Thanks

---

### Post by fr33boot3r on 2021-06-20
ajgreeny, thanks for the help.

Here is the pastebin link:

[http://paste.ubuntu.com/p/vHVjwYKYMV/](http://paste.ubuntu.com/p/vHVjwYKYMV/)

Now, after my attempts, there are five distros installed (look at the previous post) and none of their Grubs worked ... :)

Thanks for the suggestions you can give me. 

----------

The PC disk is sda.
sdb is the memory stick with BootRepair.
I don't understand why BootRepair sees Grub2 installed in sdb as well.

sda1 is an NTFS partition for a possible future installation of Windows 7.
sda5 is the / home partition common to all distros (with different user name).
sda6 is the swap partition.
sda9 is the data partition, common to all distros. 

.

---

### Post by tea for one on 2021-06-20
Well, I am not really surprised that Grub2 is having difficulty with this complicated configuration.

Three primary partitions (sda1 - sda3)
One extended partition (sda4)
Nine logical partitions (sda5 - sda13)
Five different operating systems

sda1 reserved for [COLOR="#0000FF"]Windows 7[/COLOR]? - Please do **not** install an unsupported release

In your original post, you only mentioned 3 operating systems and did not state that sda1 was a ntfs partition.

I'm pretty sure that I have read somewhere that Sparky Linux has caused difficulty with dual/multiple OS booting so I would completely remove this OS and try and restore Grub as you tried before.
You never know?

Anyway, if you have unlimited time, then continue to pursue a working Grub installation.
Subsequently expect an update (either Grub or kernel) to put you back where you are now.

Otherwise, back up your data and start from scratch using installations in UEFI mode with GPT (assuming your PC is UEFI capable)

---

### Post by oldfred on 2021-06-20
Also best not to install grub to PBR, partition boot sector or BS - boot sector.
BIOS systems can only boot from MBR, not from PBR.
Grub2 should complain about trying to install to PBR.
> Attempting to install GRUB to a partition instead of the MBR. This is a BAD idea.
Embedding is not possible, GRUB can only be installed in this setup by using blocklists. However blocklists are UNRELIABLE and its use is discouraged.

Grub does not use boot flag, only Windows and some Windows type boot loaders like syslinux.

---

### Post by fr33boot3r on 2021-06-23
> 
Well, I am not really surprised that Grub2 is having difficulty with this complicated configuration.

tea for one, I do not agree. It is not the simplest of configurations, but for years I have used this way of splitting the hard disk, on this PC and on others, with Grub2 without ever having difficulty.

> 
sda1 reserved for Windows 7? - Please do not install an unsupported release

We agree on this. I know that Windows 7 has no more support since January 2020.
I intend to use Windows 7 only to manage a photo scanner: for basic tasks it also works with Linux but to scan slides it needs the management software written for Windows. 

> 
In your original post, you only mentioned 3 operating systems and did not state that sda1 was a ntfs partition.

Now there are four operating systems, and sda1 (NTFS formatted) is empty, so it can't bother Grub2.
As I mentioned, Grub2 has been able to manage much more complex situations in my PCs.

> 
I'm pretty sure that I have read somewhere that Sparky Linux has caused difficulty with dual/multiple OS booting so I would completely remove this OS and try and restore Grub as you tried before.

I think you're right; in fact, the problems with Grub2 occurred right after installing Sparky Linux, which I removed.
It is a strange behavior, because in the past years I have used it without problems. 

> 
Anyway, if you have unlimited time, then continue to pursue a working Grub installation.
Subsequently expect an update (either Grub or kernel) to put you back where you are now.

For now, I will continue to use Super Grub2 Disk on memory stick. It is almost as fast as Grub installed in the MBR and just as efficient in detecting installed operating systems.
Later, I will repartition the hard drive from scratch and reinstall. 

> 
Otherwise, back up your data and start from scratch using installations in UEFI mode with GPT (assuming your PC is UEFI capable) 

Why install in UEFI mode with GPT? 
What are the advantages on a machine with the old BIOS (assuming my PC is UEFI capable)?

Thanks.

---

### Post by fr33boot3r on 2021-06-23
> 
Also best not to install grub to PBR, partition boot sector or BS - boot sector.
BIOS systems can only boot from MBR, not from PBR.
Grub2 should complain about trying to install to PBR.

Thanks oldfred, you're right. Also I never installed Grub2 to PBR: always to MBR.

Anyway, thank you all for your valuable suggestions. They have been useful to me or in any case may be in the future.

.

---

### Post by oldfred on 2021-06-23
I keep the current LTS as main working install, but also install each 6 month release at least once. And have installed some other distributions, flavors or the server verson on occasion. So I end up with lots of / (root) partitions and many entries in grub, many then obsolete as older version, partition not yet overwritten.
So I turn off os-prober and only add the entries I want into 40_custom.

A major update of another system may reinstall grub, and then I have to choose to boot into my main working install and reinstall grub from there.
With UEFI, I now can just edit /EFI/ubuntu/grub.cfg with correct UUID, without grub reinstall.

My older Asus system with UEFI, does get confused if I have an ESP on every drive with boot enties on each drive. When I have multiple drives connected it sometimes gets confused and will not boot at all. But this is an UEFI issue, not grub. I find I have to disconnect all drives, sometimes have had to reinstall UEFI, and often have to use rEFInd to boot the one installed system. Then it all starts working again, I can directly boot from multiple (but not too many) drives and have one grub boot any install.

---

### Post by fr33boot3r on 2021-06-23
Thanks oldfred for your suggestions.
They will be useful to me.
For now, all my PCs are old enough to have BIOS and hard drives partitioned according to the MS-DOS (MBR) method.
In fact, I need to verify that this PC is UEFI compatible.
And I'll have to study a little, so that I get to know UEFI better.

Thanks again for the suggestions.

---

### Post by tea for one on 2021-06-23
> **fr33boot3r said:**
> 
Why install in UEFI mode with GPT? 
What are the advantages on a machine with the old BIOS (assuming my PC is UEFI capable)?

A good decision to continue with Super Grub2 Disk on memory stick - if it works and you are happy with the performance, then great.

UEFI with GPT has a several distinct improvements over MBR and older BIOS.

UEFI allows you to boot an OS via a UEFI shell, completely bypassing Grub in the event that Grub is damaged.
Firmware updates via UEFI are often distro agnostic.
You can install a different boot manager rEFInd (only for UEFI systems) [https://www.rodsbooks.com/refind/](https://www.rodsbooks.com/refind/)
GPT allows more than 4 primary partitions
GPT allows access to large disks (larger than 2TB)
UEFI and GPT is essential for Windows 10 

I'm sure that there are many other advantages and a quick search will reveal hundreds of internet pages with abundant info and opinions.

Cheers

---

### Post by fr33boot3r on 2021-06-24
Thanks for the tips.
This is an interesting topic that I'll need to know better when I'll purchase the next PC.

Is there a way to know if a PC, born with BIOS and partitioned MS-DOS (MBR) is UEFI compatible?
I did a search on the net by typing the code of my laptop model (Samsung NP300E5X-A04IT) but I didn't get any results.

Thanks. :)

---

### Post by tea for one on 2021-06-24
> **fr33boot3r said:**
> 
Is there a way to know if a PC, born with BIOS and partitioned MS-DOS (MBR) is UEFI compatible?

That's a good question. I would think that you have to put your BIOS publisher and version into a search engine?

There is a way to enter UEFI firmware via the terminal

```
sudo systemctl reboot --firmware-setup
```

I don't what the error message would be if you didn't have UEFI.
Perhaps boot into Lubuntu and give it a shot. I'm sure it wouldn't cause any damage if the command cannot find UEFI set-up.

I only have UEFI on my devices so I can't find out for myself.

I would bet that your next PC purchase will be 100% UEFI - unless you buy an absolutely ancient second-hand machine :).

---

### Post by oldfred on 2021-06-24
Microsoft has required vendors to install Windows in UEFI/gpt mode since release of Windows 8 in 2012.
So almost all hardware is now UEFI.

This was changed to 2021:
Intel is planning to end "legacy BIOS" support in their new platforms by 2020 in requiring UEFI Class 3 or higher.
[http://www.uefi.org/sites/default/files/resources/Brian_Richardson_Intel_Final.pdf](http://www.uefi.org/sites/default/files/resources/Brian_Richardson_Intel_Final.pdf)

And:
[https://support.lenovo.com/us/en/solutions/ht510878-legacy-bios-boot-support-removed-in-lenovo-2020-products](https://support.lenovo.com/us/en/solutions/ht510878-legacy-bios-boot-support-removed-in-lenovo-2020-products)

---

### Post by yancek on 2021-06-24
Boot repair indicates your system is not UEFI but the best way to verify is to access your BIOS firmware and check to see if there is any reference to UEFI.

Your current boot repair shows Grub in the MBR pointing to partition 3 which is Lubuntu so I'm not sure why it doesn't boot from the hard drive as all the necessary files seem to be in place.  You have multiple entries in the filtered grub.cfg file for some of the OS's pointing to different partitions so I would boot Lubuntu from SuperGrubDisk and run:  sudo update-grub to get rid of some of them.

Having 5 or more OS's installed should not be a problem as Grub should have no problem booting all of them or more.,

---

