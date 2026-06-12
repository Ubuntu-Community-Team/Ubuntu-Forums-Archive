---
title: "Installing realplayer, help! newbi"
date: 2007-11-30
forum: Installation &amp; Upgrades
---

### Post by Amendment44 on 2007-11-30
Hey Im just getting started with linux and I am loving it expect one thing. I am trying to get Real player to install so i can watch streamed tv shows. 

I have unlocked my main universal directory to allow 3rd party programs.

When i try to run the downloaded file

realplay-10.0.6.776-linux-2.2-libc6-gcc32-i586.bin

I get the following error

"realplay-...inux-2.2-libc6-gcc32-i586.bin" cannot be opened :No application suitable for automatic installation is available for handling this kind of file.

its location is /home/matt/Desktop

Then i looked it up and found the following command line for the install and tried that.

matt@matt-laptop:~$ sudo apt-get install realplay

And i get the following error.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package realplay

please help!

---

### Post by Pumalite on 2007-11-30
sudo apt-get install build-essential

---

### Post by Amendment44 on 2007-11-30
cool, alright i did that. and i get the following

matt@matt-laptop:~$ sudo apt-get install build-essential
[sudo] password for matt:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev patch
Suggested packages:
  debian-keyring g++-multilib g++-4.1-multilib gcc-4.1-doc glibc-doc
  manpages-dev libstdc++6-4.1-doc diff-doc
The following NEW packages will be installed:
  build-essential dpkg-dev g++ g++-4.1 libc6-dev libstdc++6-4.1-dev
  linux-libc-dev patch
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 3287kB/7934kB of archives.
After unpacking 31.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media change: please insert the disc labeled
 'Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)'
in the drive '/cdrom/' and press enter

I dont have the original cd... Do i need to burn a new one? what am i doing anyway?

---

### Post by Pumalite on 2007-11-30
Go to System>Administration>Software Sources and tick off the CD as source.

---

### Post by Amendment44 on 2007-11-30
ok, I got it build essential

However i am still getting the same errors.

matt@matt-laptop:~$ sudo apt-get install realplay
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package realplay
matt@matt-laptop:~$ 

why cant it find it? this is so frustrating

---

### Post by Pumalite on 2007-11-30
If you downloaded it; where did you put it? You can do a file search.

---

### Post by Amendment44 on 2007-11-30
its right on the desktop

location it says when i right click

/home/matt/Desktop

---

### Post by Pumalite on 2007-11-30
At the Terminal:
cd ~/Desktop

---

### Post by Amendment44 on 2007-11-30
i changed the directory to desktop should of thought to do that before, dur

However I am getting the same error

matt@matt-laptop:~/Desktop$ sudo apt-get install RealPlayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package RealPlayer
matt@matt-laptop:~/Desktop$ 

I am also tried having the exact filename...

matt@matt-laptop:~/Desktop$ sudo apt-get install RealPlayer10GOLD.bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package RealPlayer10GOLD.bin
matt@matt-laptop:~/Desktop$ 

I missing my tv shows, need realplayer!

---

### Post by Pumalite on 2007-11-30
'
realplay-10.0.6.776-linux-2.2-libc6-gcc32-i586.bin'

Right click on the file and make it 'executable'
Then double click on it.

---

### Post by Amendment44 on 2007-11-30
how?

I right clicked on it, and edited the tag to .exe

saved it and tryed  the follow two ways

matt@matt-laptop:~/Desktop$ sudo apt-get install RealPlayer10GOLD.exe
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package RealPlayer10GOLD.exe


and 

matt@matt-laptop:~/Desktop$ sudo apt-get install RealPlayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package RealPlayer

i say a simpler post and they said the used a program called
Automatix?

---

### Post by Pumalite on 2007-11-30
Automatix:

[http://mjg59.livejournal.com/77440.html](http://mjg59.livejournal.com/77440.html)
[http://ubuntuforums.org/announcement.php?f=13/](http://ubuntuforums.org/announcement.php?f=13/)
[http://ubuntuforums.org/showthread.php?t=519872](http://ubuntuforums.org/showthread.php?t=519872)
[http://ubuntuforums.org/forumdisplay.php?f=302](http://ubuntuforums.org/forumdisplay.php?f=302)

BTW; I said to double click ON the file.

---

### Post by Amendment44 on 2007-11-30
when I double click i get the following error.

"RealPlayer10GOLD.exe" cannot be opened

No application suitable for automatic installation is available for handling this kind of file.

I'm reading about Automatix 

and it says "automatic is, in itself, a poor quality package which fails to
conform to Debian or Ubuntu policy."

Maybe i should keep trying without it?

---

### Post by Pumalite on 2007-11-30
If it's an .exe; it's not for Linux.

---

### Post by Amendment44 on 2007-11-30
ohh i just typed that in under its name when you said make it an executable.

I delted and downloaded a new one and got the error.

 "RealPlayer10GOLD.bin" cannot be opened

No application suitable for automatic installation is available for handling this kind of file.

It is made for linux, however it does not say ubuntu specially.

link.

[http://www.real.com/linux](http://www.real.com/linux)

---

### Post by PmDematagoda on 2007-11-30
From my personal experience I would also say that Automatix is not a very good application to use. And like Pumalite said, you cannot run a .exe on Linux natively, though you could try running it through Wine but that is another story.

I believe you can download RealPlayer for Linux from [here]("https://player.helixcommunity.org/2005/downloads/"), Real's own download page seems to be messed up.

---

### Post by Amendment44 on 2007-11-30
I went to that link and double clicking gets me the error:

"realplay-...inux-2.2-libc6-gcc32-i586.bin" cannot be opened

No application suitable for automatic installation is available for handling this kind of file.

and the line in terminal give me this.

matt@matt-laptop:~$ sudo apt-get install realplay-10.0.9.809-linux-2.2-libc6-gcc32-i586.bin
[sudo] password for matt:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package realplay-10.0.9.809-linux-2.2-libc6-gcc32-i586.bin

Ok, I am not going to install automatix. I am working around using it and down the road i think it will cause me more problems then good.

VLC is installed correctly on this computer.

How can i make it the default program

When i try to start up the link it says Xine and has a green footprint.

---

### Post by PmDematagoda on 2007-11-30
I just installed Real Player 10 and here is how I did it:-

1) Download the file from the link I gave.

2) Make a new folder in my Home folder called Real and copy the downloaded file there.

3) Open up the terminal and navigated to the Real directory using:-

```
cd Real
```

4) Make the .bin file executable using:-

```
chmod +x nameofbin.bin
```

5) Execute the .bin file using:-

```
./nameofbin.bin
```

6) After installation navigate to the directory where Real Player was installed and execute:-
```

./realplay
```

And Real Player will start up.

---

### Post by acl123 on 2007-12-01
Hi, I'm trying to run realplayer.
The link from the realplayer site was broken so I downloaded it from here: [https://player.helixcommunity.org/2005/downloads/](https://player.helixcommunity.org/2005/downloads/)

It seems to install ok but I can't work out how to run it. The command "realplay" cannot be found. If I go into the program's directory and execute realplay.bin or the realplay script I get a segmentation fault.

Do you know what I should do?

---

### Post by marco_polo99 on 2007-12-02
> **PmDematagoda said:**
> I just installed Real Player 10 and here is how I did it:-

1) Download the file from the link I gave.

2) Make a new folder in my Home folder called Real and copy the downloaded file there.

3) Open up the terminal and navigated to the Real directory using:-

```
cd Real
```

4) Make the .bin file executable using:-

```
chmod +x nameofbin.bin
```

5) Execute the .bin file using:-

```
./nameofbin.bin
```

6) After installation navigate to the directory where Real Player was installed and execute:-
```

./realplay
```

And Real Player will start up.

Hi--tried this and I get 
mark@mark-laptop:/home/Real$ sudo chmod +x realplay-10.0.9.809-linux-2.2-libc6-gcc32-i586.bin
mark@mark-laptop:/home/Real$ ./realplay-10.0.9.809-linux-2.2-libc6-gcc32-i586.bin
Extracting files for RealPlayer installation...Segmentation fault (core dumped)
mark@mark-laptop:/home/Real$

---

### Post by Pumalite on 2007-12-02
I just installed it as a test. Downloaded from here:
[https://player.helixcommunity.org/2005/downloads/](https://player.helixcommunity.org/2005/downloads/)
Right click>Permissions>Executable
Double clicked on the file which had transformed in a blue romboid after the 'executable' and this installed a folder in my Desktop. When I opened it I found another blue romboid that on double click took me to a set up program. After updating itself in the Internet, I had the program running.

---

### Post by marco_polo99 on 2007-12-02
Thanks--it worked.  This version of realplayer is way stripped down relative to the windows version I had been using for years, so it is of little use anyway-- I found and installed Amarok instead which seems more in line with what I was looking for.  

Thanks...

---

### Post by acl123 on 2007-12-04
Hmm after extracting the  file off Helix Community, I can't run either the realplay shell script or realplay.bin files. It just hangs not doing anything, or gives me a segmentation fault.

---

