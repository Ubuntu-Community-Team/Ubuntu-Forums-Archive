---
title: "Need help with installing GRUB"
date: 2007-03-03
forum: Installation &amp; Upgrades
---

### Post by ferus on 2007-03-03
Hi, 

first of all let me say that this is my first post and I have the feeling that it's going to be a long one. I'm new to Linux (Ubuntu 6.10) and I wanted to give it a shot but I encountered several problems...
I know there are several posts about installing GRUB but none of them are solving my problem. Trust me i tried them all.
Let me first explain the "layout" of my computer.
I have 3 physical harddrives in my computer.

HD1 is divided to two logical partitions: C,D.
C - contains my primary WindowsXP
D - contains just other files (photos, mp3s, documents, etc)

HD2 is one big partition: 
E - contains games, photos, mp3s, documents...

HD3 is divided to two logical partitions: H, I
H - contains my backup WinXP (in case of problems with my primary XP I want to be able to boot and work)
I - should contain my Ubuntu 6.10

So what exactly is my problem? The problem is that I can't seem to get GRUB installed on the proper place. When I install it on MBR then during booting I get the ERROR 21 and can't seem to do anything about it. I can't even fix the MBR with fixboot command in Windows recovery console. I issue the fixboot command, Windows tell me that the MBR is now 
placed on C: but after restart I still get the GRUB Error 21. So I'm stuck and the only solution is formating the C: and reinstalling windows :-(  I've already done it twice in the last 2 days. 
So why am I getting the Error 21 (which I understand is that the boot HDD can't be found) when I install GRUB to MBR?

Then I tried to install GRUB on (hd2) - which as far as I can understand should be the 3rd HD and I wrote it in the GRUB installation options. But even then, when I boot from the 3rd HD it still boots to my backup XP and I can't boot to Linux. :-(
Can anyone tell me (based on the layout of my comp) where exactly should I install GRUB to have it accessible when I boot from HD3? Perhaps (hd2) is not enough, I'm not sure. It might be something like hd2,5, I'm not sure. Should it be installed on the 1st partition of 3rd HD? Or on the partition where my Linux resides?
Also I would be very glad if anyone can explain me why am I getting the Error 21 when I install GRUB to MBR?

My last question/doubt is about reinstalling GRUB only. On several sites I found some instructions how to install GRUB without reinstalling the whole system (for example here [http://ubuntuforums.org/archive/index.php/t-24113.html)](http://ubuntuforums.org/archive/index.php/t-24113.html)).
The instructions say that I must boot from LiveCD and start issuing various commands. sn't make sense to me. 
Particularly the command "find /boot/grub/stage1" in my opinion can't be issued because I am working in the OS which is on the CD. And when I browse through the file system I can't see any other HDs or devices. So how can I issue the command for finding anything?
Not even starting GRUB and typing root(hd0,3) (as written in instrucions) can't be performed because as I said the HDs are basically "not there". The OS on LiveCD just can't see them.
I'm sure I am missing something, just please tell me what.

Btw, the only way I was able to install Linux is when I unplugged my frist two HDs and then installed LInux on HD3 (or HD1 at that time because no other HD was present), installed GRUB on (hd0) and it worked like a charm. During boot I had the option to start either Ubuntu or my WinXP.
In Linux itself I didn't have any serious problems. I was able to install my drivers, codecs, applications, even beryl :-). 

You may wonder why am I simply not using the HD3 to work with both Linux and WinXP? Well, the problem is simple - my HD3 is a Maxtor and it already has some bad sectors but I can't seem to get rid of them. So I'm only keeping it as a test HD - for Linux, backup XP and so on...But I don't want to rely on it because I already lost some data because of the bad sectors.

I think this is all...I'm really sorry about this long post and I would really appreciate if some of you experienced people could help me.

Thanks in advance and have a nice day!


-=ferus=-

---

### Post by diepruis on 2007-03-03
Are you sure you set up GRUB properly? From your post I sense that you are a little confused about the hard drive devices under Linux and in GRUB. For example: you number your devices from 1, but they need to be numbered from 0 in both programs. You also write that you typed root(0, 3), but you don't have a partition on the 1st disk at the 4th partition.

Also, error 21 makes me suspect that you misconfigured your /boot/grub/menu.lst file. Since the loader passes stage 1 it was properly installed. From the GRUB manual:

> 
21 : Selected disk does not exist
    This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system. 


This makes me think you just entered the wrong disk / partition combination.

See this page for more information: [http://www.gnu.org/software/grub/manual/html_node/](http://www.gnu.org/software/grub/manual/html_node/)

If you try again and post the relevant configuration files (/boot/grub/menu.lst would be a start) this community can help you, but otherwise we can only guess.

PS: posting the output of ls /dev/*da* would be helpful too.

---

### Post by ferus on 2007-03-03
> **diepruis said:**
> Are you sure you set up GRUB properly? From your post I sense that you are a little confused about the hard drive devices under Linux and in GRUB. For example: you number your devices from 1, but they need to be numbered from 0 in both programs. You also write that you typed root(0, 3), but you don't have a partition on the 1st disk at the 4th partition.

Also, error 21 makes me suspect that you misconfigured your /boot/grub/menu.lst file. Since the loader passes stage 1 it was properly installed. From the GRUB manual:



This makes me think you just entered the wrong disk / partition combination.

See this page for more information: [http://www.gnu.org/software/grub/manual/html_node/](http://www.gnu.org/software/grub/manual/html_node/)

If you try again and post the relevant configuration files (/boot/grub/menu.lst would be a start) this community can help you, but otherwise we can only guess.

PS: posting the output of ls /dev/*da* would be helpful too.


Thanks for the reply...I only described my harddrives as HD1, HD2 and HD3 for description. I know that GRUB counts the drives from 0.
And the root (0,3) command was only an example of a command which in my opinion doesn't have sense (if you are booting from a LiveCD). But that was regarding a different problem.
Anyway, I'm at work right now, I will post my grub menu.lst tomorrow.

EDIT: Maybe I should mention that the only way I can boot to Ubuntu is by unplugging the first two HDs. So the response of commands and lists can be a little deceptive. Therefore, I'm not sure if it will really help.

---

### Post by bulldog on 2007-03-03
To know how ubuntu thinks about your disk configuration [not necessarely the same as you think :) ] try the following command,```
cat /boot/grub/device.map
```.
Now you know how they are listed under ubuntu.
Use just (hd0) or (hd1) and not (hd0,3), because if you do so,grub will be installed into a partition instead of the MBR.
To learn more about GRUB take a look at this place,
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

With this knowledge you can install GRUB on the device you want,I should take hd0,the standard boot device,but you can make a choice which one you prefer.
To install GRUB again from the live cd you can do as follows,

Boot into the live Ubuntu cd. 
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next line 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```
Keep in mind you need to make the setup,which in this case is (hd0),into the disk you prefer.

If you put GRUB into the MBR of the disk which contains your windows install and you want to remove GRUB for some reason,you won't have to reinstall your windows.
Just use the windows install disk and go into the recovery console and type fixmbr and/or fixboot,which in most cases will reinstall your windows bootloader and remove your GRUB.

---

### Post by ferus on 2007-03-03
I'm not sure I will be able to do this... As I said in my first post - 

1. currently I can only boot to Ubuntu with my other 2 hard drives unplugged. So any commands for listing/config will not be relevant :-(
Even if I boot to Ubuntu I can't change the GRUB to be installed elsewhere because my other 2 HDs are unplugged at that time...

2. fixboot does not help me. I tried it the win recovery console but I still got the GRUB Error 21 for some reason
however, I haven't used fixmbr yet...so this might be my fault

3. as for booting from LiveCD - my issues with it are also written in the first post - I can issue commands from LiveCD but only to the OS that runs from the CD. So all the config/lists are set by default becasue they are the response from the OS on CD. My hard drives are basically "not there" so Ubuntu (booted from LiveCD) doesn't see them. 
All in all, I can't change a thing when I boot from LiveCD :-(

---

### Post by bulldog on 2007-03-03
Some basic rules,
GRUB should be installed on the hard disk you boot from by default.
It doesn't matter if this is the ubuntu disk or the windows disk.
You should have an option in your BIOS to change which one of your hard disk should be the master boot dvice.
This one should have the GRUB in the MBR.
Once installed,you can't change the boot order without having troubles booting any OS.
This can be changed manually,but that's not the point right now.

You can boot from the live cd with all your hdd's connected and perform the ```
cat /boot/grub/device.map
``` command,to see how ubuntu is configuring your hard disks.
Or ```
sudo fdisk -l
``` should give you an idea how things are listed.

Are all of your hdd's IDE disks or do you have Sata as well?
How many partitions there are on any disk is of no importance to GRUB,only your menu.lst should point to the right partition to boot any OS.

---

