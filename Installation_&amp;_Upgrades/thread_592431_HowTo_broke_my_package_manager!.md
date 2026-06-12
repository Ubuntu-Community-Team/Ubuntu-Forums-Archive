---
title: "HowTo broke my package manager!"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by feisty wookie on 2007-10-26
Hello all!
I am a new linux user and i am currently running Kubuntu 7.04

I wanted to install acrobat reader by using the Synaptic package manager, So i followed the HowTo instructions on the page:

[COLOR="Blue"]http://ubuntuforums.org/archive/index.php/t-490459.html[/COLOR]

The instructions told me to:
[COLOR="Blue"]Copy/paste the following command and hit Enter:
echo "deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free" | sudo tee -a /etc/apt/sources.list

When prompted for your password, type it in and hit Enter. Next, copy/paste this command and hit Enter:

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update[/COLOR]

Unfortunately now i am unable to install anything at all!
the error i get when trying to use sudo apt-get update in konsole is 

[COLOR="Red"]Reading package lists... Error!
E: Dynamic MMap ran out of room
E: Error occurred while processing smtm (NewVersion2)
E: Problem with MergeList /var/lib/apt/lists/ftp.de.debian.org_debian_dists_sid_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.[/COLOR]

and the same happens if i try using my synaptic package manager...

[COLOR="Red"]E: Dynamic MMap ran out of room
E: Error occurred while processing smtm (NewVersion2)
E: Problem with MergeList /var/lib/apt/lists/ftp.de.debian.org_debian_dists_sid_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.[/COLOR]

i must add that i did close the konsole whilst the process was seemingly incomplete i.e. the progress just remained on 99% for about five min and then i became impatient and closed the konsole window so as to continue with the process. 

How do i fix my problem? I have looked at some of the other pages in the forum but there doesn't seem to be any real solution to the problem that i have. Is there anyway that i could undo the changes that I made through the HowTo instructions that i followed?

Thank You!

Full error:
[COLOR="Red"]Failed to fetch [ftp://debian.mirror.ac.za/debian/dists/sid/deb/binary-i386/Packages.gz](ftp://debian.mirror.ac.za/debian/dists/sid/deb/binary-i386/Packages.gz)  Unable to fetch file, server said 'Can't open /debian/dists/sid/deb/binary-i386/Packages.gz: No such file or directory  '
Failed to fetch [ftp://debian.mirror.ac.za/debian/dists/sid/http://packages.medibuntu.org//binary-i386/Packages.gz](ftp://debian.mirror.ac.za/debian/dists/sid/http://packages.medibuntu.org//binary-i386/Packages.gz)  Unable to fetch file, server said 'Can't open /debian/dists/sid/http://packages.medibuntu.org//binary-i386/Packages.gz: No such file or directory  '
Failed to fetch [ftp://debian.mirror.ac.za/debian/dists/sid/feisty/binary-i386/Packages.gz](ftp://debian.mirror.ac.za/debian/dists/sid/feisty/binary-i386/Packages.gz)  Unable to fetch file, server said 'Can't open /debian/dists/sid/feisty/binary-i386/Packages.gz: No such file or directory  '
Failed to fetch [ftp://debian.mirror.ac.za/debian/dists/sid/free/binary-i386/Packages.gz](ftp://debian.mirror.ac.za/debian/dists/sid/free/binary-i386/Packages.gz)  Unable to fetch file, server said 'Can't open /debian/dists/sid/free/binary-i386/Packages.gz: No such file or directory  '
Reading package lists... Error!
E: Dynamic MMap ran out of room
E: Error occurred while processing smtm (NewVersion2)
E: Problem with MergeList /var/lib/apt/lists/ftp.de.debian.org_debian_dists_sid_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.[/COLOR]

---

### Post by taurus on 2007-10-26
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

p.s.  It's not a good idea to mix Ubuntu with Debian--sid!

---

### Post by scrooge_74 on 2007-10-26
open a terminal and type ps -ax and check if there is any apt-get or synaptic process there then kill it

maybe that will help

That error fetching the package may be that the server is not working or the path is wrong.

You can comment out those line you put in /etc/apt/sources.list to at least get things to what they were before you made the changes

---

### Post by anubhavrocks on 2007-10-26
```
sudo gedit  /etc/apt/sources.list
``` 

remove the line
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
 and save the file.Then give the following command

```
sudo apt-get update
```

---

### Post by feisty wookie on 2007-10-26
#deb [ftp://za.archive.ubuntu.com/ubuntu/](ftp://za.archive.ubuntu.com/ubuntu/) feisty main restricted
#deb-src [ftp://za.archive.ubuntu.com/ubuntu/](ftp://za.archive.ubuntu.com/ubuntu/) feisty main restricted
deb [ftp://mirror.ac.za/ubuntu/ubuntu-archive](ftp://mirror.ac.za/ubuntu/ubuntu-archive) feisty main restricted
deb-src [ftp://za.archive.ubuntu.com/ubuntu/](ftp://za.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.

#deb [ftp://za.archive.ubuntu.com/ubuntu/](ftp://za.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
#deb-src [ftp://za.archive.ubuntu.com/ubuntu/](ftp://za.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb [ftp://mirror.ac.za/ubuntu/ubuntu-archive](ftp://mirror.ac.za/ubuntu/ubuntu-archive) feisty-updates main restricted
deb-src [ftp://za.archive.ubuntu.com/ubuntu/](ftp://za.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

#deb [ftp://za.archive.ubuntu.com/ubuntu/](ftp://za.archive.ubuntu.com/ubuntu/) feisty universe
#deb-src [ftp://za.archive.ubuntu.com/ubuntu/](ftp://za.archive.ubuntu.com/ubuntu/) feisty universe
deb [ftp://mirror.ac.za/ubuntu/ubuntu-archive](ftp://mirror.ac.za/ubuntu/ubuntu-archive) feisty universe
deb-src [ftp://za.archive.ubuntu.com/ubuntu/](ftp://za.archive.ubuntu.com/ubuntu/) feisty universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

#deb [ftp://za.archive.ubuntu.com/ubuntu/](ftp://za.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
#deb-src [ftp://za.archive.ubuntu.com/ubuntu/](ftp://za.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb [ftp://mirror.ac.za/ubuntu/ubuntu-archive](ftp://mirror.ac.za/ubuntu/ubuntu-archive) feisty-backports main restricted universe multiverse
deb-src [ftp://za.archive.ubuntu.com/ubuntu/](ftp://za.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [ftp://security.ubuntu.com/ubuntu](ftp://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [ftp://security.ubuntu.com/ubuntu](ftp://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [ftp://security.ubuntu.com/ubuntu](ftp://security.ubuntu.com/ubuntu) feisty-security universe
#deb-src [ftp://security.ubuntu.com/ubuntu](ftp://security.ubuntu.com/ubuntu) feisty-security universe

deb [ftp://ftp.de.debian.org/debian](ftp://ftp.de.debian.org/debian) sid main

deb [ftp://download.tuxfamily.org/3v1deb](ftp://download.tuxfamily.org/3v1deb) feisty 3v1n0
#deb-src [ftp://download.tuxfamily.org/3v1deb](ftp://download.tuxfamily.org/3v1deb) feisty 3v1n0

deb [ftp://ftp.de.debian.org/debian](ftp://ftp.de.debian.org/debian) sid main non-free
deb [ftp://debian.mirror.ac.za/debian](ftp://debian.mirror.ac.za/debian) sid main non-free deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free

---

### Post by taurus on 2007-10-26
I recommend you edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and comment out the Debian sid's repos by placing a # in front of those lines.  Also, you only need one entry for medibuntu.  (You have four lines of the same at the end!).

Save it and then run

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by feisty wookie on 2007-10-26
hi is there another program similar to gksudo that i can use? i tried using vim but as i said i am a very inexperienced user and i dont know if i did it right! sorry!

[COLOR="Blue"]The program 'gksudo' is currently not installed.  You can install it by typing:
sudo apt-get install gksu
bash: gksudo: command not found
Laptop:~$ sudo apt-get install gksu
Password:
Reading package lists... Error!
E: Dynamic MMap ran out of room
E: Error occurred while processing smtm (NewVersion2)
E: Problem with MergeList /var/lib/apt/lists/ftp.de.debian.org_debian_dists_sid_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.[/COLOR]

---

### Post by taurus on 2007-10-26
```
sudo nano -Bw /etc/apt/sources.list
```
Save it with <Ctrl>o and exit with <Ctrl>x.

---

### Post by feisty wookie on 2007-10-26
also how do i know which lines contain Debian sid's repos? Are they the lines beginning with deb? or are they the lines beginning with deb-src?

---

### Post by phidia on 2007-10-26
gedit is often recommended for less experianced users or just those that don't want to use vim.
You should be able to open it from the terminal with > sudo gedit
Hope that helps.

---

### Post by feisty wookie on 2007-10-26
I think you guys have solved my problem!!! i seem to be able to: sudo apt-get update except for one problem:

[COLOR="Blue"]Reading package lists... Done
W: GPG error: [ftp://download.tuxfamily.org](ftp://download.tuxfamily.org) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
W: You may want to run apt-get update to correct these problems[/COLOR]

---

### Post by scrooge_74 on 2007-10-26
That means you have not add the security key from that server, that is for knowing for sure  the source is a trusted one, but you can go ahead and install from there

---

### Post by feisty wookie on 2007-10-27
Thank you!!! It is fixed! I am again able to install stuff...
That was really awesome help.

---

