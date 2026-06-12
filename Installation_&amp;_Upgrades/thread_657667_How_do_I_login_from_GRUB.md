---
title: "How do I login from GRUB ?"
date: 2008-01-03
forum: Installation &amp; Upgrades
---

### Post by picard12 on 2008-01-03
I have just installed Ubuntu server 7 on my HD 100GB partion. The installation was successful but I can't login.

The GRUB screen loads upon HD boot up. It showed GRUB with text prompt. I can't type in my user name or password.
 I have only Ubuntu installed on 1 partition. I am a newbie.

How do I log in?

---

### Post by taurus on 2008-01-03
If you are installing the server, don't expect to see a window manager like Gnome or KDE because server version doesn't come with one.  It's just a commandline.

So, if you want a window manager, you have to install one by

```
sudo apt-get update
sudo apt-get install ubuntu-desktop gdm
sudo /etc/init.d/gdm start
```

---

### Post by picard12 on 2008-01-03
> **taurus said:**
> If you are installing the server, don't expect to see a window manager like Gnome or KDE because server version doesn't come with one.  It's just a commandline.

So, if you want a window manager, you have to install one by

```
sudo apt-get update
sudo apt-get install ubuntu-desktop gdm
sudo /etc/init.d/gdm start
```

what are these lines of codes? Am I suppose to download this patch and install it from floppy? :confused:

---

### Post by taurus on 2008-01-03
The first line is to update your repos list.  The second line is to install Gnome window manager; and the third line is to start a GUI log in screen.  Again, assuming you have logged in with your username and password and you have a network connection.

---

### Post by steveneddy on 2008-01-03
First you have to log in where it says the name of your machine and** login:**

Then type the above commands in the terminal screen.

When you install the server edition, there are no pretty colors or screens for you to use graphically. You are in a CLI, or a Command Line Interface.

Follow the advice above to install a GUI, or Graphical User Interface that you may be more accustomed to.

If you don't want or actually need your machine to be a server install, you may consider installing the regular Ubuntu.

---

### Post by picard12 on 2008-01-04
> **steveneddy said:**
> First you have to log in where it says the name of your machine and** login:**

Then type the above commands in the terminal screen.

When you install the server edition, there are no pretty colors or screens for you to use graphically. You are in a CLI, or a Command Line Interface.

Follow the advice above to install a GUI, or Graphical User Interface that you may be more accustomed to.

If you don't want or actually need your machine to be a server install, you may consider installing the regular Ubuntu.

I don't see the machine login screen. There is only the text screen which shows: GRUB _ text box blinking. When I tried to type in text at that line, I don't see any characters appearing on screen. Is the installation still incomplete?

Should I reinstall server again?
Is Ubuntu server differ from Red Had Fedora server?

---

### Post by lvleph on 2008-01-04
I would say that since you are a noob you don't want server at all and want the Ubuntu 7.10 Desktop. I would go ahead and install that instead. Then you can install anything that you may need that has to do with having a server and uninstall anything you don't need.

---

### Post by picard12 on 2008-01-04
> **lvleph said:**
> I would say that since you are a noob you don't want server at all and want the Ubuntu 7.10 Desktop. I would go ahead and install that instead. Then you can install anything that you may need that has to do with having a server and uninstall anything you don't need.

ok. I installed Ubuntu desktop version on another partition. Ubuntu can't boot up. It showed the message:

GRUB 1.5

GRUB loading... please wait..
Error 22
_ 



What is error 22 message? I couldn't type in any command in that prompt. Should I reinstall desktop version using the whole HD?

---

### Post by lisati on 2008-01-04
An "error 22" sometimes happens when an installation has "gone wonky". You might want to consider a clean, fresh install, replacing both your copies of Ubuntu.

---

### Post by picard12 on 2008-01-04
> **lisati said:**
> An "error 22" sometimes happens when an installation has "gone wonky". You might want to consider a clean, fresh install, replacing both your copies of Ubuntu.

I reinstalled Ubuntu desktop version on the whole drive. Ubuntu boots up fine. 

now I can't seem  install nvidia driver for my Geforce 7600GS. I downloaded the Linux driver to desktop but it won't run. How do I install software that I downloaded? I open archive manager but I don't see the file exe similar to windows.

I am confused. :confused:

---

### Post by oldos2er on 2008-01-04
From the top menu, go to System, Administration, Restricted Drivers Manager.

---

### Post by insertAlias on 2008-01-04
There are no .exe files.  Is the name of the file you downloaded  > NVIDIA-Linux-x86-169.07-pkg1.run
If it is, then open up a terminal, cd to the directory and type:
```
sudo chmod +x NVIDIA-Linux-x86-169.07-pkg1.run
sudo ./NVIDIA-Linux-x86-169.07-pkg1.run
```
That should do it.

The easier route is to use the Restricted Drivers Manager like oldos2er said.

---

### Post by picard12 on 2008-01-04
> **insertAlias said:**
> There are no .exe files.  Is the name of the file you downloaded  
If it is, then open up a terminal, cd to the directory and type:
```
sudo chmod +x NVIDIA-Linux-x86-169.07-pkg1.run
sudo ./NVIDIA-Linux-x86-169.07-pkg1.run
```
That should do it.

The easier route is to use the Restricted Drivers Manager like oldos2er said.

ok. I will try both methods as you suggested.

---

