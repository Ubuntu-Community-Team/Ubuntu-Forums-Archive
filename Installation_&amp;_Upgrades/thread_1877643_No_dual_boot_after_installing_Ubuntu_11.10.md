---
title: "No dual boot after installing Ubuntu 11.10"
date: 2011-11-08
forum: Installation &amp; Upgrades
---

### Post by nicolasg on 2011-11-08
hi, I just installed Ubuntu 11.10 on my Windows XP and after reebot I can`t dual boot. I will be thank if you can help me :D

---

### Post by oldfred on 2011-11-08
Welcome to the forums.

How did you install? Wubi inside Windows or a full install to partitions.

Did you boot and test your system with liveCD. Did that work ok?

Can you boot to the grub menu? If so you may have a video issue or if just a cursor in the upper left corner it also may be a video issue. What video do you have.

From liveCD terminal, post this:

#To see video:
sudo lshw | grep -A 11 display

---

### Post by nicolasg on 2011-11-08
> **oldfred said:**
> Welcome to the forums.

How did you install? Wubi inside Windows or a full install to partitions.

Did you boot and test your system with liveCD. Did that work ok?

Can you boot to the grub menu? If so you may have a video issue or if just a cursor in the upper left corner it also may be a video issue. What video do you have.

From liveCD terminal, post this:

#To see video:
sudo lshw | grep -A 11 display

I install it from the original CD and in windows, when i reebot I didn´t see the dual boot so I couldn´t enter Ubuntu. I didn´t try to boot through the cd, should I try? how i enter the grub menu? 

Sorry for all my questions im a noob in Linux :P many thanks

---

### Post by oldfred on 2011-11-08
What does boot?

You can post this:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

This also downloads the script and can make minor repairs. You can install it to the liveCD or download its own liveCD:


Yanni has created a easy way to download boot repair & run script:
HOWTO : easily create a Boot-Info summary
[http://ubuntuforums.org/showthread.php?p=11164270](http://ubuntuforums.org/showthread.php?p=11164270)
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by nicolasg on 2011-11-09
> **oldfred said:**
> What does boot?

You can post this:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

This also downloads the script and can make minor repairs. You can install it to the liveCD or download its own liveCD:


Yanni has created a easy way to download boot repair & run script:
HOWTO : easily create a Boot-Info summary
[http://ubuntuforums.org/showthread.php?p=11164270](http://ubuntuforums.org/showthread.php?p=11164270)
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Thanks for the information:). I have now another problem, i will install Ubuntu 11.10 on my laptop( Windows 7 Ultimate) but i will like to overwrite windows O.S and just leave Ubuntu. When i open the CD of Ubuntu i have the option to overwrite windows, my doubts are, if i overwrite windows it erase all(format) the computer? I will like to clean all my PC and leave it with just Ubuntu. Many thanks for your help :D

---

### Post by fantab on 2011-11-09
> **nicolasg said:**
> Thanks for the information:). I have now another problem, i will install Ubuntu 11.10 on my laptop( Windows 7 Ultimate) but i will like to overwrite windows O.S and just leave Ubuntu. When i open the CD of Ubuntu i have the option to overwrite windows, my doubts are,** if i overwrite windows it erase all(format) the computer? I will like to clean all my PC and leave it with just Ubuntu**. Many thanks for your help :D

YES, if you choose "**Erase disk and install Ubuntu**" option during installation.

However, I recommend that use the third option "Something Else". If you choose this you will have more control on your Hard Disk partitioning. [See THIS]("https://help.ubuntu.com/community/GraphicalInstall") and also see the attached screenshot.

---

### Post by nicolasg on 2011-11-10
> **fantab said:**
> YES, if you choose "**Erase disk and install Ubuntu**" option during installation.

However, I recommend that use the third option "Something Else". If you choose this you will have more control on your Hard Disk partitioning. [See THIS]("https://help.ubuntu.com/community/GraphicalInstall") and also see the attached screenshot.

many thanks fantab

---

