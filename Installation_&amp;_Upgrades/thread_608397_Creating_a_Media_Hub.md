---
title: "Creating a Media Hub"
date: 2007-11-09
forum: Installation &amp; Upgrades
---

### Post by Silentheero on 2007-11-09
I have some questions about a project I am trying to put together. Once I put it together with the help of the community I will give back by writing up a tutorial explaining as much as I can. :)  First I will tell you what I want this media hub to do.
[LIST]
[*]Want to be able to log in from anywhere with a internet connection (multiple simultaneous connections)
[*]Want to be able to transfer files to and from said machine and stream from machine
[*]Want it to be as secure as a server on the net can be
[*]Want it to be a headless system (just a box sitting in the corner)
[/LIST]
I know that VNC is great for doing most of this and I have played with it a little, but I don't know how I should set it up, how to make it secure, and if any changes to Ubuntu are necessary. I have a box that I have been testing with but only over the lan and just networked via SAMBA. It had Dapper on it but I broke it trying to upgrade to feisty (I know, stupid me). :rolleyes:

I would like Gutsy on it, VNC, firewall (if needed). I will have the largest HD I can find (prob a 500gb) and may have another 500 external hooked up via USB.

MythTV and its like are not what I am looking for. Basically I need a secure internet-accessible hard drive. Any Ideas/ links/Instructions/flames? ;)

And yes I did search, but a project like this can go by so many names...

---

### Post by Depressed Man on 2007-11-10
Well for secure VPNing you want to SSH (secure shell I think it's called) it. That's what I'd start first (look up a phrase on here like 'VPN secure shell' (without ' of course).

I've never tried it myself, I've just read info on it (I'm a wee bit paranoid, so even with the best CIA/Pentagon/NSA/whatever protection systems I still wouldn't want to open a non-local VPN session.

---

### Post by Silentheero on 2007-11-10
So my plan of attack is to install openSSH as server on the gutsy machine and PuTTY as client on any windows machines. Then I will need to change the port from 22 to something else and use the ssh-keygen to create a RSA password and ssh-agent will remember it.

Will the different clients need separate passwords? Is there a graphical interface to access the computer as some of the users cannot use the command line? Or will it be like an extended lan that can be accessed through nautilus/explorer? Trying to find answers to these questions, but there is a lot out there.

---

### Post by Silentheero on 2007-11-10
In my searching I found [NoMachine NX Free Server]("http://www.nomachine.com/screenshot/server-install.php") that seems to have everything I need. SSH implementation, Desktop control, file transfers, etc. I have searched the forums here and found some howtos and info. I will check this out and see what I can actually do with it.

[How To: NX Free Server in Ubuntu Feisty]("http://ubuntuforums.org/showthread.php?t=1968&highlight=nomachine&page=25")

[How To: Install NX Server ]("http://ubuntuforums.org/showthread.php?t=441496&highlight=freenx")

Edit: Further searching shows that although VNC, NX, and the like will work for control, I still can't find a way to access the storage like it was a local drive or a lan drive, ie able to access files through explorer/nautilus and open/play/stream them. Any ideas?

---

### Post by daflame on 2007-11-18
If anyone is interested, I have Ubuntu packages for a working version of FreeNX  0.7.1.  Everything is quite good with only a config file change you can have unlimited sessions on your machine and RDP proxy using rdesktop.  The free version of !M server only allows 2 sessions max.  I have found this to be limiting at times.  Especially if you are trying to setup a server.  Plus it runs with the latest NX 3.0 backend and client.  I have working versions compiled for gutsy on x86_64 and i386.  If anyone needs other dist packages, please let me know and I'll start a VM to build one.

---

### Post by spupy on 2007-11-18
I don't understand much, but, if it is headless, how are you going to use VNC if the computer has no desktop to begin with (i.e. headless)? Is it nessecery at al, since you can use nautilus to manage files remotely througth ssh/ftp?
For audio, i would recommend MPD. It can stream audio in several formats over a network, and there are graphical clients that can control it over a network, too. You can even set it up as an internet radio station!
As far as i know, VLC can stream video and audio over a network, too, but I've never used it.

---

### Post by sammydee on 2007-11-21
I've done almost exactly what I think you are trying to do on my server.

For remote file access, check out sshfs. Here is a script I wrote to mount my server's root filesystem at ~/server

> #!/bin/bash
sshfs -p 2222 [email]myuser@mys.erv.ers.ip[/email]:/ ~/server &&
exit


I tunnel VNC connections over SSH for security, it's pretty easy to do this with an SSH tunnelling configuration tool like gstm (sudo aptitude install gstm). Google VNC tunnelling ssh.

I can open X applications like, amarok, nautilus, even movie players remotely through ssh just by adding the -X option and executing them from the command line.

I also do dynamic port forwarding over ssh which basically turns my server into a proxy server with a secure channel between me and it - great for unsecured wifi.

Basically SSH is a magical program which can do absolutely everything you could ever dream of that involves manipulating another machine over a network.

It's important to lock down an ssh server. I disabled password logons and root logons, so only my key certificate is allowed. I use seahorse to manage my gpg keys. Ubuntu gutsy comes with a keyring manager that automagically remembers your key password so you dont have to unlock it every time - very useful!

Google search for things to do with ssh - it is actually black magic, it's incredible what it can do.

Sam

---

