---
title: "Karmic 2.6.31-15 bad Linux Upgrade"
date: 2009-11-26
forum: Installation &amp; Upgrades
---

### Post by izz.y on 2009-11-26
I installed all of the upgrades from update manager, and 2.6.31-15 was one of the available. Ubuntu Karmic is the only OS installed, so the GRUB 2 menu never comes up, it just boot right away. When I installed the updates, I restarted the computer, I see the first loading scene, then it starts going to command line, and a lot of text came up, and then it says starting ntp, and everything starts flashing really quickly, and it gives you the option to login to command line, there is no gui or anything. However it is flashing, and the keyboard is very choppy so I can not put in the passwords. If I hit escape, I can access and boot the old kernel which works if I start in recovery mode, login in as root, and then I have to start GDM. It works but it is a major hassle. I tried to edit the Grub menu, so I can boot straight away to 2.6.31-14, by using gksudo gedit /boot/grub/grub.cfg, and I see the grub file, but when I try to save it says,  Could not save the file /boot/grub/grub.cfg, You are trying to save the file on a read-only disk. Please check that you typed the location correctly and try again. 

UPDATE: I was able to delete the 2.6.31-15 files with th rm -f command, and using update-grub to make a grub.cfg. Then I changed the timeout, and saved a copy to my desktop. Lastly, I used used the rm -f command to delete the current grub.cfg, and then the cp command to copy it from my desktop to /boot/grub/grub.cfg. I still need the 2.6.31-14 files though.[/FONT]

---

### Post by phillw on 2009-11-26
> **izz.y said:**
> I installed all of the upgrades from update manager, and 2.6.31-15 was one of the available. Ubuntu Karmic is the only OS installed, so the GRUB 2 menu never comes up, it just boot right away. When I installed the updates, I restarted the computer, I see the first loading scene, then it starts going to command line, and a lot of text came up, and then it says starting ntp, and everything starts flashing really quickly, and it gives you the option to login to command line, there is no gui or anything. However it is flashing, and the keyboard is very choppy so I can not put in the passwords. If I hit escape, I can access and boot the old kernel which works if I start in recovery mode, login in as root, and then I have to start GDM. It works but it is a major hassle. I tried to edit the Grub menu, so I can boot straight away to 2.6.31-14, by using gksudo gedit /boot/grub/grub.cfg, and I see the grub file, but when I try to save it says,  Could not save the file /boot/grub/grub.cfg, You are trying to save the file on a read-only disk. Please check that you typed the location correctly and try again. 

UPDATE: I was able to delete the 2.6.31-15 files with th rm -f command, and using update-grub to make a grub.cfg. Then I changed the timeout, and saved a copy to my desktop. Lastly, I used used the rm -f command to delete the current grub.cfg, and then the cp command to copy it from my desktop to /boot/grub/grub.cfg. I still need the 2.6.31-14 files though.[/font]

In no particular order ....  For playing with Grub2 head over here -->  [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)  It covers things like fixing a scrambled grub, adding / deleting entries from Grub etc.

People have reported issues with v15, but those I know cannot get the problem to replicate on our systems. 

There's a thread over here -->[http://ubuntuforums.org/showthread.php?t=1335464](http://ubuntuforums.org/showthread.php?t=1335464)  that I've been involved with. It seems different people have had different problems, so it's been a pain to help with.

If you post on there - I keep an eye on that thread & update it as I get new information & things to try.

Regards,

Phill.

---

### Post by slumbergod on 2009-11-26
I've been using -15 for a while now. I have also had a go reverting back to -14 to see if that resolved at least some of the weird karmic issues I have been annoyed with. 

For me there is no difference with -15. I get the same issues with both kernel versions.

---

### Post by phillw on 2009-11-26
> **slumbergod said:**
> I've been using -15 for a while now. I have also had a go reverting back to -14 to see if that resolved at least some of the weird karmic issues I have been annoyed with. 

For me there is no difference with -15. I get the same issues with both kernel versions.


If you are having a problem, please post a thread.

As a matter of couurtesy ...   
1) Did you use the LiveCD mode of Karmic to ensure that it was happy with your rig 
2) Did you upgrade or do a clean install over to 9.10 ?

Regards,

Phill.

---

### Post by jasonlbaptiste on 2009-11-26
I had the same thing just happen now.  I'm about to go to dinner for thanksgiving, but will get into it more.  Saw the same update, downloaded, installed, restarted.  Flashing shell comes up with 31-15 .  Hard to even enter user/pass .  I rebooted, went into boot selector from grub.  Went back to 31-14 and all is okay.  It also installed some vdpau and nvidia updates, but those are probably okay.  System:

UNR 9.10
Nvidia Ion and atom 330 (zotac board)
2gb ram
Using hdmi audio out.

---

### Post by punkybouy on 2009-11-26
I did the update a few hours ago and have not had any issues.  I did an install and not an upgrade from the 64 bit alternate CD last week since I wanted to encrypt the drive.  So far Karmic has been working very well for me.
MSI A5000 laptop.

---

### Post by witeshark17 on 2009-11-26
The update including kernel ** 2.6.31-15 **completed without any issues at all here. It's been running just fine for several days.

---

### Post by dhavalbbhatt on 2009-11-26
There's a bug filed for the above -

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/487355](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/487355)

---

### Post by Chimmer on 2009-11-26
> **jasonlbaptiste said:**
>  .  Hard to even enter user/pass .  I rebooted, went into boot selector from grub.  Went back to 31-14 and all is okay. 

I am also having an issue after the -15 upgrade. Like an idiot, I went in and removed the -14 version like I always do when a new one comes out.

Now, I get to the login screen but when I enter username and password, it looks like it's going to continue to load but then stops and takes me back to the username/password screen. I successfully was able to get it to load once and then after rebooting, ran into the same issue. Tried the recovery thing, had no luck. 

So basically, all I currently have is the -15 image that won't let me get past the username/password screen.

Any suggestions?

---

### Post by izz.y on 2009-11-27
Okay, I was a bit unclear in the beginning, because I was able to fix the grub problem. Pretty much when I upgraded to -15, There is a command line that was flashing or blinking very rapidly, and when you type, only some of the letters go in, so it was impossible to enter my user password. I was able to get rid of 2.6.31-15 with great difficulty, but now I just want to install all 2.6.31-14 packages, like the headers, firmware, etc. 

SIMPLY PUT: I know when you install 2.6.31-15 they install some kernel related packages like the headers, firmware, etc. , and I would like to delete the 2.6.31-15 packages, and replace them with the 2.6.31-14 packages. I don't know all the packages, so if someone could name them, and maybe provide link, that would be very helpful. I am going to try to go in synoptics, and delete all 2.6.31-15 packages, take not of them, and download and install 2.6.31-14 ones. I will add to this post when I am done with that.

---

### Post by izz.y on 2009-11-27
PROBLEM SOLVED

I was able to fully fix the problem, for reference purposes I will summarize everything that happened, and what I did.

A few days ago, I went to update manager, and I installed new updates that included the 2.6.31-14 kernel, and related packages. It said I needed to restart my computer, and i did. I say the initial white Ubuntu logo, on the black background, and it went straight to a command line. The command would quickly start blinking very quickly, and when you type, only some of the letters would come, so you have to keep on pressing them until they come up, however they were no indicators for the password, so it was impossible to know about what letters were typed on, so you could not log on. I hit escape while the computer was loading grub, and I started Ubuntu 9.10 2.6.31-15 recovery mode to be safe. I selected resume normal boot, and then I logged on the command line, and I switched to root where I typed gdm, to start gnome. I logged on as usual, opened up a terminal, and I also went to the boot folder using the regular file browser. I deleted all the files containing 2.6.31-15 by using "sudo rm -f /boot/filename.extension", and then I tried removing the grub commands by using the command "gksudo gedit /boot/grub/grub.cfg", and then editing that, but it would not save, so I tried using update-grub, and it did not detect the 2.6.31-15 kernel, so now grub worked fine. Now I knew that Ubuntu had some 2.6.31-15 packages, so I went to synoptics package manger, and searched for 2.6.31-15 and I did a complete removal of 3 packages that were installed. Now if I restart my computer it goes straight to 2.6.31-14 and it works fine. For reference purposes I have the following hardware:

Motherboard:          Biostar P4m900-m4
Grapghics Card:       PCI-e Nvidia Geforce 8400GS 512 mb RAM
Processor:            Socket 478 Pentium 4 with HT, 3.2 GHZ
RAM:                  1 2GB Corsair DDR2 Stick
Hard Disk:            250GB Excelstor Technology

The Case, power supply, cd/dvd/floppy/card reader, tv tuner, and processor are from a VAIO PCV-RS530G, that died on me, so I spent about $150 rebuilding it, and modding the case.

---

### Post by jasonlbaptiste on 2009-11-27
Yup, going to try the same thing in a few.  Wouldn't removing the packages from synaptic (mark for COMPLETE removal) update the grub properly?  I'll play around and document that way.

---

### Post by jasonlbaptiste on 2009-11-27
Yup, remove the image relating to 31-15 from synaptics.  MAKE SURE THAT 31-14 STILL EXISTS.  When it removes everything in synaptics, select the show in terminal option so you can see what's running.  It should update the grub config automatically.  Hope this also helps anyone out.

---

### Post by k()()zmi4 on 2009-11-27
> **izz.y said:**
> PROBLEM SOLVED
Grapghics Card:       PCI-e Nvidia Geforce 8400GS 512 mb RAM

G'day)
I've got the same spec video and ended up with successfull .15 boot after reinstalling drivers from console (.15 recovery boot).

---

### Post by Uss_Defiant on 2009-11-28
> **k()()zmi4 said:**
> G'day)
I've got the same spec video and ended up with successfull .15 boot after reinstalling drivers from console (.15 recovery boot).

I can confirm this as well.. i've got a Nvidia 240M and the problem was resolved after installing the linux drivers off the Nvidia website.

---

### Post by dafut on 2009-12-01
I'm running Karmic, net mini build, on a Dell Mini 10, has Poulsbo chipset for Graphics, Audio, et al.
On upgrading kernel to -15, the white logo would appear, then the same symptoms as izz.y: 
> and it went straight to a command line. The command would quickly start blinking very quickly
After a few moments of this flashing, it appeared to "reload" as the logo appeared again, followed by more flashing.

As I didn't take the time to work this problem then, I've run -14 until tonight where I ran apt-get update and upgrade, which pulled in a new gdm module, where I've now rebooted into -15, where I am now. 

I received notice that I was in "low resolution mode", which I accepted for "this session", but my display is correct after boot up. I did notice a slightly lagging mouse pointer and slow response, but that appears to have cleared up now as well.

I'm hopeful that I'm stable now...yet -14 is right around the next boot if needed.

Hope this is helpful to others having similar issues.

---

