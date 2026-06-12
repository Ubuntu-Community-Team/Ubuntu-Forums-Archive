---
title: "Dual Boot Win 7 and Ubuntu 10.10"
date: 2011-04-01
forum: Installation &amp; Upgrades
---

### Post by Tomween1 on 2011-04-01
I am back installing this newer version of Ubuntu (10.10) the last time I installed it was version 8 something. I am also running Window 7 home 32bit. From memory all I need to do was install windows on one hdd unplug it and the install ubuntu on the other (2 hard drive system). I've done this before and it created a dual boot in bios start. I'm guessing I've forgotten a step or two [IMG]http://i160.photobucket.com/albums/t171/bxprtaino/smiley%20face/crying.gif[/IMG] because after reconnecting both hdd's windows is the only boot-able. When I search the bios the hdd is detected and if I choose to boot from the drive the Ubuntu is loaded on it starts Ubuntu w/ no issues.

Where did I go wrong?

---

### Post by dieselglock on 2011-04-01
Hello,
Refer to this post and do the same. [http://ubuntuforums.org/showthread.php?t=1717958](http://ubuntuforums.org/showthread.php?t=1717958)

Len

---

### Post by wilee-nilee on 2011-04-01
About the only thing relevant in the link above is the bootscript, click on it in my signature and run it. Open a reply click on the **(#)** in the reply panel this generates code tags paste all the text from the generated file between them.

---

### Post by oldfred on 2011-04-01
Because the Win drive was not installed the os-prober could not find it. Do this with both drives plugged in, then set BIOS to boot Ubuntu drive.

sudo update-grub

If that does not find it then post the boot script wilee-nilee has suggested.

---

### Post by Tomween1 on 2011-04-01
> **oldfred said:**
> Because the Win drive was not installed the os-prober could not find it.

Sorry what Win driver

> **oldfred said:**
> Do this with both drives plugged

They are

Would it be easier to uninstall the Ubuntu from the second drive and reinstall it a different way?

---

### Post by wilee-nilee on 2011-04-01
I doubt if you need to reinstall the Linux. run the script as suggested by both of us, it will tell us what is where, and we can then get you set up. Don't forget the code tags, **(#)** in the reply window.

---

### Post by dieselglock on 2011-04-01
Your problem is more than likely a very easy fix. Do what "oldfred" said. If your computer will boot into Ubuntu with both drives connected open a terminal (ALT F2) type 
sudo update-grub and check the box that say's run in terminal and see what happens then.

Len

---

### Post by Tomween1 on 2011-04-02
> **dieselglock said:**
> Your problem is more than likely a very easy fix. Do what "oldfred" said. If your computer will boot into Ubuntu with both drives connected open a terminal (ALT F2) type 
sudo update-grub and check the box that say's run in terminal and see what happens then.

Len

Thank you, this worked, however there are multiple ubuntu options to choose from. I choose the first one and it opens it. Is there a way to delete all other ubuntus showing up?

Can I choose windows as my first boot choice?

Thank you, Tomween1

---

### Post by oldfred on 2011-04-02
It is recommended to keep two kernels, so if one has issues you can boot the other. Several ways to do what you want:

Startup manager (SUM) in synaptic will allow you to set boot default and the timeout even with grub2.
the quick and easy to make a default boot:

[https://help.ubuntu.com/community/StartUpManager](https://help.ubuntu.com/community/StartUpManager)
Download and install "StartUp-Manager from Synaptic package downloads. It will be listed under System/Administration menu. You can set it to default with Ubuntu (different versions) or Windows. You can also set the start up time in seconds.
[http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)

HOWTO: Grub Customizer 
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

Just be sure not to delete the kernel you are using or you will not be able to reboot, to confirm the one you are using:
uname -r

A easy way to remove the amount of kernels is to install Ubuntu tweak:
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

In synaptic search for linux-image to choose to delete old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

---

### Post by Tomween1 on 2011-04-02
Any idea if this would help?

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

### Post by oldfred on 2011-04-02
I have no experience with the Neo tools to edit BCD. But some windows users have posted and seem to like it. Windows users often prefer the EasyBCD as a boot loader, thinking they are using a windows boot loader. They really are using a third party tool.

I am primarily an Ubuntu user and like grub2. Grub2 is able to boot many different systems and its os-prober now finds almost all of them and sets up booting automatically.

---

