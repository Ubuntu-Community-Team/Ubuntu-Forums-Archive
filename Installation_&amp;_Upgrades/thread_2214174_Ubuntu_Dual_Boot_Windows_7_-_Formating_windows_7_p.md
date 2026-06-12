---
title: "Ubuntu Dual Boot Windows 7 - Formating windows 7 partition -No operating system found"
date: 2014-03-30
forum: Installation &amp; Upgrades
---

### Post by bobi2 on 2014-03-30
Hello,

Here is the situtation :
I have a VAIO VGN-NW21MF running on Windows 7 64-bits (furnished with the laptop). It had one partition for windows and one partition recovery so as to recover the system from scratch.
I decided one year ago to install ubuntu as a dual boot. I created then one parition for my data in ext4 format, one parition in ext4 format for ubuntu and one swap of 2 Go from what I remembered.
I had then something like :
- 2 Go Recovery (NTFS)
- 100 Go Windows (NTFS)
- 250 Go Data (EXT4)
- 50 Go Ubuntu (EXT4)
- 2Go SWAP.

Everything was working fine but after many years I thought it could be good to formate my Windows partition. I just went to Windows restore system by launching the recovery mode thanks to the Grub. I choose to format only the disk C where Windows was installed. After installing, it restarted and then "Grub rescue - error : unknown filesystem".

I looked up on the internet and created a live boot usb key so as to use the very useful tool "Boot repair". I selected, recommended repair and then restart without the USB key and ... It worked !
I was glad and even check that my data partition was still there with all my data so I was relieved.

But ... no news from Ubuntu.

I thought, well, I need to tell the MBR to boot on the ubuntu partition so as to launch the Grub. I looked up on the forum once again and did what was written there :
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) and then there
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

that is to say mount the partition where Linux was installed and then install the grub on the drive where the parition was installed.
I don't remember exactly why but I did not worked out well (sorry for this approximation).

And now once I boot without the USB key, I got an :  "Error No operating system found."
I just thought, all right I gonna repair once again my MBR thanks to boot repair from the USB boot. But the problem is when I am launching it, there is no more the recommended repair option (only the bootInfo summary that you can see below).

[http://paste.ubuntu.com/7181836/](http://paste.ubuntu.com/7181836/)

From what I understand, the MBR is completely messed up but I don't think all the data are gone. 
When I try for example to reinstall ubuntu and select a manual paritionning, it detects 2 partitions in an unknown format :
- one around 400 Go 
- one of 3 Go. 
I guess, I hope, the 3 Go is the recovery one.

Would you have any advice of what should I do now  ?

Thanks in advance for your time,

[URL="http://paste.ubuntu.com/7181836/"]
[/URL]

---

### Post by Mark Phelps on 2014-03-30
From the report, sda is pretty much trashed.  I would be surprised if you could recovery anything from it.

Since your goal of removing Win7 was obviously met, my own recommendation at this point would be to boot from Ubuntu install media, remove all the partitions from sda, and install afresh -- using the whole drive.

---

