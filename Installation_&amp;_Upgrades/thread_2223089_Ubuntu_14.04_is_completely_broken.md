---
title: "Ubuntu 14.04 is completely broken"
date: 2014-05-09
forum: Installation &amp; Upgrades
---

### Post by lonewohlf42 on 2014-05-09
I have 5 computers at home and  not a single one of them will run Ubuntu 14.04. They were all running 13.10.perfectly well but since the upgrade none of them work properly. Everything from blank sign on screens to new accounts with type custom instead of administrator being created. All computers are different brands from Ibm to Acer to home built computers. I'm running Mint  for now. Have all computers backed up, waiting for something to happen with 14.04. I can run the 14.04 from the live dvd no problem but after install all kinds of strange things happen. I am testing 14.04 in a Virtualbox on Linux Mint 16. to see if their is any progress but it seems to be getting worse rather than better. I have a computer with two monitors and the system come up with (built-in display low resolution 640-480), can't change any settings, unusable.

---

### Post by mörgæs on 2014-05-09
Let's focus on one of the computers. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by lonewohlf42 on 2014-05-09
/home/lonewohlf42/lshw.txt

---

### Post by mörgæs on 2014-05-11
Though I have a fine eyesight I can't see through your post and into the lshw.txt file. 

Please post the *contents *of said file in CODE tags.

---

### Post by lonewohlf42 on 2014-05-11
Sorry but I'm not sure how to post code tag. I'll try to send it  to you. I also just noticed that two of my computers are not working now, and when I look at at monitors in the control center
they both say the same thing. The display is set at Built-in Display with limited resolution. So Built-in Display button is on and cannot be turned off or changed. A third computer, an old IBM Thinkcenter is working fine and shows the correct display in the monitor function in the control center. Can I send you an attachment of the file instead. I'm trying to re-install ubuntu so I  can send you the file

---

### Post by mörgæs on 2014-05-11
Could we try a bare computer without Virtualbox, please? 

Code tags are available in the advanced editor.

---

### Post by lonewohlf42 on 2014-05-12
I've tried several times to install 14.04 and can't seem to get it to work to the point that I get a usable screen,can only get it to work in virtualbox.It looks like it's installed but grub won't recognize it ,only see linux mint in grub. But I'll try again.

---

### Post by lonewohlf42 on 2014-05-12
I have managed to get 14.04 working for now. I used my wifes computer to create a new iso disk. I tried to make new disks 3 times on linux mint, and none of them worked.they wouldn't even get me to the try me screen. I now have ubuntu 14.04 running on my main computer.I made 3 lshw files from my main computer, a 13.10 file, a14.04 live file and a 14.04 file. I made the live one because the first time I upgraded my main computer the live mode worked but the installed mode was a blank screen. After trying all kinds of different thing I got a screen but is was a buit-in monitor screen with 640x480 resolution screen. I could only see part of the screen. I don't now how much help the files will be now that it's working. I need to do a reboot, but before I did that I wanted to send you these files incace it crashed.

---

### Post by ubfan1 on 2014-05-12
First, you should ensure your downloaded iso files are perfect:
1) Did you md5sum check the downloaded iso?
  See [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
  Check the number against the listing in the link for your release listed at
  [http://releases.ubuntu.com](http://releases.ubuntu.com) under the MD5SUMS link.
2) If using a CD/DVD, did you burn the disc as slowly as possible?
  See [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
3) Did you select the media check before trying to install?
 [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)
4) Did you ever do a "memory check" (another live-media menu choice) on your PC?
Doing the above can save you a lot of time struggling with a bad install media.

Next, these are UEFI machines, and I didn't see any EFI partitions, so apparently you are running in legacy mode?  Why?  Read up on the community help for UEFI ([https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) )

---

### Post by lonewohlf42 on 2014-05-12
I managed to get my computer back up and running by using the Avdanced ubuntu boot setting and then the normal not recovery boot option.I also remove the fast boot option in the bios settings.

---

### Post by mörgæs on 2014-05-12
Again: CODE tags are in the advanced editor. Please don't attach files.

If your last post means that the problem is solved please mark the thread so.

---

