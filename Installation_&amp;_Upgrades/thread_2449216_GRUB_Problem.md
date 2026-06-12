---
title: "GRUB Problem"
date: 2020-08-22
forum: Installation &amp; Upgrades
---

### Post by r-orbis on 2020-08-22
Hello, I had Ubuntu installed alongside Windows 10 on my computer with GRUB showing a menu to choose between the two operating systems at each boot. However, this has recently disappeared and the following error message is being shown:

```
Reloc 8 Block size 0 is invalid
Relocation failed: Unsupported
Failed to load image: Unsupported
start_image returned: Unsupported

```

After showing this for a second, the computer continues to boot Windows 10 successfully.

I tried to reinstall Ubuntu with the hope of reinstalling GRUB as well. I formatted the Linux partition via the installer and chose to install a boot loader in it, sda5. However, upon restarting after that, the issue was still unresolved. I tried installing Ubuntu again, this time pointing /sda as the location for a boot loader installation but once again nothing changed.

Is there a way to fix that without erasing the entire drive? I don't want to lose the Windows partition. I came across this Boot-Repair application [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) but I am not sure who to show the log-file if this does not solve the issue - is that the forum to do so? Additionally, is running this tool dangerous to the Windows - can booting it be broken irreversibly, too? Thanks in advance.

---

### Post by CelticWarrior on 2020-08-22
Yes, you can use Boot Repair but to generate a report that you can post here. Do NOT apply any repair at this point.
Furthermore, use only the 2nd option, install Boot Repair in a live session.

---

### Post by ajgreeny on 2020-08-22
Windows very often makes changes to the boot system when it updates and can completely remove the ability to boot Ubuntu, even occasionally rewriting the partition-table.  It does not, or should not, have deleted any partition or the data on it so that should all still be there.

It will be best to see exactly what's going on, so, as mentioned by CW already above go to **Boot-Repair** in my signature below and follow the instructions there ***only to run the Boot-Info-Script***.	 
***Do not run any default repair just yet*** but simply copy back here the **pastebin link** you get which will show us a lot more about your system and hopefully point us towards a solution.

---

### Post by r-orbis on 2020-08-22
Thanks for the prompt responses! I didn't think it could log the issue without attempting a repair. I intend to try installing Boot-Repair in the Ubuntu live CD. Just to be clear before I start: the following commands will only install the application, right? They won't launch it automatically before I click on its icon, I suppose? I noticed that it would have a BootInfo Summary button but I don't want to launch it via the terminal inadvertently.

```
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair
```

---

### Post by CelticWarrior on 2020-08-22
The first line adds the the repository.
The second line refreshes/updates the software index.
The third line has two commands (separated by "&&"); the first installs Boot-Repair and the second runs it.

It makes no changes just by running. Again, use ONLY the button "Create a BootInfo Summary" and post the results here.

---

### Post by r-orbis on 2020-08-22
So here's what it said: [https://paste.ubuntu.com/p/Hj2HPmhQXT/](https://paste.ubuntu.com/p/Hj2HPmhQXT/)

I'm a little concerned - if I'm reading this correct, the GRUB list includes only Ubuntu and no Windows. If the repair tools activates it, would Windows no longer be bootable?

---

### Post by oldfred on 2020-08-22
> The boot of your PC is in BIOS-compatibility/CSM/Legacy mode. You may want to retry after changing it to UEFI mode.

If you boot in 'UEFI only' mode, do you still get the warnings?

You have UEFI system with UEFI installs of Windows and Ubuntu, but have installed (not sure how) boot boot loaders into MBR. With gpt drives, the MBR exists so that old partition tools see that drive is partitioned. It can be used to boot Linux in BIOS mode, but not Windows and requires additions partition to work.

Perhaps your system is trying to boot in BIOS mode, sees error & reverts to UEFI boot?
Just never boot in BIOS/Legacy/CSM boot mode.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

---

### Post by r-orbis on 2020-08-22
> **oldfred said:**
> If you boot in 'UEFI only' mode, do you still get the warnings?

You have UEFI system with UEFI installs of Windows and Ubuntu, but have installed (not sure how) boot boot loaders into MBR. With gpt drives, the MBR exists so that old partition tools see that drive is partitioned. It can be used to boot Linux in BIOS mode, but not Windows and requires additions partition to work.

Perhaps your system is trying to boot in BIOS mode, sees error & reverts to UEFI boot?
Just never boot in BIOS/Legacy/CSM boot mode.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

I'm not sure what exactly does this mean, life was simpler before all those UEFI modernist things. I will try to look into the settings to see if there is a choice between BIOS and UEFI and attempt to change it. I have not done anything to install boot loaders into MBR. I have booted some Acronis apps but that was after the problem had already occurred.

Edited to add: There is this odd thing from back when GRUB was working, that loading Ubuntu then led to a wrong timezone in Windows. This keeps happening now that I have only entered the UEFI setup but I'm not sure it is relevant to the GRUB issue.

I looked through the settings and nothing seems odd. From what I can see, this points to the Ubuntu partition (GRUB), it sees nothing bootable there and then reverts to booting from the Windows partition:

---

### Post by CelticWarrior on 2020-08-22
> [COLOR=#000000]life was simpler before all those UEFI modernist things[/COLOR]

Oh no, it certainly wasn't, at least for multi-booting anyway. UEFI allows bootloaders to co-exist and booting each OS independently. That alone is a huge improvement.

BIOS was archaic already by the late 80's.


> [COLOR=#000000]There is this odd thing from back when GRUB was working, that loading Ubuntu then led to a wrong timezone in Windows. This keeps happening now that I have only entered the UEFI setup but I'm not sure it is relevant to the GRUB issue.[/COLOR]
[https://help.ubuntu.com/community/UbuntuTime#Multiple_Boot_Systems_Time_Conflicts](https://help.ubuntu.com/community/UbuntuTime#Multiple_Boot_Systems_Time_Conflicts)
Not relevant to the Grub issue.

Other notes:
I see you have Fast Boot disabled (good) but you must also [disable Fast Startup]("https://www.windowscentral.com/how-disable-windows-10-fast-startup") in Windows.
Also recommended to disable Secure Boot, this one is UEFI, nothing to do with the OSes.
And the settings oldfred mentioned about booting "UEFI only" are likely somewhere else.

---

### Post by r-orbis on 2020-08-22
I have now gone through the entirety of that UEFI setup menu - nothing seems to be mentioning a choice between a BIOS and an UEFI-exclusive boot choice.

As for that time setting thing - I had tried doing it by changing the way Linux was using the time. I think this led to less anomalies with the timezone in Windows but did not resolve it completely.

The Secure Boot thing had always been disabled ([https://i.imgur.com/zF0MIH3.jpg](https://i.imgur.com/zF0MIH3.jpg)). Fast Startup was not enabled in Windows as well (no checkbox as per the link, screenshot below).

I remember BIOS as a static and constant thing, whereas this UEFI is like a shadow OS which you can't remove and which is too fickle by far.

---

### Post by CelticWarrior on 2020-08-22
I'ne never seen an explicit mention to "BIOS" in the context of UEFI settings.
CSM or Legacy is what you should be looking for, in order to disable it, of course.

---

### Post by zebra2 on 2020-08-22
> **CelticWarrior said:**
> Oh no, it certainly wasn't, at least for multi-booting anyway. UEFI allows bootloaders to co-exist and booting each OS independently. That alone is a huge improvement.


UEFI allows for Windows not to get a root kit virus.  Other than that it serves no purpose at all. Ubuntu doesn't need it. I have had to handle a root kit on a few occasions and it is a complete mess. Usually a reformat is the only answer. It is nice that Ubuntu is busting their butt to try to make dual boot work, but only to the effect that fast boot in Windows messes it all up. Who is it that you know that is so perfect that they are going to remember to disable fast boot every time Windows updates.  I'm currently using a MBR dual boot since I don't care if my Windows partition blows up because I have license in bios and reinstall is simple for me. Otherwise UEFI is a nuisance and I don't need it.   I'm leaning toward a separate Windows machine for the minor need I have for it and get rid of this failed concept all together.

I don't have any issues myself, but this is a heck of a mess to visit on new users to Ubuntu just to accommodate an OS that isn't participating in the solution. Their only contribution "UEFI" is the problem.  Seems to me.

---

### Post by r-orbis on 2020-08-23
> **CelticWarrior said:**
> I'ne never seen an explicit mention to "BIOS" in the context of UEFI settings.
CSM or Legacy is what you should be looking for, in order to disable it, of course.

You were right, there was a CSM option enabled - which I disabled. The error message upon booting remains unchanged. Could this all be due to some kind of a bad sector on the SSD or other such failure?

---

### Post by r-orbis on 2020-08-23
I have now run a chkdsk on the UEFI partition via Windows and this is what came up: [https://i.imgur.com/BOfRHBH.png](https://i.imgur.com/BOfRHBH.png) Should I say yes or no?

---

### Post by oldfred on 2020-08-23
You should only run on unmounted partitions.
Not sure if that is true with Windows?

You do have a backup of the ESP, so if chkdsk deletes something important for booting, you can easily restore it. Otherwise you have to use your Windows repair flash drive to make Windows repairs.

---

### Post by r-orbis on 2020-08-23
I have no idea what ESP is or where is it backed up. Will reply no to that dialog, then. That is the final result: [https://i.imgur.com/3ELf03X.png](https://i.imgur.com/3ELf03X.png)

At any rate, apparently the situation is hopeless and the entire SSD should be formatted in order to remedy all of that. I am very uncertain if I will ever be installing Ubuntu again.

---

### Post by oldfred on 2020-08-23
ESP - efi system partition
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

Shows my ESP
```
Number  Start   End     Size    File system     Name     Flags
 1      1049kB  525MB   524MB   fat32           efi      boot, [COLOR=#ff0000]esp[/COLOR]

```

Unless you specifically backed up your ESP, it would not normally be backed up.
In most cases backup not required, but may make recovery slightly easier.
You typically can just use your Ubuntu live installer to reinstall grub or your Windows repair flash drive to reinstall Windows' UEFI boot files.

---

### Post by r-orbis on 2020-08-23
> **oldfred said:**
> ESP - efi system partition
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

Shows my ESP
```
Number  Start   End     Size    File system     Name     Flags
 1      1049kB  525MB   524MB   fat32           efi      boot, [COLOR=#ff0000]esp[/COLOR]

```

Unless you specifically backed up your ESP, it would not normally be backed up.
In most cases backup not required, but may make recovery slightly easier.
You typically can just use your Ubuntu live installer to reinstall grub or your Windows repair flash drive to reinstall Windows' UEFI boot files.

Yes, I will be trying that with the flash drives before wiping everything but I don't think there is a high chance of it repairing things. I will also try the Boot-Repair thingie to see if it may make a difference. At best I could end up with a reinstalled GRUB not seeing the Windows and having to try and put in a clean Windows boot loader from its repair function. That would leave me at square one trying to put in a new Linux and a new GRUB and hoping the problem does not happen all over again. At any rate, all this requires time and I need the Windows working at least until the next weekend before I have the time to attempt anything this radical.

Thanks for all the responses.

---

### Post by r-orbis on 2020-09-12
I am happy to report that the issue was resolved successfully by formatting the UEFI system partition via an Windows bootable USB memory stick and reinstalling a new boot loader there. Afterwards I was able to reinstall Ubuntu and everything seems to be working smoothly for the moment without any loss of data (apart from the old Ubuntu which had already been toast). Hopefully this will continue to be the case. Thank you for all your assistance!

---

