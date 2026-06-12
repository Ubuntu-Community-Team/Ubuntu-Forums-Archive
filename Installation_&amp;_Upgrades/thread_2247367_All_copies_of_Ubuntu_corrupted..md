---
title: "All copies of Ubuntu corrupted."
date: 2014-10-07
forum: Installation &amp; Upgrades
---

### Post by Nate_Lowe on 2014-10-07
I have searched and found several threads with similar problems and none of the solutions worked. So here goes. I have:

[LIST=1]
[*]4x Corsair 120gb SSD in a RAID0+1 as my primary OS 
[*]2x 2TB HDD disconnected 
[*]Asus Rampage VI Extreme Mobo 
[*]This is not a dual-boot, straight Ubuntu 
[*]Opinions on my choices or setup can be kept to yourself as they can't be changed and discussing them is irrelevant here, there is a method to my madness. 
[/LIST]
 
I have taken the SSDs out of RAID and then back in to RAID to start with a clean slate, Windows is dead. Pristine medium to install on was my thought. Now for the BS.
I downloaded Ubuntu from the site booted it, used it for a day loved it. Decided to make it my daily driver. When I try to install from the same USB I got an error that I can&#8217;t even remember what it was(keep in mind I have put a lot of effort into figuring this out on my own for the last week and I can't remember every single step I took). However after the second time it did that it would boot to the &#8220;Use but don&#8217;t install/Install/OEM &#8220;something&#8221;/Check Disk&#8221; menu but no farther. I tried the Install, no joy. The check disk came back with 2 file errors.

 So here is where my due diligence kicks in, through hours of webcrawling I find that the problem is most likely corrupt files and proceed to learn about md5 checksums and how to use them (no explanation needed). Sure enough md5&#8217;s don&#8217;t match, so I go on an hours long adventure downloading new copies of Ubuntu 14.04.1 from every device in my house (it&#8217;s a lot), multiple times(torrent and direct download) with multiple USBs, and checking the md5&#8217;s. All no-go&#8217;s, I learn that the corrupt files could also be because of the way my network is setup (don&#8217;t care about fixing it, everything else on my network works besides getting an uncorrupted version of Ubuntu so please don&#8217;t address this issue.) So I get the brilliant idea and take my handy dandy smartphone and turn off Wi-Fi and use the mobile network on my phone to download the file. MD5&#8217;s match!!!!! All is right with the world (&#8230;and the Tech Gods chuckle). Does Ubuntu install, <expletive> no it doesn&#8217;t, from this point on all md5s match and yet installs fail. Now I get an error about casper/filesystem.squashfs or vmlinux.xxx which I then find out is still caused by corrupted files&#8230;so it&#8217;s not just my network? As a last resort I trucked my happy ass up to my university campus on a day when I have no classes, to use the computer lab there to make a brand new Ubuntu USB from a brand new downloaded .iso, downloaded from a brand new (to this situation) device, on a brand new(to this situation) network, setup by (I assume) professionals. NO-<EXPLETIVE DELETED>-ING JOY.
I have used multiple devices, on multiple networks, to download a file using multiple methods and every single one is corrupted. Please help, I&#8217;m in the middle of a semester and just need this to work.

---

### Post by oldfred on 2014-10-07
We have seen a variety of similar issues.

Sometimes it just is which USB port. A slower USB2 port may work. Or even some settings in UEFI/BIOS.
Sometimes it just is the flash drive or brand of flash drive.
Sometimes it just is which installer you use, a different one may work.

Default install instructions usually work.
 Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

      How to create a bootable Ubuntu USB Flash Drive - unetbootin
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)

            Usb installer from Windows - pendrive
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)
Rufus Create bootable USB drives the easy way  From Windows create Linux installer
[http://rufus.akeo.ie/](http://rufus.akeo.ie/)

            Pendrive also has page on booting ISOs
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

      Howto help USB boot drives - sudodus
A tool that helps boot some computers from [other] USB boot drives - Chainloader
[http://ubuntuforums.org/showthread.php?t=2196858](http://ubuntuforums.org/showthread.php?t=2196858)
Howto make USB boot drives 
[http://ubuntuforums.org/showthread.php?t=1958073](http://ubuntuforums.org/showthread.php?t=1958073)
pendrive speed tests USB2 & USB3 various brands - user sudodus
[http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085](http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085)
Includes links to speed tests and lists some that do not work well.
[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

I download the development version. But only download full ISO once and then use zsync to update to newer version. One advantage of zsync is that it also verifies that it is correct.

This was the one I used with trusty. You do have to have exactly the name of the ISO you are using and where it is on server.
zsync [http://cdimage.ubuntu.com/daily-live/current/trusty-desktop-amd64.iso.zsync](http://cdimage.ubuntu.com/daily-live/current/trusty-desktop-amd64.iso.zsync)
This was an older version from a different mirror server.
zsync [http://mirror.anl.gov/pub/ubuntu-iso/CDs-Ubuntu/precise/ubuntu-12.04-desktop-amd64.iso.zsync](http://mirror.anl.gov/pub/ubuntu-iso/CDs-Ubuntu/precise/ubuntu-12.04-desktop-amd64.iso.zsync)

Sorry it does not show full path like I use, as it is too long and forum seems to shorten long links. And if you click on them they may try to run, but if you do not have ISO in the path you run it from it should just error out.

---

### Post by Nate_Lowe on 2014-10-07
Installer makes no difference I have tried all of these and I have used far too large a variety to say "well it might just not like your equipment".  I have used 3 OSs (Win, Mac, Linux) and their associated USB making tools, I have used mobile, desktop, and laptop computers with more than 6 different major brands, and I have used a Kingston Data Traveler and a Corsair Voyager GT along with any USB I have found lying around the house (ended up with 5 of those San Disk Cruzers none of which work). I know it's not the UEFI because I boot from USB all the time. I'm at my wits end, I refuse to return to Windows.

---

### Post by andy102 on 2014-10-07
I had that issue for some time, slowed down the burn rate, fixed it. Bad CDROM will drive you knutz too.

---

### Post by Nate_Lowe on 2014-10-07
> **andy102 said:**
> I had that issue for some time, slowed down the burn rate, fixed it. Bad CDROM will drive you knutz too.

Burn rate? For USB? How do you control that? Learn something new everyday.

---

### Post by oldfred on 2014-10-07
I have a new Asus AR and had to change a lot of settings in UEFI.

 Asus Motherboard Change UEFI from Windows (secure boot only) to other OS
[http://ubuntuforums.org/showthread.php?t=2245911](http://ubuntuforums.org/showthread.php?t=2245911)
Minor problems with using an ASUS Z97-A Motherboard
[http://askubuntu.com/questions/503168/minor-problems-with-using-an-asus-z97-a-motherboard](http://askubuntu.com/questions/503168/minor-problems-with-using-an-asus-z97-a-motherboard)

I turned off Windows UEFI and changed to other OS.
I then had to go into CSM to turn on UEFI and to boot in UEFI mode, I could only get it to work if I set to UEFI only. But all other settings did boot in BIOS mode.
There also were some settings for turning on booting from USB and storage devices.

What video card do you have?

---

### Post by Nate_Lowe on 2014-10-07
2x GeForce GTX 670

---

### Post by Nate_Lowe on 2014-10-07
Also I saw the settings in the Bios you were talking about, switched them. Remaking the USB again and we'll see if it helped.

---

### Post by Nate_Lowe on 2014-10-07
This has to be from the development side, the exact same file is corrupt when I download from different networks and different machines. If it was just a matter of being corrupted in route then it might be the same file some of the time, but not ALL of the time. Appreciate the help but I'm moving on.

---

### Post by oldfred on 2014-10-07
My older system had a nVidia 9600GT and I always had to use nomodeset, both for live installer and first boot or until installing nVidia driver from repository.
But new system and nVidia 620 card booted without nomodeset using the open source driver. Have not yet installed nVidia driver as it works well without it using fallback/flashback gui.

---

