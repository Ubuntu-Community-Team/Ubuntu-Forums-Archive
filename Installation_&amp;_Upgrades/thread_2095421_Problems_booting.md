---
title: "Problems booting"
date: 2012-12-16
forum: Installation &amp; Upgrades
---

### Post by bencouve on 2012-12-16
Hello Experts,

There appears to be a little problem with my laptop. First off the monitor failed so I have connected an external monitor to it, which has been working fine for the last month or so.  

Today my daughter was watching Mickey Mouse on youtube when I finally got my laptop back she had somehow lost the normal firefox browser settings so I pressed a few f1-f12 keys to see if I could get my normal firefox browser back (not sure why I did that but I did). Now I cannot seem to be able to get my monitor to respond to a normal boot. It appears to be booting up with the Ubuntu startup but then  I get the "out of range" message from the monitor. 

However, if I boot from the USB where I have Ubuntu installed too then it works fine. I need to access the data on my laptop though so need my laptop back.  

Could anyone shine some light on this.

Thanks in advance.

---

### Post by bencouve on 2012-12-19
Come on guys, is there no one out there that can help me with this, please

---

### Post by grahammechanical on 2012-12-19
I do not own a laptop but I think that it is necessary to press one of those Fn keys to switch video output from the laptop screen to the external monitor. May be you have turned off the function to use the external monitor.

If you can load Ubuntu look for Displays in System Settings (assuming 12.04 and later) and try - detect displays.

Or, if you are using a proprietary video driver look for the proprietary driver setup utility in the Dash. For example, the Nvidia Driver comes with the Nvidia Xserver Setting Utility. Try using - detect displays there.

At the Grub menu press E. That will put you in the Grub Edit mode. Look for a line that says quiet splash and add nomodeset in front of those two words. Then press either Ctrl+X or F10 to boot.

That should load Ubuntu without any attempt to determine the video mode. I think that Ubuntu is trying to find the video mode for the broken screen and not the external screen.

Regards.

---

### Post by sudodus on 2012-12-19
I don't know what kind of setting you managed to get pressing those function keys, but there are a few options to try:

If your home directory is not encrypted, you can easily get your data back when the computer is booted from the USB drive. Is this the case? Otherwise you need a master passphrase to unlock ecryptfs. This is still possible, but not as easy.

It might also work to boot into recovery mode (usually the second option in the grub menu). Or try to get a text screen with

ctrl + alt + F3 (or any nearby function key).
ctrl + alt + F7 returns to the graphical desktop environment.

Another option is to move the disk to another computer and try running it there. If you have no proprietary graphical or wireless lan driver, it should work to boot without any tweaking at all.

---

### Post by churchy d on 2012-12-19
you can pull the files off of your hard drive installation with your ubuntu usb drive.  But you should be able to avoid having to go that route.

try navigating to your home directory and deleting your .config/monitors.xml file. you can get there using your ubuntu usb drive and mounting your hard drive.  

This page should provide some additional help.
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

### Post by bencouve on 2012-12-19
Thanks for your replies, much appreciated. Just working through them.

First off, churchy d, I am getting permission denied for access to the .profile folder. I thought I would try this first as it seems the easiest.

---

### Post by bencouve on 2012-12-19
Ok, sudodus, your comment

"if your home directory is not encrypted, you can easily get your data  back when the computer is booted from the USB drive. "

How do I know if my home directory is not encrypted. I can get files from the home directory through the navigator. I cannot seem to be able cd to some of the directories as it states "permission denied". The user an group is set to 1000

If the folder is not encripted then how do I go about doing a recovery?

---

### Post by sudodus on 2012-12-19
> **bencouve said:**
> Ok, sudodus, your comment

"if your home directory is not encrypted, you can easily get your data  back when the computer is booted from the USB drive. "

How do I know if my home directory is not encrypted. I can get files from the home directory through the navigator. I cannot seem to be able cd to some of the directories as it states "permission denied". The user an group is set to 1000

If the folder is not encripted then how do I go about doing a recovery?

You seem to be able to view the subdirectories of your home directory. But to be sure, cd to them with root privileges:

```
sudo -i
```
```
cd /home/'your-directory'
``` where you use the actual name of your home directory. Then you can cd to subdirectories and watch and/or copy the contents. If encrypted, you will find no files except the ecrypt files.

```
sudo rsync -avn 'source/' 'target'
``` is a good command to copy a directory and its subdirectories.
```
sudo rsync -av 'source/' 'target'
``` will do the job.

Read ```
man rsync
``` to learn more about rsync

You can also start a file browser as root, but be warned, it is easy to destroy (for example delete) a lot of files, when running a browser like that.

---

### Post by bencouve on 2012-12-20
Just to say thanks for the comments.

Churchy d, that worked, removing the .config/monitors file. Thanks.

and [sudodus]("http://ubuntuforums.org/member.php?u=1499021") I did what you said and was able to copy the files so that worked too. While I was at it I tried Churchy d's method and the external monitor is not responding.

Anyway, thanks all for your repsonses.

Best regards
B.

[]("http://ubuntuforums.org/member.php?u=1499021")

---

### Post by sudodus on 2012-12-20
You are welcome :-)

Do you need more help trying to get that monitor working again? In that case it might be a good idea to start a new thread with a title explaining that problem to attract the experts in that field.

---

