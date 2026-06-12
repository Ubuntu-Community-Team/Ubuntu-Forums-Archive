---
title: "UEFI doesn't generate grub menu"
date: 2016-08-27
forum: Installation &amp; Upgrades
---

### Post by HiSiskin on 2016-08-27
I installed Ubuntu 16.04 LTS on a new PC which had Windows 10 installed by creating partitions for / and swap on C: which is 240GB SSD and /home on D: which is a hard drive. Installation was completed without problems but on the system boot we couldn't see the familiar grub menu for selecting what OS should be booted. I have selected the whole sda as the device for the boot-loader and I can only boot Ubuntu by setting UEFI booting priority to the whole sda. In a similar way, I can only boot Windows by resetting the UEFI priority to the Windows Boot Manager.

How colud I regain the grub menu on the boot, preferably keeping the current Ubuntu install untouched?

---

### Post by sudodus on 2016-08-27
I suspect that Ubuntu's update-grub does not see the Windows partition correctly. And with only one operating system, the grub menu will not be displayed. 

The reason might be that Windows is hibernated or semi-hibernated alias fast boot. So if you turn off fast boot in Windows and shut it down completely, the file system will be completely saved in a correct way, and you can reboot into Ubuntu and run

```
sudo update-grub
```

and it will recognize Windows, create a menuentry for it and display the grub menu.

If there are still problems, maybe the NTFS file system in the Windows partition is damaged. You repair that in Windows, either in a dospromt alias cmd window with

```
chkdsk /f X:
```

where X: in the Windows partition, usually C: or with some GUI tool in Windows.

Reboot twice into Windows to fix the file system completely and after that reboot into Ubuntu and run

```
sudo update-grub
```

and it will recognize Windows, create a menuentry for it and display the grub menu.

---

### Post by HiSiskin on 2016-08-27
Thanks for the prompt reply.

Then I did:
* disabled 'fast boot' both on UEFI and on Windows.
* run update-grub.
--- they didn't work ---
* run chkdsk /f C: which actually run on the outset of the next boot.
* run update-grub again.
--- still didn't work ---

The word 'Windows' isn't found in the update-grub message.

Hopeless again so far.
Any other idea?

---

### Post by sudodus on 2016-08-27
It seems we have to dig deeper into this problem.

One way to get more knowledge about your system is to run ***Boot Repair***. At this stage, do ***not*** let it try to repair, only run the diagnostic tool ***'Create a BootInfo summary'***, and post the link to the uploaded result.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by HiSiskin on 2016-08-27
Thanks for an 'advanced' info.

Here's the output from the diagnosis:

[https://www.dropbox.com/s/rla4jmn8st2nnq3/bootrepair.txt?dl=0](https://www.dropbox.com/s/rla4jmn8st2nnq3/bootrepair.txt?dl=0)

(The tool didn't give an URL. We got a text output only.)

---

### Post by sudodus on 2016-08-28
Let us start with this piece of information from the BootInfo summary:

```
ADDITIONAL INFORMATION :
=================== log of boot-repair 2016-08-28__09h53 ===================
boot-repair version : 4ppa38
boot-sav version : 4ppa38
glade2script version : 3.2.3~ppa1
boot-sav-extra version : 4ppa38
boot-repair is executed in installed-session (Ubuntu 16.04.1 LTS, xenial, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/boot/vmlinuz-4.4.0-34-generic root=UUID=0e6ccec8-b345-48e2-a163-2942a1ca5475 ro quiet splash vt.handoff=7
Windows is hibernated, refused to mount.
Failed to mount '/dev/sda4': &#35377;&#21487;&#12373;&#12428;&#12390;&#12356;&#12394;&#12356;&#25805;&#20316;&#12391;&#12377;
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
mount -t ntfs-3g -o remove_hiberfile /dev/sda4 /mnt/boot-sav/sda4
NTFS signature is missing.
Failed to mount '/dev/sda3': &#28961;&#21177;&#12394;&#24341;&#25968;&#12391;&#12377;
The device '/dev/sda3' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
mount /dev/sda3 : Error code 12
mount -r /dev/sda3 /mnt/boot-sav/sda3
NTFS signature is missing.
Failed to mount '/dev/sda3': &#28961;&#21177;&#12394;&#24341;&#25968;&#12391;&#12377;
The device '/dev/sda3' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
mount -r /dev/sda3 : Error code 12
```

It seems you have not managed to get the NTFS partitions into a state, which can be mounted by Ubuntu. Please try again with **/dev/sda4**

```
/dev/sda4: LABEL="Windows" UUID="68128DDF128DB31C" TYPE="ntfs" PARTUUID="83650596-5d46-486e-a1f1-5ed4ed4a0856"
```

which seems to contain Windows (the Windows system). I think you should try with **/dev/sda3** too.

```
=================== Suggested repair
The default repair of the Boot-Repair utility would purge (in order to fix packages sign-grub) and reinstall the grub-efi-amd64-signed of sda5, using the following options:        sda2/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s   fix-windows-boot use-standard-efi-file


=================== Blockers in case of suggested repair
The current session is in Legacy mode. Please reboot the computer, and use this software in an EFI session. &#12371;&#12428;&#12399;&#12289;&#12371;&#12398;&#27231;&#33021;&#12364;&#26377;&#21177;&#12395;&#12394;&#12426;&#12414;&#12377;&#12290; For example, use a live-USB of Boot-Repair-Disk-64bit (www.sourceforge.net/p/boot-repair-cd), after making sure your BIOS is set up to boot USB in EFI mode.


=================== Advice in case of suggested repair
&#35686;&#21578;&#65306;&#12452;&#12531;&#12479;&#12540;&#12493;&#12483;&#12488;&#25509;&#32154;&#12375;&#12394;&#12356;&#12391;&#32153;&#32154;&#12377;&#12427;&#12392;&#12289;&#12362;&#20351;&#12356;&#12398;&#12471;&#12473;&#12486;&#12512;&#12399;&#12502;&#12540;&#12488;&#20986;&#26469;&#12394;&#12367;&#12394;&#12427;&#12391;&#12375;&#12423;&#12358;&#12290; &#12452;&#12531;&#12479;&#12540;&#12493;&#12483;&#12488;&#12395;&#25509;&#32154;&#12375;&#12390;&#12367;&#12384;&#12373;&#12356;&#12290;
PC&#12398;&#36215;&#21205;&#12399;&#12289;Legacy&#12514;&#12540;&#12489;&#12395;&#12394;&#12387;&#12390;&#12356;&#12414;&#12377;&#12290;EFI&#12514;&#12540;&#12489;&#12395;&#22793;&#26356;&#12375;&#12383;&#24460;&#12395;&#20877;&#35430;&#34892;&#12377;&#12427;&#12371;&#12392;&#12364;&#12391;&#12365;&#12414;&#12377;&#12290;
&#32154;&#12369;&#12414;&#12377;&#12363; ?


=================== Final advice in case of suggested repair
BIOS&#12399;sda2/efi/.../grub*.efi&#12501;&#12449;&#12452;&#12523;&#12395;&#12502;&#12540;&#12488;&#12377;&#12427;&#12371;&#12392;&#12434;&#24536;&#12428;&#12394;&#12356;&#12391;&#12367;&#12384;&#12373;&#12356;&#65281;

[&#20170;&#20351;&#12387;&#12390;&#12356;&#12427;OS - Ubuntu 16.04.1 LTS]&#12398;&#12502;&#12540;&#12488;&#12501;&#12449;&#12452;&#12523;&#12364;&#12289;&#12487;&#12451;&#12473;&#12463;&#12398;&#12473;&#12479;&#12540;&#12488;&#20301;&#32622;&#12363;&#12425;&#36960;&#12367;&#38626;&#12428;&#12383;&#20301;&#32622;&#12395;&#12354;&#12426;&#12414;&#12377;&#12290;BIOS&#12399;&#12371;&#12428;&#12434;&#26908;&#30693;&#12391;&#12365;&#12394;&#12356;&#12391;&#12375;&#12423;&#12358;&#12290; /boot&#12497;&#12540;&#12486;&#12451;&#12471;&#12519;&#12531;&#12434;&#20316;&#12387;&#12383;&#12354;&#12392;&#12391;&#12289;&#20877;&#24230;&#35430;&#12375;&#12383;&#26041;&#12364;&#12356;&#12356;&#12363;&#12418;&#12375;&#12428;&#12414;&#12379;&#12435; (EXT4, >200MB, &#12487;&#12451;&#12473;&#12463;&#12398;&#38283;&#22987;). &#12371;&#12428;&#12399;gParted&#12398;&#12424;&#12358;&#12394;&#12484;&#12540;&#12523;&#12434;&#20171;&#12375;&#12390;&#23455;&#34892;&#12377;&#12427;&#12371;&#12392;&#12364;&#12391;&#12365;&#12414;&#12377;&#12290; [&#12502;&#12540;&#12488;&#20462;&#24489;]&#12458;&#12503;&#12471;&#12519;&#12531;&#12398; [&#21029;&#12497;&#12540;&#12486;&#12451;&#12471;&#12519;&#12531;&#12395;/boot&#12434;&#27083;&#25104;:] &#12363;&#12425;&#12289;&#12371;&#12398;&#12497;&#12540;&#12486;&#12451;&#12471;&#12519;&#12531;&#12434;&#36984;&#25246;&#12375;&#12390;&#19979;&#12373;&#12356;&#12290; (https://help.ubuntu.com/community/BootPartition)

If your computer reboots directly into Windows, try to change the boot order in your BIOS.
If your BIOS does not allow to change the boot order, change the default boot entry of the Windows bootloader.
For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\...\grub*.efi

PC&#12398;&#36215;&#21205;&#12399;&#12289;Legacy&#12514;&#12540;&#12489;&#12395;&#12394;&#12387;&#12390;&#12356;&#12414;&#12377;&#12290;EFI&#12514;&#12540;&#12489;&#12395;&#22793;&#26356;&#12375;&#12383;&#24460;&#12395;&#20877;&#35430;&#34892;&#12377;&#12427;&#12371;&#12392;&#12364;&#12391;&#12365;&#12414;&#12377;&#12290;


=================== User settings
The settings chosen by the user will not act on the boot.




```

From this information (and from the beginning of the BootInfo script too), it seems you have booted in BIOS mode, while there is information about an EFI partition indicating that Windows was installed in UEFI mode. Please make the computer boot in UEFI mode and run BootRepair with its BootInfo summary again!

Could one of the problems be, that you have installed Ubuntu in BIOS mode? In that case you should make the computer boot in UEFI mode and re-install Ubuntu. See this link, and the links from it about UEFI.

[Installation/FromUSBStick#UEFI](https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI)

-o-

To other people reading this thread: Please chip in and suggest how to solve this problem :-)

---

### Post by mook765 on 2016-08-28
The Boot-repair-summary tells that Grub is installed it the MBR of /dev/sda. That really means that Ubuntu has been installed in CSM- mode.
Please run Boot-Repair again, but make sure that you boot in UEFI-mode.
You may run the recommended repair with Boot-repair, that will install the needed files in ESP and add needed fstab-entries.
Post URL from new summary.
Please provide information about your hardware.

---

### Post by HiSiskin on 2016-08-28
> run Boot-Repair again, but make sure that you boot in UEFI-mode
Can't do that. For a bootable USB stick, UEFI gives two boot menu entries:

UEFI: ---usb device name---
---usb device name---

But we can't select the former and the latter runs Ubuntu in bios mode.

Might I change the nature of the problem as:
How could we do a full clean install, or 'install from scratch', for both Win and Ubu?
For their perfectly peaceful coexistence on a UEFI PC, of course.
That might completely erase the current dragging problem(s).

---

### Post by mook765 on 2016-08-28
"UEFI: ---usb device name---"
Yes, this is what you have to choose.
If this doesn't work you may have to configure your UEFI-Bios-settings.
You may have to disable Secure-Boot in UEFI-Bios.
Refer to the manual of your motherboard-vendor.
Please provide us some information about your hardware. Without information it is impossible to assist...

---

### Post by yancek on 2016-08-28
> How could we do a full clean install, or 'install from scratch', for both Win and Ubu?

If you decide to go the reinstall route, the link below is the official Ubuntu documentation. 

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by sudodus on 2016-08-28
If you have install files or media for Windows, I think you can install it in BIOS mode, which makes things easier.

But if you have to rely on a backup of Windows, for example a cloned image, you have to try again to boot the Ubuntu live drive from UEFI. The more you tell us about the computer, the greater chance that we can help you. The UEFI systems are very different between computers, and some of them do not comply to the standards for UEFI.

So please specify

- the brand name and model of the computer
- the brand name and version of the UEFI-BIOS system (if you can find it)

-o-

When re-installing, start with Windows, and install Ubuntu afterwards.

---

### Post by oldfred on 2016-08-28
If you have UEFI Secure Boot on, Boot from USB may not be allowed by default as that is not secure. BIOS/CSM/Legacy mode is always Secure boot off. You will have a setting somewhere that says allow USB boot or allow UEFI boot from USB. You may also have settings to enable USB ports.

How you boot install media is then how it installs. But Boot-Repair in advanced options should let you install the UEFI verison of grub. Choose the full uninstall/reinstall option and you want to uninstall grub-pc (BIOS) and install grub-efi-amd64 (UEFI).

What brand/model system?

---

### Post by HiSiskin on 2016-08-28
Hi All,

I think the problem is solved, finally.

In the [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) doc:
> Note that in a UEFI-mode installation, Ubuntu will not ask you where to install the boot loader. If it does, or if it complains about the lack of a BIOS Boot Partition, you've probably accidentally booted in BIOS/CSM/legacy mode.

In my first install on my first UEFI machine, that was the case not *accidentally *but from my ignorance about the new bios-like software, the ignorance is continuing though.

This time I set the boot priority for UEFI to 'UEFI: ..install disk..' instead of simple '..install disk..' that I did at the first install.

Oddly enough, the installer still asked where to install the boot loader contrary to the above document. Then I selected sda2 which is the only efi partition on the machine and it has Windows Boot Manager in it.

Then, voila!!
We got/get a grub menu on the boot enabling selecting from the two OSes and the running Ubuntu is in really UEFI mode as the:

> test -d /sys/firmware/efi && echo efi || echo bios

says.

We've got the good-old grub menu finally and it seems the problem is solved.

Thank you very very much for all for helping us. This forum and the great people on it are the most indispensable things in the community. Thanks again.

---

### Post by sudodus on 2016-08-29
Congratulations and thanks for sharing your solution :KS

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

