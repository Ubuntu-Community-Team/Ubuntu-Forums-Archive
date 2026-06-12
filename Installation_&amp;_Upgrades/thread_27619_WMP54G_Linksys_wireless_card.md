---
title: "WMP54G Linksys wireless card"
date: 2005-04-16
forum: Installation &amp; Upgrades
---

### Post by pterandon on 2005-04-16
Anyone have any luck?

I tried this path, 

[http://www.linuxquestions.org/questions/answers.php?action=viewarticle&artid=328](http://www.linuxquestions.org/questions/answers.php?action=viewarticle&artid=328)

using a ndiswrapper-0.11 I found at sourceforge.  I am unable to find an application that is literally ndiswrapper which would allow me to complete this instruction:
```

ndiswrapper -i /mnt/cdrom/Drivers/wmpci54g.inf 
```

Or can anyone point me to another  place with instructions that might work?

Thanks.

---

### Post by accuser on 2005-04-17
The guide makes some assumptions:
[list=a]
[*]That you are logged in as root
[*]That you have the original windows driver on a cd in the first cdrom drive
[*]That the windows driver can be found in a particular directory on the cd
[/list] 
If you are not logged in as root - I am assuming that you are running as the main user - you will need to prefix some commands with 'sudo':
```

$ tar -zxvf ndiswrapper-0.11.tar.gz 
$ cd ndiswrapper-0.11 
$ make
$ sudo make install
$ mount /media/cdrom # <-- assumes that the cd is in the first cdrom drive and not already mounted
$ sudo ndiswrapper -i /media/cdrom/Drivers/wmpci54g.inf
$ sudo modprobe ndiswrapper # <-- will need to edit configuration (see below)
$ sudo ndiswrapper -m

```
Before the modprobe command, you will need to edit a couple of files. The first is found under /etc/ndiswrapper. Look for a symbolic link with a file name with four hex digits, a colon, four hex digits, followed by .conf. For example 1A37:101E.conf. Open this file and find the line:
```

RadioState|1

```
and change it to
```

RadioState|0

```
Save the file.

---

### Post by pterandon on 2005-04-18
Thanks for the help, but I see that when I ls the ndiswrapper-0.11 directory, I do not see a program labelled ndiswrapper.   I do see something called ndiswrapper.8, perhaps I should try that....

---

