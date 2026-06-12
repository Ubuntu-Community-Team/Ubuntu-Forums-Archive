---
title: "feisty fawn   sources.list problem"
date: 2007-07-29
forum: Installation &amp; Upgrades
---

### Post by garethmob on 2007-07-29
hey well i'm new to the linux ball park i tried fedora    and it was very unstable an i tried dapper drake ubuntu (wouldent even boot cos of a usb error) so i tried this one and it works.. to a certain degree



now unbeknown to me i mucked up the update manager     i just relised on here about not using the sudo part but thats too late now lol i listened to the update program and its mucked up




i need to fix the file but i dunno how to          is there any advice cos i cnt download no updates till its fixed :(


thanks in advance

gaz

---

### Post by forestpixie on 2007-07-29
what's wrong with the update program - what is it saying?

a little more information will be helpful

---

### Post by garethmob on 2007-07-29
sorry


well aparently the error says

failed to check for installed and avariable applications.

this is a majour failier of your software management system. please check for broken packages with synaptic (have done and it didnt work) check the file permissions and correctness of the file 'ect/apt/sources.list' and reload the software infomation with : 'sudo apt-get update' and sudo apt-get install -f





i have tried that in the terminal but it threw an error saying that it does not beging with a alphurnumeric

---

### Post by forestpixie on 2007-07-29
open a  terminal and type

gedit /etc/apt/sources.list

once that's open post the contents of your sources.list

---

### Post by garethmob on 2007-07-29
ijust did that and it opened a blank window      with nothing in it


(edit) opened the file with text editor  


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

---

### Post by forestpixie on 2007-07-29
did you type it or did you copy and paste - cos you have a typo in your second post

 'ect/apt/sources.list' isn't right 

at least I assume not - you are running 7.04 - yes?

---

### Post by garethmob on 2007-07-29
thats wot it says                 wot is it supposed to be    ye i running the standered  ubuntu 7

---

### Post by forestpixie on 2007-07-29
ok saw the edit

run this these in terminal - enter after each and post the whole thing with errors here

```

sudo apt-get update

sudo apt-get install -f
```

---

### Post by garethmob on 2007-07-29
first

Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty Release.gpg [191B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Translation-en_GB
Get: 2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Translation-en_GB
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Fetched 3B in 0s (4B/s)  
Reading package lists... Done


second


gareth@Linux-pc:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following extra packages will be installed:
  deskbar-applet
Recommended packages:
  python-beagle python-soappy
The following packages will be upgraded:
  deskbar-applet
1 upgraded, 0 newly installed, 0 to remove and 94 not upgraded.
1 not fully installed or removed.
Need to get 0B/256kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: parse error, in file `/var/lib/dpkg/status' near line 13568 package `deskbar-applet':
 `Depends' field, invalid package name ``libstartup-notification0': must start with an alphanumeric
E: Sub-process /usr/bin/dpkg returned an error code (2)
gareth@Linux-pc:~$

---

### Post by forestpixie on 2007-07-29
ok never seen that before - but found a similar error 

[http://ubuntuforums.org/showthread.php?t=496550](http://ubuntuforums.org/showthread.php?t=496550)

we can do the things they did and see what gives, first I want to check that you have a backup of a file

in terminal do

```
ls /var/lib/dpkg/status*
```


and post that

---

### Post by garethmob on 2007-07-29
gareth@Linux-pc:~$ ls /var/lib/dpkg/status*
/var/lib/dpkg/status  /var/lib/dpkg/status-old
gareth@Linux-pc:~$

---

### Post by garethmob on 2007-07-29
double post soz

---

### Post by forestpixie on 2007-07-29
ok try to purge the package


```
sudo dpkg -remove --purge deskbar-applet
```

I'm sure that's the correct syntax - if it says there's something wrong with the command come back before you do the next bit!

if that fails we can copy the status backup to the status file and hope that that's not got the error as well, with these commands, enter after each

```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status-BROKED
sudo cp -a /var/lib/dpkg/status-old /var/lib/dpkg/status
```

---

### Post by garethmob on 2007-07-29
dont know if this an error


gareth@Linux-pc:~$ sudo dpkg -remove --purge deskbar-applet
Password:
dpkg: conflicting actions -e (--control) and -r (--remove)

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license|--licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
gareth@Linux-pc:~$ 

going to try other way... just in case

---

### Post by garethmob on 2007-07-29
the second part dosent do anything.. or didnt seem to             it just droped to next line for input

---

### Post by forestpixie on 2007-07-29
try 

sudo apt-get -remove --purge deskbar-applet

---

### Post by garethmob on 2007-07-29
gareth@Linux-pc:~$ sudo apt-get -remove --purge deskbar-applet
E: Command line option &#8216;r&#8217; [from -remove] is not known.
gareth@Linux-pc:~$

---

### Post by forestpixie on 2007-07-29
sorry 

sudo apt-get remove --purge deskbar-applet

Edit - can you run

ls /var/lib/dpkg/status* 

again

---

### Post by garethmob on 2007-07-29
no worries :)      i am thankful for u helping me :) 


gareth@Linux-pc:~$ sudo apt-get remove --purge deskbar-applet
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  deskbar-applet*
0 upgraded, 0 newly installed, 1 to remove and 94 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 2920kB disk space will be freed.
Do you want to continue [Y/n]? y
Setting up python2.5-minimal (2.5.1-0ubuntu1) ...

(Reading database ... 88001 files and directories currently installed.)
Removing deskbar-applet ...
Purging configuration files for deskbar-applet ...
Setting up python2.5 (2.5.1-0ubuntu1) ...

---

### Post by garethmob on 2007-07-29
gareth@Linux-pc:~$ ls /var/lib/dpkg/status* 
/var/lib/dpkg/status  /var/lib/dpkg/status-BROKED  /var/lib/dpkg/status-old
gareth@Linux-pc:~$

---

### Post by forestpixie on 2007-07-29
ok run these two again

```
sudo apt-get update

sudo apt-get install -f
```

hopeful are the brave

---

### Post by garethmob on 2007-07-29
gareth@Linux-pc:~$ ls /var/lib/dpkg/status* 
/var/lib/dpkg/status  /var/lib/dpkg/status-BROKED  /var/lib/dpkg/status-old
gareth@Linux-pc:~$ sudo apt-get update
Password:
Get: 1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_GB
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty Release.gpg [191B]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Translation-en_GB
Get: 3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates Release             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) feisty-updates/restricted Sources
Fetched 3B in 0s (7B/s)  
Reading package lists... Done
gareth@Linux-pc:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 94 not upgraded.
gareth@Linux-pc:~$

---

### Post by garethmob on 2007-07-29
yey!! it worked :)     thank you very very much :)

---

### Post by forestpixie on 2007-07-29
excellent glad to be of service :D

if you want to try installing what you were after in the first place I'll keep an eye on this for a while

---

### Post by garethmob on 2007-07-29
well i installed it   (it was althe recent updates) and beryl        and i get a lovely white screen :(    is it my graphics card or something as every linux distro i tried      fedora         fedora server (both unstable so i thought iut was that)     the 64 bit edition of ubuntu and the 32 bit (wot i have and prefire)  v given me a big white screen

---

### Post by forestpixie on 2007-07-29
It probably is - but I can't help with beryl or compiz - I've never bothered with it.

Try posting on the absolute beginners forum - it sees a lot of movement - 

it might just need xorg reconfiguring but I wouldn't want to do that unless I was sure.

Sorry :(

the updates shouldn't have done that so I can only assume it's beryl, uninstall it so you can see what you're doing and look in the Abs Beg

---

### Post by garethmob on 2007-07-29
ye no worries u did more than help any way  :) i thank you :)


i didnt try beryl to start with but i got 512mb graphics card          so i dunn ah wel lol        thanks again :)

gareth

---

### Post by Ptero-4 on 2007-07-29
gareth. Did you got an ATI or NVIdia card? b/c if it is a NVidia all you need to do is install the nvidia-glx-* driver through the restricted drivers manager. If it´s an ATI OTOH you´ll need to use xgl b/c the POS ati drivers doesn´t support compositing.

---

