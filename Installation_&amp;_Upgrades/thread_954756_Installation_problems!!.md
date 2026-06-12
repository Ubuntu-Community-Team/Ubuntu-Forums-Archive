---
title: "Installation problems!!"
date: 2008-10-21
forum: Installation &amp; Upgrades
---

### Post by shanks129 on 2008-10-21
Hey guys i recently just moved over to windows ubuntu fairly painlessly, now my only problem is installing .gz files or .c open source files. I have followed countless tutorials on how to do it in terminal, using the tar -xzvf method and all i get is : 

tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

its driving me crazy and the ./configure thing doesn't seem to work for me either!! :( if any one can help and tell me what i am doing wrong it would be greatly appreciated. thanks. :)

---

### Post by Pumalite on 2008-10-21
sudo apt-get install build-essential
Then try again. Let me know how it goes

---

### Post by shanks129 on 2008-10-21
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

thomas@thomas-desktop:~$ tar xzvf bwpropset-0.1.tar.gz
tar: bwpropset-0.1.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors


sorry dude did not help at all. :( can you see if i am doing anything wrong there? Cheers.

---

### Post by darthshak on 2008-10-21
Try reinstalling tar.
sudo apt-get install --reinstall tar

If it complains about broken dependencies,
sudo apt-get install -f

---

### Post by Pumalite on 2008-10-21
Run:
sudo apt-get -f intall
sudo apt-get update
sudo apt-get dist-upgrade
Post outputs here

---

### Post by shanks129 on 2008-10-21
that didn't help either dude, thanks anyways. Its always the same error. the file im trying to extract and install is bwpropset-0.1.tar.gz so can you guys make sure i am typing it correctly and putting the appropriate commands in at the right time?? Because nothing seems to work and i haven't seen anyone is with this problem before :S. Is there anyway to make these files executable?

---

### Post by shanks129 on 2008-10-21
thomas@thomas-desktop:~$ sudo apt-get update
Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [189B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_GB
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty Release.gpg [191B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Translation-en_GB
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates Release.gpg [189B]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Sources
Fetched 3B in 0s (4B/s)
Reading package lists... Done
thomas@thomas-desktop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
thomas@thomas-desktop:~$

---

### Post by Pumalite on 2008-10-21
The culprit is your package then. Download a new one.

---

### Post by shanks129 on 2008-10-21
errrmmm, sorry at risk of sounding like and idiot. How do i do that? and what is the package? :S

---

### Post by Pumalite on 2008-10-21
'bwpropset-0.1.tar.gz'
If you have it in your Desktop; you have to move to it first:
cd ~/Desktop

---

### Post by shanks129 on 2008-10-21
Yeah i have it on my desktop. How do i move it and where too?? Im really sorry dude but i really don't understand. If you could tell me how to do it exactly i would be greatly appreciative. :)

---

### Post by Pumalite on 2008-10-21
Go to the Terminal; type:
cd ~/Desktop
Press 'Enter'
Now:
tar xvzf bwpropset-0.1.tar.gz
Press 'Enter'
Now:
cd bwpropset
Now:
./configure
Tell me what happens

---

### Post by shanks129 on 2008-10-22
thomas@thomas-desktop:~/Desktop$ 
thomas@thomas-desktop:~/Desktop$ tar xvzf bwpropset-0.1.tar.gz
bwpropset-0.1/
bwpropset-0.1/Makefile
bwpropset-0.1/bwpropset.c
thomas@thomas-desktop:~/Desktop$ cd bwpropset
bash: cd: bwpropset: No such file or directory
thomas@thomas-desktop:~/Desktop$ ./configure
bash: ./configure: No such file or directory
thomas@thomas-desktop:~/Desktop$ 

there you go mate that's the whole log there, it seened to get a little further but then whem I tried the  cd bwpropset it didn't work :(. :S

---

### Post by Pumalite on 2008-10-22
Sorry, my mistake:
cd bwpropset-0.1
./configure

---

### Post by shanks129 on 2008-10-22
thomas@thomas-desktop:~/bwpropset-0.1$ ./configure
bash: ./configure: No such file or directory

:( ahhh this is driving me crazy!! lol

---

### Post by shanks129 on 2008-10-22
thomas@thomas-desktop:~/bwpropset-0.1$ make
cc -g -Wall -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wredundant-decls   -c -o bwpropset.o bwpropset.c
bwpropset.c:18:22: error: X11/Xlib.h: No such file or directory
bwpropset.c:19:23: error: X11/Xutil.h: No such file or directory
bwpropset.c:20:23: error: X11/Xatom.h: No such file or directory
bwpropset.c:21:24: error: X11/Xproto.h: No such file or directory
bwpropset.c:22:28: error: X11/cursorfont.h: No such file or directory
bwpropset.c:24:34: error: X11/extensions/shape.h: No such file or directory
bwpropset.c:25:36: error: X11/extensions/Xrender.h: No such file or directory
bwpropset.c:132: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘selectWindow’
bwpropset.c:175: error: expected ‘)’ before ‘*’ token
bwpropset.c:198: error: expected ‘)’ before ‘*’ token
bwpropset.c:216: error: expected ‘)’ before ‘*’ token
bwpropset.c:294: error: expected ‘)’ before ‘*’ token
bwpropset.c:322: error: expected ‘)’ before ‘*’ token
bwpropset.c:347: error: expected ‘)’ before ‘*’ token
bwpropset.c:363: error: expected ‘)’ before ‘*’ token
bwpropset.c:372: error: expected ‘)’ before ‘*’ token
bwpropset.c:379: error: expected ‘)’ before ‘*’ token
bwpropset.c: In function ‘main’:
bwpropset.c:410: error: ‘Display’ undeclared (first use in this function)
bwpropset.c:410: error: (Each undeclared identifier is reported only once
bwpropset.c:410: error: for each function it appears in.)
bwpropset.c:410: error: ‘dpy’ undeclared (first use in this function)
bwpropset.c:412: error: ‘Window’ undeclared (first use in this function)
bwpropset.c:412: error: expected ‘;’ before ‘win’
bwpropset.c:480: warning: implicit declaration of function ‘XParseGeometry’
bwpropset.c:483: error: ‘XValue’ undeclared (first use in this function)
bwpropset.c:483: error: ‘YValue’ undeclared (first use in this function)
bwpropset.c:484: error: ‘WidthValue’ undeclared (first use in this function)
bwpropset.c:484: error: ‘HeightValue’ undeclared (first use in this function)
bwpropset.c:495: error: ‘win’ undeclared (first use in this function)
bwpropset.c:509: warning: implicit declaration of function ‘XOpenDisplay’
bwpropset.c:510: warning: implicit declaration of function ‘XDefaultScreen’
bwpropset.c:513: warning: implicit declaration of function ‘selectWindow’
bwpropset.c:521: warning: implicit declaration of function ‘XGetGeometry’
bwpropset.c:521: error: expected expression before ‘)’ token
bwpropset.c:519: warning: unused variable ‘dummy’
bwpropset.c:528: warning: implicit declaration of function ‘initializeFullscreen’
bwpropset.c:529: warning: implicit declaration of function ‘sendWmStateMessages’
bwpropset.c:530: warning: implicit declaration of function ‘sendWmLevelMessages’
bwpropset.c:533: warning: implicit declaration of function ‘setNoFocus’
bwpropset.c:535: warning: implicit declaration of function ‘setNoInput’
bwpropset.c:537: warning: implicit declaration of function ‘setNoBorder’
bwpropset.c:539: warning: implicit declaration of function ‘XSync’
bwpropset.c:539: error: ‘False’ undeclared (first use in this function)
bwpropset.c:542: warning: implicit declaration of function ‘moveWindow’
bwpropset.c:544: warning: implicit declaration of function ‘resizeWindow’
bwpropset.c:547: warning: implicit declaration of function ‘XCloseDisplay’
make: *** [bwpropset.o] Error 1

thats what i get if i use make, ah this is so messed up. If i use the command ls it tells me i have 2 files one is bwpropset.c and the other is makefile. Does that help?

---

### Post by Pumalite on 2008-10-22
Look for the README file and seek instructions

---

### Post by shanks129 on 2008-10-22
there is no read me file!! sorry.

---

### Post by Pumalite on 2008-10-22
Go back to the site where you downloaded the file from and read the instructions on how to install it.

---

### Post by shanks129 on 2008-10-23
got it all sorted man, the website had no instructions that was the problem!!. but thank you very much for all your help, cheers. Unfortunatly now i'm having a nightmare running compiz and have had no help from anyone in trying to fix it. So i may just re-install linux instead of trying to find out what is wrong!! :(

---

