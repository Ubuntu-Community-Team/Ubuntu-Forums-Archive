---
title: "Dual Booting WinXP/WIN 7 from Thumb Drive?"
date: 2014-03-07
forum: Installation &amp; Upgrades
---

### Post by tom62 on 2014-03-07
Hello, I'm new here. I've done anything with any flavor of Linux. I have a couple of old machines that work like garbage, one an XP, one a Win 7. On the Win 7 laptop, I wanted to try and dual install to try out Ubuntu, but apparently you need to burn a disc. I can do that, but I don't have any handy - but I do have a thumb drive. I thought you could do that too, but I am having a hard time digging through stuff and getting a good answer. 

This is my daughter's laptop for school, and all she uses it for is surfing the net and writing documents. This laptop is Win7 Premium, with 3GB ram, intel core i3-2310 CPU @ 2.1GHz. 

What would be the best way to go about testing it out?

The XP one has an intel Xeon CPU 5140 @ 2.33 GHz with 2GB of ram. I'm not ready to do that one yet, it's a desktop, but I will want to try it there, too. 

Thanks for any help.

---

### Post by oldfred on 2014-03-07
Your flash drive will be totally erased, so if you have any data be sure to save that first.

 Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Most Windows 7 systems use all 4 primary partitions.
      
 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

---

### Post by monkeybrain20122 on 2014-03-07
If these are old machines and Windows works like garbage why not just get rid of it? Windows XP will not be supported any more after April so I wouldn't even bother with a dual boot if I were you.

---

### Post by tom62 on 2014-03-07
Hrm, maybe the dual boot is more trouble than it's worth, a lot of this seems confusing. I wanted to try it on the Win7 laptop first, but since it doesn't work right anway, maybe I should just wipe it and install Unbuntu over it. In which case, do I need to worry about the 4 partitions?

As for the XP box, the issue is all my files on are there, it's the primary computer hooked up to the internet service, etc. So I can't mess with it until I am sure.

---

### Post by Vladlenin5000 on 2014-03-08
> **tom62 said:**
> Hrm, maybe the dual boot is more trouble than it's worth, a lot of this seems confusing. I wanted to try it on the Win7 laptop first, but since it doesn't work right anway, maybe I should just wipe it and install Unbuntu over it. In which case, do I need to worry about the 4 partitions?

No, you don't need to worry about the 4 partition. The Ubuntu installer can do it for you if you select the default option which is use the entire disk. 

> As for the XP box, the issue is all my files on are there, it's the primary computer hooked up to the internet service, etc. So I can't mess with it until I am sure.

Indeed you shouldn't mess with it until you're sure about it and know what to do. However, you shouldn't either rely in a single computer - with a soon-to-be-unsupported OS, no less - for your files. There are plenty of free cloud solutions you can use to backup your files and even sync between PCs. I would strongly advise using one or more ASAP or, at least, do a backup to another drive.

---

### Post by mörgæs on 2014-03-08
Suggestion: 

When the former Win 7 computer is running Buntu 13.10 (alone or in a double boot) you install an FTP server. 
From XP you upload everything of value to the server. Look for strange / hidden Windows files and leave them behind, as they only steal hard disk space.
Now you check that Buntu applications are able to handle all your files. Complicated Excel sheets might be a problem, for example.
When you are happy with the results you install Buntu on the desktop. 
Download all your stuff to the new Buntu on the desktop.
Now you have two working computers and a backup.

---

### Post by tom62 on 2014-03-08
As far as file backup, that's not an issue. I have CrashPlan constantly backing up my data. And really all that stuff will go on the new Mac. Right now, for the laptop, as long as she can surf the net and write documents and store photos - basic stuff - she is good to go. One of the big issues with the laptop is it always fails to connect to the network. I'm hoping Ubuntu won't have that issue.

Do I go with the latest stable version of 12 or should I go with 13?

---

### Post by oldfred on 2014-03-08
Either should work for a previous Windows 7 system.

But how old is XP and what are its specs.
How much RAM and what video.
Full Ubuntu needs more RAM and decent video card chip and only the last produced XP may work if upgraded along the way. If not full Ubuntu then Xubuntu or Lubuntu may be better.

---

### Post by tom62 on 2014-03-08
Here's the XP machine:

WinXP Professional version 2002
SP3
Intel Xeon 5140 @ 2.33Ghz
2GB RAM
NVIDIA Quadro FX 3450/4000 SDI - 256MB RAM

---

### Post by oldfred on 2014-03-08
I do run Ubuntu, but not Unity on my 2006 XP laptop with 1.5GB of RAM. I use fallback/flash back which is lighter light and very similar to the old default classic gui for Ubuntu prior to Unity.

My desktop also is from 2006 but has 4GB of RAM and a newer nVidia card. With nVidia you have to use nomodeset to boot live installer and after install until you install correct nVidia driver from repository. Not sure which version driver is correct for your card.

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

    
Only install the one correct nVidia driver from repository. Some use ppas, or direct from nVidia and have issues but that may only be required if you have a very new card and need the newest features on that card. Attempting to install more than one version over another creates huge issues. Total purge always required. But if from repository it is automatic and relatively easy.

       nVidia versions:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
Legacy drivers.
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

---

### Post by tom62 on 2014-03-09
Ok, I decided to just go for it with the Win7 machine. I made a USB installation stick following the directions I found on the site, and the install went fine and I am up and running... however. 

The laptop was not connecting to the wireless before when it was Win7. This was one of the last straws for me deciding to switch. So I didn't have an internet connection during install. I figured (hoped) Ubuntu would do a better job. I booted up, and went into network settings. I added the SSID and the password, and set the network security. I don't know what BSSID would be, nor MTU. Usually on a PC, adding the SSID/Network password gets you in. I saved the info... but nothing. 

I can find the mac address on my router, but I don't think that's the issue. I'm a bit lost on what to do next.

---

### Post by tom62 on 2014-03-09
I should have also mentioned that all the other laptops in the house (mac and pc) are having no problem seeing and connecting to the network.

---

### Post by oldfred on 2014-03-09
Are you using Wired Ethernet during install?
It then may offer to download diferent wireless driver as installer does not have all wireless drivers but has most wired drivers.
If wireless issue start a new thread with details of wireless device and title related to that issue. 
Those that know wireless issue will want all this info.
lspci > ~/abs-network.txt
lsusb >> ~/abs-network.txt
ifconfig >> ~/abs-network.txt
iwconfig >> ~/abs-network.txt
Attach (via the paperclip in advanced edit menu) the abs-network.txt file which will be in your home folder.

---

### Post by tom62 on 2014-03-09
I did not used a wired cable when I installed. 

I'm sorry, I don't get where that text file should be. There's nothing in the home folder that I can see.

---

### Post by oldfred on 2014-03-09
If you run each of those command it will create the file. The first creates it with single > and the others append data with the >> command.

---

### Post by tom62 on 2014-03-09
I assume that's command line stuff? No idea how to do that... sorry I've never used any form of Linux before.

EDIT: Looked it up, I think I did it right (I copied what you had exactly) I will post it in the new thread. Thanks.

---

