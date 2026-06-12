---
title: "Please help me"
date: 2007-06-10
forum: Installation &amp; Upgrades
---

### Post by johnsmith963 on 2007-06-10
Ok this is my first time using linux. I want to install enemy territory clicked the executable and got this error

Cannot open /home/peter/Desktop/et-linux-2.60.x86.run: No application suitable for automatic installation is available for handling this kind of file.

I didn't really mind I just went into the command line and did what this thread said. 
[http://ubuntuforums.org/showthread.php?t=5246&page=1](http://ubuntuforums.org/showthread.php?t=5246&page=1)

Still nothing. I've read through alot of the threads and I've seen something about 'sudo', the only problem is seeing as I'm currently 13 I know nothing of that command. So can someone explain to me just no how to run it but explain to me how to run other things in linux, I would buy a book but eh I have like no money.

Thanx for taking the time to read this. 

-Peter

---

### Post by taurus on 2007-06-10
Applications -> Accessories -> Terminal
```
cd ~/Desktop
chmod 755 et-linux-2.60.x86.run
sudo ./et-linux-2.60.x86.run
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by VirtualTiger on 2007-06-10
Don't worry, you don't need to spend any money on a book, you can get most of the information you need from the Internet...;)

Here are a couple of my favorite links:

[Useful Ubuntu Links]("http://www3.telus.net/lordfoul/pics/useful%20ubuntu%20links/useful%20unbuntu%20links.html")

[Ubuntu Feisty Starer Guide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty")

As for Sudo, I'm not familiar with all of the syntax yet, but I love:

```
sudo -s -H
```

This allows you to set your whole terminal session, instead of having to type sudo in front of each command.

---

### Post by johnsmith963 on 2007-06-10
Ok i tried that and got this

peter@peter-desktop:~$ cd ~/Desktop
peter@peter-desktop:~/Desktop$ chmod 755 et-linux-2.60.x86.run
peter@peter-desktop:~/Desktop$ sudo ./et-linux-2.60.x86.run
Password:
run-detectors: unable to find an interpreter for ./et-linux-2.60.x86.run 

-Peter

---

### Post by johnsmith963 on 2007-06-10
Ok i tried that and got this

peter@peter-desktop:~$ cd ~/Desktop
peter@peter-desktop:~/Desktop$ chmod 755 et-linux-2.60.x86.run
peter@peter-desktop:~/Desktop$ sudo ./et-linux-2.60.x86.run
Password:
run-detectors: unable to find an interpreter for ./et-linux-2.60.x86.run 

-Peter

---

