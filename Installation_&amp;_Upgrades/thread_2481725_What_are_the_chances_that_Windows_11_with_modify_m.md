---
title: "What are the chances that Windows 11 with modify my Ubuntu drive's bootloader?"
date: 2022-12-07
forum: Installation &amp; Upgrades
---

### Post by david503 on 2022-12-07
I've got a new PC with Windows 11.  I'm about to install 22.04 on a *seperate drive*.   

The sum of all fears for me is something ever going wrong with grub.  Booting into the ubuntu drive and seeing "grub >".  That's my nightmare.

I've heard that Windows sometimes messes with ubuntu's EFI.  Like when it upgrades or whatever.  

I'm so afraid of a grub > prompt that on my current (older) workstation, whenever I rarely have to boot into windows, I actually open the case and unplug the ubuntu drive's SATA cable.  *THAT'S* how afraid of a grub > prompt I am.  

So my questions are:

If I have windows 11 on one drive, and Ubuntu (soon to be 22.04) on an entirely different drive, What are the chances that Windows 11 with modify my Ubuntu drive's boot? 

See, I could understand if it's messing it up if they're on the same drive, but what if they're on seperate drives? 

Second question is: if I ever get a grub > prompt can I just like, reinstall grub so it fixes itself?  I could boot from a usb ubuntu and then... reinstall grub on the ubuntu drive or something?

thanks,

d

---

### Post by tea for one on 2022-12-07
Here is a little checklist for Existing Windows and then Ubuntu on Separate Disks:-

Disconnect, de-activate, isolate via UEFI settings or physically remove existing Windows OS drive so that only the target drive is accessible
Boot Ubuntu live and check that you are in UEFI mode
Open a terminal and enter:-
```
[ -d /sys/firmware/efi ] && echo "UEFI" || echo "Legacy"
```
Create GPT on your target disk using gparted
Open gparted > Device > Create Partition Table > Select gpt
Allow the installer to automatically create the necessary partitions (or your preferred configuration)
Double check that an EFI partition will be created
Boot each system independently via UEFI boot screen (ideal not cumbersome)
Boot priority can be controlled by UEFI
Each OS should be installed in UEFI mode with GPT
Each drive should have an EFI partition
Each drive should have boot manager (Windows Boot Manager and Grub for Ubuntu)
De-activate, disconnect, isolate or physically remove one drive so that you can check if the other boots independently (and vice versa)

---

### Post by oldfred on 2022-12-07
UEFI often forgets boot entries if you unplug a drive.
Most systems seem to find a Windows entry but not other systems. You may have to use live installer and efibootmgr to recreate UEFI entry. 

Windows in BIOS mode used to cause lots of issues with not correctly updating a MBR partition table. With UEFI & gpt that issue is gone.
The only time I have seen an issue was where Ubuntu drive was default drive, and Windows was installed to second drive. Windows then created its own ESP on default drive, modifying Ubuntu drive.

You need good backups. And recovery flash drive for current version of every installed system.
Then you can easily resolve any issues.

Both major updates to Windows or grub reinstall boot loaders and then make themselves first in boot order.
You often then have to manage which boots first.

---

### Post by david503 on 2022-12-07
> **tea for one said:**
> Here is a little checklist for Existing Windows and then Ubuntu on Separate Disks:-

Disconnect, de-activate, isolate via UEFI settings or physically remove existing Windows OS drive so that only the target drive is accessible
Boot Ubuntu live and check that you are in UEFI mode
Open a terminal and enter:-
```
[ -d /sys/firmware/efi ] && echo "UEFI" || echo "Legacy"
```
Create GPT on your target disk using gparted
Open gparted > Device > Create Partition Table > Select gpt
Allow the installer to automatically create the necessary partitions (or your preferred configuration)
Double check that an EFI partition will be created
Boot each system independently via UEFI boot screen (ideal not cumbersome)
Boot priority can be controlled by UEFI
Each OS should be installed in UEFI mode with GPT
Each drive should have an EFI partition
Each drive should have boot manager (Windows Boot Manager and Grub for Ubuntu)
De-activate, disconnect, isolate or physically remove one drive so that you can check if the other boots independently (and vice versa)

Yes I think I understand most of what you wrote- I understand switching boot order in what we used to call BIOS but we now call UEFI (I know it's not identical but similar in concept), and I do know how to use it to choose drive boot order. (Actually the new PC is a Dell which has a nifty feature where during boot, you can actually do that without fully going into UEFI and changing it - you can press- I think it's F12 when your PC starts up and it lets you choose. Pretty cool right.)

I understood everything you said (including the part about testing each drive being able to boot independently at the end), except for the "gpt" part there.  If I'm allowing the installer to make the partitions (including EFI), which I think it does by default anyway btw, then can I skip the gparted step?

---

### Post by tea for one on 2022-12-07
> **oldfred said:**
> UEFI often forgets boot entries if you unplug a drive.
Sometimes, although very rare, the UEFI one-time boot menu doesn't "populate" the drive entry quickly.
I've always found that this is remedied by leaving the drive attached, booting into the available OS (either Windows or Ubuntu) and then closing the OS.
The drive then always appears (for me).
It probably depends on the stability of the UEFI firmware?

---

### Post by tea for one on 2022-12-07
> **david503 said:**
> then can I skip the gparted step?
I think that Ubuntu's default is not GPT.
Please double check when you are installing.

---

### Post by david503 on 2022-12-07
> **oldfred said:**
> UEFI often forgets boot entries if you unplug a drive.
Most systems seem to find a Windows entry but not other systems. You may have to use live installer and efibootmgr to recreate UEFI entry. 

Windows in BIOS mode used to cause lots of issues with not correctly updating a MBR partition table. With UEFI & gpt that issue is gone.
The only time I have seen an issue was where Ubuntu drive was default drive, and Windows was installed to second drive. Windows then created its own ESP on default drive, modifying Ubuntu drive.

You need good backups. And recovery flash drive for current version of every installed system.
Then you can easily resolve any issues.

Both major updates to Windows or grub reinstall boot loaders and then make themselves first in boot order.
You often then have to manage which boots first.

Yea see this is the nightmare I worry about:

> **oldfred said:**
> 
The only time I have seen an issue was where Ubuntu drive was default drive, and Windows was installed to second drive. Windows then created its own ESP on default drive, modifying Ubuntu drive.


If that were to happen, what do I do?  I guess the part about booting into a live usb and using efibootmgr, right?  How hard is it to do that in efibootmgr, assuming I at least know my way around linux in general (I'm a developer for 20 years), but I don't know boot stuff?  Is it straightforward?  I guess I should google around for that...

And when you say a recovery flash drive- ok, is that for the entire boot partition, or do you mean I can have the flash drive only just backup the EFI partition's content on it and simply copy it's guts over the ubuntu drive's messed up EFI guts?

---

### Post by david503 on 2022-12-07
From what both of you are saying- the part I don't understand is what gpt is or does.  I guess I have to figure out what gpt is.  I googled for it, but I don't understand it.  ug I hate this stuff!!!

Well anyway will @oldfred's statement: "[COLOR=#000000][I]You may have to use live installer and efibootmgr to recreate UEFI entry."
[/I][/COLOR]
Does that negate any problems I might have with the ubuntu drive?  Well if I disconnect the windows drive when I do it?   I mean without doing any gpt stuff at all beforehand.  Would that fix any problem that windows causes?

---

### Post by MAFoElffen on 2022-12-07
So answering the original question:
> 
What are the chances that Windows 11 with modify my Ubuntu drive's bootloader?

1 in 1, 100%, etc.

With UEFI, Windows updates assumes it is the only OS, so changes the order to make Windows first. It's going to happen sometime down the line. It's a given. It's happened to all of us.

So additional to everyone's instructions, always keep Ubuntu boot media handy and be comfortable in resetting the boot order with the 'efibootmgr' command...

---

### Post by tea for one on 2022-12-07
> **david503 said:**
> From what both of you are saying- the part I don't understand is what gpt is or does.  I guess I have to figure out what gpt is.
I would bet that your new Windows 11 is GPT.
Here's a quick overview [https://www.howtogeek.com/193669/whats-the-difference-between-gpt-and-mbr-when-partitioning-a-drive/](https://www.howtogeek.com/193669/whats-the-difference-between-gpt-and-mbr-when-partitioning-a-drive/)

---

### Post by david503 on 2022-12-07
> **MAFoElffen said:**
> So answering the original question:

1 in 1, 100%, etc.

With UEFI, Windows updates assumes it is the only OS, so changes the order to make Windows first. It's going to happen sometime down the line. It's a given. It's happened to all of us.

So additional to everyone's instructions, always keep Ubuntu boot media handy and be comfortable in resetting the boot order with the 'efibootmgr' command...

Yea the 100% I get that. Ok I've got an idea here:  What if I turn off windows updates (can I?) and then when and if I need to update it, I shut down, disconnect the ubuntu drive, then boot back into windows and turn on updates, update, then when it's all done, turn off windows updates again, and then reconnect the ubuntu drive?  Is that a plan?

---

### Post by david503 on 2022-12-07
> **tea for one said:**
> I would bet that your new Windows 11 is GPT.
Here's a quick overview [https://www.howtogeek.com/193669/whats-the-difference-between-gpt-and-mbr-when-partitioning-a-drive/](https://www.howtogeek.com/193669/whats-the-difference-between-gpt-and-mbr-when-partitioning-a-drive/)

Oh well right from the top this is a no brainer. It says MBR only supports up to 2tb?  My ubuntu drive (when I install on it), it's an 8tb drive.  So the ubuntu installer will need to do GPT no matter what right?

---

### Post by tea for one on 2022-12-07
> What are the chances that Windows 11 with modify my Ubuntu drive's bootloader? 
If Ubuntu is on a separate drive and is not accessible to Windows (i.e. isolated, unplugged etc), the Window updates cannot interfere with Ubuntu's ESP or Grub.
Dual booting requires some care but separate drives with individual EFI partitions for each OS offer an advanced level of protection.

---

### Post by tea for one on 2022-12-07
> **david503 said:**
> Oh well right from the top this is a no brainer. It says MBR only supports up to 2tb?  My ubuntu drive (when I install on it), it's an 8tb drive.  So the ubuntu installer will need to do GPT no matter what right?
I've no idea because I've never had a drive larger than 2TB.
I certainly hope it would default to GPT.

By the way, it would be worthwhile to explore your UEFI firmware to see if you can isolate your internal Windows 11 drive via built-in settings (rather than unplugging internal cables).

---

### Post by david503 on 2022-12-07
> **tea for one said:**
> I've no idea because I've never had a drive larger than 2TB.
I certainly hope it would default to GPT.

By the way, it would be worthwhile to explore your UEFI firmware to see if you can isolate your internal Windows 11 drive via built-in settings (rather than unplugging internal cables).

Oh I definitely can (I actually said that in response to you way up there at the beginning but hey it's a long thread and you're probably juggling other posts too!) 

Yea like like I said the installer would *need* to use GPT right, it can't use MBR on an 8tb drive.  I mean I really doubt the installer will say "um sorry you can only install ubuntu on 2tb drives." haha no no.  
So negates the need for the gparted step. Woo!

---

### Post by Frogs Hair on 2022-12-07
I have been using Linux and Win 11 for over a year on on different drives and have had no issues and this includes the latest Win 11 feature upgrade. I did use boot repair to move the boot partition to the Linux drive.I have TPM, Secure Boot and Mok Utilities all enabled. I may be lucky with no boot loader overwrites in 10 years of Windows dual booting, This build is the first try without easy bcd or other software.

---

### Post by david503 on 2022-12-07
> **Frogs Hair said:**
> I have been using Linux and Win 11 for over a year on on different drives and have had no issues and this includes the latest Win 11 feature upgrade. I did use boot repair to move the boot partition to the Linux drive.I have TPM, Secure Boot and Mok Utilities all enabled. I may be lucky with no boot loader overwrites in 10 years of Windows dual booting, This build is the first try without easy bcd.

Oh wow that's a new strategy.  So wait- if the windows drive crashes (or you just remove it), and the ubuntu drive boots by itself, you get the windows bootloader and just select the only option which is the ubuntu drive it's on?

---

### Post by Frogs Hair on 2022-12-07
I changed the boot order so when Win 11 updates the Windows boot loader starts first.It's actually is listed in grub as the Windows boot loader and so far so good. Each OS was installed one at a time while the other drive was un-plugged. Win 7 was easy to dual boot but, things became more difficult with Win 10. There is a boot loader location selection in boot repair and it worked well in my case. No crashes on either system so far. This is home build, so there were no operating systems or partition schemes on either drive. One NVME2 and one mechanical drive.

---

### Post by oldfred on 2022-12-07
You do not have to unplug a Windows drive if installing Ubuntu to a second drive. But if easy to unplug or turn off in UEFI settings may be best solution.
But it requires one of several work arounds because of a very old bug in the Ubiquity installer.

 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or temporarily moving boot flag/esp flag from first drive, so only ESP is install drive. 
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall of grub to correct drive. 

I prefer to use gparted to make sure drive is gpt & has ESP - efi system partition.
You also do not want a 8TB / (root) partition. Installer default would be an ESP & / for entire drive. That was ok back when most installs were dual boot on one drive so / was a lot smaller. 
Not sure if you boot installer in BIOS mode, if it uses MBR by default, if drive is blank. Never installed to that large of a drive. And have not used BIOS boot for years.

---

### Post by ubfan1 on 2022-12-07
Re your fear of the grub prompt showing up:
Be aware of the launchpad bug 1396379 - Installer uses first EFI
system partition found even when directed otherwise (and the
workarounds in the comments):

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

Add yourself to the bug's "Does this affect me?" list (in the upper
left corner). If list count gets big enough, maybe the bug will be fixed.

The "Wrong ESP" bug puts the grub boot onto your Windows disk, even if you
specify the location of the bootloaders as your second disk. However, some
grub files are in the Ubuntu root on the other disk, so the system wont boot
without the second disk. This is why the recommendation to remove the Windows
disk is made -- any other way to disable the disk will also be OK, but removal
is certain.

Installing Ubuntu to a second disk is more difficult than it should be.

---

### Post by grahammechanical on 2022-12-07
> the part I don't understand is what gpt is or does.  I guess I have to figure out what gpt is

In the old days (still within the living memory of some of us) hard drives had a Master Boot Record (MBR) partitioning scheme. This partition only allowed four partitions (known as Primary partitions). To have more than four partitions a work around was needed. Then someone came out with Guid (Gobally Unique Identifier) Partition Table (GPT). This partition scheme allows a much larger number of partitions. The work around is not needed any more.

If you decide to disconnect the Windows drive to avoid complications when you install Ubuntu on its drive. Afterwards when you have you have tested the loading of both Ubuntu and Windows by using the UEFI settings utility then set the Ubuntu drive to have boot priority and load Ubuntu and enter this command:

```
sudo update-grub
```

Grub will then detect the Windows installation and put an entry for it in a boot menu which will appear and give you the option to load either Ubuntu or Windows.

Regards

---

