---
title: "I'd love to be part of the Ubuntu community but I've encountered a couple of problems"
date: 2006-12-14
forum: Installation &amp; Upgrades
---

### Post by Sushi Pillow on 2006-12-14
[LEFT]As a lot of people probably have, I've used Windows for ages and never really tried that "linux thing". I didn't know how great it was until I tried the live cd. Now that I'm hooked, I've successfully installed Ubuntu (after messing up my windows installation once already). This time, instead of partitioning my 120gb drive and risking all my documents I've purchased an 80gb drive. I installed Linux on it by disconnecting the 120gig and connecting the 80gig and installing Ubuntu then connecting both drives and booting up. I expected to be asked which OS to boot but it gave me no such option. This is a minor issue compared to my other one though, I can always disconnect the Windows drive when I want to boot up Ubuntu.
[/LEFT]
 
       My main issue is that I use a "Globespan-Virata USB ADSL MODEM ALE 130". It is quite a pain since half the time it isn't recognized on Windows and/or doesn't connect when it is recognized. Ubuntu obviously can't read the driver cd. I've asked my dad to switch to a regular adsl modem but he's in the United States for business right now and isn't returning for two weeks or so. My ISP (Bezeq internet) is pretty horrible. It takes an hour to get a support representative and all they can do is tell you to check the Bezeq site for Linux drivers. Obviously, there were none. My questions are:[LIST=1]
[*]Can I obtain a Linux-version of the drivers?
[*]Is there some kind of windows driver emulator I can use to run the modem?
[*]If the two options above aren't possible, will I have to switch to a modem with no usb connection or maybe wi-fi? (I'm buying a Nintendo Wii soon enough so I'll probably end up doing this later anyways.)[/LIST]

Edit: I'm not sure if this is in the correct forum. Since the first question is an installation one and the second question is a post-installation one.

---

### Post by adaptr on 2006-12-14
> **Sushi Pillow said:**
> [LIST=1]
[*]Can I obtain a Linux-version of the drivers?
[*]Is there some kind of windows driver emulator I can use to run the modem?
[*]If the two options above aren't possible, will I have to switch to a modem with no usb connection or maybe wi-fi?[/LIST]1. Don't count on it - if both the ISP and the manufacturer are this difficult then your chances are very very small.
2. There might be, but why would you want to ? See also 3.
3. I would say "want to", even.
You already shelled out for a separate hard drive for Linux - buying a decent (i.e. Ethernet) modem is an even better investment, in my opinion.

---

### Post by Sushi Pillow on 2006-12-14
I'm pretty sure I can exchange my usb modem for an ethernet modem without much extra cost, the problem is Bezeq's support is horrendous. By the time my dad gets back and Bezeq responds it could take months. So for now I think I'll have to find an answer for number two. Also, any ideas for the dual-boot issue?

---

### Post by ibanez on 2006-12-14
As for you booting windows, cant you just go into bios, (or press hot key on boot to give a boot menu) & select boot from IDE0 and IDE1 respectively, Gotta be alot easier than phisically disconnecting and reconnecting hard drives.
I have a couple of my machines configured this way,

---

### Post by Sushi Pillow on 2006-12-14
I tried the BIOS thing and it caused Linux to bug out. For some reason Grub isn't working.
Edit: Trying to add Ubuntu to the boot.ini file. What would the exact script be? And would I have to alter the Windows line?
Edit^2:Trying to use [this]("http://enterprise.linux.com/article.pl?sid=05/02/16/1919205&from=rss") guide to dual boot. Now bootpart.exe isn't running :/ Not having very good luck. Windows won't recognize the drive Linux is on either.

---

### Post by Tux Aubrey on 2006-12-14
Welcome Sushi Pillow

I think your GRUB "problem" arises because the install didn't detect your (unplugged) windows drive and therefore had no cue to provide you with a dual boot option.  Effectively you now have two bootable drives, rather than the traditional master/slave setup with a single Master Boot Record (MBR) on the master drive.  As a general "rule" Windows likes to be on the Master drive and Linux is more relaxed about where it is.  This is why you can install Ubuntu on a slave drive but GRUB needs to reside in the MBR on the Master.  Unplugging your windows drive meant you didn't have that option.

I am betting than one of the nice geeks here will have a really clever solution for you, so I won't confuse the issue with a wanna-be geek work-around.  Hang in here and if you don't hear from someone real soon, post a new thread with a title like "GRUB help needed" and I'm sure someone will respond.

Again, welcome to the community.

---

### Post by Sushi Pillow on 2006-12-14
Thanks, I really wish $rosoft would just admit that other operating systems with better features than Windows exist and AT LEAST make it easy to make Windows coexistent with them. I've found one driver loader for Linux but a few problems arise from trying to use it. It's only a trial (I thought Linux was open-source :/), it doesn't work on most devices, and it slows down the device. I think I'll wait until I get a wifi router or better modem and meanwhile try to get dual boot working. By the way, I installed Linux with the Windows drive disconnected because I knew that it wouldn't make much of a difference since both ways it'll need configuration and it's better to keep the two OSes as seperate as possible. This is why I'm trying that NTLDR linking to GRUB method.

---

### Post by bulldog on 2006-12-14
Set the disk with ubuntu  and GRUB in the MBR, as the master boot device so you always boot from this disk.
Boot ubuntu and copy your menu.lst to the forum as well the hard disk configuration.
```
sudo fdisk -l  (l as in like)
```
Copy this outcome to the forum.
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```
To make a copy from menu.lst for if things go wrong :D 
```
gksudo gedit /boot/grub/menu.lst
```Copy the outcome to the forum,so we can set things straight.

---

### Post by Sushi Pillow on 2006-12-15
How would I get to the MBR and where do I enter the code? I'm sorry, I'm new to tweaking with computers themselves, more used to php and such. Should I just wipe my linux drive and reinstall ubuntu with the windows drive connected?

---

### Post by bulldog on 2006-12-15
You don't have to go to the MBR :D 
Things are done in linux mostly with a terminal,hit ALT-F2 and type gnome-terminal,which will open one for you.
Than copy and paste my commands one by one in the terminal and provide your password to get the  requested info.
Copy and paste this info to the forum so we can have a look at your problems.

---

### Post by Sushi Pillow on 2006-12-15
I'll have to write down the commands or burn this page onto a disc since I don't have access to the internet on Linux. I'm going to sleep right now so I'll do it tomorrow.
Edit:Got dual-boot working, thanks for the help guys. I just reinstalled Ubuntu with both drives connected since the terminal was bugging out and it works fine now. Now I just need to get a new modem :P

---

### Post by daveg2 on 2006-12-16
Sushi, I'm a bit of a newb myself.  Bulldog knows what he's doing and is heading in the right direction.

My goal is to let you know that, from my perspective, you did your install absolutely the right way.  I always start with Windows correctly booting from the master hard drive.  I then uplug the Windows master drive, plug in the Ubuntu drive as master, and let the Ubuntu install deal with the grub install.  Once that is working, I plug in the windows drive as the slave.

The benefits are: If I do something stupid during the install, it can't touch my windows install.  Nothing is done to the windows install.  If one install dies or one drive dies later, I can simply unplug the defective drive, make the other one primary, and it boots with no further effort.  If I want to move one of the installs to another box, I can unplug the drive, move it to the other box, and plug it in as master.  Grub stays with the Ubuntu drive.  Windows boot stays with the windows drive.  They are not bound together at all.

As Tux mentioned: "Windows likes to be on the Master drive".  I believe Windows won't boot unless it thinks it's on the master drive.  Grub can start from your linux master drive, do some magic to swap the windows drive from slave to master, then run the windows boot off what is now the windows master drive.  Get the info back to Bulldog and he'll show you how to do this.

<Edit>:  Woops, missed your post on page two that says you got it working.  Congratulations!

---

### Post by Sushi Pillow on 2006-12-16
Thanks, I might give up on Windows altogether once all drivers are available. It's sort of an endless cycle. Most programs don't work directly with Linux, people are afraid of change so they stick to Windows which gets to charge ridiculous prices and do whatever it wants to its customers. Linux is free, faster, and has none of the annoying features Windows does. The only thing stopping it from getting rid of Windows and OS X is lack of drivers and like with firefox vs. ie or yahoo mail vs. gmail people just won't take the better thing if it isn't what they're familiar with. It's inevitable that Windows will die out though, just a matter of time. Back on topic, I still have to run my computer through a few boots in different situations to check if GRUB is working consistently and that the drives don't depend on each other.

---

### Post by Vondy on 2007-04-10
Can I ask what the resolution of the issue with Bezeq was, if any?

I am looking very seriously at switching to Ubuntu and Bezeq is my ISP. The modem/internet access issue is the only outstanding issue I need clear answers on before taking the plunge. I have no issues replacing the modem, but need to make sure Bezeq isn't going to prove to be a deal breaker.

---

