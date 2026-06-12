---
title: "Dual boot with two m.2 slots"
date: 2023-09-15
forum: Installation &amp; Upgrades
---

### Post by ken18 on 2023-09-15
I have a brand new laptop with two m.2 slots, one with preinstalled Windows 11 and the other empty.  I want to have a completely independent dual boot machine.  I purchased an m.2 drive, removed the bottom laptop cover, inserted the new m.2 into the empty slot, removed the original Windows m.2, then installed Ubuntu (22.04).  I then replaced the original m.2 and now have a dual boot system.  BIOS boot order is windows, then ubuntu.  I get no grub menu when I boot (which is what I want), and to boot ubuntu I use F12 to select ubuntu.  Seems to work fine.

I have two specific questions regarding whether I really have two isolated bootable systems.

(1). If I perform Ubuntu updates, will grub eventually be updated and modify the Windows bootloader?  I really don't want that to happen.

(2). I've read that to prevent (1) from happening, one can use Gparted and uncheck the boot and esp flags on the windows efi partition.  Is this true and safe to do?  I know I'd need to do it every time I plan to perform ubuntu updates (easy to forget), then change it back before reboot or shutdown (easy to forget).

Appreciate comments from those in the know.

---

### Post by #&amp;thj^% on 2023-09-15
I do nothing like you describe, Your on the right track with your separate disk partitions, but I disable os-prober in grub if it's not already
```
#GRUB_DISABLE_OS_PROBER=false
```
This sounds like a future headache>>" Gparted and uncheck the boot and esp flags on the windows efi partition"

Others here will include more on this as well.

---

### Post by tea for one on 2023-09-15
> **ken18 said:**
> I have two specific questions regarding whether I really have two isolated bootable systems.
(1). If I perform Ubuntu updates, will grub eventually be updated and modify the Windows bootloader?  I really don't want that to happen.
As long as you have an ESP on each drive and you boot each OS via your PC boot menu F12, then you are are in sound position.
When an Ubuntu update affects Grub, you do not want Grub to "see" your Windows disk, therefore you need this parameter in /etc/default/grub
```
GRUB_DISABLE_OS_PROBER=true [COLOR="#0000FF"]# i.e. OS_PROBER is disabled and will not search for other systems[/COLOR]
```
> **ken18 said:**
> (2). I've read that to prevent (1) from happening, one can use Gparted and uncheck the boot and esp flags on the windows efi partition.  Is this true and safe to do?  I know I'd need to do it every time I plan to perform ubuntu updates (easy to forget), then change it back before reboot or shutdown (easy to forget).
Yes, it is safe but you don't need to do this if Grub ignores Window Boot Manager.

---

### Post by oldfred on 2023-09-15
Ubuntu/Grub only installs boot code into the first drive's ESP with Ubiquity installer used in  22.04 and before.
Newer Subiquity installer lets you choose where to install grub. (I have not tested it myself, yet).

Grub will not install to Windows drive, unless you specify that. It will offer to add a boot stanza to boot Windows, if os-prober is on, and Windows fast startup and bitlocker are off.

You can see details of install with this:
Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version over somewhat older ISO with your USB installer  or any working install.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by ken18 on 2023-09-15
> **1fallen said:**
> I do nothing like you describe, Your on the right track with your separate disk partitions, but I disable os-prober in grub if it's not already
```
#GRUB_DISABLE_OS_PROBER=false
```

I'm hoping this is a typo and that it needs to be true given the below.

> **tea for one said:**
> When an Ubuntu update affects Grub, you do not want Grub to "see" your Windows disk, therefore you need this parameter in /etc/default/grub
```
GRUB_DISABLE_OS_PROBER=true i.e. OS_PROBER is disabled and will not search for other systems
```

This makes sense to me given the name, but I'm not sure based on the reply from 1fallen. Is there a simple way to tell if it OS_PROBER is active??

Oddly, my /etc/default/grub file contains nothing about OS_PROBER, so I don't know what the default is.  I'm pretty sure the OS_PROBER is active because when I first installed Ubuntu 22.04 on the 2nd NVMe drive I ended up with a grub menu with Windows and Ubuntu, which is exactly what I didn't want.  I then spent quite a bit of time researching how to back that out.  In the end I gave up and reinstalled my original NVMe Windows drive (which I fortunately saved after cloning it) and started all over.

> **oldfred said:**
> Grub will not install to Windows drive, unless you specify that. It will offer to add a boot stanza to boot Windows, if os-prober is on, and Windows fast startup and bitlocker are off.
The only thing I can think of is that I must have OK'd the install to Windows drive w/o realizing I'd done that.  I guess I'll never know.

---

### Post by tea for one on 2023-09-15
Can you confirm that you have an ESP on each drive?

---

### Post by #&amp;thj^% on 2023-09-15
> **ken18 said:**
> I'm hoping this is a typo and that it needs to be true given the below.


This makes sense to me given the name, but I'm not sure based on the reply from 1fallen. Is there a simple way to tell if it OS_PROBER is active??

Oddly, my /etc/default/grub file contains nothing about OS_PROBER, so I don't know what the default is.  I'm pretty sure the OS_PROBER is active because when I first installed Ubuntu 22.04 on the 2nd NVMe drive I ended up with a grub menu with Windows and Ubuntu, which is exactly what I didn't want.  I then spent quite a bit of time researching how to back that out.  In the end I gave up and reinstalled my original NVMe Windows drive (which I fortunately saved after cloning it) and started all over.


The only thing I can think of is that I must have OK'd the install to Windows drive w/o realizing I'd done that.  I guess I'll never know.

Both have the same result for os-prober. 
It would be nicer for you the way tea for one puts it, easier to read and understand.
For os-prober active or not just use:
```
apt policy os-prober
```
BTW os-prober is always active on the live installer only...

---

### Post by ken18 on 2023-09-15
> **tea for one said:**
> Can you confirm that you have an ESP on each drive?
Yes, both have EFI System Partitions.  Curious, why is this important?

> **1fallen said:**
> Both have the same result for os-prober.
It would be nicer for you the way tea for one puts it, easier to read and understand.
For os-prober active or not just use:
```
apt policy os-prober
```
BTW os-prober is always active on the live installer only...

Are you saying GRUB_DISABLE_OS_PROBER=true and GRUB_DISABLE_OS_PROBER=false in /etc/default/grub have exactly the same effect? This baffles me.  Can you elaborate?

Re os-prober, result of apt policy os-prober is below, but I have no idea how to interpret it:

os-prober:
  Installed: 1.79ubuntu2
  Candidate: 1.79ubuntu2
  Version table:
 *** 1.79ubuntu2 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/main amd64 Packages
        100 /var/lib/dpkg/status

Lastly, if os-prober is always active on the live installer only that explains why I got the grub menu on the initial Ubuntu install.  Thanks for clearing that up.  Question: is there any way to disable it in the live installer?  This can be handy if I ever want to do a fresh install on my 2nd NVMe drive.  I hate having to remove the laptop bottom case and the windows NVMe drive.  Sooner or later I'll drop a screw inside the laptop and won't be able to find it...

---

### Post by #&amp;thj^% on 2023-09-15
> **ken18 said:**
> 

Are you saying GRUB_DISABLE_OS_PROBER=true and GRUB_DISABLE_OS_PROBER=false in /etc/default/grub have exactly the same effect? This baffles me.  Can you elaborate?
You mis-quoted me Mine reads as:
```
#GRUB_DISABLE_OS_PROBER=false
```
Note the comment.
FTR I think you should use tea for one's method, as said easy to understand.
> **ken18 said:**
> 

Re os-prober, result of apt policy os-prober is below, but I have no idea how to interpret it:

os-prober:
  Installed: 1.79ubuntu2
  Candidate: 1.79ubuntu2
  Version table:
 *** 1.79ubuntu2 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/main amd64 Packages
        100 /var/lib/dpkg/status

Lastly, if os-prober is always active on the live installer only that explains why I got the grub menu on the initial Ubuntu install.  Thanks for clearing that up.
It is installed so it will be active until you set it different, as all here suggests
EDIT: This what i see when I manually update grub or when a kernel new or updated comes in:
```
Warning: os-prober will not be executed to detect other bootable partitions.
Systems on them will not be added to the GRUB boot configuration.
Check GRUB_DISABLE_OS_PROBER documentation entry.

```
Hope that helps.

---

### Post by tea for one on 2023-09-15
> **ken18 said:**
> Yes, both have EFI System Partitions.  Curious, why is this important?
It's important so that both disks can boot independently via F12
Therefore, with both drives attached, I suggest:-
```
sudo nano /etc/default/grub
```
Add this line
```
GRUB_DISABLE_OS_PROBER=true
```
```
sudo update-grub
```
Windows Boot Manager should _not_ be detected
> Lastly, if os-prober is always active on the live installer only that explains why I got the grub menu on the initial Ubuntu install.  Thanks for clearing that up.  Question: is there any way to disable it in the live installer?  This can be handy if I ever want to do a fresh install on my 2nd NVMe drive.  I hate having to remove the laptop bottom case and the windows NVMe drive.  Sooner or later I'll drop a screw inside the laptop and won't be able to find it...
If you have to re-install Ubuntu:-
Boot the installer
Open Gparted
Remove the esp and boot flags from the Windows drive
The installer will then use the ESP on the existing Ubuntu drive

After the Ubuntu installation is complete, don't forget to replace the esp and boot flags on the Windows disk.

---

### Post by ken18 on 2023-09-15
> **1fallen said:**
> You mis-quoted me Mine reads as:
```
#GRUB_DISABLE_OS_PROBER=false
```
Note the comment.
FTR I think you should use tea for one's method, as said easy to understand.
Ah, I think I see. By comment, you mean the # in front indicates the entry is commented out (i.e. the variable is no longer set to false), which is the same thing as an entry explicitly setting the variable to true.  Thanks!

---

### Post by ken18 on 2023-09-15
> **tea for one said:**
> It's important so that both disks can boot independently via F12
Therefore, with both drives attached, I suggest:-
```
sudo nano /etc/default/grub
```
Add this line
```
GRUB_DISABLE_OS_PROBER=true
```
```
sudo update-grub
```
Windows Boot Manager should _not_ be detected

If you have to re-install Ubuntu:-
Boot the installer
Open Gparted
Remove the esp and boot flags from the Windows drive
The installer will then use the ESP on the existing Ubuntu drive

After the Ubuntu installation is complete, don't forget to replace the esp and boot flags on the Windows disk.
Got it, thanks!

---

### Post by oldfred on 2023-09-17
Os-prober does not have anything to do with grub install to Windows, it will just offer to add a Windows boot stanza to grub, if Windows fast startup & bitlocker are off, when you boot Ubuntu. Windows will not offer to boot Ubuntu. 

You do not have to reinstall Ubuntu to change which ESP grub is using. You can edit fstab with UUID of ESP on Ubuntu drive and totally reinstall grub. Simple reinstall uses many defaults but works using ESP mount from fstab. Make sure that ESP has remounted after change in fstab, may have to reboot.
To see UUIDs
lsblk -f
to confirm mounts
mount
to reinstall grub from inside current install. or see man grub-install for optional parameters. A new UEFI install from live installer then requires many parameters.
sudo grub-install
After reboot, you can rerun commands to confirm changes.

---

### Post by MAFoElffen on 2023-09-17
LOL.

Just a recap, even though it has been discussed extensively. After the installation, the default set for OS_PROBER in Grub2 "is disabled"... It's a boolean expression that evaluates to true or false. The "DISABLE" part of that is the key. (Semantics)

So in /etc/default/grub, the line
```

# GRUB_DISABLE_OS_PROBER=false

```
Since commented out, means that OS_PROBER is disabled. It will sit there and evaluate to disabled, as that is the default setting.

Removing the comment
```

GRUB_DISABLE_OS_PROBER=false

```
Says it is OS_Prober is turned on and will search for other OS'es. 

Where as
```

GRUB_DISABLE_OS_PROBER=true

```
Is the same as the default setting, and will force it being disabled explicitly.

I get it. LOL

Just saying... You all are saying the same thing (in different ways), but may be causing a bit of confusion.

---

### Post by #&amp;thj^% on 2023-09-17
> **MAFoElffen said:**
> LOL.

You all are saying the same thing (in different ways), but may be causing a bit of confusion.
Confusion is our middle name....LOL but was you? No I didn't think so.

---

### Post by grahammechanical on 2023-09-17
> Yes, both have EFI System Partitions.  Curious, why is this important?

If you only have one EFI system partition and it is on the Windows drive then the Ubuntu boot files (Grub) will have to be in the Windows EFI system partition. If for some reason you remove the Windows drive you will not be able to boot Ubuntu even using the UEFI boot menu. The Ubuntu boot files will not be available.

Two drives = two EFI system partitions. One EFI System partition containing Windows boot files. The other EFI System partition containing Ubuntu boot files.

Regards

---

