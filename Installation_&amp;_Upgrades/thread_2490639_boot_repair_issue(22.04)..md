---
title: "boot repair issue(22.04)."
date: 2023-09-10
forum: Installation &amp; Upgrades
---

### Post by d3vestator on 2023-09-10
Was here 6 months ago because i was having the same issue
have errors when booting, and now eveytime i shutoff ubuntu, it stays loked on the ubntu symbol with the black screen and i have to push the power off button to turn it off
[https://paste.ubuntu.com/p/7bgChxJJqP/](https://paste.ubuntu.com/p/7bgChxJJqP/)

---

### Post by tea for one on 2023-09-11
> **d3vestator said:**
> i have to push the power off button to turn it off
Sometimes, this action can cause filesystem damage, which subsequently affects the boot process.

Can you boot into Windows and run chkdsk on the ntfs partitions?
Then, boot into a live "Try Ubuntu" session and run fsck on the ESP and ext4 partitions?
Any reported errors?

When the PC seems to freeze during Ubuntu shutdown, press Esc to see warning/error messages.

I notice you have Nvidia graphics, which can cause difficulty with Ubuntu during a Wayland session.
You can choose X11 at log in.

---

### Post by yancek on 2023-09-11
Another option when it is frozen:  Simultaneously hold down the left Alt key and the prt sc key in the upper right.  While holding down both keys type consecutively: r e i s u b
By the time you hit the last key it should start rebooting.  No need to have a terminal open, no need to use the Enter key.

Might be useful to post the errors you see on booting as you have not done that?

---

### Post by tea for one on 2023-09-11
You may have to edit a configuration file before using REISUB &#8211; the process may not be  fully enabled.

Open a terminal and enter:-
```
sudo nano /etc/sysctl.d/10-magic-sysrq.conf
```
Then change the number in line 26 from 176 to 244 i.e. **kernel.sysrq = 244**
Ctrl + o to save
Ctrl + x to exit

Press and hold continually the left **Alt** key
Press **Print Screen** and release
Press R E I S U B (lower case is fine) at approx. two second intervals 
By the way, the last letter in the process **B** reboots your system, sometimes you may want to power off completely by substituting the **B** for an **O**

---

### Post by d3vestator on 2023-09-12
Ok
1. i went to chdsk, i went to my local disk and went through properties, and i scanned it, and it noticed issues, fixed them, but didn't change anything

2. for the bootup errors, it says
6.82080 usb 3-2: device descriiptor read/64, error-110
22.4364761 usb 3-2: device descriptor read/64, error-110

3.    i went into try ubuntu and did fsck and it said the ext4 partition was fine, i couldn't fine the esp partition though

---

### Post by tea for one on 2023-09-13
> **d3vestator said:**
> i went into try ubuntu and did fsck and it said the ext4 partition was fine, i couldn't fine the esp partition though
[COLOR="#0000FF"]Line107[/COLOR] - nvme0n1p1	: [COLOR="#0000FF"]is---ESP[/COLOR],	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot

Boot into a "Try Ubuntu" session
Open a terminal and enter:-
```
sudo fsck /dev/nvme0n1p1
```
Any errors?

---

### Post by d3vestator on 2023-09-13
is that one that is mounted to /?

---

### Post by oldfred on 2023-09-13
For the ESP - efi system partition which is FAT32, it should be dosfsck.
man dosfsck  # but command is fsck.vfat
sudo /sbin/fsck.vfat -V <the fat32 device>
sudo fsck.vfat -t -a /dev/sdXY # where X is drive and Y is partition.
sudo fsck.vfat -t -a /dev/nvme0n1pY # where Y is ESP partition.

or for you
sudo fsck.vfat -t -a /dev/nvme0n1p1

> 6.82080 usb 3-2: device descriptor read/64, error-110
22.4364761 usb 3-2: device descriptor read/64, error-110
but it looks like error is on external drive?
Are you booting with a USB drive or other unknown device connected? Try disconnecting it.

---

### Post by tea for one on 2023-09-13
> **d3vestator said:**
> is that one that is mounted to /?
When you use a live session, the partitions on your internal device should not be mounted at all.
It is not advisable to run fsck (or fsck.vfat) on any mounted partition.

You can open Disks (gnome-disk-utility) in a "Try Ubuntu" session to check if anything is mounted.

---

### Post by d3vestator on 2023-09-13
sudo fsck /dev/nvme0n1p1
fsck from util-linux 2.37.2
fsck.fat 4.2 (2021-01-31)
/dev/nvme0n1p1: 210 files, 14487/65536 clusters

---

### Post by tea for one on 2023-09-13
No file system damage in your ESP (fat32) and System (ext4) partitions - that's good news.

In post no.2, I mentioned that Nvidia and Wayland are not best friends, can you reboot and login to an X11 session and see if there is any improvement?

You may also wish to consider purging and re-installing the Nvidia drivers just to see if it helps.
This web page seems comprehensive.
[https://linuxhint.com/clean-install-nvidia-drivers-ubuntu-22-04-lts/](https://linuxhint.com/clean-install-nvidia-drivers-ubuntu-22-04-lts/)

---

### Post by d3vestator on 2023-09-13
sorry i dont know what X11 is

---

### Post by tea for one on 2023-09-13
X11 or X or Xorg is the legacy display server.
It may be more suitable for Nvidia graphics.
Have a look at this [https://itsfoss.com/switch-xorg-wayland/](https://itsfoss.com/switch-xorg-wayland/)

---

### Post by d3vestator on 2023-09-13
This is the booting errors for xorg.[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292719&stc=1[/IMG]

---

### Post by tea for one on 2023-09-14
I don't know what the errors mean, however, it may be useful to see complete system info so that other users may spot something pertinent.
Details here [https://ubuntuforums.org/showthread.php?t=2475931](https://ubuntuforums.org/showthread.php?t=2475931)

By the way, I noticed from the boot-repair report in post no. 1 that you have Secure Boot enabled.
Did you install Nvidia drivers with Secure Boot enabled?

Even Microsoft mention that Secure Boot may need attention:-
> If you're running certain PC graphics cards, hardware, or operating systems such as Linux or previous version of Windows you may need to disable Secure Boot
More info [https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/disabling-secure-boot?view=windows-11](https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/disabling-secure-boot?view=windows-11)

---

### Post by d3vestator on 2023-09-14
It turns out that i dont have nivida driver on the Ubuntu OS, not sure if i should install them and if that would make a difference and i disable secure boot and nothing changed

---

### Post by d3vestator on 2023-09-14
for the system-info i downloaded it with ppa, is that it? 

not sure what to do next, pastebinit is also empty,

---

### Post by tea for one on 2023-09-15
> **d3vestator said:**
> It turns out that i dont have nivida driver on the Ubuntu OS, not sure if i should install them and if that would make a difference and i disable secure boot and nothing changed
If you can still occasionally boot into your installed system, no reason not to try:-
Disable Secure Boot (and any other security options in your UEFI firmware i.e. TPM, Platform Trust Technology or similar)
Install the Nvidia drivers via Software & Updates > Additional Drivers
Reboot into a xorg session.

Any good?

---

### Post by d3vestator on 2023-09-15
im not sure if ubuntu is recongizing my Nividia gpu, when i use the lshw command it says its there, but when i use ubuntu-device drivers, it doesnt show anything as well as in additional drivers.
Do i install them from the nividia site?

---

### Post by tea for one on 2023-09-16
> **d3vestator said:**
> im not sure if ubuntu is recongizing my Nividia gpu, when i use the lshw command it says its there, but when i use ubuntu-device drivers, it doesnt show anything as well as in additional drivers.
Do i install them from the nividia site?
As you can log in to your Ubuntu installation, it looks like this is not a boot-repair issue but an Nvidia driver issue.
According to the boot-repair report, your GPU is GeForce RTX 3050 Mobile and it may be better to start a new thread asking for advice about installing the correct driver.
I've never owned an Nvidia GPU therefore, regrettably, I cannot help you with exact advice.

---

### Post by #&amp;thj^% on 2023-09-16
> **tea for one said:**
> As you can log in to your Ubuntu installation, it looks like this is not a boot-repair issue but an Nvidia driver issue.
According to the boot-repair report, your GPU is GeForce RTX 3050 Mobile and it may be better to start a new thread asking for advice about installing the correct driver.
I've never owned an Nvidia GPU therefore, regrettably, I cannot help you with exact advice.

+1 for open a new thread
.```
lspci | grep NVIDIA
01:00.0 VGA compatible controller: NVIDIA Corporation TU117M [GeForce GTX 1650 Ti Mobile] (rev a1)
01:00.1 Audio device: NVIDIA Corporation Device 10fa (rev a1)

```

---

### Post by MAFoElffen on 2023-09-18
If you added the Ubuntu Forums 'system-info' PPA, then to install the script as an application, and run it, do:
```

sudo apt install system-info
system-info

```
This thread would have been at last 10 posts shorter if you had ran that report and posted the URL of where it was uploaded to. It would have save you so much work from running individual commands, and posting the output of them.

My suggestion, when you do start your new thread, is to post the URL of that report, so members can see what you have, the state of it currently, and so they can look at that to determine an educated solution geared towards the hardware you have.

That is why I wrote that script, and gave it to the Forum. To help both the Members of this Forum, and the Users coming here for help.

---

