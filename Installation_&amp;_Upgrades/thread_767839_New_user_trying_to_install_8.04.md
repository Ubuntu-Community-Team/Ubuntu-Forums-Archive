---
title: "New user trying to install 8.04"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by Loki777 on 2008-04-25
Alright, up until now I've been getting help from a user on another forum who seemed to be a seasoned Ubuntu user, but he couldn't help me with this last problem...

I have my hardrive partitions all set up, done in Norton Partition Magic, 10GB for / formatted to ext3, 4GB for swap, 30GB for /home in ext3.

The Gutsy LiveCD wouldn't boot on my laptop, but Hardy can, however, when I go to install, it can't read any of my partitions, just the two hardrives I have connected to the laptop.

Windows read the two drives as one, before I set up the partitions of course, but Ubuntu reads it as two drives with no separate partitions.

Installing within Windows it goes to Busy Box with the "type 'help' for list of commands" when choosing to run Ubuntu from the menu upon turning on the computer. Any help?

And, yes, I'm trying to dual-boot.

---

### Post by Rocket2DMn on 2008-04-26
If the LiveCD can see the drive but not the partitions, you should just let the Ubuntu installer setup the partitions for you (you can set them up manually in the installer, just as you did with Norton).  Alternatively you can use the GParted LiveCD to setup the partitions in advance, and Ubuntu should recognize those - [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)
Just make sure you don't overwrite the wrong drive.  I would disconnect your external discs when installing to help prevent accidentally overwriting them or having the installer think they are internal drives (and thus always present).

Otherwise, we need more details on your hardware.

---

### Post by Loki777 on 2008-04-27
Alright, just did the automatic install, and now it just boots to a black screen. I've also tried to set up the partitions manually both from the installer and Gparted, same thing.

I'm using an Alienware M9700.

---

### Post by Rocket2DMn on 2008-04-27
That sounds like a video driver issue, can you tell me what video card you have (make a model)?

---

### Post by Loki777 on 2008-04-27
NVIDIA GeForce Go 7900 GS, according to Device Manager.

---

### Post by Rocket2DMn on 2008-04-27
Perhaps you should try to install EnvyNG from a terminal and use the terminal interface to install the restricted drivers.  At your black screen, do CTRL+ALT+F1 to get to a tty (terminal) and login.
Hopefully you have a wired connection, because the internet should be picked up automatically.  Follow the directions here to install envyng-core - [http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A) (so you can run in terminal).  With all this you should be able to install the restricted nvidia drivers, reboot the computer, and have a GUI session.

---

### Post by Loki777 on 2008-04-27
I'm sorry, that was all greek to me, could you translate to newb?

---

### Post by MasterSander on 2008-04-27
When your ubuntu gets loaded you can always switch to terminal by pressing CTRL+ALT+ F <1 to 5>, login there, and then do what is says on that website

---

### Post by Rocket2DMn on 2008-04-27
Yes, a tty is essentially a full screen terminal (a command line interface = no graphical user interface).  The terminal is a key part of linux, so you should do your best to get comfortable with the basics of it - see [http://linuxcommand.org/](http://linuxcommand.org/)
What you need to do is get to that tty, login at the text prompt, then run
```
sudo apt-get update
sudo apt-get install envyng-core
sudo envyng -t
```
Note: it will prompt for your password when you run sudo because that command gives you super user privileges (like administrator in windows).  Type in your password and press enter - it will be accepting the password even though nothing shows as you type.
If your computer is connected to the internet through a wired ethernet connection (not wireless), this should work.  If you use wireless, the chances are that your computer is not yet configured to access the internet, unless you set it up during the installation process.
Envy will prompt you what to do, you will want to have it automatically detect the correct drivers for you and have it download them and install them.
If you are not connected to the internet, the sudo apt-get update command will fail and so will the second command, so please let me know.  We may have to figure something else out.

---

### Post by Loki777 on 2008-04-27
Yeah, no go, don't have a wired connection. =(

I do have a USB hardrive, though, could I put the files on that and copy them over to my main drive while booting from the LiveCD?

I'd need an alternate way to get the files, of course... But you think that could work?

And before I forget, thank you so much for your help!

---

### Post by Rocket2DMn on 2008-04-27
That won't really work since EnvyNG has to fetch drivers from the web.  Let's try autoreconfiguring X, then setting X to use the "vesa" fallback driver.
Reboot the computer and enter the recovery mode kernel (the second option at GRUB), so now you have a root terminal.  Run (re: second command, linux is case sensitive, don't forget the capital X in X11).
```
dpkg-reconfigure xserver-xorg -phigh
nano /etc/X11/xorg.conf
```
now you will have a terminal text editor open, use the arrow keys to move around.  Scroll down to the part that says
```
Section "Device"
     Identifier     "Configured Video Device"
EndSection
```
You will need to add a line after Identifier that looks like this:
```
Section "Device"
     Identifier     "Configured Video Device"
     Driver     "vesa"
EndSection
```
Do CTRL+X, let it save the file, it's ok to overwrite the existing one.  Now reboot with
```
reboot
```
Allow it to boot normally, and hopefully you will have a GUI login.  Let me know if you get this far, otherwise we need more extreme measures.

---

### Post by Loki777 on 2008-04-28
But that won't work because Ubuntu reads my Nvidia SATA stripe as two individual drives whereas the computer and Windows reads it as one, I lose Windows on installation and GRUB doesn't start.

I've tried installing within Windows as well, GRUB loads, and I can run Windows from it, but when trying to run Ubuntu it goes to Beat Box and says "Type "Help" for list of commands", I type help and gibberish shows up on the screen, then it crashes...

Thank you for your help so far, I'm sorry if this is a bother...

---

### Post by Rocket2DMn on 2008-04-28
Nvidia SATA stripe?  I'm not sure what that is, are you using RAID or SLI'd video cards?

---

### Post by Loki777 on 2008-04-28
I meant RAID stripe, sorry, two 250GB drives in the RAID 0 array.

I'm just using the names given to me by the Alienware customer support.

---

### Post by Rocket2DMn on 2008-04-28
That is really useful information to have.  I don't think you can effectively install Ubuntu on a RAID array with the LiveCD, you need the alternate install cd
Here is a link that has some options for you.  I don't know much about RAID, so you may have to get advice elsewhere unless you think you know what you're doing.
[https://help.ubuntu.com/community/Installation#head-86a18ab57715d9bb5f0dfaba497a928e67cd73ed](https://help.ubuntu.com/community/Installation#head-86a18ab57715d9bb5f0dfaba497a928e67cd73ed)

Sounds like a reinstall might be in order for you.  There isn't much documentation yet specifically for Hardy, but I imagine people will start producing it soon, esp. since Hardy is a long term support (LTS) release.  You can google around, or maybe make a post in the Installations and Upgrades forum, somebody there will likely have more information and advice than I can offer you for RAID -http://ubuntuforums.org/forumdisplay.php?f=333
Good luck.

---

### Post by Loki777 on 2008-04-28
Thank you very much, I'm sorry I didn't specify that in the first post. =)

---

