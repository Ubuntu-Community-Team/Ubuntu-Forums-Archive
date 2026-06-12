---
title: "'error' when following simple instructions for webcam"
date: 2007-07-27
forum: Installation &amp; Upgrades
---

### Post by abuntu-handicapped on 2007-07-27
Hi everyone,

I finally found simple instructions to install my webcam. The link is [https://help.ubuntu.com/community/EasyCam](https://help.ubuntu.com/community/EasyCam). The code is as follows

[B]Add the following line to your /etc/apt/sources.list

deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main

Then you need to update the packages and install easycam

sudo apt-get update
sudo apt-get install easycam2[/B]


My problems,
 First line, 
[B]
Add the following line to your /etc/apt/sources.list[/B]

**deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main**

I can open and edit sources.list but cant save. Why dont i have root permissions? i was the person who installed ubuntu. Is there a default password for root? because i was only asked to set up my account that i am currently using and assumed i would be set up with root permissions?

Second line,

sudo apt-get update

It runs and i get this at the end....

[B]Reading package lists... Done
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems
neil@neil-desktop:~$ [/B]

If i run apt-get update i get this...
[B]
neil@neil-desktop:~$ apt0get update
bash: apt0get: command not found
neil@neil-desktop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory[/B]

3rd line,

sudo apt-get install easycam

I get this...

[B]Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package easycam[/B]

This installation is not going as easy as some people mentioned.

Can anyone help?

Thanks in advance

---

### Post by Soybean on 2007-07-27
You need to use sudo to do things that require root access. When you type "sudo" followed by a command, that command (and only that command) is executed with root privileges. If you're using a graphical program, use "gksudo" instead.

So if you were editing the file with
```

gedit /etc/apt/sources.list

```
change it to
```

**gksudo** gedit /etc/apt/sources.list

```

It asks for your password -- it means the current user's password.

Similarly, "sudo apt-get update".

That should sort out most of your problems there. :)

---

### Post by abuntu-handicapped on 2007-07-30
I got it sorted. Thanks for your help Soybean

---

