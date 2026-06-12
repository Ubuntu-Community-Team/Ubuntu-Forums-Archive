---
title: "installing .deb files"
date: 2005-08-03
forum: Installation &amp; Upgrades
---

### Post by floyd27 on 2005-08-03
Hi.
i found the way to do this in one of the guides however it does not work.
I have downloaded neorolinux and it on my desktop
Do i have to extract it ?
i didnt and did the command to open the .deb file but i said it didnt exist? do i have it in the wrong place?
thanx for any advice on this

---

### Post by Tamir on 2005-08-03
[QUOTE=floyd27]Hi.
i found the way to do this in one of the guides however it does not work.
I have downloaded neorolinux and it on my desktop
Do i have to extract it ?
i didnt and did the command to open the .deb file but i said it didnt exist? do i have it in the wrong place?
thanx for any advice on this[/QUOTE]
 Do you mean this way:
```
dpkg -i file.deb
```
?

---

### Post by floyd27 on 2005-08-03
yes thats the one.
but i replced "flie" with the file name (unextracted)?
i dont think it was right cause it didnt work...

---

### Post by arunsub on 2005-08-03
Open the terminal and go to the desktop folder and issue the dpkg command else copy/cut the file and paste it in  your home folder. login to the terminal, type dpkg -i partial filename and press tab. it should add the full file name.

---

### Post by Xterminator on 2005-08-03
in this point apt-DEB is inferior to apt-RPM(conectiva) 
in apt-RPM  i´m install local packages simple..

apt-get install somepackage/somelocation.rpm

and the depends are solved...
see the article.
[http://lwn.net/Articles/60650/](http://lwn.net/Articles/60650/)

install packages by configuration files or solibs...
in my old distro

---

### Post by cutOff on 2005-08-03
[QUOTE=floyd27]yes thats the one.
but i replced "flie" with the file name (unextracted)?
i dont think it was right cause it didnt work...[/QUOTE]
What's the error?  paste it please.

---

### Post by floyd27 on 2005-08-03
still didnt work yet...?
i dont know if im suppost to be root or not so i did sudo and my root password?
is there a differecne between the console and the terminal?

error

roderick@ubuntu:~$ su
Password:
root@ubuntu:/home/roderick # cd /home
root@ubuntu:/home # sudo dpkg -i nerolinux-2.0.0.2-x86.deb
dpkg: error processing nerolinux-2.0.0.2-x86.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 nerolinux-2.0.0.2-x86.deb
root@ubuntu:/home #

---

### Post by kleeman on 2005-08-03
cd ~roderick/Desktop
sudo dpkg -i nerolinux-2.0.0.2-x86.deb

---

### Post by floyd27 on 2005-08-03
that seems to have done something ..
where can i find it to see if it worked??
tjanx for the help btw..:)

roderick@ubuntu:~$ cd ~roderick/Desktop
roderick@ubuntu:~/Desktop$ sudo dpkg -i nerolinux-2.0.0.2-x86.deb
Password:
Selecting previously deselected package nerolinux.
(Reading database ... 82261 files and directories currently installed.)
Unpacking nerolinux (from nerolinux-2.0.0.2-x86.deb) ...
Setting up nerolinux (2.0.0.2-1) ...
Creating /usr/share/nero/desktop/NeroLINUX.desktop... done!

Operating System: Debian GNU/Linux version 3.1

Creating /usr/share/applications/NeroLINUX.desktop... done!

roderick@ubuntu:~/Desktop$

---

### Post by floyd27 on 2005-08-03
never mind, i found it..
works great. im gona see if my wondows serial will work for it , fingers crossed..
thanx again....

---

### Post by cutOff on 2005-08-03
[QUOTE=floyd27]never mind, i found it..
works great. im gona see if my wondows serial will work for it , fingers crossed..
thanx again....[/QUOTE]
mpfff.... jua**

---

