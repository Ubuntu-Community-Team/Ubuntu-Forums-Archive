---
title: "Automatic update, now computer won't start"
date: 2010-08-22
forum: Installation &amp; Upgrades
---

### Post by rorkimaru on 2010-08-22
Ok, So my PC told me that I needed to update and I ran the update and then was prompted to restart the machine.

I restarted the computer but it got to a purple screen with 4 orange dots and the word Ubuntu and then just stalled there. I left it for a few hours and nothing changed so I powered down the computer and turned it on again. Same problem. Just stops at the purple screen.

I want to get my files back so I tried using a Live CD which is what I'm using now and I can access *most* of my files but many of the folders have a white X on them and I'm told I don't have permission to access the folders.

Is there any way I can fix the install and log in to get my files? I have no problem having to reinstall the operating system after I've done a backup but I really want to get my files back, I don't want to just wipe the drive.

If there is any way to enable permission to copy the files across or to log in to my installed user account could someone let me know how its done?

---

### Post by Rubi1200 on 2010-08-22
Hi,
let me try and help with the first problem.

What graphics card do you have installed?

Thanks.

---

### Post by rorkimaru on 2010-08-22
OMG So sorry I posted this thread and then just solved the problem like straight away!

For anyone else who has run into this problem it can be sidestepped with the sudo command

For GUI junkies like me type:

sudo nautilus 

and then a window will open up like normal but it has root access and will be allowed to get all your files back. Just brows to the hard drive and you can access and copy all your files onto an external hard drive to backup your stuff.

Doesn't say a lot for Ubuntu's default security but I don't care because I have all my stuff back!!

Since I just posted the dumbest thread in the history of these forums I've nothing to say but...

Sudo Forgive Me

> **Rubi1200 said:**
> Hi,
let me try and help with the first problem.

What graphics card do you have installed?

Thanks.

Do you think I can avoid having to re-install? It's not a huge deal but just in case this happens again it would be nice to know. I have an nvidia but I can't seem to get access to what card it is and I don't know off hand.

Sure if it's really complicated and taxing you don't need to worry since I have my files back and thats the most important thing for me.

---

### Post by Rubi1200 on 2010-08-22
First, you need to run graphical applications with ```
gksudo
``` not ```
sudo
```Second, if you are still on the LiveCD, go to the terminal and post the output of

```
lspci | grep VGA
```Try booting the computer following the workarounds here:

[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

For NVIDIA, you need to use the nomodeset parameter.

---

### Post by rorkimaru on 2010-08-22
> **Rubi1200 said:**
> First, you need to run graphical applications with ```
gksudo
``` not ```
sudo
```

Are you sure about that because "sudo nautilus" works for me? Weird?

> **Rubi1200 said:**
> 
Second, if you are still on the LiveCD, go to the terminal and post the output of

```
lspci | grep VGA
```Try booting the computer following the workarounds here:

[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

For NVIDIA, you need to use the nomodeset parameter.

I'd post the output but I can't seem the type the "|" symbol. A lot of the symbol locations are messed up since I haven't actually installed.

Thanks for the link though, I'll try and work through it after I've finished backing up my files and tested them on my laptop to make sure stuff is working.

I have to say you are absolutely awesome for helping me so much and so fast. Big thanks =D

---

