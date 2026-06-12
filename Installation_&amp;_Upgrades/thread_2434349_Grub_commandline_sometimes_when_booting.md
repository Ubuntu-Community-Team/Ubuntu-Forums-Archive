---
title: "Grub commandline sometimes when booting"
date: 2020-01-04
forum: Installation &amp; Upgrades
---

### Post by cornaljoe on 2020-01-04
I just install Ubuntu 19.10 dualboot with Windows 10.  I have Windows 10 on a SSD and Ubuntu on a HDD.  When installing Ubuntu I choose boot alongside Windows and it auto installed to the empty space on the HDD.  When restarting I sometimes get the grub command line.  If I type exit at the commandline it will go to the grub boot menu.  I can't pinpoint whats causing this as it doesn't happen all the time.  Sometimes the grub boot menu shows up just fine.  Anyway to stop the commandline from showing up or figure out what's causing it?

---

### Post by yancek on 2020-01-04
More details can be obtained on your specific situation by going to the site below, download boot repair using the 2nd option explained on that page, running boot repair as instructed using the option to Create BootInfo Summary and posting the link you get when it finishes here.  Do NOT make any repairs.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by cornaljoe on 2020-01-04
> **yancek said:**
> More details can be obtained on your specific situation by going to the site below, download boot repair using the 2nd option explained on that page, running boot repair as instructed using the option to Create BootInfo Summary and posting the link you get when it finishes here.  Do NOT make any repairs.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Here's the pastebin from Boot-Repair: [https://paste.ubuntu.com/p/M54kbYyXfh/](https://paste.ubuntu.com/p/M54kbYyXfh/)

---

### Post by yancek on 2020-01-04
You have windows boot code in the MBR of the 1TB drive which is unusual as it is a GPT drive and windows won't boot GPT unless it is an EFI install.  An EFI install doesn't put anything in the MBR.  Is that an upgrade or former install of windows 7 or earlier?  Do you just use that for data for windows now,?  You do have an EFI partition for windows on the SSD you have EFI partitions on both the SSD with windows as well as on the 1TB where you have Ubuntu.  It appears (see line 581 in  boot repair) that Ubuntu installed the EFI files on the first partition of the SSD.  You could mount that partition to verify it, see if there is an ubuntu folder there with files in it and also mount sda3 (EFI partition on the 1T) to see if there are any Ubuntu files in and ubuntu folder there.  Having 2 EFI partitions might be the problem but I'm not sure about  that.

You don't have an entry for windows in the Ubuntu Grub menu which would mean you need to access the BIOS to switch between windows and Ubuntu.  Is that the way you want it?

---

### Post by cornaljoe on 2020-01-04
> **yancek said:**
> You have windows boot code in the MBR of the 1TB drive which is unusual as it is a GPT drive and windows won't boot GPT unless it is an EFI install.  An EFI install doesn't put anything in the MBR.  Is that an upgrade or former install of windows 7 or earlier?  Do you just use that for data for windows now,?  You do have an EFI partition for windows on the SSD you have EFI partitions on both the SSD with windows as well as on the 1TB where you have Ubuntu.  It appears (see line 581 in  boot repair) that Ubuntu installed the EFI files on the first partition of the SSD.  You could mount that partition to verify it, see if there is an ubuntu folder there with files in it and also mount sda3 (EFI partition on the 1T) to see if there are any Ubuntu files in and ubuntu folder there.  Having 2 EFI partitions might be the problem but I'm not sure about  that.

You don't have an entry for windows in the Ubuntu Grub menu which would mean you need to access the BIOS to switch between windows and Ubuntu.  Is that the way you want it?

The 1TB HDD was recently installed for Ubuntu and Windows (500MB each). I previously installed Ubuntu on the HDD and used Boot-Repair to try and fix it but it added a bunch of unwanted boot entries so I deleted the entire disk and started over.  I used Windows disk manager and diskpart to delete the efi and ubuntu partition.  I then deleted ubuntu and boot repair from the efi of the SSD.  I thought I removed all traces from ubuntu before reinstalling.  Did the MBR survive?  Before figuring out how to remove ubuntu from windows boot menu I used fixmbr from my recovery partition but it failed.

Ubuntu created the EFI partition of the HDD when installing (called it ESP) so I thought it was needed.  Should I delete this partition since all the boot info is on the efi of the SSD?  When I type exit at the grub commandline the grub boot menu does have ubuntu and windows and they both launch fine.

---

### Post by yancek on 2020-01-05
If you create a mount point for sda3 and mount it and do not see an ubuntu directory with efi files for ubuntu, then it isn't used.  The info in boot repair seems to indicate that ubuntu used partition 1 on the SSD as the efi partition and that should be where the ubuntu efi files are ( /dev/nvme0n1p1).  If that's the case, then the sda3 partition isn't necessary so verify this first.  I don't know if this will resolve your problem. never seen that before.  I see you have an entry for windows efi in grub.cfg which I missed earlier as it is not in the standard location.

---

### Post by cornaljoe on 2020-01-06
> **yancek said:**
> If you create a mount point for sda3 and mount it and do not see an ubuntu directory with efi files for ubuntu, then it isn't used.  The info in boot repair seems to indicate that ubuntu used partition 1 on the SSD as the efi partition and that should be where the ubuntu efi files are ( /dev/nvme0n1p1).  If that's the case, then the sda3 partition isn't necessary so verify this first.  I don't know if this will resolve your problem. never seen that before.  I see you have an entry for windows efi in grub.cfg which I missed earlier as it is not in the standard location.

The efi on the HDD was empty so I deleted it and everything is still the same.  Guess I'll try boot-repair again.  I think I know how to clean up the mess it makes of the boot menu now so I won't have to reinstall if it doesn't work.  Anyway to get the log of boot to see if an error shows up when commandline is loaded instead of the grub menu?

---

### Post by yancek on 2020-01-06
Have you run sudo update-grub since your menuentries do not show in grub.cfg but only in the /etc/grub.d files

---

### Post by cornaljoe on 2020-01-09
> **yancek said:**
> Have you run sudo update-grub since your menuentries do not show in grub.cfg but only in the /etc/grub.d files

Yeah I tried that and it didn't work either.  I think I found a solution it says to install grub on the HDD instead of the SSD to keep Ubuntu and Windows separate.  Then boot from the HDD and add windows to grub through sudo update-grub.  It seems this problem happens when you have grub on one drive and ubuntu on another.

Is there a way for me to do this without a reinstall?  I really don't want to go through all that again.

---

### Post by dragonfly41 on 2020-01-09
One tip I picked up from reading many threads is to shut down,  go into the internals of the PC (make sure that power is unplugged), and unplug power to the internal drive (containing Windows). Then get your external Ubuntu working by using One Time Boot Option (F12 typically).

Other than that, explore efibootmgr options.

I used the efibootmgr commandline in OldFred [post #5 here]("https://ubuntuforums.org/showthread.php?t=2434378&page=2").

Study the options from efibootmgr --help 

I have two external devices (HDD and SSD) and the SSD stubbornly refuses to be seen (at times). I am still tracking the cause.
I have an efi partition on each external device.
I am now thinking that writing an automation script might automate my workflow.

[Added link] [efibootmgr usage]("https://www.linuxbabe.com/command-line/how-to-use-linux-efibootmgr-examples")

---

### Post by cornaljoe on 2020-01-11
> **dragonfly41 said:**
> One tip I picked up from reading many threads is to shut down,  go into the internals of the PC (make sure that power is unplugged), and unplug power to the internal drive (containing Windows). Then get your external Ubuntu working by using One Time Boot Option (F12 typically).

Other than that, explore efibootmgr options.

I used the efibootmgr commandline in OldFred [post #5 here]("https://ubuntuforums.org/showthread.php?t=2434378&page=2").

Study the options from efibootmgr --help 

I have two external devices (HDD and SSD) and the SSD stubbornly refuses to be seen (at times). I am still tracking the cause.
I have an efi partition on each external device.
I am now thinking that writing an automation script might automate my workflow.

[Added link] [efibootmgr usage]("https://www.linuxbabe.com/command-line/how-to-use-linux-efibootmgr-examples")

Just tried reinstalled putting grub on the HDD with ubuntu and still getting the grub commandline at times.  Do you have this problem aswell when a disk can't be seen at times?

Edit:  I just typed ls at the grub commandline and it looks like its not detecting my HDD.  Which is weird since grub is now on the HDD so how did the commandline even load.
Edit2:  I just checked and ubuntu installed grub to the SSD even though I picked the HDD no wonder it's still not working.  Going to try to put grub on the HDD now.
Edit3: Ok installed grub into the HDD and now the commandline is gone but when I select Windows it says no such device.  Ubuntu loads fine even tried sudo update-grub and it doesn't work.

---

### Post by dragonfly41 on 2020-01-12
I will try to add my notes although I am still in first grade in trying to learn the ins and outs of efi/gpt/mbr

I am of the view that a parsing script is need to make sense of each boot-repair report placed on pastebin. And an automation script.

From your earlier pastebin report I glean .. (use browser Find > efibootmgr to get to the point in the report)

```
[COLOR=#666666]==================[/COLOR] efibootmgr -v
BootCurrent: [COLOR=#666666]0002[/COLOR]
Timeout: [COLOR=#666666]0[/COLOR] seconds
BootOrder: [COLOR=#666666]0002[/COLOR],0000
Boot0000* Windows Boot Manager    HD[COLOR=#666666](1[/COLOR],GPT,0c0d8994-00ff-4133-a221-4f50fddc4b11,0x800,0x82000[COLOR=#666666])[/COLOR]/File[COLOR=#666666]([/COLOR]EFIMICROSOFTBOOTBOOTMGFW.EFI[COLOR=#666666])[/COLOR]WINDOWS.........x...B.C.D.O.B.J.E.C.T.[COLOR=#666666]=[/COLOR].[COLOR=#666666]{[/COLOR].9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.[COLOR=#666666]}[/COLOR]....................
Boot0002* ubuntu    HD[COLOR=#666666](1[/COLOR],GPT,0c0d8994-00ff-4133-a221-4f50fddc4b11,0x800,0x82000[COLOR=#666666])[/COLOR]/File[COLOR=#666666]([/COLOR]EFIUBUNTUSHIMX64.EFI[COLOR=#666666])[/COLOR]
```


I interpret this as two bootable partitions.  Windows and ubuntu. Both in HD 1, GPT.

If (at your risk) you wish to experiment with grub menu list (as I resorted to), then in my working Ubuntu (one of three) or even LiveUSB I installed Grub Customizer.

[http://tipsonubuntu.com/2018/03/11/install-grub-customizer-ubuntu-18-04-lts/](http://tipsonubuntu.com/2018/03/11/install-grub-customizer-ubuntu-18-04-lts/)

Under "default entry" I ticked &#8220;previously booted entry&#8221; instead of default &#8220;predefined&#8221;.

You can right click on a menu item and change (for example) &#8220;ubuntu&#8221; to &#8220;Ubuntu 18.04&#8221;.

When on occasions I get into a mess ("device not found") I reboot and type F2 to inspect boot items.

Sometimes I have had to recreate a boot item manually. To do this, reboot and enter Boot Sequence by tapping F2.  In my case I have three drives to contend with. In your case you only have one (HD 1).  I am on Dell.

I recommend studying all OldFred posts on UEFI. This is a huge corpus but I have found references to Ubiquity bugs, for example.  As an exercise I intend to try to index all these references to automate this painful multi-booting process.

**[Later edit]** [COLOR=#0000ff]Use the Forum advanced search feature ..

Advanced Search
Search Type:   Posts
Search for Posts
Keywords:       UEFI ....................Search entire posts
User Name:    OldFred..............Find Latest Posts by User     Exact name



      [/COLOR]**[Adding another reference] ** From OldFred's corpus of many links I unearthed this very helpful tutorial.

[https://forums.linuxmint.com/viewtopic.php?t=287353](https://forums.linuxmint.com/viewtopic.php?t=287353)

I plan to explore the rEFInd method.

[COLOR=#0000ff]

[/COLOR]

---

### Post by P-I H on 2020-01-12
I made a bootable USB stick with rEFInd according to the rEFInd method description on this page
[https://forums.linuxmint.com/viewtopic.php?t=287353](https://forums.linuxmint.com/viewtopic.php?t=287353)
I used an Ubuntu 19.10 installation. Because Ubiquity always stores the boot info in the 1:st disk, sda or nvme0n1, you have open a terminal and use the **ubiquity -b**
command to later be able to store grub on the USB stick
I have set BIOS to only boot in UEFI mode and to boot from the USB stick, I select the USB stick in BIOS.
I don't know how it actually works because when I check with Disks the boot file is mounted on sda.
I suppose the /boot picture is from the installation on the USB stick and the /boot/efi/EFI picture is from sda, even though I took the pictures from files on the USB stick installation.

---

### Post by dragonfly41 on 2020-01-12
I have not get around to trying rEFInd.

I throw in here a mention about falling back to use Windows as a recovery tool.

I have just now experienced the older HDD in my two external USB drives not booting.
Now I might be pushing my luck by having external HDD & SSD with ESP partition, EXT4 partition and NTFS partition in each device.
Moreover one (SSD) is GPT and the other is MBR (and I read from OldFred guide that I should not mix them). 
But this is an interim stage and eventually I will have only external SSD's.

The point is I hit a booting error.

I opted to boot into Windows where I had testdisk installed.
I ran testdisk and three drives were detected.

The problem drive showed "bad GPT partition, invalid signature".
I selected the problem drive and choose ..
if MBR .. choose Intel
if GPT .. choose EFI GPT

Analysed and changed the partition status from D to P.

Rebooted and I am writing this post from my recovered drive.

I could also use LiveUSB for running testdisk.

Now I am back to experimenting. Keep testdisk in mind to recover screwed up partitions.

---

### Post by cornaljoe on 2020-01-17
I pinned down the problem.  When booting grub doesn't see all drives only the one it's booting from sometimes (it seems to happen randomly).  With grub on the SSD when it couldn't see the ubuntu drive (HDD) it would load the command prompt.  Exiting the command prompt properly loads all drives somehow and I'm able to boot from either.  When grub is on the HDD it sometimes couldn't see the SSD therefore says no such device when trying to boot windows. If I press ESC to load the command prompt and type exit it properly sees all drives.

I can't really pinpoint why it's not seeing all drives sometimes.  Maybe the drive hasn't fully booted yet.  Is there a way to make grub take a little longer to load so all drives get read?

---

### Post by dragonfly41 on 2020-01-17
[COLOR=#000000]> I can't really pinpoint why it's not seeing all drives sometimes. Maybe the drive hasn't fully booted yet. Is there a way to make grub take a little longer to load so all drives get read?

I have to write that I have been experiencing similar problems in booting up my external SSD which has Ubuntu 18.04 installed. In fact my external HDD with an earlier version of Ubuntu is more reliable in booting up. Problems only started when I added my external SSD. I am guessing that there must be some HDD/SSD timing issue as you suggest.  I am reaching the point where I might consider an earlier idea in these forums to add an inline power switch so that the SSD has priority (i.e. Windows drive switched off by pressing a button before booting up SSD). Admittedly a crude fix  but might work in this case. Of course this requires SSD to have its own efi partition (which I have with boot flags).

[I am referring to post #15 here]("https://ubuntuforums.org/showthread.php?t=2434378&page=2").



[/COLOR]

---

### Post by cornaljoe on 2020-01-18
> **dragonfly41 said:**
> [COLOR=#000000]

I have to write that I have been experiencing similar problems in booting up my external SSD which has Ubuntu 18.04 installed. In fact my external HDD with an earlier version of Ubuntu is more reliable in booting up. Problems only started when I added my external SSD. I am guessing that there must be some HDD/SSD timing issue as you suggest.  I am reaching the point where I might consider an earlier idea in these forums to add an inline power switch so that the SSD has priority (i.e. Windows drive switched off by pressing a button before booting up SSD). Admittedly a crude fix  but might work in this case. Of course this requires SSD to have its own efi partition (which I have with boot flags).

[I am referring to post #15 here]("https://ubuntuforums.org/showthread.php?t=2434378&page=2").



[/COLOR]

I found a solution.  Installed refind bootloader and it doesn't have any of the problems grub has.  Plus I changed to this [theme]("https://github.com/bobafetthotmail/refind-theme-regular") and it looks great.  One thing that i changed was the console text it shows during boot and turned it off.  Do this by opening refind.conf and uncomment use_graphic_for and set your OS. Also lowered the autoboot time to 7 secs instead of 20.

---

### Post by dragonfly41 on 2020-01-21
I have installed rEFInd and I now have sanity restored in my multi-boot workflow.
I can boot into any of four OS (and LiveUSB). 
Windows 10
Ubuntu 16.04 on shared internal HDD with Windows
Ubuntu 18.04 on recently added USB 3.0 SSD in dual bay docking station
Ubuntu 18.04 on old USB 2.0 HDD container

---

