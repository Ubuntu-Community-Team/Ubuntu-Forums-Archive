---
title: "install warning: using same 2 mount points -- but on 2 separate drives"
date: 2023-04-30
forum: Installation &amp; Upgrades
---

### Post by watchpocket on 2023-04-30
So I'm doing a fresh install of 22.04 on an empty internal nvme drive *(**nvme******1****)*.  I've already got 20.04 on a *separate* internal nvme drive *(**nvme0**)*.

After formatting nvme1 with the installer, and hitting "install" - I get this warning:

[I][B]"Identical mount points for two file systems (as superuser)"

"Two file systems are assigned the same mount point (/boot/efi): /dev/nvme1n1p1 and /dev/nvme1n1p1.  Please correct this by changing mount points."[/B][/I]

I don't get this, because my /boot/efi mount points are on 2 completely separate drives.

The installer is likely seeing ***/dev/nvme**0**n1p1*** and ***/dev/nvme******1******n1p1*** as the same drive. I need a way to make sure the installer can distinguish between them, and see two separate ***/boot/efi****'s* as two mount points on two separate drives.

What can I do to ***not*** get this warning and to make sure my install gets onto nvme1 with no such problems?

---

### Post by tea for one on 2023-04-30
> **watchpocket said:**
> What can I do to ***not*** get this warning and to make sure my install gets onto nvme1 with no such problems?
Jump into your UEFI firmware and de-activate nvme0 so that only your target disk nvme1 is visible to the installer.

---

### Post by watchpocket on 2023-04-30
I disabled nvme0 from booting (also disabled the SSD drive that I have a backup 20.04 on from booting) and then realized I'd only disabled them from ***booting***.  And that I didn't actually ***deactivate*** them so that the installer wouldn't see them.  Of course, that had no effect on the installer.

So I'm poking around the UEFI interface looking for where to deactivate the drives and not finding where I'd do that.  Any hints?

---

### Post by aljames2 on 2023-04-30
You can check your Mobo manual.  In UEFI, likely press F7 to enter advanced mode and look under the Advanced tab, Onboard Devices Configuration and see what options you have for your M.2_1, and M.2_2 slots.  It could be that if there is no disable option then likely the only way to make the other NVMe invisible is to physically disconnect it until your new installation is complete.

---

### Post by oldfred on 2023-05-01
The Ubiquity installer always wants to install grub to first drive.
And it automounts the ESP. But even during install, where you specify other partitions you change ESP entries or location of grub and it accepts those changed but still uses first drive's ESP. I even see it saying it installs to second drive, but actually installs to first drive.

I found that when booting that my ESP is in the live installer's mount & that is the only place it wants to install into.
I manually umount (unmount) that ESP & mount the ESP I want at about the screen where you input username & password.
Posted work around to manually unmount & mount correct ESP during install #55 or( #23 & #26)
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

Another alternative posted in bug thread, is to just temporally remove esp,boot flags from other ESP(s).
Remove esp flag from Windows before install to second or external drive - Tim Richardson
[https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator) &

---

### Post by TheFu on 2023-05-01
UEFI wants 1 and only 1 efi partition in any computer.  We can trick it a number of different ways.  The other posts are providing "tricks" to get around the EFI standards.
The main aspect for the work-arounds is to disable access to the drive that has the EFI partition you don't want used.  That can be done in the BIOS or by physically disconnecting power or by pulling the NVMe from the motherboard.  Most people would do it in the BIOS.
Some BIOS allow controlling which EFI partition is used.  That would be BIOS specific.

I've heard of efi-manager (or something like that), but I don't dual boot (prefer to use virtual machines myself), so I don't know much and can't remember ever seeing it. Probably everyone else in this thread knows more that I about that.

There are a few other methods possible, but they are worse.

For me, EFI booting solves a problem I've never had. I have 1 laptop that uses it and a new Ryzen system that I regret allowing to use EFI for boot. I have another Ryzen with the identical motherboard, CPU, RAM that boots using legacy and it has zero issues whereas the EFI booting one won't work with my KVM switch.  I'm not an EFI fan.

---

### Post by watchpocket on 2023-05-01
Excellent feedback, thank you all.
  
I decided the easiest way to proceed is by using Gparted to un-check the *boot* and *esp* flags of the drives I *DON'T* want the ubiquity installer to see and muck with.

Having done that from within the installer flash drive's "Try Ubuntu", I then began the install process. I *think* everything went well but for one possible snag which made me hold off on going ahead with the installation.

When the *"write changes to disks? (as superuser)"* dialog came up, it said this:

[I]"WARNING: This will destroy all data on any partitions **you have removed** as well as on the partitions that are going to be formatted."

[/I](The bold emphasis above is mine.)  Now, I did remove the ESP partitions of the drives I want the installer to *ignore*. 

What I'm wondering is: [I] 
Am I being told by the installer that those ESP partitions (that I removed by unchecking their boot flags) could/would/might be destroyed?

[/I]Or, is this just a standard warning in the* "write these changes to disks" *dialog? Does it always say this?

If it's a standard warning, I'll go back and proceed with the install.  

But if that warning is because the installer detected that I removed ESP partitions, and they might be destroyed, I'll need to re-think the process.

---

### Post by oldfred on 2023-05-01
If you did the uncheck in the installer, it will not work. I have tried that multiple times.
If you then run mount command you will still see the original ESP mounted & that is where it installs.

I always use manual partitioning & have had warnings, but I am only installing / (root). I use a large data partition for everything else and normally have several installs using that same data. Sometimes I want different settings, other times I copy /home or parts of it into new install.

---

### Post by watchpocket on 2023-05-04
This issue has not exactly been solved, but my installation of jammy is on hold until I can use a properly functioning Ubiquity installer. 

As stated before, the installer doesn't work if you're installing to a system that has more than one drive. The installer puts Grub in the first ESP partition it sees, and that will royally mess up the drive that that happens to.

The supposed method of un-checking the boot/efi flags of non-target  partitions doesn't work, and I've been unable to find in the UEFI  interface how I can disable non-target drives there. Not sure if it's  possible on my motherboard.

Apparently the installer for 23.04*** is working*** for installation to a system with multiple drives, [via Tim Richardson (post #108)]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379"), but not the installer for 22.04 (and earlier).  Oldfred's workaround is a little too cryptic for me to mess with, so I'll either install 23.04, knowing ***its*** installer won't bugger me (though I'd rather go with LTS jammy), or wait for a working 22.04 installer.  

As stated several times on the bug-report page, it's almost beyond belief that this installer bug could persist *for more than eight years, *turning off god-knows-how-many attempting to install Linux for the first time.

---

### Post by oldfred on 2023-05-04
My work around Post #55 of bug report, has always worked to let me directly install grub to sdb, or my external drive with a full install.
I open terminal & umount incorrect ESP & mount correct ESP during install.
Have not tried with new Ubuntu installer as Kubuntu still is using Ubiquity.

You used to be able to not install grub with ubiquity -b parameter. And then manually install grub or use Boot-Repair.
Grub will install to any drive in UEFI or BIOS mode depending on what version you select. Issue is with Ubquity.

---

### Post by watchpocket on 2023-05-04
I'll look further into your method.  I just need to be sure of what I'm doing, understand how each step is going to work. I don't even get how you'd open a terminal when you're in the external flash drive's installer. It seems limited there to go window by window ("continue" button etc) inside that installer box.

---

### Post by tea for one on 2023-05-04
> **watchpocket said:**
> The supposed method of un-checking the boot/efi flags of non-target  partitions doesn't work
It does if you follow oldfred's advice in post 10.
Or unmount them via Disks
> **oldfred said:**
> I open terminal & umount incorrect ESP & mount correct ESP during install
> **watchpocket said:**
> and I've been unable to find in the UEFI  interface how I can disable non-target drives there. Not sure if it's  possible on my motherboard.
If your UEFI settings do not allow you to de-activate non-target drives, you still have the option of physically removing them.
It may be a bit fiddly, but guaranteed to be viable alternative.

---

### Post by tea for one on 2023-05-04
> **watchpocket said:**
> I don't even get how you'd open a terminal when you're in the external flash drive's installer. It seems limited there to go window by window ("continue" button etc) inside that installer box.
Try Ubuntu > Open Terminal
i.e. Do not start the installer.

---

### Post by watchpocket on 2023-05-04
> Try Ubuntu > Open Terminal i.e. Do not start the installer.
I have a terminal open all day, every day. This can all be done *outside of the installer?  *If I'm in the installer, I can't have a terminal open, AFAIK.

When am I in the terminal and when am I in the installer?  If I could go do all this in test or practice mode, I'd feel better than just plunging in deleting and creating partitions while jostling between installer and command-line.  Again, I'll look into it to see how the steps go. Maybe I can "learn by doing," at the risk of borking a drive.
> **tea for one said:**
> It does if you follow oldfred's advice in post 10.
In post #10 he's talking about a different method.  Un-checking boot/efi flags of non-target drives in Gparted *does not work*. Oldfred himself said it.
> Or unmount them via Disks
Now *this* is a potentially viable notion.  It would have to be done from within *"Try Ubuntu."* 
> If your UEFI settings do not allow you to de-activate non-target drives, you still have the option of physically removing them.
It may be a bit fiddly, but guaranteed to be viable alternative.

I'd prefer to avoid that, if possible, It's more than a bit fiddly in my case (pun intended).

---

### Post by tea for one on 2023-05-04
> **watchpocket said:**
> In post #10 he's talking about a different method.  Un-checking boot/efi flags of non-target drives in Gparted *does not work*. Oldfred himself said it.
There seems to be a misunderstanding here.
If you remove the boot/efi flags using Gparted _before_ starting the installer, the procedure does work.
If you start the installer and then try and remove the flags during the partition stage of the installation, then there will probably be a failure.

---

### Post by watchpocket on 2023-05-04
No.  I've done it both ways.  That method doesn't work.  Not from inside the installer or before using the installer.  At least I couldn't get it to work. The installer still saw all my drives.  I did it from within "Try Ubuntu" before starting install, and I did it while logged into my main working system, before ever inserting the installer flash drive.  

Do you have personal experience un-checking the flags and having it work?

---

### Post by tea for one on 2023-05-04
> **watchpocket said:**
> If I'm in the installer, I can't have a terminal open, AFAIK. When am I in the terminal and when am I in the installer?  If I could go do all this in test or practice mode, I'd feel better than just plunging in deleting and creating partitions while jostling between installer and command-line.  Again, I'll look into it to see how the steps go.
After you have booted into a live session, open a terminal and unmount the non-target EFI partitions.
Then close the terminal and start the installer.
A new EFI partition will be created on your target drive and you will see a message about the new partitions to allow you to double check.

---

### Post by tea for one on 2023-05-04
> **watchpocket said:**
> Do you have personal experience un-checking the flags and having it work?
Yes, I have unchecked the flags and found that it worked.
However, for my own peace of mind, my UEFI settings allow me to de-activate drives.
Also, If I make a silly mistake, I can re-install Grub from a live session or boot via an EFI shell.
Lastly, I always have data backups, which is probably the most important issue.

---

### Post by watchpocket on 2023-05-04
> **tea for one said:**
> Yes, I have unchecked the flags and found that it worked.
In Gparted?  Opening Gparted from within the live session's "Try Ubuntu" mode?  (This didn't work for oldfred, If I understand him correctly.)

Or in Gparted* before* inserting the installation medium?  This just didn't work for me either way.

---

### Post by watchpocket on 2023-05-04
> **tea for one said:**
> After you have booted into a live session, open a terminal and unmount the non-target EFI partitions.
Then close the terminal and start the installer.

OK so this is done by opening the terminal *from within* the installation medium's "Try Ubuntu" mode. 

> A new EFI partition will be created on your target drive and you will see a message about the new partitions to allow you to double check.

FWIW, I already have an ESP partition in the target drive. It'll need to be formatted as fat32, which I'll do the installer. (I do also have full backups via Timeshift of my working system, at least.)

Thank you, will give it a go.

---

### Post by oldfred on 2023-05-04
When I manually unmount with the terminal, I am during that during the install.
I first check mount and typically do not see the mount of the ESP immediately.
Only after partitioning stage of install do mounted partitions show in terminal with:
mount

Changing ESP on partitioning screen has not worked for me. Mount still shows the default.
I do that and even see grub say it is installing to the ESP on sdb, but Ubiquity installs to my first or default drive.

---

### Post by tea for one on 2023-05-05
I&#8217;ve just double-checked the method of installing Ubuntu 22.04 to a second drive.
For me, removing the boot and esp flags on the non-target drive works.
I used my testing PC, a low specification Intel NUC6, which has Xubuntu 23.04 and Windows 11 (both UEFI on gpt disk with one EFI partition).

Attach Ventoy USB containing Ubuntu 22.04.
Attach new target disk, which has gpt but without partitions. (I used an external HDD via usb).
Boot into a live session of Ubuntu 22.04 (not Ubuntu Mate &#8211; if there is a difference?).
Open Gparted, remove esp and boot flags from sda1 (the internal disk EFI partition).
Close Gparted.
Start the Ubuntu 22.04 installation process.
When you reach the partition option - Choose Something else.
Select target disk &#8211; sdb in this example
I created an EFI partition size 512MB and an EXT4 system partiton of 60GB.
Device for bootloader installation = sdb.
I paused the installation and opened Disks.
I double-checked the status of sda1 (the internal disk EFI partition) and it was not mounted.
Installation restarted and continued as normal.
After completion of the installation, choose &#8220;Continue testing&#8221;.
Open Gparted again, restore esp and boot flags to sda1.
Close all open applications and power off.

The new installation on the external HDD was now portable and booted on another PC.
Both Windows 11 and Xubuntu 23.04 booted normally after this exercise.
Grub was not compromised.

It&#8217;s becoming clear that this does not work for everybody, possibly my hardware and UEFI firmware is simply very compatible with this procedure.

Edit: My preference remains that it would be more reliable to de-activate non-target disks via UEFI settings (or physically remove them).

---

### Post by oldfred on 2023-05-05
@tea for one
Thanks for update.

I think for me what has never worked was trying to unmount ESP on the partitioning screen during install. Have noticed that ESP is not mounted at beginning of install when I use mount. But it is mounted after finishing the partitioning screen. But changes on that screen to ESP do not seem to work.

---

### Post by watchpocket on 2023-05-07
Two questions:  

Let's say I am booted from the flash drive installer, and I've successfully *unmounted* both of my non-target drives. 

***Question 1:***  If I've done that, when I'm running the installer, specifically when I'm in the partition window in the installer, should I still be seeing the non-target drives and partitions in a long list there? Or should they NOT show up there if they're unmounted? 

Or is it normal that, if unmounted, they would still appear there?  (Obviously if I were to physically unplug them, they wouldn't appear.)

It would be a great visual help if the way you knew that your non-target drives were really unmounted and disabled (as far as the installer is concerned) was that the non-target drives didn't show in the partitioning window.  

I'm asking this because right now, if, while booted from the flash drive,  I open a terminal window in one monitor, and the installer in the other monitor, if I enter ***mount*** in the terminal,* mount *does not show my two non-target drives as being mounted. Neither * /dev/nvme0 *nor* /dev/sda *appear in the list of things under the *mount* command.

Yet in the installer's partition window, I see all drives listed there.

Likewise,*** lsblk -f***  shows only the flash drive as mounted.  This is whether I've un-checked (non-target drive) boot flags in Gparted (before opening the installer) or not.

*sudo umount -lrf /dev/nvme0n1p1 *
returns that nvme0n1p1 is not mounted.

***Question 2:*** Is it that your non-target default drive(s) (first drive the installer sees) will not be targeted by the installer ***if it's merely unmounted?***  Or do non-target drives [B][I]have to be actually disabled?
[/I][/B]
Under which condition is it safe to pull the trigger on the actual installation?

--------------------------------------------------------------
My target drive (internal): [B][I]nvme1n1
[/I][/B]
My two (internal) non-target drives: ***nvme0n1**; *and* **sda *** 
(*nvme0n1* is my current working 20.04 system; *sda* is a near-identical bootable backup of that 20.04 system.)
 
My (internal) storage drive:[B][I]sdb
[/I][/B]
My (external flash drive) installation medium:* **sdc***

---

### Post by oldfred on 2023-05-07
The installer is like gparted, it shows all partitions whether mounted or not.  
Why would it not show all partitions, since you may want to use that partition.

I find it only mounts my ESP, after the partitioning screen and about the time I am putting in user name & password.
Run mount command again when you get to that screen or have started to enter your user data.

---

### Post by tea for one on 2023-05-08
> **watchpocket said:**
> ***Question 1:***  If I've done that, when I'm running the installer, specifically when I'm in the partition window in the installer, should I still be seeing the non-target drives and partitions in a long list there? Or should they NOT show up there if they're unmounted?
All available partitions/drives will appear during the install procedure (as confirmed by oldfred in post 25)
> **watchpocket said:**
> ***Question 2:*** Is it that your non-target default drive(s) (first drive the installer sees) will not be targeted by the installer ***if it's merely unmounted?***  Or do non-target drives [B][I]have to be actually disabled?
[/I][/B]
If a partition/drive is unmounted, the installer will not target it.

_Some comments_
Dual/triple booting is not a simple exercise and it is a good idea to proceed with caution.
The installer will show a synopsis of the target drives after the partitions have been chosen.
You can still abort the installation at that stage if it targets the wrong partitions i.e. no damage done.
Grub will still find the other operating systems although the partitons are unmounted.

---

### Post by watchpocket on 2023-05-08
*> I manually umount (unmount) that ESP & mount the ESP I want at about the screen where you input username & password.*

But the installer doesn't let me get that far.  As soon as I hit the install button, I get this same warning as in my first post, saying to go back & fix, with the installer leaving me no other choice: 

[B][I]"Identical mount points for two file systems (as superuser)"

"Two file systems are assigned the same mount point (/boot/efi): /dev/nvme1n1p1 and  /dev/nvme1n1p1. 
Please correct this by changing mount points."[/I][/B]

Note that it's pointing to the same location twice. (Though I'd guess it's actually referring to both *nvme0* and *nvme1* as *nvme1*.)

Since the "Disks" app and the *mount* command issued in the terminal are both telling me that *nothing* is mounted (except the flash drive installer medium)*, *I entered this in the terminal (while I was in "Try Ubuntu"):[I] 
 
sudo mount -lrf /dev/nvme1n1p1

[/I]and it returned:[I]
mount: /dev/nvme1np1: can't find in /etc/fstab  

[/I]So on one hand, the installer is saying I have two identical, assigned (about-to-be, I guess) mount points.  On the other hand, "Disks" and *mount* show that nothing is mounted. (Though maybe they'd show otherwise if I could move beyond the warning in the install process.)
[I]
Of note: [/I] If I open the "Disks" app, select the* nvme1n1p1* partition, click on "Additional partition options," and select "Edit Mount Optons...", the "Mount Point" field entry there is: "/mnt/E23B-29C2".  

Right now I'm looking for a way to get past the above warning in the installer.

---

### Post by tea for one on 2023-05-09
Not much progress made yet, but let’s try to examine the mountpoints.

Can you boot your install USB into a live session
Open Gparted and make a GPT (partition table) on your target drive
Remove boot and esp flags from non-target drives
Close Gparted
Open terminal and enter:-
```
lsblk -e 7 -o name,size,type,fstype,fsuse%,fsavail,mountpoint
```
```
ubuntu@ubuntu:~$ lsblk -e 7 -o name,size,type,fstype,fsuse%,fsavail,mountpoint
NAME         SIZE TYPE FSTYPE  FSUSE% FSAVAIL MOUNTPOINT
sda        111.8G disk                        
&#9500;&#9472;sda1       487M part vfat                 
&#9500;&#9472;sda2      49.8G part ext4                   
&#9500;&#9472;sda3        16M part                        
&#9492;&#9472;sda4      61.5G part ntfs                   
sdb         74.5G disk   [COLOR="#0000FF"]Target disk visible without partitions  [/COLOR]                    
sdc         28.6G disk                        
&#9500;&#9472;sdc1      26.6G part exfat                  
&#9474; &#9492;&#9472;ventoy   3.4G dm             100%       0 /cdrom	[COLOR="#0000FF"]Only Ventoy live 22.04 USB mounted[/COLOR]
&#9500;&#9472;sdc2        32M part iso9660                
&#9492;&#9472;sdc3         2G part vfat 
```
At this point, if any other disks are mounted, then they have to be unmounted before the next step.

Start the installation process
Installation type > Choose “Something else”
Select your drive which only has free space
Create an EFI partition of 512MB
Create System partition /
Don’t forget to nominate the drive (not a partition) to accept the bootloader
Continue and you should see a dialogue box similar to:-
> If you continue, the changes listed below will be written to the disks. Otherwise, you will be able to make further changes manually.
The partition tables of the following devices are changed:
SCSI3 (0,0,0) (sdb)
The following partitions are going to be formatted:
partition #1 of SCSI3 (0,0,0) [COLOR="#0000FF"](sdb)[/COLOR] as ESP
partition #2 of SCSI3 (0,0,0) [COLOR="#0000FF"](sdb)[/COLOR] as ext4

Pause the installation at “Where are you”, open a terminal and enter:-
```
lsblk -e 7 -o name,size,type,fstype,fsuse%,fsavail,mountpoint
```

```
ubuntu@ubuntu:~$ lsblk -e 7 -o name,size,type,fstype,fsuse%,fsavail,mountpoint
NAME         SIZE TYPE FSTYPE  FSUSE% FSAVAIL MOUNTPOINT
sda        111.8G disk                        
&#9500;&#9472;sda1       487M part vfat                   
&#9500;&#9472;sda2      49.8G part ext4                   
&#9500;&#9472;sda3        16M part                        
&#9492;&#9472;sda4      61.5G part ntfs                   
sdb         74.5G disk                        
&#9500;&#9472;sdb1       487M part vfat        0%    486M /target/boot/efi	[COLOR="#0000FF"]mounted[/COLOR]
&#9492;&#9472;sdb2      38.1G part ext4        5%   33.6G /target		[COLOR="#0000FF"]mounted[/COLOR]
sdc         28.6G disk                        
&#9500;&#9472;sdc1      26.6G part exfat                  
&#9474; &#9492;&#9472;ventoy   3.4G dm             100%       0 /cdrom		[COLOR="#0000FF"]mounted[/COLOR]
&#9500;&#9472;sdc2        32M part iso9660                
&#9492;&#9472;sdc3         2G part vfat                   
ubuntu@ubuntu:~$
```
EFI and System targets mounted together with Live installer mounted at /cdrom.
I appreciate all this is a bit cumbersome but it may yield a clue?

Although, removing drives is "more than a bit fiddly in my case", you still have this up your sleeve ;)

---

### Post by watchpocket on 2023-05-09
Before I try this, just a couple of quick questions: 
 
[I]> Can you boot your install USB into a live session.
[/I]Will do.

[I]> Open Gparted and make a GPT (partition table) on your target drive.

[/I]That's already been done.  (See attached screengrab of the current state of my target drive as seen in Gparted. As you can see, I've already formatted partition 1 as *fat32*; partition 2 as *ext4*, and (pre-) labeled *nvme1n1p2* as "UbuntuMATE-22.04_nvme1"). You can see that the GPT table has already been created.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292202&stc=1[/IMG]

*> Create an EFI partition of 512MB*

Its current size of 402 MB should be fine, correct?  Also, this is where, in the installer, I may need to (again) format this efi partition as fat32. Or maybe not, since it's already fat32.  (The installer may prompt me to format it, and I'm thinking (or remembering) that I may need to, before the installer allows to continue.)  Also, this is where, in the installer, I set the ESP's mount point at */boot/efi*, correct? Just before going on to make sure to set the ext4 partition to be mounted at "/".

> *Pause the installation at &#8220;Where are you&#8221;*

"Where are you"?  Is that what the installer will actually say?  I don't remember ever seeing it. Do you mean pause after I see the dialogue box saying what's about to happen?

> [I]I appreciate all this is a bit cumbersome but it may yield a clue?

[/I]Not cumbersome. I appreciate your staying with me.  Just if i could be sure of these minor points before I continue, thanks.

---

### Post by tea for one on 2023-05-09
The installer will not allow you to format an EFI partition, which is why I suggest allowing the installation process to be as near to default as possible.
The size of ESP and System is probably not important but it may be better to let the installer do the work.
You do not set /boot/efi independently, again let the installer find it.
"Where are you" is the installation page for your location i.e. London, New York, Utopia etc.

I'm hoping that interesting info will appear when we see the terminal output.
By the way, when posting terminal output, please use code tags for legibility.

Fingers and toes crossed........

---

### Post by watchpocket on 2023-05-09
> In the live installer, the command 
*lsblk -e 7 -o name,size,type,fstype,fsuse%,fsavail,mountpoint*

indicated that sdc1 (sdc is the USB installer flash drive) was mounted at /cdrom and that sdc4 was mounted at 
/var/crash. I asusme that's OK.  Nothing else was mounted.

[I]> Select your drive which only has free space
> Create an EFI partition of 512MB[/I]

In the installer partition window, If I select the EFI partition as *"Use as EFI*", I cannot then set this partition's 
mount point, ( which I want to set at */boot/efi* ), because the *"Format the partitions"* checkbox is grayed-out.

I can only set the mountpoint if I select *"Use as fat32 file system"*.  But if I do that, after I hit "install now",
the warning is: *"No efi partition found, go back and create one."*

And when I go back and change *"fat32 file system"* in the dropdown menu to *"efi"*, after I hit "install now', the 
"write changes to disk" message says that only partition 2 will be formatted as ext4 -- it only wants to format 
the "/" partition.

If I were at this point to set the /boot/efi mountpoint for the ESP in the terminal, would I need to close the 
"write changes" dialog and reopen it?  Would setting in terminal cause the installer to recognize that setting 
& say both partitons will now be formatted?

*[EDIT: this post was sent before I saw your last post.]*

---

### Post by tea for one on 2023-05-09
> **watchpocket said:**
> EDIT: this post was sent before I saw your last post 
OK, understood.

Can you post the terminal output after removing unwanted boot and esp flags but before starting the installer?
As my first example in post 28.

---

### Post by watchpocket on 2023-05-09
Do you need the full output? I can do that, I'd have to take a pic of it with my phone, and post *that*, but what I wrote above explains everything you'd see after unchecking boot flags & before starting installer:

      > In the live installer, the command 
       *lsblk -e 7 -o name,size,type,fstype,fsuse%,fsavail,mountpoint*

       indicated that sdc1 (sdc is the USB installer flash drive) was mounted at /cdrom and that sdc4 was mounted at 
       /var/crash. I asusme that's OK.  Nothing else was mounted.


I AM planning on taking a pic of it in a few minutes after I go through the install process, at "Where are you".

---

### Post by tea for one on 2023-05-09
Please do not take a picture of terminal output.
When the terminal has provided the output, copy and paste within code tags.

If you haven't used code tags before, have a look at this attachment.

---

### Post by watchpocket on 2023-05-09
Finally I've now successfully installed 22.04 onto my nvme1 drive.  Thanks both of you for bearing with me. When I boot, GRUB 
gives me my three choices of bootable drives.  I've already logged into all three of them to make sure everything is as it should be.

Just to answer your last post, I couldn't copy-paste from terminal to a browser in "Try Ubuntu" because I'd have to log back into 
Ubuntu Forums, and I have an insanely long password that only my password manager (which is located in my other drive) knows.  
That's why I suggested posting a pic of the terminal output.  

(I'm familiar with using the code tags, and know it's important to use them when posting code.)

When I got to the timezone page, I ran the command again in terminal, and amazingly, the only things mounted were the 
flash drive and the 2 partitions of nvme1:  ESP was* /target/boot/efi* and the system ext4 partition was mounted at root.

The big news for me was what you just told me, that you can't set the ESP's mountpoint manually.  I kept trying to do that. 

Also, I think the upshot is that un-checking non-target drives (as long as you don't do it while you're in the installer) actually DID work for me.
I think that's what prevented my non-target drives from showing up, in the terminal,  as mounted.

I was totally expecting to see other drives mounted when I checked the command-output in the terminal after I was on the timezone page.
Thanks again for your persistence.

---

### Post by tea for one on 2023-05-09
> **watchpocket said:**
> Just to answer your last post, I couldn't copy-paste by opening a browser in "Try Ubuntu" because I'd have to, from there, log back into 
Ubuntu Forums, and I have an insanely long password that only my password manager knows.  That's why I suggested posting a pic of the terminal output.  (I'm familiar with using the code tags, and know it's important to use them when posting code.)
Ah, I understand
> When I got to the timezone page, I ran the command again in terminal, and amazingly, the only things mounted were the the flash drive and the 2 partitions of nvme1:  ESP was* /target/boot/efi* and the system ext4 partition was mounted at root. The big news for me was what you just told me, that you can't set the ESP's mountpoint manually.  I kept trying to do that. 
Yes, the installer does its work.
> Also, I think the upshot is that un-checking non-target drives (as long as you don't do it while you're in the installer) actually DID work for me.
I think that's what prevented my non-target drives from showing up, in the terminal,  as mounted.
I was totally expecting to see other drives mounted when I checked the command-output in the terminal after I was on the timezone page.
Thanks again for your persistence
All in all, good news.
Happy to have helped.

---

