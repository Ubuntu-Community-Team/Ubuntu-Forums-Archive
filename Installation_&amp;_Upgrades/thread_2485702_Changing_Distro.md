---
title: "Changing Distro"
date: 2023-04-06
forum: Installation &amp; Upgrades
---

### Post by ajohnl on 2023-04-06
:P  To Ubuntu of course.
I have used another distro for rather a lot of years. Recent upgrades have been a bit problematic in terms of some software packages not being updated to run on it. I am not a console warrior. I am primarily a desktop user. So I feel it's time for a change.

I have a machine that dual boots windows 10 and the other distro. I hardly ever use windows. Maybe once or twice a year. So I want to install Ubuntu over the distro without interfering with windows use. I understand that the current installs do not check for what is currently installed. I have trashed a new pc with win11 by installing linux assuming it would do what it always has done before - shrunk windows partition and then installed linux in the space created. No warning and even the bios has problems due to uefi corruption. The older PC also uses this but the install didn't corrupt it. It looks like it will take a while to sort out the new machine.

So advice needed. I'd be reluctant to try and install via the windows boot and obviously that has been replaced by a linux boot anyway.

:o Help!

---

### Post by ubfan1 on 2023-04-06
I think what you recall "what it always has done before" is not accurate, but for your current re-install, select the "something else" choice, and you can then select the partition you want root, swap, etc. No changes needed in the partitioning, just select the one on which the old distribution uses.

---

### Post by ajohnl on 2023-04-06
Thanks for the suggestion but one of the partitions will be the for boot which currently also supports a windows boot. From an Ubuntu review it seems that the recent releases use a new version of grub. It mentioned that if this was used when windows was on the machine it would not set up dual booting, windows would be lost. If Ubuntu can be installed without touching the boot partition all should be fine. However wouldn't grub report my current disto name not the new one? Or does gub obtain the name from the partition it's booting to. I have no idea.

Partitions. The current distro on the machine doesn't ise a swap partition and has a specific partition mapped to home and a couple of other partitions mapped in a certain way. I can tidy that up with Kabuntu as I assume that running Ubunto from a usb stick doesn't allow the main machines disks to be interfered with. I guess that Kubuntu probably still doesn't offer a UK keyboard. Pain but can cope.

Trying to change the partitioning in the way needed while the current distro is running is probably impossible as some will be active.

I have installed Linux a number of time. The recent ignore window being there and not setting up a dual boot is completely new to me or at least offering a choice. This maybe because Linux can be installed via wndows and it's boot system. That would seem to be a safer option if windows 11 is around. Not sure if it can be done with 10.

---

### Post by oldfred on 2023-04-06
Kubuntu is Ubuntu and has all of its features, just a different gui & set of default apps.
Underneath the same Linux & drivers. 

As suggested Something Else is the only way to preserve anything you have.
Only with BIOS installs does grub overwrite Windows boot loader in MBR, but then grub will boot working Windows. Some hassle then if Windows breaks.
With UEFI installs, you can always boot either install from UEFI boot menu.

Better to backup data rather than reuse /home. Your current /home may have settings that are not compatible with new Kubuntu. But needed setting should overwrite anything Kubuntu needs.

Install choices also include LVM, full drive, LVM full drive with encryption and those totally erase entire drive. Windows users may think a drive is just a partition as Microsoft has confused drives & partitions for years.

Newer Windows still can have its NTFS partition made smaller by installer, but some users end of having issues and blame Linux when almost always it was an issue in Windows. So best to always shrink NTFS partitions with Windows tools & reboot to run the required chkdsk after any resize.
Then Linux can be installed to unallocated space, or overwrite existing Linux partitions. Usually best to check format as part of install so partition is clean, but some cases users want to preserve some data & can install over the existing install & preserve some data.

---

### Post by ubfan1 on 2023-04-06
I heard grub changes ignore other Linux distros, but still catch Windows, but no direct experience with that.  You EFI System Partition (ESP) (one per boot device) should easily handle the Window and Ubuntu bootloaders if it's big enough. 4M Ubuntu bootloaders, 2M Boot device bootloader copies, 26M Microsoft.  A 100M partition might be on the small side if there is a leftover set of bootloaders from your old Linux. Just delete the old Linux files if space is a problem.  Whether or not grub boots Windows, you always can boot Windows directly from the EFI menu (some key at poweron to allow you to select a boot device or OS).
 A  /home should not be touched, but then if it was actually mounted at /home, and you actually mount it at /home on the new system, you get all the old dot files (.config, .local, .cache, etc.) -- configuration files for the old versions of programs which may cause problems.   Mount it under your new home as /home/<user>/data or some such.
  swapfile is used these days when there is no swap partition, so no need to make one.  Still see no need to do any partitioning if you are just going to overwrite an existing Linux partition. In any case, highly recommended to have full backups of everything before you start. The "something else" will do exactly what you tell it, and if you type in the wrong partition to install, it will happily write there, no warnings like "Overwrite Windows?...

---

### Post by MAFoElffen on 2023-04-06
@ubfan1 --

Grub2 is multi-OS... Si it treats Windows, Linux (which includes Ubuntu), MAC OSX, and UNIX as just OS'es that it supports.

It, currently has OS Prober disabled by defualt. it used to on by default... So if installed with current versions of Ubuntu, you have to add a line in the /etc/default/grub file to enable it...

***
If you do not care about what was there, my thoughts last might on what might be easier: First, as oldfred said, get a backup. You never know for sure what might be important to you. 

Then I would be to use "Try" in the LiveUSB and start GParted. In GParted, delete the partitions of the old Linux distro. Apply the change. Exit GParted. Be careful to select the correct partitions. This decision is not reversible. But having a good backup, you have a fallback.

At the desktop, start the installer. After the language and keyboard panels, the probe process should then see Windows, with unallocated space there and toggle the install option to show "Install alongside Windows..."

That would be easier for a new user to do.

---

### Post by ActionParsnip on 2023-04-07
Be sure to run a full backup before you start any of this. You can then restore if things go awry

---

### Post by guiverc on 2023-04-07
You didn't provide any Ubuntu product/release specifics... but mention a *recent* change to grub version; the last change I can recall was in [late 2021]("https://lists.ubuntu.com/archives/ubuntu-devel/2021-December/041769.html") which I don't consider recent.  That change caused a number of issues in the following weeks (*but it was easily worked around!* *being a change to OS_PROBER*) and the issue was then resolved (*well prior to jammy's [22.04] release**, ie. OS_PROBER is now as it was before in Ubuntu*).

I purchased five new [*refurshed]* systems in February (*from more than a single source too so installs differed*), they all came with windows installed (some w10 & others w11) & used them for QA-testing.. All had a Ubuntu system *installed alongside* & four were perfect, alas one had an issue that required work to get windows booting normally.. The *install alongside* (or auto-resize) however is the install that involves shrink, new partition & install, and is more likely to go wrong (*in my opinion!*) than a *replace* type of installation.

If the boot system is already booting with a GNU/Linux distribution, I'd not see any problem with just replacing that OS with a Ubuntu system, I perform that install ~weekly as part of my QA testing anyway...   though knowing what OS/product/release is involved (*which you didn't specify*) & details of the hardware may alter my opinion..  Also note I'm not a windows user, so when I re-install an OS, my 'testing of windows' involves just ensuring it boots & shutting down as quickly as I can before it wants to force upgrades on me...

FYI:  My last QA-test (for Lubuntu *lunar* anyway), was yesterday on an system that included 4 OSes including a non-Ubuntu. On reboot all OSes are picked up; its one of the things I test for!

---

### Post by yancek on 2023-04-07
> shrunk windows partition and then installed linux in the space created 

When doing a dual boot, installing any Linux after windows, you should always use the windows Disk Management tool to shrink the partition then reboot and run chdsk from windows.

> one of the partitions will be the for boot which currently also supports a windows boot 

Is this a windows boot partition or are you referring to the EFI partition with windows EFI boot files?  If your computer has an EFI install of windows, the boot files for it will be on the EFI partition and installing Ubuntu on it will create a separate ubuntu directory on the EFI partition and will NOT overwrite the windows boot files as they are in a separate directory named Microsoft.

> I assume that running Ubunto from a usb stick doesn't allow the main machines disks to be interfered with.

No, that is not correct and is actually the preferred way to do it. 

>  This maybe because Linux can be installed via wndows and it's boot system. 

I'm not sure what you mean by this comment.   You can't install Linux via windows unless you are using something like WSL or using it to create a bootable USB.  I'm not aware of any way you can boot an EFI install of Linux with the windows bootloader.

---

### Post by ajohnl on 2023-04-07
The trashed win11 machine is my fault. On the distro I have used in the past the default install with windows around was shrink it's partition and then install. Normally I would change the partitioning but the reasons for doing that have gone so didn't really look at what it was about to do and went ahead. Net result working Linux, unhappy windows and an unhappy bios in places. An HP machine. Rather compact work station. The comment about grub probing being disabled by default may be the root cause. I haven't really looked at methods of recovering it. I suspect it will need work via HP doing it.

I'm probably confused concerning install via windows. Talk some time ago concerning windows being happy about other OS's on the same machine. For my use of it really it would be best to create installation media and install it via a VM under LInux. HP do not seem to be keen on providing the key to reinstall windows on a label on the ,machine. I also wonder what happens when this was done via a VM. This link outlines using windows  winn11 ?? don't know. Not something I would choose to do anyway,
[https://learn.microsoft.com/en-us/windows/wsl/install](https://learn.microsoft.com/en-us/windows/wsl/install)

The old machine that I mustn't trash. There is more than enough space available to create a new partition on it specifically for Ubuntu. Boot - not sure what it uses. I'd need to be using it. Linux was installed on in ~3years ago, It was a long term release. I looked at updating but noticed that a new version would be available  so didn't.  Now I do need to install and use some new applications I must update. Everything is backed up. Moving target. The email on the new machine now needs backing up in case any recovery method destroys it.  I'm trying to return the new HP machine for a refund, It has a design flaw. ;) Who messed it up - me but that''s another problem.

---

### Post by MAFoElffen on 2023-04-07
LMAO -- Yes. I can relate to self-inflicted issues over the years. No one is "immune."

Just tell us where you want to go to from here. The plan you have in your head. Your goal.

---

### Post by ajohnl on 2023-04-08
LOL The plan is tricky.
I've run Ubuntu from usb in trial mode. Ok but a bit of a culture shock from KDE for rather a long long time. But Ok, A few apps I use couldn't be found but are probably maintained.

I expected the machine to boot from USB as had given that priority via the bios. It didn't due to the installation. Fair enough. I noticed a UEFI setting entry on the distro start up menu so selected that. It came up with a section of HP's bios but with a different background colour. I didn't try to use it. I gave USB priority via the bios. Windows boot was marked disabled in both views of UEFI settings. Same code, for both or a duplicate???? Pass.

Then in order to look at the installation I had used I booted it up again. It came up with "policy violation, something is seriously wrong" and turned the PC off. I wanted to check if I had missed any install options such as view current partitioning as there is an option to quit without installing at the end. :( So now wonder what an upgrade on the older machine will show.

A plan. Tricky. Windows has been totally formatted over. It's gone. The HP bios is unhappy but it's not clear about what. It can usually access the web. There is reset option but no idea what that would do. Adding win11 to  a machine costs a fair amount of money. I think ~£200 for pro. I suspect I'll need help from HP to sort that out. It seems win iso's can be downloaded but 2 keys may me needed to activate it.Seems there are 2 but don't know which are actually needed.

The boot partition is 250m. I'll have to look on the older one. Probing the bios and uefi from the console with utilities doesn't show anything amiss other than win boot disabled - did the install do that? Pass. So plan currently is visit it's bios again to to try and see why it's unhappy and then start using the older machine and chase HP about the new one. Which I may not send back. Fan usage seems to have changed with use. Short very noisy periods. CPU fan which is a bit odd as the cpu is not that hot.

---

### Post by oldfred on 2023-04-08
Windows has its Product key in UEFI.
So you can just download Windows and install it, as long as same version. Home, pro etc.
Issues can be proprietary drivers which you have to download from HP's support site.

HP is not particularly Linux friendly, but most are able to get it to work.
It does not support efibootmgr's change of boot order, so new install will not be default. Grub uses efibootmgr to install entry into UEFI and change that entry to first in boot order. You have to go into UEFI settings (not UEFI boot menu) to change boot order.
HP also often wants to only boot entry "Windows Boot Manager". If not dual booting, we can create a new UEFI entry that says Windows but boots Ubuntu. The only check description not actual boot file.

Does system have Optane? Can can be an issue from many brands. Microsoft required small boot SSD (optane) to speed boot when using HDD. Most new systems now are SSD or NVMe SSDs, so do not need Optane. And now Intel is phasing out Optane as it was an expensive type SSD.

See link below in my signature for some general install info & links to more info.

---

### Post by MAFoElffen on 2023-04-08
> **oldfred said:**
> Windows has its Product key in UEFI.

HP, Dell and Lenovo do have their digital entitlement license key burned into the UEFI BIOS. As an On-Site Warranty Tech for HP, Dell, and Lenovo, when I changed motherboards, I had to burn the old key into the new motherboard, so that Windows would stay activated.

When reloading the Windows OS on a new drive, it would also be activated automatically, but, what is took was the OEM version of Windows from HP, Dell or Lenovo. That also ensured that the vendor util's and drivers were there.

Quoted from HP Support, RE: [https://support.hp.com/us-en/document/c04640037](https://support.hp.com/us-en/document/c04640037)
> 
Digital Product Key (DPK): A unique key provided by Microsoft and injected into a system BIOS that is used for activating Windows 10 on the system. This is also called a Digital License.

It is the same for Windows 11.

You could call HP and they mailed out their Windows USB thumb drive with Windows, or could provide you with a download link for that. At least for HP users that were still under warranty. I didn't deal with Users that were out of warranty. What would happen if they wanted us to reload the OS on a new drive, was that they mailed out the USB drive to the customer, and shipped the parts to us techs.

The link HP Support gave us Tech's to create our own install media was just from Microsoft: [https://www.microsoft.com/en-us/software-download/windows11](https://www.microsoft.com/en-us/software-download/windows11)

---

### Post by ajohnl on 2023-04-09
I've had several HP machines and this is the first I have had any problems installing Linux and retaining a running windows. They can also be bought Linux ready but that is not exactly obvious. Probably factory versions installed - pass, never looked into it. Personally after many years of use I am not fond of the Linux side saying it's them it's them etc as often it isn't as clear as that.

;)Anyway still on the new machine having checked the bios out as far as I can. Most seems to be ok. The missing aspect is web access for updates at that level. It asks me to choose a net connection. I use wire but wifi is also there. Selects ok but fails to use it. They have added a new facility though. Extended diagnostic facilities. Wont work as it tells me it's out of date and wont update via the net. Some where or the other I read that various parties can but software in the boot partition. Some concern expressed as to what might get put there. I'm just wondering due to the additional diagnostics they have added. The comment I found may be incorrect. If it is playing with the size of the partition is likely to be bad news. Adding further boot options shouldn't be a problem as I feel that is bound to be extendable.

Call HP seems to be the only viable option but maybe the bios needs correcting as well. If I reinstall win I can also ask them about complications if I do that via a VM. I'd be inclined to use virtual box. I do sometime use some rather specialised technical windows apps under wine. I started using Linux via a VM rather a long time ago. It didn't take me long to switch.

Any way a lot of problems down to me having a bad day but wouldn't it be a good idea for the installers to warn? I'll be away for a while and get onto HP when I come back and update. It's a brand new machine so hopefully I'll get support. Otherwise £200 down the drain and a part functioning bios.

---

### Post by oldfred on 2023-04-09
Unless you have pre-installed Linux, first level support by every vendor is only Windows.
The minute you mention Linux they will say they do not support it.

Many vendors now at least provide some support via UEFI updates. Those are the vendors/models that I would first consider if purchasing.
[https://fwupd.org/](https://fwupd.org/)
[https://fwupd.org/lvfs/devices/](https://fwupd.org/lvfs/devices/)

Dell was one of the first to support fwupd. HP seems to only have a few commercial models on list.
Lenovo also now adds all new systems to list.
None of the desktop motherboard manufacturers that I have used, Asus, MSI, & Gigabyte are on list, but they are relatively easy to download & update UEFI.

---

### Post by ajohnl on 2023-04-09
HP do support Linux. They validate several disto's. Not the problem anyway. The problem is loss of £200 worth of Win11 that I have paid for. Linux on it - all ok other than on my current distro my USB sound card may still need pulse to be around to be detected correctly on the desktop.

Anyway I had a thought so installed virtualbox and downloaded a win11 iso. Virtual box proved interesting but Oracle helped set up keys for kernel changes, copy past style, So got that working.
It looked promising once I realised that I had seconds to hit a key and get to install. Choice of pro versions and may have picked the wrong one. On the install there are 2 options personal use or  business / school. I picked the latter and it wouldn't accept my email address so switched and it then accepted that. Password - wouldn't have it. I may have slipped up entering that as the machine arrived just with windows. So selected emails for a reset. Nothing arrived - so far. I gave it an hour. Also tried the web way. No joy. Interesting that it would accept my email when I used personal use as I did on the original set up but I also have one for win10 from the other machine. Done natively that password can be reset. In a VM though?? Maybe not.
Had enough for now so at some point will delete the vm machine and try with the other iso option

---

### Post by ajohnl on 2023-04-19
Just a bit of an update. Finally talked to HP. No problem sir. ;) Seems I am not the only one to loose windows. They directed me to a cloud download application via an email. Tried it under wine but it kicked out immediately. So they will be sending me a USB stick that I should get this week. They will phone back on Monday to see how things went and also book a service call concerning fan noise.
Back on my old machine for now.

---

### Post by ajohnl on 2023-04-25
Some one else may have the same problem. HP's stuff arrived today. They have sent me installation dvd's for win 10 and 11 and also USB sticks marked system recovery. HP machines only of course. I'd guess all makers that keep activation in ROM can do the same. Others - they should come with the installation software.

Now I have received the stuff I should get a phone call telling me what to do with them. Not sure what the sticks do so best to wait.

---

### Post by ajohnl on 2023-05-02
Thanks Oldfred. This is an area I know 0 about. HP is listed on the site
[LVFS: Vendor Status (fwupd.org)]("https://fwupd.org/lvfs/vendors/")

;) Anyway  on with the tale. The USB's and DVD's not much use. No signed drivers for storage found. Might be because it's a very recent new model. I had used the bios to wipe the drive as they suggested and that reported an error. Couple of hours wasted. A reboot came up with no OS would you like to recover - yes but failed out. Changed various thing in the bios security associated - secure boot off may have done it. This time the restore worked  - couple of hours then another hour or so updating win. Many update reboots and I feel they don't handle that well. It looks like other updates can continue loading.

I'm using it for this post and need to sort a couple of aspects on it such as choice of net access. Stuck in wifi and I usually use wire, Currently they are on separate ISP's. ;) Found a bug in 11 within an hour - start menu refused to work, fix easily found on the web. An HP admin app there after the recovery gone  on the next boot.  Pass on that at the moment.

I need to ask a few questions on here now concerning the Ubuntu USB stick, dual booting and etc.

---

### Post by oldfred on 2023-05-02
Sounds like we are back to post #1?
Or starting all over.

Only use Windows to shrink an NTFS partition to make unallocated space & reboot, so it can run chkdsk.

Ubuntu or Kubuntu install will use same ESP - efi system partition.
Default install creates only / (root) partition. It will use existing ESP and create swap file, not a swap partition.
For newer users that is all that is required.
Make sure Windows fast start up is off & bitlocker is off, or else installer will not see Windows & may overwrite it.
Sometimes other UEFI/BIOS settings are required.

You can create swap of 4GB, many that primarily use servers suggest swap partition is somewhat better?
You can create separate /home partition. Or data partition(s). 
Or do LVM install, but LVM or LVM with encryption default install erases entire drive, so then no Windows.

We normally suggest the most current Long Term Support version or now 22.04.1LTS unless very new hardware and then latest 23.04 will have newer kernel & drivers for support of newer systems. If extremely new, you may need newer kernel & drivers than what are in a distribution. Due to time to compile, configure, & verify a distribution, a distribution is often one or two kernel versions older than the very latest kernel.

---

### Post by ajohnl on 2023-05-02
> **oldfred said:**
> Sounds like we are back to post #1?
You can create swap of 4GB, many that primarily use servers suggest swap partition is somewhat better?
You can create separate /home partition. Or data partition(s). 
Or do LVM install, but LVM or LVM with encryption default install erases entire drive, so then no Windows.

That's what I did on my last install, different distro. Several times. Also home and a couple of others more to see what was going on. Later no swap at all as given sufficient memory, there was suggestions it's not needed. Can't remember how much and have left the new one at 16. I think the previous machine has 64 and no swap for a number of years, Maybe 32. would have to look and will.


:) LOL sort of but at least I now know and install can wreck windows. That also messed up the machine's fan running with linux running. High speed for no apparent reason and very loud. There was some of this at times while restoring but now under windows it's as silent as a mouse.

Bitlocker - don't think that is activated by default.
HP bios. Not sure on the new one The earlier one spotted boot changes and asked if ok to continue - just once.

There is a space available now but all I know for certain is it's size. The partitioner I used has a conventional display so partitions are probable where it says and of that size.

Gparted is mentioned for use on Win11 but I think it's the bootable version. Just saw it mentioned and didn't look any further. ;)Mention made me think of bootable floppies to do similar things.
 [How to resize partition on Windows 11 or 10 using GParted - Pureinfotech]("https://pureinfotech.com/resize-partition-windows-10-gparted/")

---

### Post by oldfred on 2023-05-02
Use Windows tools for Windows & Linux tools for Linux.
Did not know gparted even worked with Windows.
I use gparted from live installer, or download the most current gparted ISO and use it.

---

