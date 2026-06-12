---
title: "doing install, installation type window"
date: 2020-01-17
forum: Installation &amp; Upgrades
---

### Post by mawil10132 on 2020-01-17
Final Update >>>   After two days of attempts to install, went back to USB with U18 on it, I'm happy to say that ubuntu is now installed on my dell insprion 5575 laptop, with no idea what has been stopping the installs.


I'm doing install and just started. Now at Installation Type window.  I want to retain half of drive for Windows 10. What option should I select. It seems the default is; Erase Ubuntu 18.10 and reinstall. This is first install so what is there of Ubuntu to delete?

Update:. So I download ef Ubuntu 19, installing I think,  it jumped right to language selection, then select specifically English, nothing yet about drives or partition, but I selected full install, I believe install with win removed, figured it may be easier to load Ubuntu then adjust hd then install win 10 later, any way going sloe. See what happens..

Update Day Two:  Used two different download DVD's with U19 and a USB with U18 on it have all failed to install completely.  What has been done is the HD has been erased of WIN10 (Newer Dell Inspirion 5575) verified when U18 was able to load and run from DVD.  The U19 DVD after 3 tries gave same message about what I think said there was no info on DVD in order to do insatll and twice the error details were sent back to ubuntu. Also the DVDs were verified twice!  My current situation is WIN10 is gone, ubuntu was set up HD, no version of ubuntu of U18 nor U19 are able to install on this laptop, but can run ubuntu off DVD.   There are posts below which show HD info.  Also there is an igmur link showing hd before being taken over by ubuntu.

---

### Post by CelticWarrior on 2020-01-17
Better shrink the Windows partition using Windows tools before installing Ubuntu. Also disable Fast Startup in Windows.

IN UEFI disable Legacy/CSM to assure you're booting (and installing) Ubuntu in UEFI mode. Most likely you were booting in Legacy mode in your attempt.

---

### Post by oldfred on 2020-01-17
If you want to keep partitions, always best to only use Something Else.
But then you have to create your own / (root) partition as ext4. That is all that is really required if a new user.
But you can then also create smaller / and larger /home if desired. 
You can create those partitions in advance with gparted, but still have to use Something Else to tell installer which partition is / and if any others what they are.

UEFI install  Windows 10
[https://askubuntu.com/questions/221835/installing-ubuntu-alongside-a-pre-installed-windows-with-uefi](https://askubuntu.com/questions/221835/installing-ubuntu-alongside-a-pre-installed-windows-with-uefi)
[https://askubuntu.com/questions/324132/partition-concerns-installing-ubuntu-12-04-on-new-laptop/324216#324216](https://askubuntu.com/questions/324132/partition-concerns-installing-ubuntu-12-04-on-new-laptop/324216#324216)
[https://askubuntu.com/questions/6328/how-do-i-install-ubuntu](https://askubuntu.com/questions/6328/how-do-i-install-ubuntu)
UEFI install,windows 8 with Something Else screen shots
How to Install Ubuntu 18.04 Alongside With Windows - screenshots Something Else
[https://www.tecmint.com/install-ubuntu-alongside-with-windows/](https://www.tecmint.com/install-ubuntu-alongside-with-windows/)
How To Install Ubuntu Linux Alongside Windows 10 (UEFI)
[http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html](http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html)

---

### Post by mawil10132 on 2020-01-18
> **CelticWarrior said:**
> Better shrink the Windows partition using Windows tools before installing Ubuntu. Also disable Fast Startup in Windows.

IN UEFI disable Legacy/CSM to assure you're booting (and installing) Ubuntu in UEFI mode. Most likely you were booting in Legacy mode in your attempt.


I believe I've properly Shrunk C: and here is a picture of chart where I think Disk ) Partition 5 seems to be the freed up partition.  [https://imgur.com/dJTmG9l](https://imgur.com/dJTmG9l)

But have been unable to find a valid web site for Disabling Legacy.

---

### Post by mawil10132 on 2020-01-18
> **oldfred said:**
> If you want to keep partitions, always best to only use Something Else.
But then you have to create your own / (root) partition as ext4. That is all that is really required if a new user.
But you can then also create smaller / and larger /home if desired. 
You can create those partitions in advance with gparted, but still have to use Something Else to tell installer which partition is / and if any others what they are.

UEFI install  Windows 10
[https://askubuntu.com/questions/221835/installing-ubuntu-alongside-a-pre-installed-windows-with-uefi ]("https://askubuntu.com/questions/221835/installing-ubuntu-alongside-a-pre-installed-windows-with-uefi")
[https://askubuntu.com/questions/324132/partition-concerns-installing-ubuntu-12-04-on-new-laptop/324216#324216](https://askubuntu.com/questions/324132/partition-concerns-installing-ubuntu-12-04-on-new-laptop/324216#324216)
[https://askubuntu.com/questions/6328/how-do-i-install-ubuntu](https://askubuntu.com/questions/6328/how-do-i-install-ubuntu)
UEFI install,windows 8 with Something Else screen shots
How to Install Ubuntu 18.04 Alongside With Windows - screenshots Something Else
[https://www.tecmint.com/install-ubuntu-alongside-with-windows/](https://www.tecmint.com/install-ubuntu-alongside-with-windows/)
How To Install Ubuntu Linux Alongside Windows 10 (UEFI)
[http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html](http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html)


On the first link, questions/221835, Here is my problem with install, The following does not appear during install instructions >> "Select Install Ubuntu (Install Ubuntu alongside Windows)"  WHich is why I'm having such a difficult time installing, years ago I saw that same selection but it isn't available now.

---

### Post by jeremy31 on 2020-01-18
I think you may not be booting in UEFI mode.  Do you see a grub menu when booting Ubuntu ISO?

---

### Post by mawil10132 on 2020-01-18
> **jeremy31 said:**
> I think you may not be booting in UEFI mode.  Do you see a grub menu when booting Ubuntu ISO?

The procedure I used to get USB to load was rebooting and then tapping F12 until a special window appeared which allowed my to use USB to boot.
   

I'm trying to figure out the Legacy and UEFI stuff but each time I find a web page, it's always for winodws 8 or if for win 10 the guide instructions and pictures of screens that are supposed to appear, well nothing lines up.

This is the screen I see; [https://tutorials.ubuntu.com/es6-bundled/src/codelabs/tutorial-install-ubuntu-desktop/img/8d4c3c33957b4ef.png](https://tutorials.ubuntu.com/es6-bundled/src/codelabs/tutorial-install-ubuntu-desktop/img/8d4c3c33957b4ef.png)

---

### Post by oldfred on 2020-01-18
You may be pressing too many keys as that screen is well beyond the boot screen.

Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by mawil10132 on 2020-01-18
> **oldfred said:**
> You may be pressing too many keys as that screen is well beyond the boot screen.

Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)


That's as far as I performed install, because I didn't see what I saw a few years ago, which is a selection to dual install.  After that and more reading C drive was reduced thereby creating a new partition as can be seen in a reply to another helper.  Partition;  [https://imgur.com/dJTmG9l](https://imgur.com/dJTmG9l)

---

### Post by jeremy31 on 2020-01-18
In Windows press the Windows key + r to get a command prompt window, type msinfo32.exe and see what it says for BIOS mode, then boot Ubuntu ISO and see what result is for
```
mokutil --sb-state
```

---

### Post by mawil10132 on 2020-01-18
> **jeremy31 said:**
> In Windows press the Windows key + r to get a command prompt window, type msinfo32.exe and see what it says for BIOS mode, then boot Ubuntu ISO and see what result is for
```
mokutil --sb-state
```

here's an update, so far the C: in HD has been shrunk, just before getting this message the fast Boot was disable, Now to your question Bios EUFI, now, after I disabled fast boot, I can no longer boot USB.   Here's what I'm doing, Restart, tap F12 to get to boot options, it's defaulted to the USB so I assume system sees the USB,  but unlike earlier the USB is not able to run ubuntu, a message says basically there is nothing there, I guess nothing visible on USB, but I open File Explorer and ubuntu is still on USB.  Soo it seems disabling fast boot has set install back by now being unable to see on USB??   Oh, and I also simply let laptop reboot normally with USB in but it went to Windows as it has all along.

---

### Post by oldfred on 2020-01-18
What model Dell?
Most Dell need UEFI update, and if SSD, firmware update for SSD.
You need drives changed from RAID/Intel RST to AHCI.
And best to have UEFI Secure Boot off. You may then still need to have allow USB boot and/or full USB support in UEFI settings.
Secure Boot may not be called Secure Boot, many call it "Windows" and "Other". But fine print says use "Other" for Windows 7. 
When Secure Boot is off, you should have two boot options in UEFI boot menu for flash drive.
My Asus Motherboard shows [noparse]UEFI:PMAP[/noparse] or PMAP which is a BIOS emulation boot. Many systems use name or label of flash drive where mine has PMAP.

---

### Post by mawil10132 on 2020-01-19
Next day report, Decided to go with full install. Clean off HD of WIN10, make 100% Ubuntu using 19 as not much success with 18.  Also switched to DVD instead of USB as USB keep showing nothing on it which was false.   I was able to go through U19 install process, making it through all basic set up, user name, passwords, wifi connection, telling it to wipe HD and install fresh U19, when it looked like it was finally going to start the process there was an error message again stating nothing on DVD, even though verified DVD twice. After 3 more attempts to install U!19 and things getting worse by not even being able to bring up the run off DVD or if it did open U19 the screen froze.  So I tried the U18 DVD and again it wiped drive (No WIN ISO on drive) wouldn't install, but the run off DVD is working and with the persistent icon on screen asking if I want to install U18?

---

### Post by mawil10132 on 2020-01-19
Next day report; decided to go with full install. Clean off HD of WIN10, make 100% Ubuntu using U19 as not much sucess with U18. Also switched to DVD instead of USB as USB keep showing nothing on it which was false. I was able to go through U19 install process, making it through all basic set up, user name, passwords, wifi connection, telling it to wipe HD and install fresh U19, when it looked like it was finally going to start the process, there was an error message again stating nothing on DVD, even though verified twice. After 3 more attempts to install U19 and things getting worse by not even being able to bring up the run off DVD, or if it did open U19 the screen froze. So I tried the U18 DVD and again it wiped drive (No WIN10 ISO on drive) wouldn't install, but run off DVD is working and with the persistant icon on screen asking if I want to install U18, same as when I was attempting U19 install.  I used gparted and it shows a reformated HD;;; Partition dev/sda1/Name EFI System Partition/File System fat32/ Size 512.00MiB/Used 1.04MiB/Unused 510.96MiB/ Flags boot,esp, and Partition /dev/sda2/ Name ext4/ Size 931.01 GiB/ Used 21.10Gib/ Unused 909.91GiB/Flag has nothing

---

### Post by mawil10132 on 2020-01-19
> **jeremy31 said:**
> In Windows press the Windows key + r to get a command prompt window, type msinfo32.exe and see what it says for BIOS mode, then boot Ubuntu ISO and see what result is for
```
mokutil --sb-state
```

Sorry I thought I replied to you.  It looks like BIOS is set for both Legacy and EUFI ?      I remember the last time I did install on this laptop I had to create an ?administrator? password to be able to change settings in Bios, boot options for sure.

---

