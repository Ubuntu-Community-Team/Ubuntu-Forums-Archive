---
title: "install of .bin files"
date: 2007-10-08
forum: Installation &amp; Upgrades
---

### Post by Caitilin on 2007-10-08
hi all,

i'm an idiot beginner on ubuntu, so please bear that in mind. 

I bought a modem from irish broadband (ripwave) today, as i was told by support it was supported. 

Low and behold, I  not only have a little signal, but when I go to install I have a file, NavDiag_linux.bin

So here I am happily trying to run it. 

I've tried: double clicking it (yeah, windows background, how did you guess?)
in terminal: 
under my own userid: 
sudo apt-get install 'media/cdrom0/NavDiag_linux.bin' 

This results in: 
reading package list done
building dependency tree done
reading state in<something i can't read my handwriting> 
e: couldn't find package

I then tried logging on as root user in the terminal and running it again and it gave the same results. 

Neither of my books give any tips (i mean, its not that obscure...is it?)
and i'm hijacking a neighbours connection for this. 

Can anyone explain to me what I need to do?
I"m on feisty fawn, the modem is a ripwave modem, but it hasn't even got to using it. 
the file is listed as NavDiag_linux.bin on the cdrom, the e drive. 

help?:confused:

---

### Post by Prefader on 2007-10-08
try the following in a terminal:

```
sh /media/cdrom0/NavDiag_linux.bin
```

and if that doesn't work, or it complains about needing root access, use:

```
sudo sh /media/cdrom0/NavDiag_linux.bin
```

Of course, the usual disclaimers about sudo apply - you need to know what this program does for a living before you go running it as root.  However, if it's supplied by your ISP, odds are it's safe.  Do be careful, though.

---

### Post by Caitilin on 2007-10-08
Thank you! 

I'll give it a try and let you know.

---

### Post by Caitilin on 2007-10-08
ok, well that started running, which is something, and then failed. 

on both versions: 
preparing to install
extracting the JRE from installer archive
unpacking the JRE
extracting the installation resources from teh installer archive
configuring the installer for this system environment
dirname: error while loading shared libraries: libc.so.6 L cannot open shared fobject file: no such file or object. 
/bin/ls : error while loading shared libraries: libc.so.6 L cannot open shared fobject file: no such file or object.
basename : error while loading shared libraries: libc.so.6 L cannot open shared fobject file: no such file or object.
dirname : error while loading shared libraries: libc.so.6 L cannot open shared fobject file: no such file or object.
basename : error while loading shared libraries: libc.so.6 L cannot open shared fobject file: no such file or object.
hostname : error while loading shared libraries: libc.so.6 L cannot open shared fobject file: no such file or object.

launching installer
rm : error while loading shared libraries: libc.so.6 L cannot open shared fobject file: no such file or object.
rm : error while loading shared libraries: libc.so.6 L cannot open shared fobject file: no such file or object.


that's it...any thoughts?

---

### Post by Prefader on 2007-10-08
first, try:
```
sudo apt-get install libc6
```
and then try running the other command again.  If that doesn't work, see if the /lib directory does indeed have libc.so.6 in it.  Post back if it's not there, and I'll be happy to pound my fists in frustration with you, while we defer to the more experienced members of the forum for further assistance.  ;)

---

### Post by jfinkels on 2007-10-08
And if installing libc6 doesn't work, try installing the build-essential package:```
sudo aptitude install build-essential
``` which includes a bunch of C libraries and such. As for installing software in general, read the first link in my signature.

---

### Post by karik on 2007-10-08
When you try to install *.bin files, you just need to 
1) run the console Application->Accessories->Terminal. 
2)Navigate to the folder where your BIN file is located using *cd* command. 
3)And then type *sudo ./filename.BIN*. When the system will ask your password, just enter it and the application will be installed.

---

### Post by jfinkels on 2007-10-08
> **karik said:**
> 
3)And then type *sudo ./filename.BIN*. When the system will ask your password, just enter it and the application will be installed.
You don't necessarily need to use 'sudo' to run the executable file. You will only need to use 'sudo' if the installation is system-wide, or requires root privileges for some other reason.

---

### Post by Caitilin on 2007-10-09
ok, so far...

running it normally and under sudo does not work. 

installed libc6, and it told me I already had the newest version. tried installing again, under user and under sudo. installed build-essential, or tried to and it gave me the following. 

Writing extended state information... Done
Get:1 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) feisty/main g++ 4:4.1.2-1ubuntu1 [1428B]
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main linux-libc-dev 2.6.20-16.31
  404 Not Found
Get:2 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) feisty/main dpkg-dev 1.13.24ubuntu6 [147kB]
Get:3 [http://ie.archive.ubuntu.com](http://ie.archive.ubuntu.com) feisty/main build-essential 11.3 [6974B]
Fetched 155kB in 3s (48.3kB/s)    
Selecting previously deselected package dpkg-dev.
(Reading database ... 107425 files and directories currently installed.)
Unpacking dpkg-dev (from .../dpkg-dev_1.13.24ubuntu6_all.deb) ...
Setting up dpkg-dev (1.13.24ubuntu6) ...
E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-libc-dev_2.6.20-16.31_i386.deb:](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-libc-dev_2.6.20-16.31_i386.deb:) 404 Not Found


am i jumping from the frying pan into the fire?

---

### Post by jfinkels on 2007-10-09
> **Caitilin said:**
> 
am i jumping from the frying pan into the fire?

Yes, so let's not worry about that for now :D

What we need to do is see if you have a libc.so.6 file. To do this, we can use the 'locate' program.

First we need to make sure that all the files on your system are indexed (i.e. searchable). Type the following in the terminal:```
sudo slocate -u
```Enter your password at the prompt. This creates a database of all the files in your system.

Once slocate is done creating its database (your hard drive stops spinning and your command prompt returns), we can use it to search for libc.so. Type the following in the terminal:```
slocate libc.so
``` Also feel free to try:```
slocate libc.so.6
``` or ```
slocate libc
```. If you get any results, let's say for example that the first command shows you that there is a libc.so file in /usr/lib/, you can find out more information by doing a command like this:```
ls -l /usr/lib
```or ```
ls -l /usr/lib/libc.*
```

---

### Post by Caitilin on 2007-10-09
Ok, did those...

mneme@mnemosyne:~$ slocate libc.so
/lib/libc.so.6
/lib/tls/i686/cmov/libc.so.6
mneme@mnemosyne:~$ slocate libc.so.6
/lib/libc.so.6
/lib/tls/i686/cmov/libc.so.6


The last command gave me a whole plethora i'm not cutting and pasting to save sanity. 

So i'm guessing I do have it. It did tell me it had the most up to date version though, 7 files not updated, when i tried to update it. That's why I can't figure out why the silly installer can't find it! :confused::confused:

---

### Post by Caitilin on 2007-10-09
ls -l /usr/lib gave me another plethora of information i have no  clue how to interpet..want to see?

---

### Post by Kephron on 2007-10-09
> **Caitilin said:**
> hi all,

i'm an idiot beginner on ubuntu, so please bear that in mind. 

I bought a modem from irish broadband (ripwave) today, as i was told by support it was supported. 

Low and behold, I  not only have a little signal, but when I go to install I have a file, NavDiag_linux.bin




Caitlin, I can't help you with the install of the bin file as I am no Linux expert, even though I do run Ubuntu :-)  I do, however, work for IBB and I can tell you that you don't need the bin file to run the Ripwave.  All it is is a diagnostic's file.  The Ripwave is a standard Ethernet bridging device that will work on anything that has Ethernet.  You don't need to install any drivers in the same way that you don't need to install drivers if you connect to a router or switch.    It is not the end of the world if it doesn't run or install.  AFAIK it is a fairly new package.  The signal is a function of where you have the modem.  Unfortunately, unlike the more advanced mobile phone networks (read older) we don't have complete 100% coverage everywhere.  My suggestion is to move it around until you can get the best signal.  Keep it away from large EMF's like CRT monitors, TV's, coiled cables or your PC :-).  By away I mean the length of the patch cable is fine.  Try getting the Ripwave up as high as possible and either as close to the window as possible or in the back of the room opposite the window.  If you want to PM with your real name or contact details I can contact you from work and assist you in getting it up and running as best as possible.

 ciao, K,

AKA, Pat Maher
IBB Technical Trainer :-)

Of course this is unofficial and I am not acting, currently, on behalf of Irish Broadband in any way (standard disclaimer)

---

### Post by jfinkels on 2007-10-09
> **Caitilin said:**
> 
/lib/libc.so.6
Well, I guess I can't really help you beyond this, since we don't know what the executable file is doing. If we had the source code, we could figure it out and direct it to look for libc6 at /lib/libc.so.6, but the way it stands, we can't really do anything else.
> **Kephron said:**
> Caitlin, I can't help you with the install of the bin file as I am no Linux expert, even though I do run Ubuntu :-)  I do, however, work for IBB and I can tell you that you don't need the bin file to run the Ripwave.  All it is is a diagnostic's file.  The Ripwave is a standard Ethernet bridging device that will work on anything that has Ethernet.

Lucky!!

I don't really know what Ripwave is, but I bet Kephron here can help you!

---

### Post by jackheh on 2007-10-13
Hi, 

I have a similar problem with trying to install JDK 1.5.

I've tried all the various options listed in this thread, but none of them work.

What I got in the terminal
> jack@LINUX:~$ sh /home/jack/Desktop/jdk-1_5_0_13-nb-5_5_1-linux-ml.bin

          Initializing InstallShield Wizard........

          The launcher "/home/jack/Desktop/jdk-1_5_0_13-nb-5_5_1-linux-ml.bin" 
          is not executable for the current user.  Please give 
          execute permission for the current user before 
          attempting to launch the installer.

jack@LINUX:~$ sudo sh /home/jack/Desktop/jdk-1_5_0_13-nb-5_5_1-linux-ml.bin
Password:

          Initializing InstallShield Wizard........

          The launcher "/home/jack/Desktop/jdk-1_5_0_13-nb-5_5_1-linux-ml.bin" 
          is not executable for the current user.  Please give 
          execute permission for the current user before 
          attempting to launch the installer.

jack@LINUX:~$ sudo apt-get install /home/jack/Desktop/jdk-1_5_0_13-nb-5_5_1-linux-ml.bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package 

jack@LINUX:~$ cd /home/jack/Desktop
jack@LINUX:~/Desktop$ dir
jdk-1_5_0_13-nb-5_5_1-linux-ml.bin  untitled\ folder
jack@LINUX:~/Desktop$ ./jdk-1_5_0_13-nb-5_5_1-linux-ml.bin
bash: ./jdk-1_5_0_13-nb-5_5_1-linux-ml.bin: Permission denied
jack@LINUX:~/Desktop$ sudo ./jdk-1_5_0_13-nb-5_5_1-linux-ml.bin
sudo: ./jdk-1_5_0_13-nb-5_5_1-linux-ml.bin: command not found
jack@LINUX:~/Desktop$ 

Oh wait... never mind. I just thought of something... I'm new to Linux, don't blame me for not immediately thinking of right-clicking and changing the permissions of the file...

---

### Post by jfinkels on 2007-10-14
You probably shouldn't be installing the JDK this way, I will tell you why at the bottom of this post.

You can view the permissions of a file by typing the following in the terminal:```
ls -l /home/jack/Desktop/jdk-1_5_0_13-nb-5_5_1-linux-ml.bin
```
You will get an output that looks like this:```
-rw-r--r--  1 jeff jeff         0 2007-10-01 18:53 /home/jack/Desktop/jdk-1_5_0_13-nb-5_5_1-linux-ml.bin
```
The very first part of this line shows the permissions set on the file. The first line indicates that this is a regular file, and not a directory or a link to another file. The next three characters, in this case 'rw-' indicate that the owner of the file has read and write permissions on this file. The next three, 'r--' indicate that the group to which this file belongs has read permissions. The next three, 'r--' indicate that all other users have read permissions. The 'jeff jeff' part just means that the file belongs to user 'jeff' and to group 'jeff'. To make a file executable, type the following in the terminal:```
chmod +x /home/jack/Desktop/jdk-1_5_0_13-nb-5_5_1-linux-ml.bin
```This will change the mode of the file (the permissions) so that it is executable to the owner, the group, and all other users. If you don't have permissions to change the mode of this file, you can do this:```
sudo chmod +x /home/jack/Desktop/jdk-1_5_0_13-nb-5_5_1-linux-ml.bin
```which just does the same thing, but as the super user (aka root user). The super user has rights to do anything.

To run a file simply change to its directory and type:```
./jdk-1_5_0_13-nb-5_5_1-linux-ml.bin
```

Or if you don't own it and you want to run it as root, type:```
sudo ./jdk-1_5_0_13-nb-5_5_1-linux-ml.bin
```

You cannot type:```
sudo aptitude install /home/jack/Desktop/jdk-1_5_0_13-nb-5_5_1-linux-ml.bin
```Aptitude/apt-get is a system that downloads packages from specific repositories (specified in the file /etc/apt/sources.list). You can search for packages using:```
apt-cache search *whatever*
```or look online at [http://packages.ubuntu.com/](http://packages.ubuntu.com/) .

To install software, you should always check in the repositories first by searching around. To install JDK 1.5, type the following in the terminal:```
sudo aptitude install sun-java5-jdk
```

Read more about installing software in my signature.

---

