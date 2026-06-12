---
title: "Printer Driver"
date: 2010-03-01
forum: Installation &amp; Upgrades
---

### Post by rubenlane on 2010-03-01
Hey everyone, 

First off thanks for any help anyone can give and second sorry if this question has been answered before.  I've been searching for awhile.

So I have a printer driver I'm trying to install.  The instructions that come with it seem pretty straight forward but I'm having trouble accessing the file in the terminal.

Right now I have it on my desktop.  I've tried typing every combination of /root/file/file I can think of and all I ever get is "no such file or directory"  I feel like either I just don't know the correct file path or I'm doing something wrong.

So I guess my question is 2 fold can anyone tell me either how to discover the full file path of something on my computer starting with /root or am I doing something wrong all together?

Thanks again everyone!

---

### Post by cjhabs on 2010-03-01
The path to your desktop is:
~/Desktop
To find a file called myfile.txt:
find / -name myfile.txt -print

---

### Post by khelben1979 on 2010-03-01
I think it would be easier for you to just use [Synaptic Package Manager]("http://en.wikipedia.org/wiki/Synaptic_package_manager") and search for a suitable printer driver and install it from there. 

Have you tried this?

---

### Post by hhlp on 2010-03-01
give us more information ?

what kind of printer do you have?

where do you find the drivers?

what are you trying to do?

---

### Post by rubenlane on 2010-03-01
The synaptic package manager worked perfectly.

Thanks, I'm just really new to linux so this is a learning experience for sure.

---

### Post by blur xc on 2010-03-01
[http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php)

Check that link out.  You don't have to be a command line guru to run Linux- but if you know some of the simple things, how to navigate directories, copy, move, delete, rename files, etc., it'll make your life a lot easier in the long run.

Glad to hear you got your printer working...  good luck and welcome to the club.

BM

---

### Post by khelben1979 on 2010-03-02
Good that you got it working. I think it's important for new users that things don't get any more complicated than it haveto.

---

