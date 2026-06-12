---
title: "is there a problem with the 14.04.1 installer?"
date: 2014-10-08
forum: Installation &amp; Upgrades
---

### Post by fbaerkir on 2014-10-08
I'm having loads of trouble trying to install Ubuntu on a machine that previously ran it (I think the previous version was 13, but wouldn't swear to that), and I'm starting to wonder if it's possible the problem is with the download.
Backing up, I had a machine I was using as a file server. It was going along pretty well, but then started having what looked like hard drive issues, which didn't surprise me since it was a drive I had pulled out of a much older computer. So I put in a new HDD for the OS. I had four other drives in the machine I had arranged into 2 RAID1 arrays using LVM, but those seemed problematic before so I had planned to rescue the files and make one large volume after the new installation.
So I downloaded the 64-bit 14.04 desktop version and tried to install, only to be met with an error saying the installer crashed. Tried again, same result. So I tried re-burning the ISO using Linux Live USB Creator, per the community documentation. It was the method I used for the previous installation, so I know it does work. But, still no luck. Then I tried the server edition, with the same result.
Each time, I get partway through the installation and, usually right after I enter a new password for the user account, it crashes. A window pops up indicating an I/O problem, like a bad HDD or a cooling issue. The fans all work, and I tried using a different HDD. I also tried swapping SATA cables and the SATA ports on the motherboard. I also tried using different USB ports and also a different USB memory stick. Having swapped out every component, I'm confident this is not a hardware issue.
I've also tried running a live version of Ubuntu and hitting the install button within that. That gave a series of errors along the following lines: "The following file did not match its source copy on the CD/DVD /target/lib/firmware/s5p-mfc/s5p-mfc.fw" There were several of those indicating different files that did not match.
But given that I've tried several different downloads on multiple pieces of hardware, and it's a fresh installation onto a new HDD, is it possible the downloader is faulty? What other avenues can I try? I don't have a CD/DVD drive on this machine, but it is connected to the Internet.

---

### Post by ajgreeny on 2014-10-08
You should check the md5sum of your .iso file with the data listed at [UbuntuHashes - MD5sum]("https://help.ubuntu.com/community/UbuntuHashes")

If it does not match totally you will need to download again, preferably using a torrent client which checks the integrity of the file as it comes down.

---

### Post by fbaerkir on 2014-10-08
Hmm. It checks the same.

---

### Post by geomcd1949 on 2014-10-08
Make sure you have what you want - 32-bit or 64-bit. I had the wrong one one time, and it drove me nuts. When I got the right one, it worked perfectly.

---

### Post by fbaerkir on 2014-10-08
Thanks - it's the 64-bit version, though. I'm just not getting my head around what could be causing this.

---

### Post by fbaerkir on 2014-10-08
OK, here's another weird thing. When I try Ubuntu Server (14.014) I can get most of the way through the install, but it has a problem at the select and install software step (it's not specific, it just says there's a problem). If I skip that step, it finishes the install. But there's no GUI installed. I type startx and it says there's no program. I went through this a couple days ago and found advice on how to apt-get install ubuntu-desktop. But it returns an error saying that can't be found. This is a new install, so I haven't altered the lists of software sources or anything. Could this be a firewall issue or something?

---

### Post by fbaerkir on 2014-10-09
Well, I've now tried going back to version 13, and that didn't work either - same I/O error. I also tried it with the HDD outside the case to ensure there was no overheating issue, with the same result. I tried a third HDD, and reseated the RAM, and changed all the cables. I reset the CMOS on the motherboard. Every time I run into the same issue of files not matching (but always different files) and then the installer crashes. I'm at a complete loss here.

---

### Post by mastablasta on 2014-10-09
> **fbaerkir said:**
> . This is a new install, so I haven't altered the lists of software sources or anything. 

now would be a good time to check that file. you can do it with live session.

also the previous errors really do indicate something is wrong with the image itself. and you say md5sum matches hmm...

can you download via torrent (desktop), burn it on DVD (or USB) and then on boot test the "burned" image (it's on boot after language selection I believe).

if oyu are burning with nero I think there is a check box available where it tests the data is written correctly.

---

### Post by fbaerkir on 2014-10-10
Well, this is interesting. 
Last night I tried actually burning a DVD and trying to install with an external DVD drive; same result.
So I then downloaded the 14.04 server edition via torrent, and checked the md5sum, which did match. Then I ran the disc check via the server install home screen. It came up with the following: "Integrity check failed. The ./pool/main/linux/firewire-core-modules-3.13.0-32.57_amd64.udeb file failed the MD5 checksum verification. Your CD-ROM or this file may have been corrupted."
I'm far from an Ubuntu expert, but I can usually at least get my head around the concepts going on. This one has me completely befuddled. How would the md5 sum match in one place and not another, barring hardware error? But I've tried 3 HDDs and swapped cables/ports. The RAM checked fine on the server install utilities. The processor seems to work, as the install at least starts. If it's the mobo or PSU, it doesn't seem likely it would fail at the same place every time.
And yet if it's the installer, why am I getting the same errors on different editions and versions? It can't be an IP issue, because everything should be on that install DVD (I tried unclicking the download updates option). Problems with Linux Live USB Creator wouldn't explain why the DVD drive didn't work. I'm at a complete loss here.

---

### Post by sudodus on 2014-10-10
You may have problems with burning the DVD. Have you tried the lowest possible burning speed? Maybe try another tool. I like ***k3b***.

But I would suggest that you try to flash the iso file to a USB pendrive and boot that way. I think it is easier and more reliable today compared to CD/DVD.

See this link

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by fbaerkir on 2014-10-10
Thanks for the response, but the USB method is what I tried first (per previous posts). The DVD option only came out after numerous failed attempts using other methods.
As for pen drive utilities, I tried Linux Live USB Creator (that's my main application for this; tried over a dozen times now) and, thinking maybe that was the issue, I've also tried unetbootin, both per suggestions in community documentation.

---

### Post by sudodus on 2014-10-10
Then it sound like there is a bug. It is possible that "The ./pool/main/linux/firewire-core-modules-3.13.0-32.57_amd64.udeb file failed the MD5 checksum verification" because the checksum is wrong (maybe belongs to an older version of that udeb file).

Did you try the version 14.04 LTS or the newer and debugged version 14.04.1 LTS (the first point release)? If you have not tried the newer and debugged version, please do so :-)

The md5sum is

```
ca2531b8cd79ea5b778ede3a524779b9  ubuntu-14.04.1-server-amd64.iso
```

---

### Post by sudodus on 2014-10-10
> **fbaerkir said:**
> OK, here's another weird thing. When I try Ubuntu Server (14.014) I can get most of the way through the install, but it has a problem at the select and install software step (it's not specific, it just says there's a problem). If I skip that step, it finishes the install. But there's no GUI installed. I type startx and it says there's no program. I went through this a couple days ago and found advice on how to apt-get install ubuntu-desktop. But it returns an error saying that can't be found. This is a new install, so I haven't altered the lists of software sources or anything. Could this be a firewall issue or something?

Ubuntu Server comes without a GUI.  Linux servers are usually run without a GUI. If you want a graphical desktop environment, install one of the desktop flavours (standard Ubuntu, Kubuntu, Lubuntu, Xubuntu, Ubuntu Gnome, Ubuntu Studio, ...). It is possible to install a simple graphical window manager, for example fluxbox or openbox if you really want.

You can also built your own system with exactly the packages you want from the Ubuntu ***mini.iso***.

---

### Post by fbaerkir on 2014-10-10
Thanks - I was previously able to install a GUI on Ubuntu Server (that earlier install I mentioned). Trying to remember back, I think I installed it using apt-get. But that's not working this time 'round. Something seems corrupt.
And I should have been more specific: it is the 14.04.1 version of Desktop I was trying. I'm at work now while while a USB installer for Suse burns at home. I'll find out tonight if my problem is specific to Ubuntu (given that I had the same issue yesterday trying version 13, I have my doubts). But given that it's fresh hardware I can't imagine what else might be causing this. Maybe something buried in the boot record that doesn't actually delete when I select that option at install? Even then, swapping the HDDs should have addressed that.

---

### Post by fbaerkir on 2014-10-10
Whaddya know, the OpenSuse installer worked! I still have no idea what was up with the Ubuntu installers, but at least I can get my files worked out now and make for an easier transition someday down the road. Thanks for the help!

---

### Post by ecophobia on 2014-10-11
I would do a Network Install instead. This way you should get the files downloaded form the net \ it is slower, but it looks like you have already wasted a lot of time on troubleshooting.

---

