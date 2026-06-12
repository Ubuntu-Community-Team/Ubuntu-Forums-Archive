---
title: "Booting issues - [Boot-info link included]"
date: 2020-01-19
forum: Installation &amp; Upgrades
---

### Post by deveshkhilwani on 2020-01-19
Ubuntu 18 was installed about half a year ago and that is the only OS. I am suddenly unable to boot.
I ran boot-repair using Ubuntu live and the dialogue box displayed error during boot repair.
 The link for boot-info report is - [https://paste.ubuntu.com/p/vffJKTKCbw/](https://paste.ubuntu.com/p/vffJKTKCbw/)

---

### Post by oldfred on 2020-01-20
What boot error?
You have to press Escape key right after UEFI screen to get grub menu, since you only have one install. Were you able to boot recovery mode?
Or UEFI one time boot key to see UEFI boot options. Yours did not seem to have an ubuntu entry?

It says it re-installed grub without error.

Most flash drives are not standard partitions, either dd as hybrid DVD/flash or other configuration. So flash drive often generates various errors as partitions are not correct.

You did not have an ubuntu entry in UEFI before? How were you booting? Or did you unplug drive as then entries are often lost.
You also show an boot parameter in line 591 (grub) and boot -  nvme_core.default_ps_max_latency_us=5500  but do not show any NVMe drives.

What model Asus? Some do need boot parameters?
Have you updated UEFI to latest available for your system from Asus?

---

### Post by deveshkhilwani on 2020-01-20
The original error was that the following message appeared right after the logo screen - "Reboot and select proper Boot device or Insert Boot Media in selected Boot device and press a key".

I ran Ubuntu live and then boot-repair. After this, I tried to restart the PC. The screen blacked out and a message appeared instructing to restart after removing flash drive.
 I followed the prompt to see that the original problem persists. Also, I did not try booting into recovery mode.

Things to try - 1) Repeat the boot-repair procedure and restart without plugging out the flash drive.  2) Try Booting into recovery mode.  3) Check for UEFI updates and model number of PC.
I will update the thread if something works.
Thank you for your help.

---

### Post by CelticWarrior on 2020-01-20
If it was working before and now you a "Reboot and select proper Boot device or Insert Boot Media in selected Boot device and press a key" this probably means drive corruption and/or unwanted changes to UEFI boot order.

Now, Boot Repair has a very narrow usage/purpose and is not for this cases. 

First thing to check is the UEFI boot settings and re-adjust - re-select "Ubuntu" - if any change is detected. Also check drive health.

---

### Post by deveshkhilwani on 2020-01-21
The only boot option was "HL-DT-ST DVDRAM GUE1N".
 Now, after many reboots luckily few other boot options appeared (ubuntu, uefi, etc.). I don't know how it happened.

For now I was able to boot into Ubuntu. But, I am unsure whether the problem will resurface if I reboot.

---

### Post by deveshkhilwani on 2020-01-25
[IMG]https://drive.google.com/file/d/17-zNJv6_WLQWlDJmyMXXHhEeGdMBEmMa/view?usp=drivesdk[/IMG]
[This]("https://drive.google.com/file/d/17-zNJv6_WLQWlDJmyMXXHhEeGdMBEmMa/view?usp=drivesdk") text appears on a black screen after startup and also before shutting down.

---

### Post by oldfred on 2020-01-25
That looks like sda drive errors.
Have you run fsck on the ext4 partitions on sda?
And in Disks and icon in upper right corner checked Smart Status of drive?

To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1


All I know is if drive is said to be good or bad.
In Disks alias gnome-disks you can click on icon in upper right corner and see Smart Status
[https://www.smartmontools.org/wiki/Howto_ReadSmartctlReports_ATA_542.1](https://www.smartmontools.org/wiki/Howto_ReadSmartctlReports_ATA_542.1)

---

### Post by deveshkhilwani on 2020-08-20
Seems like the issue was a loose hard drive connection. It has been working fine now.
Thanks everyone for your help.

---

### Post by cg-152 on 2020-08-20
Thanks for posting your solution!

---

