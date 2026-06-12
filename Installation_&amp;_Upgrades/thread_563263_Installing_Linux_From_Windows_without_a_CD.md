---
title: "Installing Linux From Windows without a CD"
date: 2007-09-29
forum: Installation &amp; Upgrades
---

### Post by sanjayc on 2007-09-29
Hey guys I have been following the guide posted on the ubuntu community about the method in which we can install linux ubuntu through windows without the help of a CD. I have been trying to install the latest version of luinux and I have a problem when i try to append the boot.ini cause it says access is denied. I think it's the only thing that's stopping me from using Ubuntu right now and would like to know a solution for it. I am the computer administrator and also I have followed the instructions accordingly on the webpage [https://help.ubuntu.com/community/Installation/FromWindows]("https://help.ubuntu.com/community/Installation/FromWindows")

---

### Post by Pumalite on 2007-09-29
There is also network install:

[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

And:

[http://hugi.to/blog/archive/2006/12/...ll-via-windows](http://hugi.to/blog/archive/2006/12/...ll-via-windows)
[http://ubuntuforums.org/showthread.php?t=332343](http://ubuntuforums.org/showthread.php?t=332343)

---

### Post by logos34 on 2007-09-29
> **sanjayc said:**
> ...I have a problem when i try to append the boot.ini cause it says access is denied. I think it's the only thing that's stopping me from using Ubuntu right now and would like to know a solution for it.

You could try this:

Go to **Start>Run**

type **CMD** in run box, hit enter/ok

In the DOS window that pops up, at the prompt type:
[B]
cd\[/B]

hit enter
[B]
attrib -s -h -r boot.ini[/B]

hit enter

Hopefully this will open the file and allow you to edit it

---

### Post by jbuc89 on 2007-09-30
> attrib -s -h -r boot.ini

hit enter

Hopefully this will open the file and allow you to edit it

The attrib command just changes the file file attributes as follows:

-s remove system attribute
-h remove hidden attribute
-r remove read-only attribute

You will still need to edit the file either using the edit command from the command prompt or notepad from Windows.  Hope this helps.

---

### Post by logos34 on 2007-09-30
> **jbuc89 said:**
> You will still need to edit the file either using the edit command from the command prompt or notepad from Windows.

right, my error, you still need to open the file...look in C: directory or type 'C: \boot.ini' in windows explorer address bar

---

