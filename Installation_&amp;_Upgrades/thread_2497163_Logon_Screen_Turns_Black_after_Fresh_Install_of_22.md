---
title: "Logon Screen Turns Black after Fresh Install of 22.04"
date: 2024-04-25
forum: Installation &amp; Upgrades
---

### Post by Rick St. George on 2024-04-25
Running with new 1TB SSD and 32 GB Ram and 8 core AMD CPU.

After fresh install of v22.04 on new 1TB SSD, system worked beautifully for 1 day. 2nd day boot up, see Logon Screen for 1 second before both screens turn BLACK and can't do anything. 
Tried typing password anyway, nothing!

Don't see any posts on this issue. Anyone have a clue?

---

### Post by Rick St. George on 2024-04-25
Finally got it up by holding the SHIFT key and was able to input my password.
At end of day, since I suspected the GPU driver, I checked (after finding where they moved Software Sources) and sure enough - 
the fresh installed OS is using X-Org instead of Nvidia driver 390. Tried to select Nvidia's driver and this Error Pop-up showed;

"pk-client-error-quark: Error while installing package: installed nvidia-dkms-390 package post-installation script subprocess returned error exit status 10 (313)"

Any suggestions???
Thanks!

---

### Post by #&amp;thj^% on 2024-04-25
Can you post back from:
```
sudo apt full-upgrade
```

---

### Post by MAFoElffen on 2024-04-25
Nvidia 390 is no longer supported by NVidia, but is still being patched by the Ubuntu Graphics Team. My Lenovo Thinkpad T520 uses this driver...

Try this:
```

sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
sudo apt install -y nvidia-graphics-drivers-390 

```

---

### Post by Rick St. George on 2024-04-26
> **1fallen said:**
> Can you post back from:
```
sudo apt full-upgrade
```

```

Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libwpe-1.0-1 libwpebackend-fdo-1.0-1
Use 'sudo apt autoremove' to remove them.
Get more security updates through Ubuntu Pro with 'esm-apps' enabled:
  vlc-plugin-qt libvlc5 libimage-magick-perl vlc-data libvlccore9 vlc
  imagemagick vlc-bin libpathplan4 vlc-l10n libmaven3-core-java graphviz
  libavdevice58 libgvpr2 libgvc6 libdcmtk16 ffmpeg libopenexr25
  libmagick++-6.q16-8 libpostproc55 libcgraph6 libmagickcore-6.q16-6-extra
  vlc-plugin-samba libcdt5 libavcodec58 libimage-magick-q16-perl
  libmagickwand-6.q16-6 vlc-plugin-notify libavutil56 imagemagick-6.q16
  libswscale5 libeditorconfig0 libmagickcore-6.q16-6 vlc-plugin-access-extra
  vlc-plugin-skins2 libgsl27 vlc-plugin-video-splitter liblab-gamut1
  libswresample3 imagemagick-6-common vlc-plugin-video-output libavformat58
  libgslcblas0 libvlc-bin vlc-plugin-base vlc-plugin-visualization
  libavfilter7
Learn more about Ubuntu Pro at https://ubuntu.com/pro
The following packages have been kept back:
  python3-update-manager update-manager-core
The following packages will be upgraded:
  libnghttp2-14
1 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 standard LTS security update
Need to get 76.9 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue? [Y/n] 


```

---

### Post by Rick St. George on 2024-04-26
> **MAFoElffen said:**
> Nvidia 390 is no longer supported by NVidia, but is still being patched by the Ubuntu Graphics Team. My Lenovo Thinkpad T520 uses this driver...

Try this:
```

sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
sudo apt install -y nvidia-graphics-drivers-390 

```

For some odd reason, after repeating it a 2nd time ... it worked and installed the Nvidia 390 driver. 
My system ReBooted 3 times now OK with freshly installed UbuntuStudio v22.04 . Looks and Runs Great!

---

### Post by Rick St. George on 2024-04-26
Where can I find "Ubuntu Pro" ? It is not showing up in Settings / System Settings /Driver Manager / Software Sources.

---

### Post by #&amp;thj^% on 2024-04-26
> **MAFoElffen said:**
> Nvidia 390 is no longer supported by NVidia, but is still being patched by the Ubuntu Graphics Team. My Lenovo Thinkpad T520 uses this driver...

Try this:
```

sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
sudo apt install -y nvidia-graphics-drivers-390 

```

+1
That's what I looking for, if Rick indeed did add it. I guess i should have lead  with that...Oh Well All is good now. :)

---

### Post by #&amp;thj^% on 2024-04-26
> **Rick St. George said:**
> Where can I find "Ubuntu Pro" ? It is not showing up in Settings / System Settings /Driver Manager / Software Sources.
Like this:
```
 pro status --all
SERVICE          AVAILABLE  DESCRIPTION
anbox-cloud      yes        Scalable Android in the cloud
cc-eal           no         Common Criteria EAL2 Provisioning Packages
esm-apps         yes        Expanded Security Maintenance for Applications
esm-infra        yes        Expanded Security Maintenance for Infrastructure
fips             no         NIST-certified FIPS crypto packages
fips-preview     no         Preview of FIPS crypto packages undergoing certification with NIST
fips-updates     no         FIPS compliant crypto packages with stable security updates
landscape        yes        Management and administration tool for Ubuntu
livepatch        yes        Canonical Livepatch service
realtime-kernel  no         Ubuntu kernel with PREEMPT_RT patches integrated
ros              no         Security Updates for the Robot Operating System
ros-updates      no         All Updates for the Robot Operating System
usg              no         Security compliance and audit tools

This machine is not attached to an Ubuntu Pro subscription.
See **[COLOR="#B22222"]https://ubuntu.com/pro[/COLOR]**

```

Or just right here:  [https://ubuntu.com/pro](https://ubuntu.com/pro)

---

### Post by Rick St. George on 2024-04-26
I have already subscribed, but after upgrading to 22.04 it is no longer there to select in Software Sources.

---

### Post by #&amp;thj^% on 2024-04-26
> **Rick St. George said:**
> I have already subscribed, but after upgrading to 22.04 it is no longer there to select in Software Sources.

You will have to re-enroll:
```
sudo pro attach <your_pro_token>
```

I think advantage-tools is needed as well.
```
sudo apt install ubuntu-advantage-tools
```

---

### Post by MAFoElffen on 2024-04-27
+1 --

If you first use 1fallens commands to see if it is enrolled, and if, what services are turned on... Then use his instruction to re-enroll. 

That process will add the sources to the ESM repo's, managed by the Ubuntu Pro ESM Services:
```

mafoelffen@Mikes-ThinkPad-T520:~$ grep . /etc/apt/sources.list.d/ubuntu-esm-apps.list
deb https://esm.ubuntu.com/apps/ubuntu jammy-apps-security main
# deb-src https://esm.ubuntu.com/apps/ubuntu jammy-apps-security main
deb https://esm.ubuntu.com/apps/ubuntu jammy-apps-updates main
# deb-src https://esm.ubuntu.com/apps/ubuntu jammy-apps-updates main

```

---

### Post by Rick St. George on 2024-04-28
> **MAFoElffen said:**
> Nvidia 390 is no longer supported by NVidia, but is still being patched by the Ubuntu Graphics Team. My Lenovo Thinkpad T520 uses this driver...

Try this:
```

sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
sudo apt install -y nvidia-graphics-drivers-390 

```

Strange that it is no longer supported, but Ubuntu Graphics Team "patches" it?!? 
When attempting it, I get this message; "unable to locate package nvidia-graphics-drivers-390".

I still get a Black Screen, approx, 1 sec, after Login shows up.
Looking at the Log, I suspect "adjusting startup timeout" .... below is a portion of the log.

```

Apr 28 09:37:26 stephen-ms7640 systemd[1]: Started Dispatcher daemon for systemd-networkd.
Apr 28 09:37:26 stephen-ms7640 NetworkManager[793]: <info>  [1714315046.0277] modem-manager: ModemManager available
Apr 28 09:37:26 stephen-ms7640 avahi-daemon[789]: Server startup complete. Host name is stephen-ms7640.local. Local service cookie is 24220589.
Apr 28 09:37:27 stephen-ms7640 snapd[832]: overlord.go:271: Acquiring state lock file
Apr 28 09:37:27 stephen-ms7640 snapd[832]: overlord.go:276: Acquired state lock file
Apr 28 09:37:27 stephen-ms7640 snapd[832]: daemon.go:247: started snapd/2.62 (series 16; classic) ubuntu/22.04 (amd64) linux/6.5.0-28-lowlatency.
Apr 28 09:37:27 stephen-ms7640 kernel: [    8.695939] loop8: detected capacity change from 0 to 8
Apr 28 09:37:27 stephen-ms7640 snapd[832]: daemon.go:340: adjusting startup timeout by 1m0s (pessimistic estimate of 30s plus 5s per snap)
Apr 28 09:37:27 stephen-ms7640 systemd[1]: tmp-syscheck\x2dmountpoint\x2d2709513200.mount: Deactivated successfully.


```

And how could a mountpoint be deactivated? Moreover, looking back at Driver Mgr / Software Sources / Additional Driver - I see that it switched back to X.org X Server Nouveau display driver, instead of the proprietary Nvidia 390 driver. How can I update this driver for my GPU ASUS GeForce GT 610, with 2GB DDR3, running dual monitors, and force the OS to take it?

EDIT: After adding UbuntuPro, did update / upgrade / ReBoot and now won't Boot. 

Any ideas? Thanks!

---

### Post by Rick St. George on 2024-04-28
Continuing from above comment: "After adding UbuntuPro, did update / upgrade / ReBoot and now won't Boot";
Managed to write down the Error, screen fills up with ...

"UBSAN: array index out of bounds in /var/lib/dkms/virtualbox 6.1.50/build/vboxdrv/SUPDrvGip"

Holding 'Shfit' key upon Reboot brings up GRUB ... choosing 2nd option then shows GRUB BOOT MENU .. all black and at the bottom the 4 options;
select; Enter:Boot; e:edit; c:command line

After a few minutes ... it shuts down.
Still can't get anywhere with v22.04 !!!???

---

### Post by Rick St. George on 2024-04-28
FYI - had this saved from earlier via txt on my thumb drive, maybe it will help shine light on this subject.

```

~$ sudo apt update
Hit:1 https://brave-browser-apt-release.s3.brave.com stable InRelease
Hit:2 http://archive.ubuntu.com/ubuntu jammy InRelease                           
Hit:3 http://security.ubuntu.com/ubuntu jammy-security InRelease                 
Hit:4 http://archive.canonical.com/ubuntu jammy InRelease                        
Hit:5 http://archive.ubuntu.com/ubuntu jammy-updates InRelease                   
Hit:6 https://esm.ubuntu.com/apps/ubuntu jammy-apps-security InRelease           
Hit:7 https://esm.ubuntu.com/apps/ubuntu jammy-apps-updates InRelease            
Hit:8 https://esm.ubuntu.com/infra/ubuntu jammy-infra-security InRelease
Hit:9 https://esm.ubuntu.com/infra/ubuntu jammy-infra-updates InRelease
Hit:10 https://ppa.launchpadcontent.net/graphics-drivers/ppa/ubuntu jammy InRelease
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
2 packages can be upgraded. Run 'apt list --upgradable' to see them.

~$ apt list --upgradable
Listing... Done
python3-update-manager/jammy-updates,jammy-updates 1:22.04.20 all [upgradable from: 1:22.04.18]
update-manager-core/jammy-updates,jammy-updates 1:22.04.20 all [upgradable from: 1:22.04.18]

~$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  python3-update-manager update-manager-core
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up nvidia-dkms-390 (390.157-0ubuntu0.22.04.2) ...
update-initramfs: deferring update (trigger activated)
update-initramfs: Generating /boot/initrd.img-6.5.0-17-lowlatency
INFO:Enable nvidia
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
Removing old nvidia-390.157 DKMS files...
Deleting module nvidia-390.157 completely from the DKMS tree.
Loading new nvidia-390.157 DKMS files...
Building for 6.5.0-17-lowlatency 6.5.0-28-lowlatency
Building for architecture x86_64
Building initial module for 6.5.0-17-lowlatency
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/nvidia-dkms-390.0.crash'
Error! Bad return status for module build on kernel: 6.5.0-17-lowlatency (x86_64)
Consult /var/lib/dkms/nvidia/390.157/build/make.log for more information.
dpkg: error processing package nvidia-dkms-390 (--configure):
 installed nvidia-dkms-390 package post-installation script subprocess returned error exit status 10
dpkg: dependency problems prevent configuration of nvidia-driver-390:
 nvidia-driver-390 depends on nvidia-dkms-390 (<= 390.157-1); however:
  Package nvidia-dkms-390 is not configured yet.
 nvidia-driver-390 depends on nvidia-dkms-390 (>= 390.157); however:
  Package nvidia-dkms-390 is not configured yet.

dpkg: error processing package nvidia-driver-390 (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                        Processing triggers for initramfs-tools (0.140ubuntu13.4) ...
update-initramfs: Generating /boot/initrd.img-6.5.0-28-lowlatency
Errors were encountered while processing:
 nvidia-dkms-390
 nvidia-driver-390
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any help is appreciated ... note: "follow-up from previous failure". Why is it failing? And is there anything I can do (subject to install a newer GPU)?

---

### Post by Rick St. George on 2024-04-29
Apparently this is a Bug (see: [https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/2037082/comments/32]("https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/2037082/comments/32")) so ... should I uninstall VirtualBox and wait till they fix the problem??? I have this VM running my Trading Software, which I also am running on my Laptop, so I won't lose any charting / analysis / quotes etc. Maybe this would allow the OS v22.04 to boot properly??? Don't understand since  Vbox is not running upon Boot, why is it preventing it from booting??? Things that make you go HHmmmm!!!

---

### Post by Rick St. George on 2024-04-30
Tried Boot Repair ... Paste Bin before [http://paste.ubuntu.com/p/HvNtphQbcj]("http://paste.ubuntu.com/p/HvNtphQbcj")
After [http://paste.ubuntu.com/p/vkH6CzBXz4]("http://paste.ubuntu.com/p/vkH6CzBXz4")
but get weird Yellow Shell prompt (EFI Shell version 2.31)  .... Don't know what to do?!?

Noticed during Boot Repair process it stated, boot files are far from start of disk, ude gParted to create /boot at start of disk.

I remember when doing the fresh install, I made 3 partitions.
1. /boot efi
2. /  
3. /home

But don't know where it put them! Logically, it should have put the 1st partition - /boot, at the start of the drive. In looking at the paste bin file, 
it shows Partition table entries are not in disk order. Maybe I chose wrong options during installation of the OS (certainly more than I've ever seen)?!?

Would it be futile to Re-install the OS?
Wouldn't it be the same problem with an old GPU & Driver and VirtualBox interfering with the kernel as the messages show? 

Or .... Maybe I should just Re-install v20.04 ???
Any help would be appreciated... Thanks!

---

### Post by tea for one on 2024-05-01
> **Rick St. George said:**
> I remember when doing the fresh install, I made 3 partitions.
1. /boot efi
2. /  
3. /home
[COLOR="#0000FF"]Line 156[/COLOR] - sda	: is-GPT,	hasBIOSboot,	[COLOR="#0000FF"]has-noESP,[/COLOR] 	not-usb,	not-mmc, has-os,	no-wind,	2048 sectors * 512 bytes
There is no sign of an EFI partition in the boot-repair report
> but get weird Yellow Shell prompt (EFI Shell version 2.31) .... Don't know what to do?!?
It appears that your PC is EFI compatible.
When you installed the OS, did you not boot the installer in UEFI mode?

---

### Post by Rick St. George on 2024-05-01
Not sure what you mean by booting installer in UEFI mode? The installer boots on its on via USB thumb drive, and BIOS settings was for UEFI Ubuntu to boot first, which it must have recognized via the /boot efi partition. I assume by partitioning the New SSD 1 TB drive as noted above, that the installer would recognize them as such. And apparently it did. Hoever, I believe the Boot Repair program changed it some how and don't know what it did to my computer. I am about to try again with the ISO thumb Drive to find out, and possibly do a Repair installation or a Re-install. Just not sure what to do about it installing the Home Dir when I have a separate /Home partition with GBs of files. It also bothers me "partition talbes are not in disk order" which is the fault of the installer. The /boot partition is at the beginning of the disk however.

Thanks for your reply and help!

---

### Post by tea for one on 2024-05-01
> **Rick St. George said:**
> Not sure what you mean by booting installer in UEFI mode?
When you boot the installer in UEFI mode, Ubuntu will create the essential ESP and root partitions automatically.
Of course, you can change this to use a separate home if required.
> or a Re-install.
If you decide to re-install, backup your data first
When you have booted the installer, open a terminal and enter:-
```
[ -d /sys/firmware/efi ] && echo "UEFI" || echo "Legacy"
```

---

### Post by Rick St. George on 2024-05-01
Did so ... and it replied "Legacy". But what did that do? 
Should I REPLACE - or - MAUAL Partition??? I would like to keep the /home partition with all my files.
I see that the Partition Table is MBR and not GPT ... maybe that was part of the problem. If I choose GPT Table it will delete all data on the disk. 
Should to another Fresh complete INSTALL? Built this system in 2014, MOBO is MSI 990FXA-GD65 v2 with AMD Fishara 8 core CPU.

---

### Post by tea for one on 2024-05-01
> **Rick St. George said:**
> Did so ... and it replied "Legacy". But what did that do?
This means that you have booted in old-fashioned Legacy mode.

UEFI mode is the modern way and I suggest that you search for articles explaining the distinct advantages of UEFI installations.
After 6 days in the life of this thread without a permanent solution, my advice is:-

Backup your data
Boot the installer in UEFI mode
Create GPT on your disk
Install
Restore your data

I realise that this may seem a brutal option but, if done correctly, your PC will be sprinkled with magic powder.

Here is a little screenshot showing a USB with two boot choices
Look at the titles (same disk)  - USB: UEFI:

---

### Post by Rick St. George on 2024-05-01
I understand there is a difference, but how do you BOOT in UEFI mode? In BIOS I selected UEFI Boot as 1st Option. SATA SSD as 2nd Option after installation.
But first I have to choose to boot the USB ISO thumb drive in order to install the OS. The rest is upto the Installer. 

In the BIOS my optinos are;

USB Hard Disk: SanDisk Ultra Backup 2.01   (thumbdrive)
UEFI: Built-in EFI Shell
Hard Disk: WD Blue 
USB Floppy
USB Key
USB CD/DVD
BEV

Previously chose Sandisk Backup, the thumb drive. Which should I choose?

---

### Post by tea for one on 2024-05-01
> **Rick St. George said:**
> I understand there is a difference, but how do you BOOT in UEFI mode?
PC powered off
Attach your Ubuntu install USB
Power On
Press your dedicated key (F2 or F10 or other) to access PC one time boot menu
Stop and take a photo with your smart phone
Post the picture here

---

### Post by Rick St. George on 2024-05-01
Found in BIOS screen -> UEIF BBS Priorities, selected UEFI SanDisk.
Then found that in BOOT Order, selected as no.1.
Booted to USB Installer, once up, ran the d firmware code and verified Boot in UEFI mode.
Selected to Format and Flag 500 MB partition as EFI Boot,
Selected to Format and Flag 300 GB partition as /  ext4
Selected to keep 650 GB /Home partition   (which saves all my data).
Now I can move relevant files into their respective folders.

Will post under Virtualization problem i had after installing VirtualBox which prevented it from booting properly in the first place.  Thanks Tea!

---

