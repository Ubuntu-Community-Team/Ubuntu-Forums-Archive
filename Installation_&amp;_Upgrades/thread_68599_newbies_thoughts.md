---
title: "newbies thoughts"
date: 2005-09-23
forum: Installation &amp; Upgrades
---

### Post by garwaymatt on 2005-09-23
Hi, Ive just started using ubuntu /linux after getting my own laptop.   I now have an acer travelmate  2200 laptop (celeron d 2.6 256 ram ati 9100 graphics 40 gig hdd partitiond 50/50 ubuntu/xp(unfortunatley my school does not use linux grrr.).  I did not have many problems installing the os (after i realised that when creating the password,nothing actually appeared!)  Congrats to the designer of the installer,very clear. 

However, i am having a few problems
[list=1]
[*]Lack of sound(realtek ac97)
[*]Trackpad (synaptics) not working
[/list] 
I downloaded the drivers from the net then I realised one of the worst parts of linux in general.  the installation of drivers and program.  I looked on the net and found at least 5 different ways.

so i am looking for some advice
thanks 
matt ](*,)

---

### Post by Burbruee on 2005-09-23
[QUOTE=garwaymatt]Hi, Ive just started using ubuntu /linux after getting my own laptop.   I now have an acer travelmate  2200 laptop (celeron d 2.6 256 ram ati 9100 graphics 40 gig hdd partitiond 50/50 ubuntu/xp(unfortunatley my school does not use linux grrr.).  I did not have many problems installing the os (after i realised that when creating the password,nothing actually appeared!)  Congrats to the designer of the installer,very clear. 

However, i am having a few problems
[list=1]
[*]Lack of sound(realtek ac97)
[*]Trackpad (synaptics) not working
[/list] 
I downloaded the drivers from the net then I realised one of the worst parts of linux in general.  the installation of drivers and program.  I looked on the net and found at least 5 different ways.

so i am looking for some advice
thanks 
matt ](*,)[/QUOTE]

I've got an AC97 too and it is working.
However, I have noticed that there are no sound in some applications or games.
So what I did was: ( In Terminal. )
```

sudo ps ax | grep 'esd'

```
Returned something about --nosound

Anyway, to solve this simply:
```

sudo killall esd

```

Second question..
Installing applications ( drivers. ) depending on what extension the file has you have a few different ways to go.

**.tar.gz**
Use the following in the Terminal:
```

tar -xzvf archive.tar.gz

```
This will unpack the compressed file and should also create a new directory.
```

cd archive_folder
./configure
make
sudo make install

```
Enters directory, runs configure to check if all dependencies are met then compiles and installs it.

You will need tools to compile, there is a sticky-thread somewhere around here 
( customization forum I think. ) with a nice little scipt that installs build-essentials gcc g++ and some other stuff required to compile from sourcecode.

**.deb**
Debian package, use this simple command and it's all installed and done:
```

dpkg -i package.deb

```
Where package.deb of course is the filename of your program.

**apt-get**
apt-get is a very nice way to install software to your system.
```

apt-get update

```
Reads from /etc/apt/sources.list to fetch the sites to download from.

In order to search for a package:
```

apt-cache search PACKAGE

```

And to install:
```

sudo apt-get install PACKAGE

```

You could use synaptic as well for this..

And you may want to uncomment some lines in /etc/apt/sources.list in order to have more software available to you.
NOTE: Must run 'apt-get update' afterwards.

**.rpm**
Used by many distributions such as Mandriva and Fedora.
You can convert an rpm to a deb package but first you must fetch the 'alien' package.
```

sudo apt-get install alien

```
Then to convert an rpm to an deb use:
```

alien -d package.rpm

```
And it will generate a package.deb file.
Then you may just use dpkg as described above to install.

Well, I don't know if I cleared out some questionmarks or if I even understood your question correct, but I hope I did. :)

---

### Post by garwaymatt on 2005-09-24
Thanks a lot, i feel more confident now (and I can Listen to my Mp3's!)

matt \\:D/

---

