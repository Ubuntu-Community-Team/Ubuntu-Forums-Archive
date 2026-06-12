---
title: "Installing Xubuntu 24.04 to HP Probook 645 G - Error 3F0"
date: 2024-05-13
forum: Installation &amp; Upgrades
---

### Post by james-peterson-1978 on 2024-05-13
Hello, I'm a newbie to Ubuntu and I'm attempting to replace the Windows 7 Ent OS on an old work computer with Xubuntu as I'm tired of paying Microsoft licensing fees. My goal is to have a single OS system running Xubuntu, I don't really care which version; but 24.04 was the most recent so why not... If this is easier with older versions I have no issue changing.
I haven't really worked with setting up operating systems since the last century. My background is more in software development and design; leaning more towards mentoring "the kids" in the last 5 years. I'd really appreciate any assistance that can be given; there just doesn't seem to be a simple, or standard, solution with these damn HP laptops. 

System details:
HP ProBook 645 G
500GB HDD
Original OS: Windows 7 Enterprise
Bios Version: L72 Ver. 01.02 (12/04/2013)

USB boot drive created using Rufus and 24.04 iso. 

Steps taken to originally install:
1) Booted from USB drive with option 1 (Try or Install Xubuntu).
2) Used gparted to reformat HDD as it was locked with Bit Looker.
* /dev/sda1 - file system = unknown; size = 1.00MB; flags = bios_grub
* /dev/sda2 - file system = ext4; size = 465 GB; flags = (none)
* unallocated - file system = unallocated; size = 1.02MB; flags =
3) Ran install with standard options + 3rd party drivers, doing the format drive and install.
4) Reboot failed with error 3F0 no OS on boot drive.

My assumption after several hours on Google and reading things on this forum is that the issue has to do with the BIOS not liking hard drives that don't have a msdos partition, or something like that. The wall I'm hitting is that nothing I've read has worked and I simply don't have the experience to "think outside the box" on this stuff. 

Trouble shooting steps I've taken:
1) Ran quick hard drive check. Both checks passed.
2) Bios changes
2.1) SecureBoot Config - was already turned off
2.2) Tried all 3 boot modes - Legacy (default), UEFI Hybrid (with CSM), and UEFI Native (without CSM) 
Reboots experienced the same issue - 3F0

3) Booted from USB and tried using gparted to reformat drive and use msdos partition table.
4) Reinstalled Xubuntu using same options but my assumption is that the format step blew away the msdos partition table.
Reboot - 3F0

Here are some of the pages I've used as points of reference.
[https://h30434.www3.hp.com/t5/Notebook-Boot-and-Lockup/Ubuntu-choice-at-startup/td-p/6718820#:~:text=To%20have%20Ubuntu%20as%20OS,run%20first%20at%20next%20boot](https://h30434.www3.hp.com/t5/Notebook-Boot-and-Lockup/Ubuntu-choice-at-startup/td-p/6718820#:~:text=To%20have%20Ubuntu%20as%20OS,run%20first%20at%20next%20boot).
[https://dev.to/tylerlwsmith/getting-ubuntu-linux-installed-on-an-hp-probook-x360-11-2ei3](https://dev.to/tylerlwsmith/getting-ubuntu-linux-installed-on-an-hp-probook-x360-11-2ei3)
[https://ubuntuforums.org/showthread.php?t=2477549](https://ubuntuforums.org/showthread.php?t=2477549)
[https://ubuntuforums.org/showthread.php?t=2234019](https://ubuntuforums.org/showthread.php?t=2234019)

---

### Post by Rubi1200 on 2024-05-14
Not sure where things are holding now but please run the boot info script from a live USB.

Choose to Try Xubuntu and then follow the instructions to create a summary report. It will offer to create a pastebin link which you can then post back here.

Hopefully, this will give us some clues as to what is going on.

---

### Post by james-peterson-1978 on 2024-05-14
Thank you Rubi1200; here is the link. [https://pastebin.com/s0fPLd9b](https://pastebin.com/s0fPLd9b)

---

### Post by oldfred on 2024-05-14
You are not showing grub installed to MBR of sda?
With gpt you have to have bios_grub partition, and you have it. So did you get an error  message on grub install?

If drive was gpt, was Windows installed in UEFI boot mode? And then HP wants to boot Windows in UEFI mode, but cannot find Windows.

You may only need to install grub to MBR of sda & set UEFI/BIOS to BIOS/CSM/Legacy boot mode.
Usually Boot-Repair offers to reinstall grub to drive. You may need Boot-Repair's advanced options and choose drive & total reinstall of grub.
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by tea for one on 2024-05-14
> **james-peterson-1978 said:**
> there just doesn't seem to be a simple, or standard, solution with these damn HP laptops
Yes, agreed, HP laptops sometimes display recalcitrant behaviour.
> **james-peterson-1978 said:**
> [https://ubuntuforums.org/showthread.php?t=2477549](https://ubuntuforums.org/showthread.php?t=2477549)
The thread you mentioned had a suggestion in post 20 - did you try it?
> Boot into a live session of Xubuntu 22.04 (Legacy mode)
Open Gparted
Create an msdos partition table
Create one partition Ext4 but not using the complete disk (I used 50% of disk space)
Start the installer
Installation type - choose something else
Locate your prepared partition, use as ext4, format, mountpoint = root /
Grub bootloader to /dev/sda
Allow installer to continue


---

### Post by james-peterson-1978 on 2024-05-14
Well it looks like the post I just typed up didn't post...
Tea for One - Yes I tried to follow those steps (see Trouble Shooting steps 3 & 4) but when in the install it wouldn't let me select where to do the install to move forward.

After loading boot-repair the report it generated matched that of the boot-info output. I ran the suggested repairs and generated a new report.
[https://pastebin.ubuntu.com/p/bq8McxNwwj/](https://pastebin.ubuntu.com/p/bq8McxNwwj/)
Rebooted and still getting the same 3F0 error. Tested with Legacy, UEFI Hybrid, and UEFI Native.
Booted off USB, reloaded boot-repair, under Advanced I checked the GRUB location says /dev/sda then back on the main tab selected Grub Install and Apply. Boot-repair is now giving me this notification "**Please enable a repository containing the [linux-generic] packages in the software sources of Ubuntu 24.04 LTS (/dev/sda2). Then try again.**"

---

### Post by oldfred on 2024-05-14
Still no grub in sda's MBR??
Installer should have put grub into MBR with a BIOS install.

Do you have Internet connected when running Boot-Repair?
Are you running Boot-Repair from Xubuntu live installer or from its own ISO. Better from Xubuntu's installer.

---

### Post by tea for one on 2024-05-15
> **james-peterson-1978 said:**
> Tea for One - Yes I tried to follow those steps (see Trouble Shooting steps 3 & 4) but when in the install it wouldn't let me select where to do the install to move forward.
I've just re-tested a Legacy installation to an external disk with _one_ partition using Xubuntu 24.04 Minimal.
I did not have any difficulty selecting a pre-prepared partition as a target.
The disk booted in Legacy mode on a 8 year old HP-Stream netbook with 2GB ram.
```
test@test:~$ sudo parted -l
[sudo] password for test: 
Model: Hitachi HTS541680J9SA00 (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  32.2GB  32.2GB  primary  ext4

test@test:~$ 
```
You will notice an 80GB disk with one 32.2GB partition.

As your installation remains incomplete, can you add more detail about what you see after selecting "Manual Installation"?

---

### Post by james-peterson-1978 on 2024-05-16
When attempting to follow these steps I run into a blocker step 6. The install options are "Install Xubuntu alongside other partitions", "Erase disk and install Xubuntu", and "Manual install"; my assumption is that "Manual install" is what is meant by 'choose something else'. The blocker is on the very next screen titled "Manual partitioning". The screen allows me to select the sda device or even sda1 but the Next button is never enabled. I should point out that my assumption on this screen is that sda does not need to be mounted.

[COLOR=#000000]*1) Boot into a live session of Xubuntu 22.04 (Legacy mode)*[/COLOR]
[COLOR=#000000]*2) Open Gparted*[/COLOR]
[COLOR=#000000]*3) Create an msdos partition table*[/COLOR]
[COLOR=#000000]*4) Create one partition Ext4 but not using the complete disk (I used 50% of disk space)*[/COLOR]
[COLOR=#000000]*5) Start the installer*[/COLOR]
[COLOR=#000000]*6) Installation type - choose something else*[/COLOR]
[COLOR=#000000]*7) Locate your prepared partition, use as ext4, format, mountpoint = root /*[/COLOR]
[COLOR=#000000]*8) Grub bootloader to /dev/sda*[/COLOR]
[COLOR=#000000]*9) Allow installer to continue*[/COLOR]

---

### Post by Rubi1200 on 2024-05-16
Manual Installation = Choose something else. They changed the language some time back (don't recall exactly when).

At this stage you need to click on the partition you wish to install to. Let''s say for example sda1.

At the bottom of the screen it should show a + - and Change sign.

Click on Change and then enter the filesystem type if not defined. ext4 is the default.

Either choose not to format if you already formatted or click to format.

Under Mount point >> choose / for the root partition

You should then see a check in the box for sda1 and be able to continue with the install.

Did you create just the 1 partition for Xubuntu on sda?

---

### Post by tea for one on 2024-05-16
Manual Installation > Select sda1 > Change > Leave formatted as Ext4 > Mountpoint / (forward slash is root) > OK
Do you see the activated Next button?

@Rubi1200 - you were already on your starting blocks  ;)

---

### Post by james-peterson-1978 on 2024-05-16
Yes, I created just 1 partition on the drive that left 5MB of unallocated space. 
So the step I was missing was clicking the "Change" button; I didn't understand what those buttons were for so I didn't play with them. As soon as I clicked it I was able to move forward with the install.  
After the install I still ran into issues with the computer not finding an OS on the drive so I started digging around and doing more reading. What I noticed in some screen shots of gparted was that the single partition was flagged as bootable where as mine wasn't. After adding this flag my install is working.

Now how do I mark this as resolved? Just change the title of the thread?

Single Partition:
[COLOR=#000000][COLOR=#000000]*1) Boot into a live session of Xubuntu 24.04 (Legacy mode)*[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]*2) Open Gparted*[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]*3) Create an msdos partition table*[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]*4) Create one partition Ext4 but not using the complete disk (I used 50% of disk space). _Partition should be flagged as "**bootable**"_*[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]*5) Start the installer*[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]*6) Installation type - _Manual Install_*[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][I]7) Locate your prepared partition, use as ext4, format, mountpoint = root /
_7.a) Check the box if you want the system to format the partition before doing an install._
[/I][/COLOR][/COLOR]_8) Click "Change" button and enter the file system if not defined, format = ext4, and mount point = "/"_
[COLOR=#000000][COLOR=#000000]*8) Grub bootloader to /dev/sda*[/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][I]9) Allow installer to continue
[/I][/COLOR][/COLOR]

---

### Post by Rubi1200 on 2024-05-16
Glad to hear you finally got this sorted out.

To mark as Solved go to your first post >> Thread Tools >> Mark Solved.

Good luck with the new install!

---

