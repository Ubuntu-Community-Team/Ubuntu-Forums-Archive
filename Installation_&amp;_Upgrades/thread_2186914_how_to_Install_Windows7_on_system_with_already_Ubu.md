---
title: "how to Install Windows7 on system with already Ubuntu OS"
date: 2013-11-09
forum: Installation &amp; Upgrades
---

### Post by raheem.syed.786 on 2013-11-09
Hi,

can any one please let me know the procedure to install either Windows7 or 8 on my laptop with already installed Ubuntu 13.04.

I have much data on Ubuntu, but facing many problems when trying to get new softwares/drivers for some devices in the market, as market is providing the softwares/drivers for either Mac or Windows version.. for ubuntu those are not fully supported with wine or any else softwares..

so requesting to share teh procedure to install Windows7/8 on my ubuntu 13.04 ...


thanks in advance.....

---

### Post by fantab on 2013-11-09
First, you need to have a NTFS partition on your HDD. If you don't have one then make one. Install Windows, reformat the partition with NTFS again with Windows installer. Finish installation. 
The Windows Install will corrupt Ubuntu booting so you will need to [Reinstall GRUB]("https://help.ubuntu.com/community/Grub2/Installing#via_the_LiveCD_terminal"). Have a same version Ubuntu on DVD/USB ready to be used to reinstall Grub.

Also what problems are you having with Ubuntu... perhaps we can help you. Most of the Hardware out there is supported in Linux/Ubuntu.

---

### Post by raheem.syed.786 on 2013-11-11
Hi,


thanks for the reply,..I will try to install windows...as you said.


also for the second queury,

I was facing  problems with the device detecting in virtual box, so i tried to install the virtual box 4.3 by removng the Virtual Box 4.2X , & found my UI was not proper, so i got some blogs to where the fix was available ...
so i followed below steps in order:
1. sudo su
2. apt-get update
3. apt-get install linux-headers-generic
4. apt-get dist-upgrade
5. reboot 
6. sudo su
7. apt-get install nvidia-current-updates
8.-- i rebooted
here my WIFI went & net disconnected....
& no more  net & also direct wired LAN connection i tried no connectiong(this was first time connecting the LAN cable for internet as i was using with WIFI)...
for the both WIFI & wired LAN showing connecting status & then ..it automotically shows disconneted status..
(I checked my internet connection in other it is fine)

please help me how to recovery this problem as not able to connect internet & also the desktop UI is not showing the Status Bar/Quick Launch menu bar ...(only the files on the desktop is displayed)

---

### Post by raheem.syed.786 on 2013-11-12
Hi , can u please reply

---

### Post by fantab on 2013-11-12
Have you installed Windows?

I am not familiar with Virtual Box... and I can't help you with it. Once you have all the OS installed and working then start an  NEW Thread with an appropriate title and someone here will guide you to a solution. 

IMO the commands you ran are unrelated to the problem you are having with VB.
To remove/uninstall an application use Software Center or Synaptic Package Manager. Synaptic does a better job with "mark for complete removal" option.

Also start a separate thread to find out whats wrong with your wifi... Only people who can help you with "how to Install Windows7 on system with already Ubuntu OS" will get here. You will get better response if you open a new thread with Wifi in the title. 

Good Luck.

---

### Post by raheem.syed.786 on 2013-11-14
Hey, 

many thanks , but i resolvedall my problems...

1. WIFI was not connecting--> I have installed the reinstalled the drivers from the .deb back ups availabe in the path([LEFT][COLOR=#000000]var/cache/apt/archives[/COLOR][/LEFT]
)...with cmd([LEFT][COLOR=#000000]sudo dpkg --install *deb[/COLOR][/LEFT]
)

2. ubuntu app menu, Launchpad & Status bar was not displayed on desktop: 
[LEFT][COLOR=#000000]for compiz reset: Install dconf-tools[/COLOR]
[COLOR=#000000]dconf reset -f /org/compiz/ log out and in.[/COLOR]
[COLOR=#000000]To refresh your Unity launcher with the default set of icons: unity --reset-icons

3. [FONT=arial]To come to actual requested post, thanks for your suggestion & i have done below things:

a. I already have ubuntu 13.10 at /dev/sda2 (with UEFI & secure boot enabled).
b. Now I got the win-8.1 CD & started the instalation &
in one of this win-8.1 instalation wizard asked to either " upgrade OS to win 8.1 --or --custom install", 
in that i selected custom selection (because the upgrade can happen only if my current OS was Win-7 or 8),
then next screen was the partion screen where it listed my all partitions, 
in that i selected my desire partion(/dev/sda5) where i need my win-8.1, then pressed "Delete"--& then next to continue the installation &
succesfully installed win-8.1.

Here, as you said my grup corrupted & i can load only win-8.1, & my ubuntu at boot was not shown at all,
then as you said i gone through the site suggested to reinstall grub 
where i tried 
[/FONT][/COLOR]**1. via Partition Files Copy: **[COLOR=#000000][FONT=arial]
[/FONT][/COLOR]this method does not worked as I think GRUB files have been deleted. 
[B]
2. via bootRepair tool: [/B][COLOR=#000000][FONT=arial]
[/FONT][/COLOR]1. it was not able do repair if secure boot was enabled & the task was repeating even pressing ok or exit.


**& other methods were so confusing...**


except this, below method I have not tried...
[B]may be this would have been worked
[COLOR=#000000][FONT=arial]aaa: [/FONT][/COLOR][COLOR=#800000][FONT=arial]via Live CD terminal[/FONT][/COLOR][/B]


[LIST]
[*][COLOR=#b22222]sudo fdisk -l
sudo blkid[/COLOR][COLOR=#b22222]In the following commands: [/COLOR]
[LIST]
[*][COLOR=#b22222]Use the partition number of the Ubuntu installation with *mount* command. [/COLOR]
[*][COLOR=#b22222]Do **not** use the partition number with the *grub-install* command. [/COLOR]
[*][COLOR=#b22222]**X** is the drive letter (a, b, c, etc.); **Y** is the partition number (1, 5, etc). [/COLOR]
[*][COLOR=#b22222]*--boot-directory* is the folder in which the GRUB folder is located. This is normally */boot* but should be changed if the *grub* folder is located elsewhere. [/COLOR]
[*][COLOR=#b22222]On systems with a separate */boot* partition, that partition should be mounted to */mnt/boot*. For instance: sudo mount /dev/sda6 /mnt/boot [/COLOR]
[*][COLOR=#b22222]grub-install will restore missing files in the *grub* folder but will not restore intentionally deleted or corrupted files. To accomplish these tasks GRUB 2 must be completely removed and reinstalled. [/COLOR]
[COLOR=#b22222]sudo mount /dev/sdXY /mnt # Example: sudo mount /dev/sda5 /mnt
sudo grub-install --boot-directory=/mnt/boot /dev/sdX # Example: sudo grub-install --boot-directory=/mnt/boot /dev/sda[/COLOR][COLOR=#b22222]**If Ubuntu is installed on B-tree file system i.e. btrfs** then */boot* changes to */@/boot* in above commands such that : [/COLOR]
[COLOR=#b22222]sudo grub-install --boot-directory=/mnt/@/boot /dev/sdX # Example: sudo grub-install --boot-directory=/mnt/@/boot /dev/sda[/COLOR][COLOR=#b22222]**For GRUB 2 version 1.98 and earlier (Ubuntu 10.04)**, the installation command is slightly different. Rather than designating the *--boot-directory*, the switch is *--root-directory*. In this case, the location changes to */mnt* [/COLOR]
[COLOR=#b22222]sudo grub-install --root-directory=/mnt /dev/sdX[/COLOR]
[/LIST]
[/LIST]
[COLOR=#000000][FONT=arial]

[/FONT][/COLOR][COLOR=#006400][FONT=arial]then I have done below in the **Live CD terminal**:

[/FONT][/COLOR][COLOR=#006400]sudo add-apt-repository ppa:danielrichter2007/grub-customizer

sudo apt-get update

sudo apt-get install grub-customizer[/COLOR][COLOR=#333333][FONT=Helvetica Neue][SIZE=2][COLOR=#006400]With *Grub-Customizer, highlight the OS entry and click up / down arrow button to change its order. Or set the default OS in [I]General Settings tab.*[/I][/COLOR][/SIZE][/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue][SIZE=2]*[I][[COLOR=#006400][IMG]http://ubuntuhandbook.org/wp-content/uploads/2013/08/grub-customizer-300x214.jpg[/IMG][/COLOR]]("http://ubuntuhandbook.org/wp-content/uploads/2013/08/grub-customizer.jpg")*[/I][/SIZE][/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue][SIZE=2][COLOR=#006400]*[I]**If you&#8217;re comfortable with running some terminal commands, it&#8217;s not difficult to change default OS without installing any third-party program.***[/I][/COLOR][/SIZE][/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue][SIZE=2][COLOR=#006400]*[I]**1.) Press [B]Ctrl+Alt+T to open terminal. Edit the &#8220;/etc/default/grub&#8221; via below command and change [B]GRUB_DEFAULT=0 to [B]GRUB_DEFAULT=saved. This will make it easy to change default OS later.**[/B][/B][/B]*[/I][/COLOR][/SIZE][/FONT][/COLOR]
[SIZE=2][COLOR=#006400]*[I]**[B][B]sudo gedit /etc/default/grub**[/B][/B]*[/I][/COLOR][/SIZE][COLOR=#333333][FONT=Helvetica Neue][SIZE=2][COLOR=#006400]*[I]**[B][B]2.) Update grub to apply changes to grub configuration:**[/B][/B]*[/I][/COLOR][/SIZE][/FONT][/COLOR]
[SIZE=2][COLOR=#006400]*[I]**[B][B]sudo update-grub**[/B][/B]*[/I][/COLOR][/SIZE][COLOR=#333333][FONT=Helvetica Neue][SIZE=2][COLOR=#006400]*[I]**[B][B]3.) After that, you can run [B]sudo grub-set-default with the number of menu entry to boot (the first entry is 0) at any time, which will set the entry as default OS permanently. Or run [B]sudo grub-reboot only for next boot.**[/B][/B][/B][/B]*[/I][/COLOR][/SIZE][/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica Neue][SIZE=2][COLOR=#006400]*[I]**[B][B]For example, below command will set Windows 7 as default OS (Windows 7 is 4 in picture at top) permanently.**[/B][/B]*[/I][/COLOR][/SIZE][/FONT][/COLOR]
[SIZE=2][COLOR=#006400]*[I]**[B][B]sudo grub-set-default 4**[/B][/B]*[/I][/COLOR][/SIZE][FONT=arial][SIZE=3][B][COLOR=#b22222][U]


Even my problem was not solved then i found 
[/U][/COLOR][/B][/SIZE]

then I saw another post & in win-8.1 i done below things:


[COLOR=#ff0000][B]1. disable the fast boot mentioned in the site: 
[/B][/COLOR]
[/FONT][http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)[FONT=arial]

[/FONT][COLOR=#333333]**[SIZE=1]To Turn "Fast Startup" On or Off in System Settings[/SIZE]**[/COLOR]
[COLOR=#333333][SIZE=1][B]
1. [/B]Open the _**[Control Panel (icons view)]("http://www.eightforums.com/tutorials/2627-control-panel-open-windows-8-a.html")**_, and click on the **Power Options** icon.

**2.** Click/tap on the **Choose what the power buttons do** link on the left side. (see screenshot below)[/SIZE][/COLOR]
[COLOR=#333333][SIZE=1]
[[IMG]http://www.eightforums.com/attachments/tutorials/6230d1337576251t-fast-startup-turn-off-windows-8-step-1.jpg[/IMG]]("http://www.eightforums.com/attachments/tutorials/6230d1337576251-fast-startup-turn-off-windows-8-step-1.jpg")[/SIZE][/COLOR]
[COLOR=#333333][SIZE=1][B]
3.[/B] Click/tap on the **Change settings that are currently unavailable** link at the top. (see screenshot below)[/SIZE][/COLOR]
[COLOR=#333333][SIZE=1]
[[IMG]http://www.eightforums.com/attachments/tutorials/6231d1337576251t-fast-startup-turn-off-windows-8-step-2.jpg[/IMG]]("http://www.eightforums.com/attachments/tutorials/6231d1337576251-fast-startup-turn-off-windows-8-step-2.jpg")[/SIZE][/COLOR]
[COLOR=#333333][SIZE=1][B]
4.[/B] If prompted by _**[UAC]("http://www.eightforums.com/tutorials/5509-user-account-control-uac-change-settings-windows-8-a.html")**_, then click/tap on **Yes**. 

**5. **Do **step 6 or 7** below for what you would like to do. 

[B]6. [COLOR=#0000cd]To Turn On "Fast Startup" (Hybrid Boot) for a "Hybrid Shutdown" 
[/COLOR][COLOR=#ff0000]NOTE: [/COLOR][/B]*This is the default setting*.[/SIZE][/COLOR]
[COLOR=#333333][SIZE=1]
A) Under **Shutdown settings**, check the **Turn on fast startup** box, and click/tap on the **Save changes** button. (see screenshot below)
**[COLOR=#ff0000]NOTE:[/COLOR]*** If the **Turn on fast startup** setting is not listed, then you will need to close the System Settings window, _**[enable hibernate]("http://www.sevenforums.com/tutorials/819-hibernate-enable-disable.html")**_, then start back at step 1 again*.[/SIZE][/COLOR]
[COLOR=#333333][SIZE=1]
[[IMG]http://www.eightforums.com/attachments/tutorials/6232d1337576251t-fast-startup-turn-off-windows-8-step-3.jpg[/IMG]]("http://www.eightforums.com/attachments/tutorials/6232d1337576251-fast-startup-turn-off-windows-8-step-3.jpg")[/SIZE][/COLOR]
[COLOR=#333333][SIZE=1]
B) The _**[Shut down]("http://www.eightforums.com/tutorials/2584-lock-log-off-restart-shut-down-switch-user-windows-8-a.html")**_ Power option will now perform as a **hybrid shut down** when used.

C) Go to **step 8** below.[/SIZE][/COLOR]
[COLOR=#333333][SIZE=1]
**7.** **[COLOR=#0000cd]To Turn Off "Fast Startup" for a "Full Shutdown"[/COLOR]**[/SIZE][/COLOR]
[COLOR=#333333][SIZE=1]
A) Under **Shutdown settings**, check the **Turn on fast startup** box, and click/tap on the **Save changes** button. (see screenshot below step 6A)
[COLOR=#ff0000]**NOTE:**[/COLOR]* If the **Turn on fast startup** setting is not listed, then _**[hibernate]("http://www.sevenforums.com/tutorials/819-hibernate-enable-disable.html")**_ has been disabled that removed this setting and also disabled fast startup*.

B) The _**[Shut down]("http://www.eightforums.com/tutorials/2584-lock-log-off-restart-shut-down-switch-user-windows-8-a.html")**_ Power option will now perform as a normal **full shut down** when used.

C) Go to **step 8** below.[/SIZE][/COLOR]
[COLOR=#333333][SIZE=1]
**8.** You can now close the Power Options window if you like.[/SIZE][/COLOR]
[/LEFT]


[B]2. after disable the fast boot, i done below things in win-8.1 OS 

[/B][COLOR=#333333][FONT=UbuntuRegular]The way to do this that's most reliable is to use bcdedit in Windows. Open an *Administrator* Command Prompt window and type:[/FONT][/COLOR]
[COLOR=#0000ff]bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[/COLOR][COLOR=#333333][FONT=UbuntuRegular]If you're booting with Secure Boot active, change grubx64.efi to shim.efi([COLOR=#ff0000]i have taken as mine is secure boot enabled[/COLOR]) (or maybe it'sshimx64.efi; in Linux, check the contents of /boot/efi/EFI/ubuntu to see what's there). Doing this in Windows is more reliable than other methods because some users have reported that some versions of Windows repeatedly re-register themselves as the default boot loader if the default is set outside of Windows. Although this is rare, it's consistent with what you're seeing, so using Windows for this task may be necessary.

[COLOR=#ff0000]After done above command able to boot only Linux then I done below command in my ubuntu linux terminal(not with LIVE CD):
[B]$ sudo grub-install /dev/sdX
$ sudo update-grub[/B][/COLOR]

[COLOR=#008000]After doing above now my boot menu came with both ubuntu & windows ,

but but, Windows was not able to boot because i found the [FONT=Ubuntu Mono]\EFI\Windows\grubx64.ef was missing which i copied from folder [/FONT][FONT=Ubuntu Mono]\EFI\ubuntu\grubx64.efi[/FONT][/COLOR][/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][COLOR=#000000][FONT=Ubuntu Mono]
then even not able to boot, so i just[B] disabled the secureboot, that s it my issue fixed,

[/B][/FONT][/COLOR][SIZE=4][COLOR=#006400][FONT=Ubuntu Mono]**both OSs (ubuntu & windows 8.1) able to boot successfully.**[/FONT][/COLOR][/SIZE][/FONT][/COLOR]

---

### Post by fantab on 2013-11-14
Well done. Congratulations!

If all is solved, mark the thread as 'Solved' using thread tools.

---

### Post by raheem.syed.786 on 2013-11-15
Hi,

here one more problem regarding when Secure boot is enabled,

1. when secure boot is enabled in BIOS, 
    not able to launch the windows 8.1 but ubuntu is working fine.

2. when secure boot is dis-abled in BIOS,   able to launch both.


so, please let me know how i can boot the win-8.1 with seucre boot enabled with grub?


if this is solved i will move it solved state as you said....

thanks in advance again...

---

### Post by fantab on 2013-11-15
If you can boot both OS with 'Secure Boot' disabled, then keep it disabled. No issues. 
[What is 'Secure Boot']("http://fossforce.com/2011/10/secure-boot-whats-microsofts-agenda/")?

---

### Post by oldfred on 2013-11-15
There is a bug that may be part of the issue.
 Unable to chainload Windows 8 with Secure Boot enabled  Also post #11 on using refind
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464)
Windows will not chain load from grub -
file path: /ACPI(a0341d0,0)/PCI(2,1f)/UnknownMessaging(12)/HD(2,96800,32000,7c043777b8608641,87,f6)/File(\EFI\Microsoft\Boot)/File(bootmgfw.efi

With UEFI you should not need EasyBCD. That is just another boot manager which UEFI and grub also are. Boot managers give you a choice of what to boot. Grub is both a boot manager and a boot loader for Ubuntu.
With BIOS some Windows users liked EasyBCD as you could only have one system boot from MBR. With UEFI all systems are equal in efi partition as boot able devices.

---

