---
title: "Dual boot ubuntu crashes"
date: 2021-06-10
forum: Installation &amp; Upgrades
---

### Post by raxhacks on 2021-06-10
Hello, I want to dual boot windows 10 and ubuntu 21.04 but I can't. The installer always crashes. I have 2 disks, a SSD 480 gb with windows in it and a HDD 1 tb for storage unit. I did partitions in the two disks and at the time I was installing ubuntu I set the partition in the SSD as root and the partition in the HDD as /home. Sometimes the installer crashes there or in the last step. It keeps loading and then a message pops up and says that the installer has crashed:[B][COLOR=#000000][FONT=&amp]"We're sorry; the installer crashed. After you close this window, we'll allow you to file a bug report using the integrated bug reporting tool. This will gather information about your system and your installation process. The details will be sent to our bug tracker and a developer will attend to the problem as soon as possible."

[/FONT][/COLOR][/B][COLOR=#000000][FONT=&amp]I already have my bios running as UEFI, I disabled CSM. My 2 disks are configured as GPT. The USB entry is running in UEFI mode also (I disabled the legacy mode in the usb ports). My bootable usb was created with Rufus, I configured it as GPT partition in UEFI mode (no CSM), and as FAT32. I don't know why the installation crashes. I will be grateful with your help.[/FONT][/COLOR]

---

### Post by oldfred on 2021-06-10
What brand/model system? What video card/chip?
Have you updated UEFI to latest firmware version.
And updated SSD's firmware, also?

What version/flavor of Ubuntu?

Post this:
sudo parted -l

---

### Post by raxhacks on 2021-06-10
I have a built pc with a motherboard gigabyte h310m-h, my graphic card is a 1050 ti from Nvidia, intel i5 8th gen, 16 gb ram. I think I have neither updated UEFI to the latest version nor my SSD firmware. But I will look it up on yt and do it. 
[COLOR=#000000]sudo parted -l[/COLOR]

---

### Post by raxhacks on 2021-06-10
Ok, i checked. My bios and my ssd firmware are updated. What should I do?

---

### Post by coley9225 on 2021-06-10
Hello raxhacks. I have a lenovo laptop and installer always hung on installing grub package. after many attempts, I found a work around. I have to install any linux system WITHOUT a bootloader. After the install, but before rebooting, I have to run boot-repair to install bootloader, after which I have the standard grub menu at boot. In my case, I also, from the booted system, have to purge and reinstall grub. After the first linux system is in, I can install other linux systems without bootloader and boot normally into an already installed os and do a grub update to find the new install. After that everything runs fine. If your installer is hanging on the grub install, this may be an option. Good luck.

---

### Post by raxhacks on 2021-06-10
Thanks for sharing but in my case is a little bit weird. My installer crashes in random steps, sometimes in the last part, mainly when it is installing firefox. Sometimes it crashes when I assign the partitions or when I am typing my new user. I already changed my usb to a newer of 16 gb, and also inserted it in different ports but that doesn't seem to work either.

---

### Post by MAFoElffen on 2021-06-10
Welcome to the adventure and journey. All my respect to oldfred, always. He doesn't get enough credit. My first "Dual Boot" with Ubuntu, Windows and "other" was 11 years ago. I think oldfred was one of the people who helped me through that then. He is an amazing wealth of knowledge and skills!!! You are in very good hands! This post is not to encroach on him, but to try to help him, help you. And to provide you some tips to think about.

Even more basic, and additional to oldfred's requests for info... If you boot on the image you are installing, before trying to install, if you select "Try" instead of install. does it run successfully and is the system stable?  From there, that will tell him a lot. Besides that the hardware might be compatible, but that might also tell him that you have [COLOR=#ff0000]a *good* image[/COLOR] to install from. From there you can supply him a lot of information that Windows 10 is shielded from and cannot provide.[SUP]*[/SUP] From there, you can open a terminal to give him the later info he requested with fdisk.

What you also *might* want to tell him... (Because he *might* need to know eventually):
[LIST]
[*]What product version and build of Windows 10.
[*]What system architecture? (Processor, 32bit or 64bit)
[*]Do you know if your partition scheme is MBR or GPT? (You added disks to this system, so I assume you already might know)
[*]What your long range plans are... (Do you have a plan? On dual boots, you may want to have "information" that both can share and live together with.)
[*]What boot manager do you want to end up with? (Grub or BCD Boot Menu)
[*]When you "were' installing, did you select "With Updates" and what medium were you connected to the internet with (if at all)? (Hardwired or Wifi?)
[/LIST]

Even if you have a newer system, your BIOS may still have been set to either boot legacy or UEFI in your BIOS. And if it is capable and set to UEFI, do you have "Secure Boot" set to "OFF" in your BIOS for Linux to boot. 

Important note is that, before you start, you are going to want to configure the power settings in Windows 10 to completely shutdown it's filesystem on power down, instead of hibernating. (<- From experience) Another is that even if you do not image/backup your Win 10 system before you start (recommended)... If you decide to go with a Windows BCD Menu for your Boot Menu, then you are going to least want to get an exported backup file of your partition table of the SSD, before you try to setup that menu. The Windows tools for that can be unintelligent, unaware, cruel and unforgiving. They will do exactly as you ask, even if that is not what you mean. just saying. It's easy if "you have a plan", and somewhere to fall back to.

[HR][/HR]Notes: * - When working, I keep two current Ubuntu LiveCD  USB's (32bit and 64bit) with me to rescue/recover Windows Systems.

**EDIT:**: Fails in Random phases of the install? SO did you verify that the sha of the image is good? (That you have a good install image?)

---

### Post by raxhacks on 2021-06-10
Hello, thanks for the answer. The first thing, I don't know why it doesn't show the Try option in the usb menu. It just shows Ubuntu, Ubuntu OEM Install, Ubuntu safe graphics,  boot from next volume and UEFI firmware settings. 
Extra:
-I have Windows 10 Pro, Build 19043 and the latest version update.
-My architecture is 64 bit
-The partition scheme is GPT
-My plan with dual boot is to use my main PC to develop and learn to code, I already use windows to code using specialized IDEs, but I got into machine learning and a lot of the libraries aren't available for windows. I don't want a VM because I want to really grasp the "powerness" of my pc, and I tried WSL but it didn't work when I tried to install a special library for linux only.
-The boot manager... I think I will like the Grub from ubuntu, the one of linux.
-All the times I tried installing Ubuntu I always unselected "With Updates" and the other one of Third party software. about my internet connection I am always connected via ethernet. (note: i tried once selecting the option of with updates and third party software but it crashed assigning the partitions)

My BIOS is running in UEFI mode:
[IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAPYAAAAXCAYAAAA4CrLvAAADhklEQVR4Ae1asY4TMRB1TwlfgIQEDfVtTUfHFWnQteELqOlSEokCieZKJGpEfgAoTvwAUv4AKjqKSINmyTNvZ 295BROd84rIjuesWe8fm9mvEky25g egbCQFsYSDrQtg5U56nzdAyI2KpYVLE1iAERu8FDVdZW1haxRWxl7AYxIGI3eKjK2MrYR0PsX/bRztMDe7k2ZSgFs YxkIntwH TkqXt507qMglc9j6d2lvnxBYUU/rQsfXCTmnNNL/I87OObSyvVZH3uquZsU88f5e 2xCxlcl2wUpJp4YfHs84JswDsyXZ/eWPHvuRWyX7 44NiD0A/mpmqXtn38zGxreEfbb6R3SQOI tF3aWHufg4I5tlq8GwQHO4uF03clAH/Lf9t0 dQ tJofeVAsbytgi9xROarIafnic 3GdmszHr5fY64U97V4Xif11nsyjTXTeKBg40TF/pBdKQWz6bH5ipaz c/nI7i7PRxnX/UCFgSDEtlge53uw ND9nY oynPVVwBgDACjMTHwOPd5rvdrMh /VmI7mUBeNl5zEM7DyUycbdaPG XvWPPF vOIvDWZ 8dk7klMpXyU 3cm8EB/jyDEfqt/POQHDm8lsfmOzaTxTYGwnonn6flkSc2b7wnmd44JgvND6/UjQecXg4jH iAX 1iT46oR5Sj12W sq/Z4yDt11hEz0OVx7w84lJLdS/OeKyWZX1t9PHMrVLKwcZV28o7NTsE4byQanHLSCYv1SvNKpGNbsQ9/sNa 8ngAnM2xplqRGhhgfGHMWx7nPutEPZb5nIhlll 1XyU2O8nGUWKjTB8Y5jt2iD6Yl1 ukZxt XrI2mh9jHW4D/vsY01eCh6Yr1YknsJAFb9UwZZwhzVrMsYtdA/RVontL8KQYUfGS2/F489Rq1m o7ujtY2VZK7rGZWzaJzf35GpvB/cmW1jpe 8XpQf4mFqjbaDQ6nqZBxFjDIeajIf/ 8Zm8tTJkHRePiNGkEAm0GEy2 tU7JStnb90qY5W9d0 oeK3wyJ5K4f7T9ZfRm8mHObvN pdwDYk9q2ibvL Q4w59ij90EjTG2xibs0Kka2U QWVbOsu08/Z x9JklXABcGbjYGROwDREeB/GaD/BjPR8QWscd/NNIzufXPRMQWiG89iI8xI1 2ZxFbxBaxG8SAiN3goV4WzSVv/52AiC1iK2M3iIE/ETkKCYmuP7oAAAAASUVORK5CYII=[/IMG]
I also have Secure Boot disabled and, just to be sure, I also disabled CSM. [B]Extra: I disabled legacy mode in the usb ports just in case
[/B]Beforehand, thanks for your help!

EDIT: It crashes in random phases of the install, and I think that I have a good install image.

---

### Post by MAFoElffen on 2021-06-10
Yes. Lots of free Dev resources in Linux. (As well as other things)

Yes. WSL is "Console Only." So that has been a big disappointment in Windows to many people.

Yes, there is quite a difference in real-time performance running on metal, rather than Hyper-V as a VM. You can always change your mind later if you decide you want to be able to cut and paste between Windows and Linux in an enhanced VM session.

First, from what you just said... I have two ideas. One is that you verify your ISO image that you downloaded. I've done over 2000 Linux installs in the past 15 years. If it does *random error*s in the install, that's the first thing I suspect.

Second is how and what did you use to you create your USB install image? Because the start menu you described brings some things to mind. Depending on how you created your USB Media, it may have installed it as a LiveCD (somewhat like Windows PE) type image, which installed SELinux and Grub2 for the initial boot. When you select Ubuntu, in what may look like a Grub2 type menu, if you select Ubuntu, does it (then) boot to the Graphical installer, where it gets to "Try" or "Install" page? 

I think you need to answer those two things before you do anything else.

---

### Post by oldfred on 2021-06-10
Since you have nVidia, you need to use Safe Graphics.

It think that just adds nomodeset like we used to have to recommend manually adding.
And you want proprietary drivers so when you boot install, you already have then nVidia driver. Or else you then need nomodeset until you do add nVidia from Ubuntu repository.
You can just do the update after install & that should be essentially the same as update during install, but will not interfere with install.

I prefer to partition in advance. 
You still have to use Something else to tell installer which partition is which. I use ESP (if Windows you already have that, do not create another), / (root) as ext4. If newer user, I suggest /home as separate partition. If just testing you do not even need that. Some still like swap partition of 4.1 GB, others like installer create swap file which defaults to 2GB. If lots of RAM, a few users do not even add swap, but that is not recommended as a run away process can then crash system.

I also like data partition(s), but that is more advanced.
I do not typically allocate entire drive as I do not know if adding 25 or 30GB for a test install, so I do not corrupt main working install or want more space for data.

Did you post your current partitions. Sometimes Windows does strange things like convert basic to dynamic which then causes major partitioning issues. Only use Windows to shrink your largest NTFS partition & immediately reboot into Windows & run chkdsk. Make sure Windows fast start up is off, or else installer may crash as it cannot correctly see the hibernated NTFS partitions. Windows likes to turn fast start up back on with updates, so even if you turned it off, check again.
  Leave unallocated & then use gparted to create partitions.

Show partitions with this:
sudo parted -l

See also link below in my signature. Much is special cases or specific repairs which you can skim thru if desired. But install steps & links to more info with those are important.

---

### Post by raxhacks on 2021-06-10
Ok, i will try safe graphics. Anyway, I will leave you the link to the tutorial I watched: [https://www.youtube.com/watch?v=kLf8lTiXsAg](https://www.youtube.com/watch?v=kLf8lTiXsAg), **I DON'T KNOW IF THIS PROCESS IS THE CORRECT ONE. **As I said before, I'm trying to install it on my ssd and hdd. Thanks for pointing out that I need to use Safe Graphics.

---

### Post by raxhacks on 2021-06-10
Hello thanks, I tried with safe graphics but still I can't. Now, I don't know if this is relevant but in the last phase of the installation there was a part where it showed that it was scanning the CD-ROM. I don't know if this means that my bootable usb was flashed in the wrong way. Another thing is that now it crashed when it was scanning the hardware, almost ready to be completely installed.

---

### Post by oldfred on 2021-06-10
Installer still refers to DVD/CD even when from flash drive.
ISO is intended for either flash drive or DVD and does not check.
I install from another internal drive and still get at end cannot unmount DVD.

We see various issues, and many times, they try new ISO,  a different port, different flash drive or different installer. We never know what was exact issue, but then it works.
So you may need to experiment.

Does installer pass verification when you first boot.
We used to always use md5sum to verify ISO download. 

 md5sum (older versions) or sha256sum (new versions)
[https://help.ubuntu.com/community/HowToSHA256SUM](https://help.ubuntu.com/community/HowToSHA256SUM)
[https://ubuntuforums.org/showthread.php?t=2449090](https://ubuntuforums.org/showthread.php?t=2449090)

Lots of info on USB boot for installing
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb) & 
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by tea for one on 2021-06-11
> **raxhacks said:**
> It crashes in random phases of the install, and I think that I have a good install image.

You should really [COLOR="#0000FF"]verify[/COLOR] your ISO image. Do you know how to do this?

By the way, can you provide the link from where you downloaded the ISO?

You mentioned that you have not seen [COLOR="#0000FF"]Try Ubuntu[/COLOR] in your live session and this leads me to think that your image may be imperfect.

Lastly, as requested twice by [COLOR="#0000FF"]oldfred[/COLOR], boot into a live Ubuntu session, open a terminal and post the output of your partitions with
```
sudo parted -l
```

Please wrap the terminal output in code tags because it makes it easier to read.

---

### Post by raxhacks on 2021-06-11
Hello, yeah. I got my ISO image from the official page: [https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop)
Also, I don't know how to open the terminal in an Ubuntu session. As I said I can't run try ubuntu and I've seen that in the installation some people have the option to open some apps, but in my case it only appears the installation menu. Is there a way to open the terminal without entering in that mode?

---

### Post by ubfan1 on 2021-06-11
Type ctrl-alt-t at the desktop to start a terminal.

---

### Post by tea for one on 2021-06-11
When you boot into a live session, the top entry is Ubuntu.
Select the top entry and the live session will load.
The next screen will be a Desktop with [COLOR="#0000FF"]Try Ubuntu[/COLOR] and [COLOR="#0000FF"]Install Ubuntu[/COLOR]
Select Try Ubuntu

Any joy?

---

### Post by raxhacks on 2021-06-11
OOOOH yeah, ok, let me try it and run the code.

---

### Post by raxhacks on 2021-06-11
Another thing, I don't know if this is important but my HDD (storage unit) apparently has a Windows Boot Manager and a partition called System Reserved. I don't know why. I installed windows on my SSD and always boot it from it.

---

### Post by raxhacks on 2021-06-11
Yooo. Look I can't try ubuntu either:
[https://drive.google.com/file/d/10vFtSgzX83pNACGQ4RxDK11oaodbOcmp/view?usp=sharing](https://drive.google.com/file/d/10vFtSgzX83pNACGQ4RxDK11oaodbOcmp/view?usp=sharing) (it's my screen)

---

### Post by raxhacks on 2021-06-11
I don't know if it's my usb or my pc.

---

### Post by tea for one on 2021-06-11
Unplug your USB device and remove any other extraneous devices (e.g. headphones etc.)

Double check that you can still access your Windows 10 OS?

---

### Post by oldfred on 2021-06-11
Are you using Safe Boot or nomodeset boot parameter.

This also says you may also need this boot parameter.
[https://askubuntu.com/questions/1153926/linux-keeps-on-logging-and-freezing-after-entering-password](https://askubuntu.com/questions/1153926/linux-keeps-on-logging-and-freezing-after-entering-password)
[https://askubuntu.com/questions/863150/pcie-bus-error-severity-corrected-type-physical-layer-id-00e5receiver-idpci=noaer](https://askubuntu.com/questions/863150/pcie-bus-error-severity-corrected-type-physical-layer-id-00e5receiver-idpci=noaer)

pci=nomsi
or
pci=noaer

Safe Graphics Boot option on installer adds nomodeset.
At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by raxhacks on 2021-06-11
Hi, thanks I finally ran it. I needed to replace de quiet splash as you said. I entered the code sudo parted -l in the terminal as you said, here is the exit: 

[B]Model: ATA KINGSTON SA400S3 (scsi)
Disk /dev/sda: 480GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  2456MB  2455MB  ntfs               msftdata
 2      2456MB  454GB   451GB   ntfs               msftdata
 3      480GB   480GB   105MB   fat32              boot, esp


Model: ATA WDC WD10EZEX-08W (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  2456MB  2455MB  ntfs         Te    msftdata
 2      9212MB  790GB   781GB   ntfs               msftdata


Model: ADATA USB Flash Drive (scsi)
Disk /dev/sdc: 15.5GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                 Flags
 1      1049kB  15.5GB  15.5GB  fat32        Main Data Partition  msftdata[/B]

---

### Post by raxhacks on 2021-06-11
Yes I can still run windows 10.
I have nothing connected but my mouse and keyboard.

---

### Post by tea for one on 2021-06-11
Some progress now - splendid.

Now, is it still your intention to install Ubuntu OS (i.e. root /) on your 480GB Kingston drive but install the /home on the 1000GB drive?

You have to make free space on each drive (using Windows tools to shrink Windows partitions).

Do you know how to do this?
[U]
Edit[/U]

To be honest, my personal preference would be to have each OS including users on separate drives.

---

### Post by MAFoElffen on 2021-06-11
So at this point... What kernel boot options let you boot up the the LiveCD Image where it is stable?

On what "Tea For One" said... I second it, on using Windows tools if you are going to shrink a "Windows" drive... The reason for that is if you use Linux tools to do that, it will do it fine, but... It will do nothing to the Windows NTFS indexs. So when you resteart Windows later, then if the filesystem was indexed, those indexes will be broken (and need to be rebuilt. If you use the Win Disk Manager to do it, It will take care of those on it's own. (just a learning moment.)

*** And both oldfred and I have told you that you should turn off fastboot, so that it shutdowns the NTFS File system completely on shutdown, instead of hibernation. This is "very" important!.

Like oldfred and I mentioned. Once you can run the LiveCD and have confidence that you can run it and know which boot options you need to do that... Did you come up with your plan yet? For example...

I usually, on any install, lay out my partition myself... (custom). I decide which file systems I want and where they will be. I usually like to have a root, boot, swap and home partitions. I would suggest your root, boot and swap on the ssd, and the home on 1TB Sata. On the home, you may decide to make that as NTFS. If not, at least add another partition as NTFS so you can esily have somewhere where you can move share between the systems. I 

I prefer using the Grub2 Boot Menu, and Grab2 as a bootloader. (instead of the Windows BCD Boot menu. It is more durable, and easy to customize. On dual boots, I add a partition just large enough for one or two ISO's, so that I add a custom Grub entry to boot it if I need recovery services. Why? Because things happen, when you customize, tweak and explore the limits of things. LOL

---

### Post by raxhacks on 2021-06-11
Yeah i already did some partitions, on the ssd I did a 30 gb partition and on the HDD a 200 gb partition. Let's see if it works.

---

### Post by raxhacks on 2021-06-11
MMM.  I tried installing it again but now it crashed when I was assigning partitions. It was running in nomodeset and I connected it to another USB port. I think that I will just install it in a partition of my HDD, my question here is where should I install the grub. In my case, will it show the option to boot windows even though is not in the HDD?

---

### Post by MAFoElffen on 2021-06-11
You said you wanted to learn to code... So what languages do you think you want to learn? 

I'm asking this to get an idea of what you are going to need in resources and layout... And the things you may want to test with...

And oldfred mentioned you had NVidia(?) AS you said your goal is to learn Linux and play, somewhere where you can customize and tweak, and see the results of your work... A poweruser. Right? Get familiar with the gnome terminal. It is an emulated terminal session. As Tea For One mentioned, the hot keys to toggle open a Gnome Terminal (graphical) session is <CTRL>+<ALT>+<T>.

Since you have been having troubles, here's a crash course.

Under the Graphics Layer are 7 TTY Terminal sessions... Even when you are installing with the LiveCD in Ubiquity... So if there is an error, you can toggle between TTY sessions to see what is going on... You can toggle with the hotkeys <CNTRL>+<ALT>+<Session#> where The third key is the TTY Session number of 1 through 7. This is for after 18.04 1 is usually System Messages during boot, until it gets to the Graphical Login, which displays in TTY1. After login, The Grapihics display in TTY2 for the first logged in user. 3-7 are TTY Terminal sessions for use as terminal sessions. 

In Ubiquity, the LiveCD installer, the system messages show on TTY1. 2 is usually where Ubicuity uses to install and such, where the scripts are executing, and you see the progress and such. The errors will show there or TTY1. Any other you can use as a terminal session. Before 18.04, the Graphics was on TTY 7.

I tell you this, because if X is scrambled for some reason, you can still get to a TTY session using those hotkeys...

So, at any Terminal Session, please do 
```

sudo lshw -c video

```
Becuase oldfred mentioned you had NVidiia, and I didn't hear you mention that or what type...

---

### Post by MAFoElffen on 2021-06-11
> **raxhacks said:**
> MMM.  I tried installing it again but now it crashed when I was assigning partitions. It was running in nomodeset and I connected it to another USB port. I think that I will just install it in a partition of my HDD, my question here is where should I install the grub. In my case, will it show the option to boot windows even though is not in the HDD?
You install Grub2 to whichever partition that contains the /boot directory ...

So in a default install, with no special file system, the root partition contains /boot. If LVM, then it has it's own boot partition. Or if custom, you can create your own /boot partition.

Did you ever verify that the filesystem of the LiveCD is okay and the ISO was good? Oldfred, myself, and others have asked you this. 
> **oldfred said:**
> Does installer pass verification when you first boot.
We used to always use md5sum to verify ISO download.

md5sum (older versions) or sha256sum (new versions)
[https://help.ubuntu.com/community/HowToSHA256SUM](https://help.ubuntu.com/community/HowToSHA256SUM)
[https://ubuntuforums.org/showthread.php?t=2449090](https://ubuntuforums.org/showthread.php?t=2449090)

Lots of info on USB boot for installing
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb) &
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
In Windows CLI it is as follows:
```

# C:\> certUtil -hashfile <PATH_TO_FILE> <HASH_ALGORITHM>

##MD5 checksum example (md5sum):
C:\> certUtil -hashfile C:\file.img MD5

```
There is also an option on the install disk to check the filesystem of the LiveCD in the Installers grub menu... Just saying.

**EDIT: I read through this thread again... You never mentioned which ISO Image (Name) you are installing from(???)**

---

### Post by raxhacks on 2021-06-11
I got my ISO hash with the FileHash command on Windows PowerShell and I verified it with Ubuntu's repository. The image I'm using is [U]ubuntu-20.04.2.0-desktop-amd64.iso

[/U]I got the sha256: 
PS C:\Users\Rax\Desktop> certutil -hashfile ubuntu-20.04.2.0-desktop-amd64.iso sha256
SHA256 hash of ubuntu-20.04.2.0-desktop-amd64.iso:
93bdab204067321ff131f560879db46bee3b994bf24836bb78538640f689e58f
CertUtil: -hashfile command completed successfully.

According to ubuntu's releases page is the correct one: [https://releases.ubuntu.com/20.04/SHA256SUMS](https://releases.ubuntu.com/20.04/SHA256SUMS)

---

### Post by raxhacks on 2021-06-11
I tried using Ctrl+Alt+F3-7 but all it showed was this screen: [https://drive.google.com/file/d/10vFtSgzX83pNACGQ4RxDK11oaodbOcmp/view?usp=sharing](https://drive.google.com/file/d/10vFtSgzX83pNACGQ4RxDK11oaodbOcmp/view?usp=sharing)
In the last attempt it crashed after waiting a long time.

---

### Post by MAFoElffen on 2021-06-11
Ouch!!!!!! That is horrible. That is a lot of errors going on behind the scenes. Telling me that it is definitely not runnign stable yet. Not enough to even bother installing until that is worked out.

What is the system this is running on? What motherboard, processor and video? Something is definitely going on "device wise." I don't see it because I'm not there. But something weird is going on there.

Please be patient...

Start with starting in safe graphics mode on "try" or with any other option that got you to running the LiveCD Environment in some sort of stable mode. From there, post the video info I asked for... And with all those "PCIE errors, I would like to see the results of 
```

sudo lspci -l

```
Cut and paste the results of that into text file and Please attach that as an attachment to your post. You can do that from Firefox in the LiveCD session.

EDIT: If you do this, it will write the results to a file
```

sudo lspci -l >> ~/Documents/lspci_info.txt

```

---

### Post by raxhacks on 2021-06-11
-The motherboard is a Gigabyte (h310m-h), it is running in UEFI mode, legacy mode disabled, CSM disabled, also the usb ports are running in UEFI mode. The PCIe ports I don't know I will check them.
-i5 8400 
-1050ti 4gb vram 
let me enter in a stable mode to give the info you want.

---

### Post by raxhacks on 2021-06-11
Video code exit:
 [B] *-display UNCLAIMED       
       description: VGA compatible controller
       product: GP107 [GeForce GTX 1050 Ti]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller cap_list
       configuration: latency=0
       resources: memory:a2000000-a2ffffff memory:90000000-9fffffff memory:a0000000-a1ffffff ioport:5000(size=128) memory:c0000-dffff[/B]

sudo lspci -l exit (i do not know what is wrong):
**invalid option -- 'l' **

---

### Post by raxhacks on 2021-06-11
Video code exit:
 [B] *-display UNCLAIMED       
       description: VGA compatible controller
       product: GP107 [GeForce GTX 1050 Ti]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller cap_list
       configuration: latency=0
       resources: memory:a2000000-a2ffffff memory:90000000-9fffffff memory:a0000000-a1ffffff ioport:5000(size=128) memory:c0000-dffff[/B]

sudo lspci -l exit (i do not know what is wrong):
[B]lspci: invalid option -- 'l'
Usage: lspci [<switches>]

Basic display modes:
-mm        Produce machine-readable output (single -m for an obsolete format)
-t        Show bus tree

Display options:
-v        Be verbose (-vv or -vvv for higher verbosity)
-k        Show kernel drivers handling each device
-x        Show hex-dump of the standard part of the config space
-xxx        Show hex-dump of the whole config space (dangerous; root only)
-xxxx        Show hex-dump of the 4096-byte extended config space (root only)
-b        Bus-centric view (addresses and IRQ's as seen by the bus)
-D        Always show domain numbers
-P        Display bridge path in addition to bus and device number
-PP        Display bus path in addition to bus and device number

Resolving of device ID's to names:
-n        Show numeric ID's
-nn        Show both textual and numeric ID's (names & numbers)
-q        Query the PCI ID database for unknown ID's via DNS
-qq        As above, but re-query locally cached entries
-Q        Query the PCI ID database for all ID's via DNS

Selection of devices:
-s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]    Show only devices in selected slots
-d [<vendor>]:[<device>][:<class>]        Show only devices with specified ID's

Other options:
-i <file>    Use specified ID database instead of /usr/share/misc/pci.ids.gz
-p <file>    Look up kernel modules in a given file instead of default modules.pcimap
-M        Enable `bus mapping' mode (dangerous; root only)

PCI access options:
-A <method>    Use the specified PCI access method (see `-A help' for a list)
-O <par>=<val>    Set PCI access parameter (see `-O help' for a list)
-G        Enable PCI access debugging
-H <mode>    Use direct hardware access (<mode> = 1 or 2)
-F <file>    Read PCI configuration dump from a given file
[/B]

---

### Post by MAFoElffen on 2021-06-11
Okay... with that Motherboard and graphics, use both "nomodeset: and "acpi=off" boot options. Becuase of the chipset on that board, you will have to make the "acpi=off" permanent in the Grub2 options. (I'll go over that later.)

On reboot after the install, you will still have to use those two options to boot. You will then have to update/upgrade, then edit your Grub options file to insert the boot option for ACPI,. The update your grub. Then install your drivers for your NVidia card...

Still waiting on your results, to see if there's any changes to that plan.

---

### Post by MAFoElffen on 2021-06-11
You had posted while I was typing. Saw it... LOL

Sorry. Typo above...
```

sudo lspci -v

```

---

### Post by raxhacks on 2021-06-11
Ok, so now i just run the grub and turn acpi off? Lets see if it works

---

### Post by MAFoElffen on 2021-06-11
Don't install yet...

After booting with the "acpi=off" boot option into the LiveCD environment, if you toggle over to the TTY sessions, do you still see those PCIe errors?

I just wnat to ensure those are taken care of before you try to install.

---

### Post by MAFoElffen on 2021-06-11
Note that there is a firmware update for that Gigabyte H310M-H (Rev 1) motherboard for chipset that you should apply sometime... Dated 2020.06.16

That chipset firmware update "may" or "may not" correct those ACPI errors. They had 2 updates to the firmware on that chipset since the board was made. There has also been 4 new BIOS updates for that board.

You might want to ensure your firmware on both is up to date. One of the BIOS updates addresses a [COLOR=#ff0000]vulnerability[/COLOR] issue.

---

### Post by raxhacks on 2021-06-11
Hello, sorry for taking too long. It worked just fine turning off the acpi. If you think I'm ready to install I will. Just to be sure, do I need to assign a swap partition? or can i just add the "/" root partition and home partition?
I will go for my main plan:
On the ssd assign the root partition
On the hdd assign the /home partition
But as you say. If I need a swap partition, is it okay if assign it to my hdd?
Another thing I read in a lot of forums is that I need to select the efi partition that has the Windows Boot Manager to install the bootloader, is it like that? or can i just select my ssd?

---

### Post by MAFoElffen on 2021-06-11
A swap partition is where it pages to if it needs more memory... Windows uses one also, except it's only a file in Windows. Paging is also where both operating systems write the session to if they are put to sleep or in hibernation.

It you put it on your SSD, it's going to be a lot faster  than if it was on a Sata drive. Rule of thumb for that is 1.5 times the size of your memory.

Now did you decide if you are going to make your /home in native "ext4" or "NTFS". The Default is ext4. but if your make it NTFS, both operationing systems would be able to see it and share data. If you leave it as ext4, only Linux can see it.

EDIT: Once you answer those questions... go ahead and try to install. The answers are all your choice. Your plan.

---

### Post by raxhacks on 2021-06-11
I think that i'll leave it as ext4, I just want linux to be used for that. Regarding the swap partition, I think i will assign it on the ssd as you said.

---

### Post by MAFoElffen on 2021-06-11
Tell me how it goes. If the installation is successful, on reboot, use those two boot options to get into a desktop. Then post back from there and I'll walk you through what needs to be done from there.

---

### Post by MAFoElffen on 2021-06-11
Well? Have not heard from you in a while, so I'm hoping that is good news. I will leave a progress note for you to see, in case I miss you....

Once you get it installed, reboot and use those two boot options to get to your new desktop, then:

Go to Additional Drivers and install your NVidia Drivers. Once those are installed. You will not have to use the "nomodeset" boot option anymore.

Then open a graphical terminal session <CNTRL><ALT><T> And open the editor with elevated privileges.
```
sudo gedit
```
Select "OPEN" and navigate to "Other", ""Computer" /etc/Default/ and other the Document named "Grub".

Go down to the 10th line that starts with "GRUB_CMDLINE_LINUX_DEFAULT", and copy  the line. Goto the start of that line and comment is out with the '#" character.
Add a line and paste your copy of that line, 

Change it to:
```

# GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"

```
Once done, Save it. Then exit the Text Editor.
You''ve then edited the "Default" file for the Grub2 Menu, but it will not pick up that change you rebuild the Grub Menu, via:
```
sudo update-grub
```
Once that is done, you should be good to go with a working system.

---

### Post by raxhacks on 2021-06-12
Hello thanks for helping me. I'm sorry but yesterday I needed to attend a personal event. I tried installing it and apparently all worked fine. Just at the end, when it was installing the grub2, it popped up an error that said: Executing 'grub-install /dev/sda' failed. This is a fatal error. I don't know if this has something to do with the bootloader option, in which I selected the SSD.

---

### Post by MAFoElffen on 2021-06-12
Remember me telling you NOT to try to install Grub to a Drive, but rather to a partition? By changing the default, you overrode the setting that was aware that it was booted and installed in UEFI mode. In UEFI mode, it has to keep track of where the existing EFI boot directory is (dev/sdX/EFI/BOOT/, and where the Ubuntu lives... So that it can add to EFI to point to where Ubuntu lives... I believe the pointers/logic/convention [COLOR=#ff8c00]*was*[/COLOR] /dev/EFI/BOOT (the original EFI boot partition) to /dev/sdX/boot/efi (the folder where Ubuntu lives and the Grub EFI files are), with a mount line in fstab pointing back to the EFI boot partition...

In odfred's signature line is:
> **oldfred said:**
> For more info on UEFI boot install & repair - Regularly Updated :
[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)
Easiest for you, is to boot on the LiveCD, to the LiveCD environment, install "boot-repair"... Follow the instructions from yannbuntu's application page and from this AskUbuntu answer ...which deals with earlier EFI, but has how to use boot-repair with EFI, and Windows/Ubuntu dual boots:
    [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
    [https://askubuntu.com/questions/221835/how-do-i-install-ubuntu-alongside-a-pre-installed-windows-with-uefi](https://askubuntu.com/questions/221835/how-do-i-install-ubuntu-alongside-a-pre-installed-windows-with-uefi)
I personally know that yannbuntu keeps his app up to date and current. He still messages me from time to time, to ask what is current relating to graphics and kernel boot options. It will save you lots of time and headaches. Even more, it is updated to whatever is current with Windows and Ubuntu living on the same Machine...

---

### Post by raxhacks on 2021-06-12
Hi, when I am trying to install the boot-repair in Try Ubuntu mode it shows me an error exit code that says I do not have space: 
Error: Timeout was reached
Reading package lists... Error!
E: Write error - write (28: No space left on device)
E: IO Error saving source cache
E: The package lists or status file could not be parsed or opened.

I am running it on a 16 GB USB.

---

### Post by MAFoElffen on 2021-06-12
yanbuntu also has his own Boot Repair LiveCD (ISO) at: [http://sourceforge.net/p/boot-repair-cd/home](http://sourceforge.net/p/boot-repair-cd/home)

It had that link in the Boot Repair page I linked to in the previous post... As Option #1.

---

### Post by raxhacks on 2021-06-12
Hello, I see. I fixed it. Now I can run Ubuntu and Windows 10. Unfortunately I have another problem. I can't install my graphic's card drivers and Ubuntu is running very slow. I went to Additional Drivers (it took so much time to open), then there weren't extra drivers available. I looked up on the internet for a solution and when I tried to run the code of apt-get update it showed me the same error of not space left. I think that this has to be with my partitions. On the installation I assigned a 6 GB partition on my SSD and was configured as the swap partition, then I configured a 20 GB partition as root (on the SSD), and finally I assigned the /home partition on my HDD (200 GB partition). I installed the bootloader on the Windows Boot Manager partition (EFI).

Ubuntu runs super slow and the apps take a long time to open. I will need to re-install it because it is pretty slow. I think I will make the root partition bigger.

---

### Post by tea for one on 2021-06-12
> **raxhacks said:**
>  I will need to re-install it because it is pretty slow. I think I will make the root partition bigger.

Two days and more than 50 posts in this thread - I think that you should re-consider the installation of each OS and user data on separate disks.
You are in a good position with your PC having two disks - many users do not have that luxury.

---

### Post by raxhacks on 2021-06-12
Yeah, I will, thank you all for your help.

---

### Post by MAFoElffen on 2021-06-12
LOL. Yes. now (at the start) is a good time to reinstall. You lose nothing at this point except the time to reinstall. You should be getting better at it now. (And now the installer works for you...)

NVidia Drivers are 3rd Party Proprietary, so you used to have to add the 3rd party Repo to see any NVidia drivers in Additional Drivers. I'm not sure if that has changed. No matter.

For me, I go to the NVidia site to download the drivers straight from them. 

In the past, I used to use the drivers from the Ubuntu Graphics Team PPA here: [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

---

### Post by MAFoElffen on 2021-06-12
@raxhacks  

You never mentioned how much memory your System has... If running Win 10 Pro, I'm assuming at least 4GB right? As I said, a rule of thumbs is 1.5 times the installed RAM for a Linux Desktop.

*** But Paging on a running system at medium load is a safeguard. If you ran "sudo top" it would show you if the paging is getting hit, and if there were running processes eating up your resources.

But I think you were right, in that a fresh system, running on an SSD should scream. Something is wrong. You were learning, and had problems installing. Starting fresh would ensure at least that part is good, and checked off your list.

Once you get a good install, then get the NVidia drivers installed, then the Graphics load will get offloaded to the Graphics Card, and use it's memory for that. Processing graphics will be faster. You got some recent, powerful hardware. It should not be running slow.

---

