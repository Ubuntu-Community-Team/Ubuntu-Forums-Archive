---
title: "How to install Firefox on Server"
date: 2007-01-13
forum: Installation &amp; Upgrades
---

### Post by ckemami on 2007-01-13
Hi all,
I am very new to Linux. I just installed Ubuntu 6.10 Server on my old Dell PowerEdge 2300
server (with slow Pentium II). But I need to get on internet and download some files. I have no idea how to do this. You may ask why I am not using Ubuntu desktop. The reason is that it did not install on my machine. I had no problem with the server install. I appreciate your help with this. Please note I am a beginner. I would appreciate if you spell out the scripts and commands I need to use to do this.

Thanks,
cke

---

### Post by icefaerie on 2007-01-13
I'm not exactly sure what you mean... a server is generally supposed to be headless (meaning no GUI), especially on older hardware because the server will be a lot slower if it also has to deal with a GUI.

If you know what files you need and where they are located, you can download them from the command line using wget.  Here is an example:
```
wget http://www.google.com/intl/en_ALL/images/logo.gif
```
That will download the google logo into whatever directory you are running the command in.    (To find out what directory you are in in the command line, run the command "pwd".)

You can also transfer files onto your server from another computer using SCP or FTP.  Here is how you would use SCP from your computer to your server:
```
scp /PATH/TO/file_to_transfer user@server:/PATH/TO/file
```
(That's assuming the computer you're transferring from is a Linux box...if not, you can get SCP tools for Windows.  [WinSCP]("http://winscp.net/") is a very nice graphical SCP client and looks much like an FTP client.)
Replace user with your username and server with the address of the server.  Replace the /PATH/TO/file_to_transfer with the path of the file on your machine that you would like to transfer to the other machine, and replace /PATH/TO/file with the name and path where you want the file to be on the server.

If you really want to install a GUI on your computer, I would recommend Xubuntu due to the old hardware, so you can just do:
```
sudo aptitude install xubuntu-desktop
```
But there are probably solutions that don't involve installing a GUI.  I'm just not really sure what you mean.

---

### Post by Hub-1 on 2007-01-13
I don't know why it didn't install on your old PC, but I guess it didn't have enough RAM or some other parts of its hardware were not powerful enough to run a Desktop Environment.
However, you should be able to install it, maybe it just works. To install a desktop environment you have to type the following after logging in:
```
sudo apt-get install xubuntu-desktop
```
This installs the meta-package xubuntu-desktop, which is a compilation of packages required to run Xfce4. Xfce4 is a lightweight desktop manager which should run with no problems on your pentium II. The *sudo* command gives administrator rights to the program you use. *apt-get* is  a command line install utility.

Whenever you want to know what a program is for, type *man yourprogram*. In this case it would be *man apt-get*. Type *q* to exit.
You can start Xfce4 with:
```
startx
```

---

