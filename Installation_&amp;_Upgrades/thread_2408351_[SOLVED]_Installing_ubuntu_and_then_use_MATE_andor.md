---
title: "[SOLVED] Installing ubuntu and then use MATE and/or how to install UEFI grub?"
date: 2018-12-17
forum: Installation &amp; Upgrades
---

### Post by david503 on 2018-12-17
I just totally got burned by installing Ubuntu MATE and then later connecting my windows drive.  Apparently grub/BusyBox  couldn't hand the basic idea that another drive exists in the universe and it dropped me down to (initramfs) prompt. 

   I know that's probably not MATE's fault directly but I'd rather try again by installing regular ubuntu (and maybe choosing a different bootloader than grub (or BusyBox I guess- is that the same thing? It's using BusyBox). 

   Anyway the real ubuntu installer was more complex if I remember correctly and I'd rather use real ubuntu and then just switch to the mate window manager after it's running without being absurdly flakey and switching down to an (initramfs) prompt.    So can I install the MATE window manager over regular ubuntu?  Thanks

---

### Post by TheFu on 2018-12-17
You can switch the GUI if you like. There are about 50 different choices.  The GUI is just another program.  There are some caveats when switching between different GUIs since some settings can conflict if they use the same libraries.

I would be surprised if the installer had anything to do with the issue you are reporting.  Could it be something else?  What do the system log file show?

OTOH, installing Ubuntu takes 8-15 minutes these days, so it isn't really much of a commitment to do a fresh install, provided you have backed up anything you want to retain.

---

### Post by david503 on 2018-12-17
Right but what if this happens down the road when I do have stuff I want to retain?  The uncertainty is unnerving.  For example right now I can't even get to the log files, I'm stuck with this horrible (initramfs): prompt which I have no idea what to do with.  Hell- I can't even get in to look at the log files.

---

### Post by CatKiller on 2018-12-17
The term "booting" is a contraction of "pulling up by your bootstraps." When the computer is booting, it is not able to read files. That ability needs to be loaded in later. In that state, the computer can only load into RAM, and execute, a specially-prepared INITial RAM FileSytem telling it how to load the next part, and where to load it from. You've changed the *where to load it from* part by adding another drive, and not updated the initramfs accordingly, so it can't proceed. BusyBox is a tiny shell environment that's small enough to be contained in the initramfs. Since the computer can't figure out what to do, it's launched that so that you can tell it what to do.

It has absolutely nothing to do with whichever desktop environment you're using. That comes *way* later in the process.

With appropriate skill, it *is* possible to recover the system just using the limited tools available in the intiramfs and BusyBox. A more user-friendly method is to boot into a live environment, use **chroot** to use the framework of the live environment to fix your installed environment, and then reboot. Or you can use the live environment to backup your files before you nuke. Installing anew will give you a non-broken system in about 10-15 minutes.

To answer the question of the thread, as already noted you can easily add or remove different desktop environments at will.

---

### Post by deadflowr on 2018-12-17
You can respond to oldfred's request in your other thread:
[https://ubuntuforums.org/showthread.php?t=2408298]("https://ubuntuforums.org/showthread.php?t=2408298")

---

### Post by TheFu on 2018-12-17
> **david503 said:**
> Right but what if this happens down the road when I do have stuff I want to retain?  The uncertainty is unnerving.  For example right now I can't even get to the log files, I'm stuck with this horrible (initramfs): prompt which I have no idea what to do with.  Hell- I can't even get in to look at the log files.

I would boot from a USB flash drive and have a look around on the disk and at the logs.
Pretty much anything can be fixed from the "Try Ubuntu" environment that is available by all *buntu ISO image desktop files - mate, xfce, lxqt, gnome3, and KDE each can be used in this way.

As a guess, I'd check the boot.log since that is likely where the issue is, if there is anything there.  The answer could be in the BIOS boot priority settings if the 2nd disk is higher priority and it has a minimal boot environment.  Any chance the 2nd disk ever had **any**  linux installs previously?  CatKiller's idea seems like an excellent idea.

Ah ... and the info that oldfred asked for (boot-repair info) would be very helpful. Be certain that all disks are connected at the time.  If a Windows disk was added as the other thread claims, then using the live boot flash ubuntu and a chroot, then installing grub and updating grub will let it find both the Ubuntu and the Windows installations.  A mention of that other thread was very helpful. Many thanks deadflowr.

---

### Post by david503 on 2018-12-17
How come windows doesn't have this problem when I connect a new drive?

(Oh, and yes, I have the ubuntu drive higher priority in bios.)

Also:

> **CatKiller said:**
> 

It has absolutely nothing to do with whichever desktop environment you're using. That comes *way* later in the process.


Yes I'm well aware- but it's nonetheless a different distro, right?  I mean the options in the install are even different.

But still, like I said, I know it's probably a grub problem not a distro problem...

---

### Post by ajgreeny on 2018-12-17
> **david503 said:**
> How come windows doesn't have this problem when I connect a new drive?

(Oh, and yes, I have the ubuntu higher priority in bios.)

Most normally it does not happen in Ubuntu either, so as others have suggested, I suspect this is not directly related simply to adding another drive.

Boot to a live Ubuntu system and see if the Windows drive is mountable from that or if it throws a lot of errors when you try mounting it.
Also run terminal commands ```
sudo fdisk -l | grep /dev/sd*
sudo blkid -c /dev/null
``` We might get some better clues about what went wrong from that.

---

### Post by david503 on 2018-12-17
Ok quick question- the ubuntu mate dvd is also a live disk, right? Like you mean I should boot into it and there's a live mode instead of an install mode?

Alternatively I've got a recent knoppix disc and an ALT Regular Rescue disc that buned last night to run smartctl on this drive thinking it's a hardware problem (that's actually what they told me to do on the MATE forum when I posted about this problem.) 

So the ubuntu mate disc has a live mode is that what you mean right?

---

### Post by TheFu on 2018-12-17
Yep.  "Try Ubuntu" or something like that.  I'm assuming you got the ISO from an official source.  Non-official places can mix whatever they want.

If there's a Rescue Mode offered, that can be handy too.  It is always best to use the same release that you installed to try and fix things since the programs will be built with the same libraries.  If you use a different release/version, it is possible that some configs had changed and the older tools won't work with the newer versions.  For example, for a few years, it wasn't safe to use fdisk with GPT partitioned disks. We had to use parted instead.  Between 16.04 and 18.04, network configurations have been completely changed.   And the versions of grub are different between every major release, I would expect.

Why doesn't Windows have issues like this?  Because they ignore non-MSFT OSes.  Just for fun, install any Linux, get it working, reboot a few times to be certain life it great.  Then install Windows.  I hope you didn't need any of that data.

---

### Post by david503 on 2018-12-17
Oh- windows is running on the other drive- in fact that's why I unplugged the drive when I installed ubuntu, because I didn't want ubuntu's installation to even be able to touch it.  So, no need to worry if I reinstall windows but I bet you're right that if I did it on the same dive it'd kill the ubuntu install.

Hey but you mention that the versions of grub are different between 18.04 and 16.04?   Do you know if  the MATE distro is an install for 18.04?  I guess I can find that out....

Ok what they told me when I asked about my problems in the mate forum is that it could be a broken drive.  Now from what you guys have told me, that was probably wrong.

Nonetheless- here's my plan- tonight I'm going to run smartctl -t long on the ubuntu drive (booting from an ATL Regular Rescue disc).  I booted to it before and checked and it's say it'll take like 220 minutes. So I'll run it while I'm sleeping.  I figure that's easy enough to do and hell I should do it anyway if I'm gonna switch back to ubuntu from windows and use that drive as my main drive.

Thanks for your help TheFu and algreeny, I'll tell you how it all goes down tomorrow.

> **ajgreeny said:**
> Most normally it does not happen in Ubuntu either, so as others have suggested, I suspect this is not directly related simply to adding another drive.

Boot to a live Ubuntu system and see if the Windows drive is mountable from that or if it throws a lot of errors when you try mounting it.
Also run terminal commands ```
sudo fdisk -l | grep /dev/sd*
sudo blkid -c /dev/null
``` We might get some better clues about what went wrong from that.


Ok answering questions here: Yes I was able to mount the windows drive without error.

mount -t ntfs /dev/sda4 /mnt


Here are the other two commands you asked for:

```

ubuntu-mate@ubuntu-mate:/mnt/Users/bog/Downloads$ sudo fdisk -l | grep /dev/sd*
grep: /dev/sda1: Permission denied
grep: /dev/sda2: Permission denied
grep: /dev/sda3: Permission denied
grep: /dev/sda4: Permission denied
grep: /dev/sda5: Permission denied
grep: /dev/sdb: Permission denied
grep: /dev/sdb1: Permission denied

```


```

ubuntu-mate@ubuntu-mate:/mnt/Users/bog/Downloads$ sudo blkid -c /dev/null
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/sda1: LABEL="WINRE_DRV" UUID="DCAC19E4AC19B9CA" TYPE="ntfs" PARTUUID="10eea588-35ec-4e97-8603-c805b554b92c"
/dev/sda2: LABEL="SYSTEM_DRV" UUID="0E1A-A3A8" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="b9a920a8-9965-4fea-b730-fdedcc050bd7"
/dev/sda3: PARTLABEL="Microsoft reserved partition" PARTUUID="b2f7d6ee-9af9-444c-a2c9-57de2c0f20ce"
/dev/sda4: LABEL="Windows8_OS" UUID="7E2E1CCB2E1C7E79" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="38f917af-94a9-46fc-88db-3522e0a99b31"
/dev/sda5: LABEL="Lenovo_Recovery" UUID="3EAC1812AC17C2F7" TYPE="ntfs" PARTUUID="13f0c9ad-733b-4191-b87f-7eaf02cfbf76"
/dev/sdb1: UUID="65f144b4-d277-4b55-9faf-328931842dcc" TYPE="ext4" PARTUUID="09fb2230-01"
/dev/sr0: UUID="2018-07-25-03-37-28-00" LABEL="Ubuntu-MATE 18.04.1 LTS amd64" TYPE="iso9660" PTUUID="4ad90688" PTTYPE="dos"


```

For good measure since I'm pasting this boot repair summary to oldfred in the other thread I may as well paste it here:


Here's the output of  (too big to post):

[https://paste.ubuntu.com/p/5np2H4ZTjM/](https://paste.ubuntu.com/p/5np2H4ZTjM/)

thanks

---

### Post by oldfred on 2018-12-18
You are into other version issues.
There are two versions of grub, one for UEFI grub-efi-amd64 and one for BIOS grub-pc. You seem to have both.
Since Windows is UEFI, you should only be booting and installing in UEFI mode to gpt partitioned drives. And with UEFI better to use gpt (I suggest gpt in all cases unless booting Windows in BIOS mode on same drive).

Your sdb drive is MBR(msdos), you can convert to gpt, but it looks like it would be better to just reinstall. And since second drive better to either disconnect Windows drive and boot install media in UEFI mode to install in UEFI mode.
Or if not disconnecting drive, you have to convert drive to gpt, and partition with at least an ESP - efi system partition (FAT32) and / (root). Other partitions like /home or data partitions are then optional.

Only boot installer in UEFI mode.
       Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [URL="https://help.ubuntu.com/community/UEFI"]https://help.ubuntu.com/community/UEFI
      [/URL]
 MBR(for BIOS) or gpt(for UEFI) partitions:
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) 
    [URL="https://help.ubuntu.com/community/UEFI"]
[/URL]

---

### Post by david503 on 2018-12-18
Note: I did not start two threads on the same issue.


This thread is asking if I could install MATE on an existing  ubuntu install.  I mentioned the reason why which led to a different  conversation.

I did not start two threads on the same issue.

---

### Post by oldfred on 2018-12-18
You can install as many desktops as you want as meta packages.
But when I have done it in the past, I had some conflicts between versions.
I suggest separate installs.

 The key meta packages of Ubuntu are :
ubuntu-base (the whole base system which everybody should install)
ubuntu-desktop (the whole gnome environment)
kubuntu-desktop (the whole kde environment)
xubuntu-desktop (the whole xfce4 environment)
lubuntu-desktop (the whole LXDE desktop environment)
edubuntu-desktop (the whole kids/schools oriented gnome environment)
mate-desktop (MATE Desktop Environment)
Or:
sudo apt-get install ubuntu-desktop 
sudo apt install mate-desktop

then at log in screen and gear icon choose which desktop you want.

---

### Post by david503 on 2018-12-18
@oldfred

Wow that first link is great- so much info there.

So here's something to make things more complicated:

I had set up my BIOS to use "legacy boot first" and "UEFI" second.  I don't mean the drive order- I mean the method- legacy over UEFI.  

If I set it back to "UEFI first" in BIOS and reinstall ubuntu- from what I read in the first link page it looks like if I use the "automatic partitioning" and "erase the entire drive", then it will use UEFI, right?  I don't need to specify UEFI during the install, right? It will just default to UEFI when it installs grub?  

If that's the case- here's my plan, let me know if this is right:

1. I'm going to go into bios and switch to UEFI.  
2. I'll disconnect the windows drive. (I really don't want this to change anything on the windows drive at all.)
3. I'll reinstall Ubuntu mate on the other drive.
4. I'll boot into ubuntu just to see if it works.  (I saw in the first url that if I see the purple screen then that's not the UEFI version of grub. The black screen will be the UEFI grub, right.)
5. I'll reconnect the windows drive.
6. I'll reboot. 
7. What will happen? Which drive will boot?  I can still set the drive order in the bios right?


Is that a good plan?

---

### Post by CatKiller on 2018-12-18
That sounds like a plan.

It will be best to set the Linux drive to boot first. It's much easier to make the Linux bootloader chainload the Windows bootloader than the other way round.

---

### Post by oldfred on 2018-12-18
Many UEFI lose the UEFI boot settings for a disconnected drive.
But most of those will auto find Windows, they just never find any other system.
You can then use efibootmgr from live installer, or a repair disk to reinstall boot loader which also then adds a new UEFI boot entry.

See 
man efibootmgr

Some examples of recreating UEFI boot entries with efibootmgr in link in my signature.
See restore Windows boot manager in C:

---

### Post by david503 on 2018-12-18
> **oldfred said:**
> Many UEFI lose the UEFI boot settings for a disconnected drive.
But most of those will auto find Windows, they just never find any other system.
You can then use efibootmgr from live installer, or a repair disk to reinstall boot loader which also then adds a new UEFI boot entry.

See 
man efibootmgr

Some examples of recreating UEFI boot entries with efibootmgr in link in my signature.
See restore Windows boot manager in C:

God, the more I'm reading about UEFI the more terrible it seems. I don't see the advantage; what's the point.  It's just needless trouble with no advantage...

---

### Post by TheFu on 2018-12-18
> **david503 said:**
> God, the more I'm reading about UEFI the more terrible it seems. I don't see the advantage; what's the point.  It's just needless trouble with no advantage...

There are multiple advantages to UEFI
* faster boot, 
* effectively unlimited boot software size, 
* more advanced encryption can be used earlier in the boot.  
* And for Windows, support for booting on GPT formatted disks.  
That's just off the top of my head.

The negatives are 
* it is a change
* it can be more complex in a mix-environment

BTW, the Linux Foundation recommends using Secure Boot + UEFI BIOS to get the best validation of the entire boot process and help prevent pre-boot malware.  [https://github.com/lfit/itpol/blob/master/linux-workstation-security.md](https://github.com/lfit/itpol/blob/master/linux-workstation-security.md) has their guidelines.
> This is a set of recommendations for your workstation before you even start with OS installation.
Checklist
[LIST]
[*]    UEFI boot mode is used (not legacy BIOS) (ESSENTIAL)
[*]    Password is required to enter UEFI configuration (ESSENTIAL)
[*]    SecureBoot is enabled (ESSENTIAL)
[*]    UEFI-level password is required to boot the system (NICE)
[/LIST]



---

### Post by david503 on 2018-12-18
Thank you for the info.  But doesn't it tie the pc into certain OSes/companies?  I mean since it locks to firmware.... ?   Or at least make it a pain in the ass to use anything else but windows?

I mean this whole potential mess that oldfred was just talking about in his last post above- I would never have that problem in the "legacy" bios way to do it.  (And as for "faster boot", I couldn't care less.)

Hey what happens if I want to boot from a dvd or usb stick that doesn't have UEFI?  The bios says that UEFI drives boot first.  So what do regular people who don't know how to change their bios like we do- what do they do?

---

### Post by oldfred on 2018-12-18
It was Microsoft that converted all new systems to be UEFI when it released Windows 8 in 2012. Apple had started using an early version of EFI which became UEFI v1 where Microsoft in 2012 was UEFI v2.

I saw somewhere that Intel's recommendation to hardware vendors is that in 2020 systems be UEFI class 3 which is UEFI only, no CSM/Legacy/BIOS boot mode.
        CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

---

### Post by david503 on 2018-12-19
> **oldfred said:**
> It was Microsoft that converted all new systems to be UEFI when it released Windows 8 in 2012. Apple had started using an early version of EFI which became UEFI v1 where Microsoft in 2012 was UEFI v2.

I saw somewhere that Intel's recommendation to hardware vendors is that in 2020 systems be UEFI class 3 which is UEFI only, no CSM/Legacy/BIOS boot mode.
        CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode

OK and what's your opinion of that?  Is it so they can lock their OS in?  Well the reason I ask- the PC I'm on now (a Lenovo from about 3 years ago), it's running Win10 (it came with win 8), and I was on the phone with tech support about something unrelated to this, but I was astonished to find out that my copy of win 8 could only be used on this PC.  That's because of UEFI right?  What's your opinion of that?  I hate that...

Anyway btw, I'm about to go back down in right now and execute my plan as describe above, wish me luck! I'll let yall know how it goes either way.  Thanks guys here I go,

d

....and total frustrating failure again.  Here's what I did:

(And hopefully this whole struggle with benefit others..... )

1. Went into bios and switched to UEFI first instead of legacy first.
2. Rebooted just to see if windows can still start up. Yes.
3. Shut down and disconnected windows drive. Rebooted to ubuntu mate install disc.
4. Installed to (what I hoped will become) the ubuntu drive.
5. Shut down, connected the windows drive, checked bios to set the ubuntu drive to have priority in boot sequence. 
6. Saved bios and booted to ubuntu drive.

7. (initramfs) prompt. 


[bitchmode]
I can't believe how difficult this whole thing is, this is like pulling teeth. Would I have this problem in windows?  It's impossible for me not get frustrated and bitch about this whole thing. I mean I'm obviously not saying it's your guys' fault it's just; this seems to be a simple scenario that ubuntu is failing at. Ok moving on,
[/bitchmode]


Some information- the (initramfs) prompt was direct- meaning there was no purple screen first, it went straight to black; which from reading the url oldfred provided, means that it was, in fact, using the UEFI version of grub.  So at least that's a "success". 


8. Rebooted into ALT Rescue disc, ran fdisk -l to check, and both drives are using gpt now.  (before, one of them was using msdos right? so at least that was successful. )
9. Rebooted into ubuntu mate install cd again in live mode.
10. Installed Boot-Repair and pbcopy.
11. Realized I didn't need pbcopy since it lets me get a pastebin directly lol haha- but pbcopy is damn handy fyi if you haven't heard of it.
12. Here's the Boot-repair summary:  [http://paste.ubuntu.com/p/k8JphNzDsG/](http://paste.ubuntu.com/p/k8JphNzDsG/)
13. Rebooted, went to ubuntuforums posted thorough documentation of events, and bitched about ubuntu.


From the pastebin I noticed right away that it says:


```

============================= Boot Info Summary: ===============================


 => No boot loader is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.

```


I have a feeling you're going to suggest that I have Boot repair actually do something instead of just the summary?  (In other words, the "Recommended repair" button....) 


The saga continues,


d

---

### Post by oldfred on 2018-12-19
Windows has always been licensed to only the PC you originally install it into. 
And new UEFI has the Windows product key in the UEFI. That does make it easier to reinstall as then it automatically is used.

Lenovo has become one of those that modified UEFI and use description as part of boot. And of course only valid description is "Windows Boot Manager". That is not allowed if they fully complied with UEFI standard. 
Did you update UEFI from Lenovo for your system? Some others with similar issues found it helps. Not sure about Lenovo, though.

The main work around is the UEFI fallback or hard drive boot entry. That is /EFI/Boot/bootx64.efi.
You already have that in your ESP on sda, but that probably is a copy of Windows boot file.
You have the folder /EFI/Boot in your ESP on sdb, but it only has fbx64.efi. Report is not showing a bootx64.efi.
Report also is not showing a /etc/fstab? And it shows file corruption on your Linux partition sdb2.

First lets see if this fixes corruption.
       To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb2 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb2
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb2

Years ago the fix for systems that only booted Windows by description was to manually copy shimx64.efi to /EFI/Boot/bootx64.efi and then boot hard drive entry in UEFI not ubuntu entry.
If you run Boot-Repair it will do the copy.
You have an old ubuntu UEFI entry to boot an older install in your sda. That entry in UEFI will not work. Only the new entries for ESP on sdb. Later we can delete the old entry.

---

### Post by david503 on 2018-12-19
Ok great thank you, I will attempt your first suggestion.

Two things:

If it doesn't work and I have to run Boot-Repair, will it modify the windows drive?  I'm ok with running it as long as it doesn't touch the windows drive.  But for now I'll  go in and attempt your first suggestion.  

Second thing- fyi (and you might already know this)- but when I did the install I chose the "erase entire drive" install.  So there's no remnant of anything we tried before. (I bet you already gathered that sorry!)

Last thing- you had said "[COLOR=#000000]Windows has always been licensed to only the PC you originally install it into. "[/COLOR]


Well, yea, but you could go to a store and buy windows and then install it on any pc you want.  But right now if you buy it bundled with the actual PC then you can't use it on any other PC- and that's new, right? They couldn't do that before UEFI,  no?  When reading your response I think I understand that lenovo is doing something against the standard, so they're sort of breaking the "rules"?  If that's the case I won't buy anything from lenovo again.  What kind of PCs do you buy? or do you make your own (like I used to)? 

Thanks as always, here I go,

d

---

### Post by oldfred on 2018-12-19
When I purchased XP, and installed it to my own build, it connected to Microsoft and recorded the PC info.
I then had a video card short out and when I replaced it, I had to nicely tell Bill Gates it really was the same computer & they reauthorized it.
And all new systems regardless of vendor comply with Microsoft and the original copy of Windows is only valid for your system. That is why backups are vital. 

The Ubuntu grub in UEFI boot mode, only installs to the ESP on the first drive. So you have left over info in your Window's drive's ESP. Its an extra /EFI/ubuntu folder which you now can delete. And UEFI remembers setting until a drive is disconnected. You can use efibootmgr to remove old or duplicate entries in UEFI's memory. UEFI uses GUID to know which ESP to look for more boot info.

       to see GUID/partUUID for each device, post with code tags to preserve formatting:
lsblk -o +PARTUUID /dev/sda 
   # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr

---

### Post by david503 on 2018-12-19
Wow I'm impressed with how much you know about this! Amazing!

So I'm back from the struggle again, here's the output:

 ```

ubuntu-mate@ubuntu-mate:~$ sudo parted -l
Model: ATA ST1000DM003-1ER1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags:

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  1050MB  1049MB  ntfs                                       hidden, diag
 2      1050MB  1322MB  273MB   fat32        EFI system partition          boot, esp
 3      1322MB  1456MB  134MB                Microsoft reserved partition  msftres
 4      1456MB  989GB   987GB   ntfs         Basic data partition          msftdata
 5      989GB   1000GB  11.5GB  ntfs                                       hidden, diag


Model: ATA WDC WD1001FALS-0 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  538MB   537MB   fat32        EFI System Partition  boot, esp
 2      538MB   1000GB  1000GB  ext4


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Model: HL-DT-ST DVDRAM GP65NB60 (scsi)
Disk /dev/sr0: 2007MB
Sector size (logical/physical): 2048B/2048B
Partition Table: mac
Disk Flags:

Number  Start   End     Size    File system  Name   Flags
 1      2048B   6143B   4096B                Apple
 2      1967MB  1969MB  2392kB               EFI




```



Wow it says "mac" and "apple" in there! Is that normal?


```


ubuntu-mate@ubuntu-mate:~$ sudo e2fsck -C0 -p -f -v /dev/sdb2
e2fsck: Superblock checksum does not match superblock while trying to open /dev/sdb2
/dev/sdb2:
The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device> 

```



Also- while I was in there on the live disc I tried looking at the drives in the GUI, and I could see and modify the windows drive ok, but when I clicked on the ubuntu drive (hard drive not dvd),  I got a dialog "Error mounting /dev/sdb2 at /media/ubuntu-mate/[and some long serial number]:  cannot mount; probably corrupted filesystem on /dev/sdb2.


It's important that I point out- about 3 nights ago I ran smartctl -t long on this drive overnight and it took 4 hours and passed.  Also, I've run badblocks on it drive and it passed too.


So then I ran this: (and I didn't include all of the results, because it was a hundred lines of "Inode [34023625] seems to contain garbage.  Clear? yes" so this is just the tail:


[COLOR=#000000]sudo e2fsck -f -y -v /dev/sdb2[/COLOR]

```


Inode 34023625 seems to contain garbage.  Clear? yes

Inode 34023626 seems to contain garbage.  Clear? yes

Inode 34023627 seems to contain garbage.  Clear? yes

Inode 34023628 seems to contain garbage.  Clear? yes

Inode 34023633 is in use, but has dtime set.  Fix? yes

Inode 34023633 has a extra size (8295) which is invalid
Fix? yes

Special (device/socket/fifo) inode 34023633 has non-zero size.  Fix? yes

Inode 34023634 is in use, but has dtime set.  Fix? yes

Special (device/socket/fifo) inode 34023634 has non-zero size.  Fix? yes

Inode 34023634, i_blocks is 791289928, should be 0.  Fix? yes

Inode 34023649 is in use, but has dtime set.  Fix? yes

Inode 34023649 has imagic flag set.  Clear? yes

Inode 34023649 has a extra size (17735) which is invalid
Fix? yes

Special (device/socket/fifo) file (inode 34023649) has extents
or inline-data flag set.  Clear? yes

Special (device/socket/fifo) inode 34023649 has non-zero size.  Fix? yes

Inode 34023650 is in use, but has dtime set.  Fix? yes

Inode 34023650 has a extra size (29811) which is invalid
Fix? yes

Inode 34023650 has INDEX_FL flag set but is not a directory.
Clear HTree index? yes

Inode 34023650, i_size is 3461371753639920978, should be 0.  Fix? yes

Inode 34023650, i_blocks is 107044649846087, should be 0.  Fix? yes

Inode 34023651 is in use, but has dtime set.  Fix? yes

Inode 34023651 has imagic flag set.  Clear? yes

Inode 34023651 has a extra size (29285) which is invalid
Fix? yes

Inode 34023651, i_size is 3761078573959809363, should be 0.  Fix? yes

Inode 34023651, i_blocks is 41920581870346, should be 0.  Fix? yes

e2fsck: aborted

/dev/sdb2: ***** FILE SYSTEM WAS MODIFIED *****
ubuntu-mate@ubuntu-mate:~$


```


(And no, I didn't manually abort it.)


I tried sudo e2fsck -C0 -p -f -v /dev/sdb2 afterwards and got the same results as before.


So then I tried rebooting into the ubuntu drive and still got the  (initramfs) prompt

> **oldfred said:**
> When I purchased XP, and installed it to my own build, it connected to Microsoft and recorded the PC info.
I then had a video card short out and when I replaced it, I had to nicely tell Bill Gates it really was the same computer & they reauthorized it.
And all new systems regardless of vendor comply with Microsoft and the original copy of Windows is only valid for your system. That is why backups are vital. 

The Ubuntu grub in UEFI boot mode, only installs to the ESP on the first drive. So you have left over info in your Window's drive's ESP. Its an extra /EFI/ubuntu folder which you now can delete. And UEFI remembers setting until a drive is disconnected. You can use efibootmgr to remove old or duplicate entries in UEFI's memory. UEFI uses GUID to know which ESP to look for more boot info.

       to see GUID/partUUID for each device, post with code tags to preserve formatting:
lsblk -o +PARTUUID /dev/sda 
   # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr

Oh Ok I'm only just seeing this now because I was down and under doing your other recommendation. (see previous post right above)

---

### Post by oldfred on 2018-12-19
The second command I posted on e2fsck has the -y for auto answer yes, to avoid those issue.
If this is a new install, at this point I might find it easier just to reinstall with total new reformat of sdb2.
You could run the suggested command with alterative superblocks if you really need to try to recover partition.

Not sure I have seen Mac except on Apple systems. But I do not know Mac, and only have a bit of info in my files. But it may depend on what tool you used to create live installer on DVD. DVDs normally are some sort of hybrid configuration now.
I have not used a DVD for years. In past I used to create a lot of coasters (bad burns). I even used one as a coaster for years. I converted to flash drives as they can be reused. but now mostly use grub to directly loopmount ISO from one drive to install to another drive. I typically have a full install on every drive including larger flash drives.

Are you burning DVD at slowest speed you can use. It may take longer but often has better results.

Make sure you have a valid download of ISO. I normally use zsync which just updates an ISO & verifies it, but I have to run that from command line on a working install.

---

### Post by david503 on 2018-12-20
> **oldfred said:**
> The second command I posted on e2fsck has the -y for auto answer yes, to avoid those issue.
If this is a new install, at this point I might find it easier just to reinstall with total new reformat of sdb2.
You could run the suggested command with alterative superblocks if you really need to try to recover partition.

Not sure I have seen Mac except on Apple systems. But I do not know Mac, and only have a bit of info in my files. But it may depend on what tool you used to create live installer on DVD. DVDs normally are some sort of hybrid configuration now.
I have not used a DVD for years. In past I used to create a lot of coasters (bad burns). I even used one as a coaster for years. I converted to flash drives as they can be reused. but now mostly use grub to directly loopmount ISO from one drive to install to another drive. I typically have a full install on every drive including larger flash drives.

Are you burning DVD at slowest speed you can use. It may take longer but often has better results.

Make sure you have a valid download of ISO. I normally use zsync which just updates an ISO & verifies it, but I have to run that from command line on a working install.

Wow ok, so, if I read you right, you're suggesting that the problem could be the iso file and/or the dvd media itself?  

Well, I'll burn at a slower speed I spose, and I'll even switch to a different brand of blank dvd, but... I mean we both know there's a 99% likelihood that the exact same thing will just happen again.  

Oh- btw, I downloaded the iso via torrent.  So- as you probably know- the file is almost surely clean because otherwise the torrent would stop (well or correct the file). I mean I guess it's still *possible* but it's so rare...

Oooohhhh wait- are you saying that the problem is that the *windows* drive has a remnant  /EFI/ubuntu[COLOR=#000000] somewhere?  I mean I can't see it when I search C:/  So it's either in some other partition of the windows drive, or like in the MBR or something like that right?  I think I'm beginning to understand...[/COLOR]

So before I burn the media I'll try your instructions from 7 hours ago.

But- that's going to alter the windows drive, right?  Isn't there a risk?  I guess your CLI line:

[COLOR=#000000]sudo efibootmgr -v[/COLOR]

I see, I'm reading your comment again- so that's where I'll determine what I should be deleting on the windows drive right? Without touching anything...yet. 

Ok I'll go back in to the live disc and take a look using the -v option.  One more question though-

When you said "You could run the suggested command with alterative superblocks if you really need to try to recover partition"  Are you talking about one of the windows partitions?  Because if you mean the ubuntu drive's partitions, I don't care about them at all. But the windows partitions- I can't loose my ability to go back into windows (even though I'm backed up, I still can't be without the use of windows entirely). 

thanks as always.

---

### Post by oldfred on 2018-12-20
The e2fsck command you posted suggested running the repair of sdb2 with alternative superblock. It a command gives a suggested additional fix, often best to also try that.

Windows does not normally show boot partitions(BIOS) or the ESP(UEFI). You have to manually mount using Windows tools & then you can see that partition.

Use of efibootmgr is just to manage the entries in the UEFI for booting.
see this, not sure man page is in live installer
man efibootmgr

If Windows is the first drive and still plugged in, grub will install its boot files into the existing ESP and a new folder /EFI/ubuntu on the Windows drive.
Only when installing Ubuntu on the same drive as Windows and you choose one of the install options that is a full drive install does Ubuntu delete Windows.  Or if you force an auto install on same drive when Windows is hibernated/fast start up on. Then the installer does not see the NTFS partition.

But you should always have good backkups. And in particular should have a new backup when making major system changes.

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)
Microsoft Windows 8.1 reinstall/refresh
[http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media)

---

### Post by david503 on 2018-12-20
Ok I read what you're saying a couple times- 

Would it be equivalent risk if I just give up and connect the windows drive and do a ubuntu reinstall on the ubuntu drive again?  

So- once again- I do the same install as before- intentionally erasing the ubuntu drive during the install only this time with the windows drive plugged in, the installer will modify the windows drive's "hidden" EFI stuff? (the "[COLOR=#000000]boot partitions(BIOS) or the ESP(UEFI)" ?)  but presumably it will leave the rest of the data alone?  (And windows will still be bootable afterwards?) [/COLOR]

(And yes I've backed everything up, I'm just wondering what will happen)

So that will be equivalent to the [COLOR=#000000]efibootmgr lines you advised[/COLOR]?

thanks

d

---

### Post by oldfred on 2018-12-20
I still prefer to have an ESP on every drive, but you have to partition in advance.

You can just reinstall as you suggest and grub will be in the ESP on the first drive. Windows should not be modified.
If overwriting an existing install, still best to only use Something Else install option. Then you can see and have more control over what it really is doing.

---

### Post by david503 on 2018-12-21
Ok wait when you say an "existing install" you mean the ubuntu install right?  As you know I don't care about that drive, I've wiped it every time I've installed it.

But anyway let's make two scenarios:

I connect the windows drive and do an install on ubuntu drive and choose default options instead of "Something else".
Presumably (fingers crossed) all will be well and the bootloader (in the "hidden" partition of the windows drive) will provide me the option of which to boot, yes.

But if I disconnect the windows drive, will ubuntu still boot. And/or inversely  if I disconnect the ubuntu drive, will windows still boot? 


Second scenario is to use the "Something else"...  you're advising that that's preferred, yes?  But I don't know what to select within those options. You know what I'm sayin? What should I do within "something else"? I mean I know how to allocate /home in one partition and / and /swap and the relative sizes for each, and maybe like, /tmp I guess, but is there anything else in there in the "something else"? 

thanks upon thanks man,

d

---

### Post by oldfred on 2018-12-21
I prefer to partition in advance with gparted, and then in Something Else you you still choose change, but partition already exists, you do not have to recreate it.

       gparted & fdisk instructions:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[URL="https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions"]https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions
[/URL]
 It is recommended to use always GPT for UEFI boot as some UEFI firmwares do not allow UEFI-MBR boot.
You can also use gparted but must change default partitioning first.
Select gpt under device, advanced over msdos(MBR) default partitioning before starting. 

 UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu) 
    [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) 
    [URL="https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions"]
[/URL] I suggest 300-500MB efi partition - FAT32, 25GB /(root) - ext4, and then  either /home - ext4, or /mnt/data partition(s). But you cannot do data  partitions as part of install. 

 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap(prior to 17.10), but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]25-30+ GB Mountpoint / primary or logical beginning ext4 
[*]all but 2 GB or all (See below if 18.04 or later) Mountpoint /home logical beginning ext4 
[*]2 GB Mountpoint swap logical (not required with 17.04 and later uses a swap file, if no swap partition found) 
[*]You do not need to create swap, as it either finds existing swap partition, or creates in fstab the following swapfile entry: 
[*]No swap partition for 18.04 or later, it uses a swap file like this entry in fstab: 
[/LIST]
   /swapfile                                 none            swap    sw              0       0

---

### Post by david503 on 2019-01-02
Ok, holidays are over; so here's how things have resolved: This is mostly a happy ending:

My Windows hit by a horrible virus.  A trojan, and not a normal one- it was a *manual* attack- as in, I later could tell someone had physically logged in to the windows pc and attempted to get stuff to fulfill the message in my browser claiming I had to call a 1800 number to "stop identity theft".  :o 

So, anyway, all that spurred my to get around to tackling MATE installation again:

I bought a new 2 gig drive (thus eliminating the possibility of corruption),

I disconnected the windows drive and then installed MATE on the new drive.

After booting into MATE I immediately shut down, connected the windows drive, and rebooted into Windows to see if doing so destroys MATE's bootloader because windows is evil, then booted into bios and took the windows drive out of the boot sequence entirely, then rebooted into MATE to see if it could still boot. It could.  (I'm in MATE right now.)

Then there was a bit of a snafu because I tried installing LXQT, and it totally rendered my MATE install useless (unless you're a WM developer which most ubuntu users aren't.)  And when I installed MATE I had told it to log me in automatically rather than prompt for a password.   So I posted to the LXQT forum and got exactly what I expected- a bunch of tapdancing and "not our problem", "it's your fault", etc.  I'll post a link to it if you want, it's hilarious.

So anyway, I did the entire process over again - disconnect windows, reinstall MATE, boot to windows, etc...

So the "resolution" is that, as intended, my "bootloader" (well, I mean the aspect of switching between OSes), is now simply just my bios (and by that I mean UEFI- I mean going into bios and changing the boot sequence).  So, if I want to boot to windows (which I basically hope to never have to do), I boot into bios, give the windows drive priority, and then boot.  And when I want to go back to ubuntu, I do the reverse.

Also I've installed a virtualbox running Windows, so I think the only time I'll ever need to boot into that windows drive is if the ubuntu drive crashes.  (Which is what happened months ago).  

So that's how the dust settled.  Bios itself is my bootloader.  (well, I mean, in terms of switching between OS's- I mean "bootloader" means more than that I know.  I should probably use a better term...) 

Thanks guys, especially @[COLOR=#000000]oldfred[/COLOR]

And if anyone with similar problems finds this in their search results and has any questions let me know I'll answer,

d

---

### Post by oldfred on 2019-01-02
I think it is boot manager that UEFI & rEFInd call it. Grub then is both a boot manager & a boot loader.

With UEFI, I have issues with grub and multiple installs of Ubuntu or other flavors. Every install uses /EFI/ubuntu. But I have one main working install which I want to be the default and boot the others from grub. There is a way to not install grub by using command line and using ubiquity -b. But I also want to see what improvements (if any) they have made to grub. So I quickly learned to backup my ESP - efi system partition which usually is not backed up.

You can change to [Solved] so others can find thread.

---

### Post by CatKiller on 2019-01-02
> **david503 said:**
> So the "resolution" is that, as intended, my "bootloader" (well, I mean the aspect of switching between OSes), is now simply just my bios (and by that I mean UEFI- I mean going into bios and changing the boot sequence).  So, if I want to boot to windows (which I basically hope to never have to do), I boot into bios, give the windows drive priority, and then boot.  And when I want to go back to ubuntu, I do the reverse.

As a potential optimisation of this step, there may well be a key you can press to bring up the boot priority menu for just that boot without having to go into the BIOS. Saves you two reboots.

---

### Post by david503 on 2019-01-02
> **oldfred said:**
> I think it is boot manager that UEFI & rEFInd call it. Grub then is both a boot manager & a boot loader.

With UEFI, I have issues with grub and multiple installs of Ubuntu or other flavors. Every install uses /EFI/ubuntu. But I have one main working install which I want to be the default and boot the others from grub. There is a way to not install grub by using command line and using ubiquity -b. But I also want to see what improvements (if any) they have made to grub. So I quickly learned to backup my ESP - efi system partition which usually is not backed up.

You can change to [Solved] so others can find thread.

Oh wow I didn't think of just copying /boot somewhere as a backup. So that if windows messes with the ubuntu drive, I can presumably just boot to a live disc and just copy the old boot back?   (I keep hearing people say that windows can render a ubuntu drive unbootable)

Anyway thanks again, I marked it solved,

d

---

### Post by oldfred on 2019-01-02
Yes, maybe.
UEFI has the boot file in the ESP. As long as it is the same ESP as UEFI searches for boot entries by GUID which is reset (like UUIDs) if partition is reformatted. New install may reformat it, but you should make sure not to check format box on ESP (and /home parttion) when installing, anyway.

And the grub in /EFI/ubuntu/grub.cfg which is just three lines, looks for the install & full grub.cfg to boot from. I now typically backup ESP, but just edit the ESP's grub.cfg.

Both Windows & Ubuntu/grub on a new install or major update will reset themselves to first in UEFI boot order. Then as CatKiller pointed out, you should be able to manually choose what to boot from UEFI boot menu (same menu you used to choose flash drive installer).
Then you can use your UEFI or efibootmgr in Ubuntu to reset boot order.
see this for more options of managing UEFI boot entries in UEFI from Ubuntu.
man efibootmgr

---

### Post by david503 on 2019-01-02
Oh ok I think I get it.  So to get the UEFI boot menu without going into bios, there's probably some other F key to hold down (F1 is bios), and that will vary per pc vendor, (per bios firmware), so I'll have to just google around or look in the spec pdf for which key, right.

Also- when I installed MATE I don't remember anything about ESP.  (Is it probably unchecked by default I hope?)  I didn't see that setting, I took the default partition scheme, not custom...

Ok I'll go look at the man page for efibootmgr.

Thanks as always,

d

---

