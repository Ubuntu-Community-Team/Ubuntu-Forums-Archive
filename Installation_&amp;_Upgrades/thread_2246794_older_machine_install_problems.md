---
title: "older machine install problems"
date: 2014-10-03
forum: Installation &amp; Upgrades
---

### Post by simrick on 2014-10-03
Hi. I am a Windows Wiz, but a Linux Newbie, so please bear with me. Any help needs to be "Linux for Dummies" format or I will not get it.

I have an old Dell Latitude D600 laptop, 1.4GHz Pentium M, 64Kb Pri Mem Cache, 1024 secondary mem cache, not hyper-threaded, 80 Gb HDD (71Gb free), 512Mb RAM, with Samsung CDRW/DVD optical drive & 2 USB ports. HDD SMART=healthy, Mobility Radeon 9000 display adapter, SigmaTel C-Major Audio, Broadcom 570x Gb integrated controller & Intel Pro Wrls 2200BG, Conexant D480 MDC v.92 modem (yeah, it's that old!). The BIOS does **NOT **have an option for booting to a USB drive.

The laptop came with XP Pro, which has gone end-of-life, and I want to dual-boot with Ubuntu as the primary OS. I will try to remember what I have done so far:

Tried to install Ubuntu v14 ISO, but computer would not boot to a DVD - have to use a CD, so I reverted to my old Ubuntu v9, which is still small enough to fit on a CD.

I went through the install, selected "transfer documents & settings from [user]" and completed the install, booting up to the desktop. I connected the wireless to my SSID successfully. At this point, I wanted to update to a supported version. I tried to open Firefox and the computer locked up. I had to use the power button to shut it down.  I rebooted and opened the software updater, and the computer froze again. I rebooted again. Opened "files" - window opened, but as soon as I tried to resize it, it froze again.

Now I took the Ubuntu v14 DVD and tried to boot the computer from it - and it did! Started the install and got an error about the chip being non-PAE. So I went looking for alternatives. I tried Xubuntu Alt Install; no joy. Then I went to "mini.iso"; got into the install part way, then the screen went blank and nothing.

I seem to recall an error about needing non-free firmware "tigon/tg3_tso.bin" at some point during the other installations, but can't remember the specifics, only that I skipped through that because I just don't know what to do.

So here's where I stand: Grub shows the following options:

[LIST=1]
[*]Ubuntu, Linux 2.6.31-14-generic 
[*]Ubuntu, Linux 2.6.31-14-generic (recovery mode) 
[*]Memory Test (Memtest86+) 
[*]Memory Test (memtest86+, serial console 115200) 
[*]Microsoft Windows XP Professional (on /dev/sda1) 
[/LIST]

It will boot into Ubuntu v9.10, I can login to my user, I have wireless and sound. But anything I try to do results in a locked-up computer. I can not even open Terminal.

Any and all help is appreciated. Remember, Linux for Dummies here!

---

### Post by grahammechanical on 2014-10-03
This may help you with regard to the Pentium M and the non-pae problem.

[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

As regards Ubuntu 9:10 not only is it way out of End of Life but I wonder who among us would remember how to do things in that user interface. The best advice that I can give is to choose the second Grub boot option - Ubuntu, Linux 2.6.31-14-generic (recovery mode) and at the recovery menu select resume. That should load to a desktop using a VGA mode (if I remember correctly - things have moved on a bit since 2009).

You will have trouble updating and installing software including upgrading to newer versions and you have a long way to go to get the 12.04. I am not sure that your graphic adapter has enough of its own memory to cope with Unity on 14.04. Even on 12.04 you may need to use Unity 2D. If you get to 10.04 you can leap to 12.04. But you will need to read this,

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Regards

---

### Post by zvacet on 2014-10-03
You have old comp with low ram. If you want to install Ubuntu, try [Lubuntu]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO"). That way you will able to install and run Ubuntu. ;)

---

### Post by sudodus on 2014-10-03
> **zvacet said:**
> You have old comp with low ram. If you want to install Ubuntu, try [Lubuntu]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO"). That way you will able to install and run Ubuntu. ;)

+1

Try ***Lubuntu 14.04.1 LTS***. Use the boot option **forcepae** according to this link

[https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M)

1. Try Lubuntu 14.04.1 LTS, PC 32-bit. Download it from

[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)


If you have problems with some driver (because of the old age of the computer), you may have better luck with ***LXLE*** based on Ubuntu 12.04 LTS.

2. try LXLE from [http://lxle.net/download/](http://lxle.net/download/)

LXLE 32-bit revisited (current 12.04.4) via torrent

or normal download of the isohybrid version from

[http://phillw.net/isos/linux-tools/hybrid-isos/](http://phillw.net/isos/linux-tools/hybrid-isos/)


If these distros are too big or modern to run, try Wary Puppy for old hardware
[URL="http://www.puppylinux.com/download/"]
Puppy Linux download page[/URL]

---

### Post by simrick on 2014-10-03
Thank you everyone for your suggestions. I have some reading to do, so I can see! Meanwhile, I am wondering - how do I uninstall what I've done, should I need to start over? Thanks.

---

### Post by sudodus on 2014-10-04
No problem: You reuse the partitions by selecting them for the new system and letting the installer format them during your next attempt to install linux.

But please try some different linux 'distros, versions, flavours, re-spins' ***live*** before starting to install.
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]

---

### Post by Dennis N on 2014-10-04
FYI: Next time you install, you CAN (most likely) use a USB:

There is a small program called Plop Boot Manager that is burned onto CD and after booting it with your CD drive, allows you to then boot from a USB flash drive. So, you are not really limited by the size of the install media if you use Plop. Testimonial: I have used it twice to boot installers on USB flash drives on an old Dell Desktop that would not normally do so and successfully installed. 

Google for where to download if you are interested.

---

### Post by simrick on 2014-10-17
Okay, so I've tried all these without success, and moved on to Wary Puppy. That auto-runs live, and then I installed it on the largest partition from the original linux install(s). It seemed to be installed correctly, but GRUB was still showing Ubuntu/WinXP, and the Ubuntu selection would not boot to Puppy. (XP does still boot from its selection.)

So I installed GAG boot manager. In setting up the selections in GAG, it saw a total of 3 partitions, and I wasn't sure which Puppy was on, so I added them all. Well, none of them work except XP. 

I am now in XP, deleting/merging and formatting these two partitions and I guess I will start from scratch.

Any additional help would be appreciated. Getting pretty frustrated now...

Update: Installed Wary Puppy, went into GAG and set the selection. Tried to boot Puppy and got an error that it's missing or something like that. I had set the boot flag on that partition, and formatted it to ext3, so I'm not sure what to do now.

---

### Post by mörgæs on 2014-10-17
Does this mean that you now have only XP left on the hard disk and empty space where the Linux partitions used to be?

---

### Post by simrick on 2014-10-17
correct

Am trying this now. Will report how it goes.
[https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M)
I didn't want to do the force PAE because of all the warnings, but maybe it is my only choice...we will see.

Update:
An installation step failed: "select and install software"
Tried it several times and it continued to fail. So I went to the next step - "install Grub boot loader" - Failed as well.

Got a message "...need to boot manually with the /vmlinuz kernel on partition /dev/sda6 and root = /dev/sda6 forcepae passed as a kernel argument"

No idea what that means or how to accomplish that.
I went into GAG and found 3 partitions in addition to the XP partition now, so I set them all up and tried them all, and none of them will boot.

---

### Post by mörgæs on 2014-10-18
Just ignore the warnings about Forcepae. It's a great little option used by many people here in Ubuntuforums (and rest of the world, I assume).

I have never heard of GAG. Why do you need it, isn't Grub working alone?

---

### Post by simrick on 2014-10-18
Grub worked only after the first try of installing Ubuntu v9 (which would not function properly on the computer). After that, it never worked, so I installed GAG to try and get the different installations to boot, as I installed them on the computer.

I have since uninstalled GAG and am trying Lubuntu again with the "forcepae" command during install.

Update:
It appears I was successful installing this time. Grub is also working. However, it has leftover selections from the original Ubuntu which did not function on this laptop. Any idea how to edit the menu to get rid of them?

In the meantime, I will make sure Firefox is working, install Flash, and connect the wireless, etc.

I would like to put either OpenOffice or Libre Office on here - do you know if this OS will handle them? I need something compatible with *.docx and *.xlsx.
Thanks.

Update #2:
I opened a terminal window and typed: sudo apt-get install libreoffice
Libre Office installed and appears to be working.

So now I just need to know how to get rid of the unnecessary selections in Grub and I should be good to go.
Thanks.

---

### Post by mörgæs on 2014-10-18
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by simrick on 2014-10-20
> **mörgæs said:**
> [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Thanks for the link. I am a bit overwhelmed with this. After all I've gone through to get this working, I don't want to mess it up and have to start all over again. Maybe I'll just leave it as it is.

---

### Post by mörgæs on 2014-10-20
There's nothing to be overwhelmed about. Boot-Repair simply finds out which operative systems are installed, overwrites the old GRUB and installs a new one which fits the operative systems. You could do it all by hand, Boot-Repair just does it all automatically.

---

