---
title: "Wubi Ubuntu installation problems"
date: 2011-01-16
forum: Installation &amp; Upgrades
---

### Post by XJLanzaro on 2011-01-16
I'm trying to install Ubuntu on Windows XP as a dual boot using Wubi, but whenever I try to install it I get an error message that says:

An error occurred:

Permission denied

For more information, please see the log file: c:\docume-1\lanzaro\locals-1\temp\wubi-10.04.1-rev190.log

Does anyone know what this means and if I can fix it? Any help will be appreciated.

---

### Post by bcbc on 2011-01-16
What are you trying to install? Netbook-edition, Xubuntu or plain old Ubuntu. How are you trying to install it, through the wubi.exe alone? or do you have a CD you burned?

---

### Post by lisati on 2011-01-16
Did the log file provide any clues?

On XP, click on Start->Run and type in: ```
%temp%
```
Look for a file named wubi-10.04.1-rev190.log and open it up in any text editor e.g. Wordpad or Notepad.

---

### Post by XJLanzaro on 2011-01-17
I am trying to install the netbook version through wubi.exe alone, and every time I try to I get the same error message. Is there any way I can fix it?

---

### Post by bcbc on 2011-01-17
> **XJLanzaro said:**
> I am trying to install the netbook version through wubi.exe alone, and every time I try to I get the same error message. Is there any way I can fix it?

You can't install the netbook-edition from the wubi.exe on [http://www.ubuntu.com/desktop/get-ubuntu/windows-installer]("http://www.ubuntu.com/desktop/get-ubuntu/windows-installer")

There is a bug - that wubi.exe is at 10.04.1 and there is no release of 10.04.1 in Netbook-edition. So it keeps downloading the 10.04 version and then rejecting it (wubi.exe will only install something on the same release).

So... if you want the 10.04 version of Netbook (which personally I think is better than 10.10) get it from here: [http://people.canonical.com/~evand/wubi/lucid/wubi-r189.exe]("http://people.canonical.com/~evand/wubi/lucid/wubi-r189.exe")

Or download the 10.04 .iso of Netbook edition and extract it from the .iso.

Alternatively if you want 10.10 Netbook edition, use wubi.exe from here [http://releases.ubuntu.com/maverick/](http://releases.ubuntu.com/maverick/)

PS to speed up the install you can download the .iso yourself using bittorrent and place it in the same folder as wubi.exe before running.

PPS wubi installs have problems with grub updates. Do not update packages grub-pc and grub-common. See [here]("http://ubuntuforums.org/showthread.php?t=1639198") for more info.

---

### Post by leckers on 2011-01-17
I have another problem with using wubi and Ubuntu 10.10 Desktop AMD64 to install on Win7 64bit. WIN7 is set up up a BIOS RAID stripe set-up. Ubuntu is installed in 380GB of free space in this partition.
I have the wubi.exe for Ubuntu 10.10 and the initial install seems to run OK right through to re-boot. Then, on doing re-boot I get the Grub screen with 2 choices: 1) Win7, and 2) Ubuntu.
Select Ubuntu, and loading seems to be OK right through to almost getting initial desktop screen.... BUT, I then get Error on init boot, with the message:
No root file system defined. Please correct from partitioning menu.
The screen then locks up, and I have to shut down.
I have tried uninstalling/re-installing several times all with same result. Any ideas please????

---

### Post by leckers on 2011-01-17
I have another problem with using wubi and Ubuntu 10.10 Desktop AMD64 to install on Win7 64bit. WIN7 is set up up a BIOS RAID stripe set-up. Ubuntu is installed in 380GB of free space in this partition.
I have the wubi.exe for Ubuntu 10.10 and the initial install seems to run OK right through to re-boot. Then, on doing re-boot I get the Grub screen with 2 choices: 1) Win7, and 2) Ubuntu.
Select Ubuntu, and loading seems to be OK right through to almost getting initial desktop screen.... BUT, I then get Error on init boot, with the message:
No root file system defined. Please correct from partitioning menu.
The screen then locks up, and I have to shut down.
I have tried uninstalling/re-installing several times all with same result. Any ideas please????

---

### Post by leckers on 2011-01-17
I have another problem with using wubi and Ubuntu 10.10 Desktop AMD64 to install on Win7 64bit. WIN7 is set up up a BIOS RAID stripe set-up. Ubuntu is installed in 380GB of free space in this partition.
I have the wubi.exe for Ubuntu 10.10 and the initial install seems to run OK right through to re-boot. Then, on doing re-boot I get the Grub screen with 2 choices: 1) Win7, and 2) Ubuntu.
Select Ubuntu, and loading seems to be OK right through to almost getting initial desktop screen.... BUT, I then get Error on init boot, with the message:
No root file system defined. Please correct from partitioning menu.
The screen then locks up, and I have to shut down.
I have tried uninstalling/re-installing several times all with same result. Any ideas please????

---

### Post by leckers on 2011-01-17
I have another problem with using wubi and Ubuntu 10.10 Desktop AMD64 to install on Win7 64bit. WIN7 is set up up a BIOS RAID stripe set-up. Ubuntu is installed in 380GB of free space in this partition.
I have the wubi.exe for Ubuntu 10.10 and the initial install seems to run OK right through to re-boot. Then, on doing re-boot I get the Grub screen with 2 choices: 1) Win7, and 2) Ubuntu.
Select Ubuntu, and loading seems to be OK right through to almost getting initial desktop screen.... BUT, I then get Error on init boot, with the message:
No root file system defined. Please correct from partitioning menu.
The screen then locks up, and I have to shut down.
I have tried uninstalling/re-installing several times all with same result. Any ideas please????

---

### Post by XJLanzaro on 2011-01-18
Thank's for the help bcbc, I used the link you provided and successfully installed Ubuntu.

---

### Post by Rubi1200 on 2011-01-19
> **leckers said:**
> I have another problem with using wubi and Ubuntu 10.10 Desktop AMD64 to install on Win7 64bit. WIN7 is set up up a BIOS RAID stripe set-up. Ubuntu is installed in 380GB of free space in this partition.
I have the wubi.exe for Ubuntu 10.10 and the initial install seems to run OK right through to re-boot. Then, on doing re-boot I get the Grub screen with 2 choices: 1) Win7, and 2) Ubuntu.
Select Ubuntu, and loading seems to be OK right through to almost getting initial desktop screen.... BUT, I then get Error on init boot, with the message:
No root file system defined. Please correct from partitioning menu.
The screen then locks up, and I have to shut down.
I have tried uninstalling/re-installing several times all with same result. Any ideas please????
RAID arrays can be complicated at the best of times, but with a Wubi install we need to see what you have done and the current state of your setup.

Here is what I suggest:

Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

