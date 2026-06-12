---
title: "firmware-b43-installer problem"
date: 2011-04-18
forum: Installation &amp; Upgrades
---

### Post by DoFlooterMoose on 2011-04-18
Sorry to bother everyone. Having an issue here. I'm a recent Linux convert from windows 7 (and I have to say I absolutely love Ubuntu!) I don't know what took me so long to switch over. but ill never go back. Any ways, I am some what computer savy. But still learning, so simple is better (if possible) I tried to install a pci wireless card, just to see if it was faster than my usb antenna. after trying to install the kernel, or firmware or driver, not sure which. i fallowed the instructions on the site that Terminal posted to me. Well... it didn't work. kept getting error msg's. now every time I install updates, new programs, or even uninstall something. weather it be in Terminal, synaptic, Ubuntu software centre, I keep getting firmware-b43-installer error. I'm not using the card, cause I couldn't get it to work. but how do I get rid of the error code that keeps coming up, even though I'm not trying to install it. This is what popped up in Terminal after installing Minitube.   

```
Errors were encountered while processing:  firmware-b43legacy-installer E: Sub-process /usr/bin/dpkg returned an error code (1) legion@juggernaut:~$ sudo apt-get remove --purge firmware-b43-installer [sudo] password for legion:  Reading package lists... Done Building dependency tree        Reading state information... Done Package firmware-b43-installer is not installed, so not removed 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 1 not fully installed or removed. After this operation, 0B of additional disk space will be used. Setting up firmware-b43legacy-installer (4.178.10.4-4) ... Not supported card here (PCI id 14e4:170)! Use b43 firmware. This is just for the b43legacy driver. Aborting. dpkg: error processing firmware-b43legacy-installer (--configure):  subprocess installed post-installation script returned error exit status 1 Errors were encountered while processing:  firmware-b43legacy-installer E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Can someone please help me out with this one. I'm not worried about installing the card anymore. I just dont want to keep seeing the error code pop up every time I want to install something. Thank you so very much for any and all help.

---

### Post by mörgæs on 2011-04-18
Hi, welcome to the fora.

Please post again, using CODE-tags around relevant sections of the text.

---

### Post by DoFlooterMoose on 2011-04-18
I will do that... as soon as I google what you just asked me to do so i know what your talking about. sorry... im a noob. Still learning.

---

### Post by drs305 on 2011-04-18
DoFlooterMoose,

Welcome to the Ubuntu forums !

Try renaming the script which is causing the problem so that the error isn't generated. Be very careful with this command, as you are running as the administrator. Copy/paste the command in a terminal by highlighting the command with the mouse, clicking in a terminal, and pasting by clicking the middle mouse button. (Or CTRL-c to copy, CTRL-SHIFT-v to paste in terminal.)


```
sudo mv /var/lib/dpkg/info/firmware-b43legacy-installer.postinst /var/lib/dpkg/info/firmware-b43legacy-installer.postinst.bad

```

If you would rather do it graphically, open your file browser as root, right click on the *firmware-b43legacy-installer.postinst* file and rename it with a ".bad" extension:
```
gksu nautilus /var/lib/dpkg/info
```



Posting info: When posting information from the terminal, open a post and press the # icon in the post's menubar. This will generate 'code' tags. Copy the content between the two tags - it helps with the formatting, especially with long output.

---

### Post by DoFlooterMoose on 2011-04-20
I appreciate your help. I tried both of those ways. the first one told me "no such file exists" and the second way i kept getting some error. and it kept popping up over and over again on its own. I'm guessing i just didnt do it right. so after spending an hour just tryin to figure out how to do what you told me to. And coming up with 20 different answers for how to do it. I just Did a fresh install. I hadnt got that far with the set up anyways. So now things are back to normal. and Ill just have to keep Studying up on Linux. I Havent lost my faith in it, its a big learning curve for me. Going from Windows to Linux. But I still absolutely love Linux. And I will do what ever it takes to keep from going back to it. No matter how bad my head hurts at the end of the day lol. Thank you again guys. Your help was much appreciated!

---

### Post by drs305 on 2011-04-20
I'm glad you have a working system again. :-)

You may not have done anything wrong. Nautilus can be a bit stubborn when run that way. Since you have a new installation, you may want to install "nautilus-gksu". It adds the ability to right click a folder and select 'open as administrator'. It's very helpful when you want to access a system file.

```
sudo apt-get install nautilus-gksu
```

Even though you didn't 'solve' the problem, if you don't require any more assistance with this problem you can mark the thread 'Solved' via the 'Thread Tools' link near the top right of the first post. You may not wish to do it at this time, but it allows 'helpers' to concentrate on posts with unresolved issues.

---

### Post by DoFlooterMoose on 2011-04-23
Thank you very much for that gksu. Im sure it will come in handy at some point. And as far as solving or not solving the problem. Im sure it would have. I just have to keep working with it. Read up on Linux and Ubuntu as much as i can. Maybe in a few years ill be able to solve my own problems :D. So anyways... again thanks for all your help. Best wishes to you and yours.

---

### Post by FiFE on 2011-11-16
Hi,

This solution didn't work for me but:
I've removed all firmware related to b43 driver by issuing "sudo apt-get purge firmware-b43*".
I've reinstalled firmware "sudo apt-get install firmware-b43-lpphy-installer". Worked like a charm.
Of course, I was connected to the Internet through a wired connection.

---

