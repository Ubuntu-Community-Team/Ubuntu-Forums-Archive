---
title: "Install Ubuntu Server on brand new Lenovo Thinkserver TS140"
date: 2015-12-04
forum: Installation &amp; Upgrades
---

### Post by gregory18 on 2015-12-04
Hi, I just bought a Lenovo Thinkserver TS140 with Xeon processor, 500GB HD, and 4GB RAM. I am a first-time Linux user but have some familiarity with the Unix terminal. The issue I'm having is that I simply cannot get Ubuntu to install. I keep getting an "Error 1962: No operating system found...."

What I tried: I burned a DVD with the file "ubuntu-14.04.3-server-amd64.iso", popped it into the DVD-ROM, turned on the server, and got the 'no operating system' error. So I did some googling and found that I should press F1 during set-up and change the boot order so that it goes to the DVD-ROM first. I also fiddled with other things like enabling and disabling CSM, boot in legacy mode, etc. No difference. Obviously, this is really frustrating and I cannot believe it is this hard. This Lenovo Thinkserver TS140 has lots of positive reviews on Amazon and it seems as if Ubuntu would be a good fit.

In short, if anyone has any suggestions I would greatly appreciate it!

---

### Post by QIII on 2015-12-04
Hello!

Did you "burn" the .iso or simply copy it to the DVD?

---

### Post by gregory18 on 2015-12-04
Hi, 

Thanks for the reply! I did it on my Macbook -- I dragged it from the downloads folder to the DVD and then burned it.

---

### Post by Bucky Ball on 2015-12-04
Welcome. If you mean you dragged the ISO file to the DVD and then burned using a standard disk burning app, that is not going to work. That is a copy of the ISO on the disk, not bootable media. 

To create bootable media you can use [UNetbootin]("http://unetbootin.github.io/") to create the USB then install on a PC (it won't install on a Mac). The Mac version of UNetbootin is on that link, top right. ;)

---

### Post by gregory18 on 2015-12-04
Thanks, but what do you mean "install on a PC?" Do you mean the Lenovo? I just installed UNetbootin on my Macbook, then popped in an empty USB stick, then in UNetbootin chose "Distribution --> Ubuntu --> 14.04_Live" for Type: USB Drive....that installed a bunch of files on the USB drive. I put that in the Lenovo, started it up, and....same error. No operating system. Did I do something wrong? 

I should also say that when I pop in the Lenovo Easysetup CD included with the Lenovo it just takes me to a screen with "grub>" on it -- but I can't do anything on that screen. This is just weird.

---

### Post by ubfan1 on 2015-12-04
Did you change the boot order again to have the USB first?  Did you hashcheck the downloaded iso to ensure it was not corrupted?  The grub> prompt seems to be booting grub off the DVD, so we know the DVD boots, but some machines don't boot off USB.

---

### Post by gregory18 on 2015-12-04
I did change the boot order to have the USB first. I didn't do a hashcheck but I just Googled it now and think the command is md5? So just ran that in the terminal $ md5 ......-amd64.iso and go this as output:


MD5 (.../Downloads/ubuntu-14.04.3-server-amd64.iso) = 9e5fecc94b3925bededed0fdca1bd417

Is that right?

---

### Post by Bucky Ball on 2015-12-04
Try this. Format the USB to FAT32 so it is blank, nothing on it. Open UNetbootin. At the bottom, you can choose the ISO you have downloaded. Do not choose the default from the drop-down at the top, choose your ISO from the selections toward the bottom of that window. Burn the USB and boot from that. Any different?

---

### Post by oldfred on 2015-12-04
Another thread with same issue:
 [SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)

---

### Post by gregory18 on 2015-12-04
Thanks for this suggestion. I actually didn't do that, but your earlier reply made me think the culprit was how I was creating the boot disk. So I found this and tried it: [http://computers.tutsplus.com/tutorials/how-to-create-a-bootable-ubuntu-usb-drive-for-pc-on-a-mac--cms-21187](http://computers.tutsplus.com/tutorials/how-to-create-a-bootable-ubuntu-usb-drive-for-pc-on-a-mac--cms-21187) 

The good news: It worked! I installed Ubuntu server and a minimal desktop environment and things seem to be going OK. 

Thanks again to you and the others for the helpful suggestions.

---

