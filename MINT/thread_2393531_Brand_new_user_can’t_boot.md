---
title: "Brand new user can’t boot"
date: 2018-06-04
forum: MINT
---

### Post by ssbama on 2018-06-04
Hi, I’m brand new to this and have no clue what I’m doing really. 
My computer messed up, hard drive was done for, so I purchased a brand new hard drive. 
I downloaded and made a dvd Linux mint 64 bit. 
Popped it in, loaded it up and installed it. Great smooth so far. 
Restarted and it asked me to take my disk out, and it won’t boot up. Just says ERROR. NO BOOT DISK HAS BEEN DETECTED. 
So I followed a guide, loaded it back up and did a boot repair process, still won’t boot up. 

What should I do?
ive tried entering my bios screen but I can’t change my bios boot source. 
All I can change is the order I boot from. HD, dvd drive, usb, etc...

It said my boot was successfully repaired. And to post this link if I have any issues. 
[Http://paste.ubuntu.com/p/67v2pm7zCV](Http://paste.ubuntu.com/p/67v2pm7zCV)
It said to change my boot to an shimx64.efi file but have no clue how to do that??

any help would be fantastic!!

---

### Post by QIII on 2018-06-04
Moved to MINT as a more appropriate sub-forum.

---

### Post by ssbama on 2018-06-04
Oh sorry about that, thanks!

---

### Post by mwl128340 on 2018-06-04
The pastebin link you reference says it doesn't exist. It's hard to say without more info but I've had a garmin watch hooked up to my comp before and the boot settings were set to go to usb first so it would throw me this error cuz it was trying to boot off the garmin watch.

---

### Post by ssbama on 2018-06-04
[Http://paste.ubuntu.com/p/67v2Pm7zCV/]("Http://paste.ubuntu.com/p67v2Pm7zCV/")

---

### Post by ssbama on 2018-06-04
Why does that not work... I took a screenshot and everything

---

### Post by mwl128340 on 2018-06-04
Are you trying to post the screenshot?

---

### Post by ssbama on 2018-06-04
Na I looked at it again and retyped the link and still doesn&#8217;t work. I guess if you want to post a pic you need to host it somewhere. Don&#8217;t have an account anywhere to host a pic.

---

### Post by ssbama on 2018-06-04
Just wondering how the heck to change where the pc boots from. My bios has nowhere to change my bios boot. Other then just selecting what to boot from first. Ie. hd, cdrom, usb

---

### Post by mwl128340 on 2018-06-04
[https://ubuntuforums.org/showthread.php?t=1291280](https://ubuntuforums.org/showthread.php?t=1291280) try following these instructions from a live environment for a boot script and post the code here in the thread. You will get the most help when you post the most info you can

---

### Post by mwl128340 on 2018-06-04
Bootinfoscript makes a nice pastebin file to reference

---

### Post by ssbama on 2018-06-04
So I booted off the disk, and got to the desktop. Downloaded that program and saved, extracted it to the download folder. 
When I run the script on that how too, all it says is it can&#8217;t find the program? What am I doing wrong?

sorry guys, I&#8217;m such a noob

---

### Post by ssbama on 2018-06-05
[http://paste.ubuntu.com/p/Py2ps2pPZK/](http://paste.ubuntu.com/p/Py2ps2pPZK/)

---

### Post by ssbama on 2018-06-05
Redid it all and got a working link. What do I need to do?

---

### Post by oldfred on 2018-06-06
Is this your link?
[http://paste.ubuntu.com/p/67v2Pm7zCV/](http://paste.ubuntu.com/p/67v2Pm7zCV/)

I see mention of Acer, if an Acer you need to set "trust" on .efi boot files from within UEFI.
       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)

---

