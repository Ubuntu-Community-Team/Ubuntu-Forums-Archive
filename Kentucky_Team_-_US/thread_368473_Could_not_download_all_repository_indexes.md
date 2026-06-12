---
title: "Could not download all repository indexes"
date: 2007-02-23
forum: Kentucky Team - US
---

### Post by JarG0n on 2007-02-23
Help!

I'm getting this message when trying to reload the packages in  Synaptic.  Can anyone tell me how to resolve this?

**Could not download all repository indexes**

*The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.*

[i][http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.bz2:](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.bz2:) Could not open file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_edgy-security_universe_binary-i386_Packages - open (2 No such file or directory)
[http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2:](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2:) Could not open file /var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_edgy-security_main_binary-i386_Packages - open (2 No such file or directory)
[/i]

then.. this error is raised after dismissing the above.

[B]
An error occured

The following details are provided:[/B]

[I]W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_edgy-security_main_binary-i386_Packages)
[/I]

---

### Post by jkeyes0 on 2007-02-23
Can you post the contents of your /etc/apt/sources.list file?

---

### Post by JarG0n on 2007-02-24
> **jkeyes0 said:**
> Can you post the contents of your /etc/apt/sources.list file?

Well, I don't see an exact duplicate.  What should I remove, and how did this get here in the first place? :(

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main multiverse restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe main multiverse restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main multiverse restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) edgy-security universe main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-updates universe main
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by JarG0n on 2007-02-24
I tried the update again today, and now I'm not getting an error!!  ](*,)

---

### Post by Ptero-4 on 2007-02-24
the third ¨edgy-security¨ entry have ¨main¨ after universe. That`s what is probably giving the problems there.

---

### Post by jkeyes0 on 2007-02-24
I was thinking the same thing about two mains, but if it's working, don't worry about it. :)

---

### Post by sarvan.rb on 2009-02-07
Hi.. even i got the same problem while trying to install vlc. can anyone help me?

E: Malformed line 38 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

---

### Post by jkeyes0 on 2009-02-20
> **sarvan.rb said:**
> Hi.. even i got the same problem while trying to install vlc. can anyone help me?

E: Malformed line 38 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

Hi, sorry for the delay, but can go to the terminal (Applications -> Accessories -> Terminal) and post the output of the command 
```
head -38 /etc/apt/sources.list | tail -1
```

What this code does is it tells the system to output the first 38 lines of the file, but only show you the last 1 line (the 38th line, the one with the problem)

---

### Post by aKidNamedStoney on 2009-03-29
Just installed an older version of ubuntu in an emergency, 7.04 feisty fawn I think. I get this message trying to install or update anything.

[IMG]http://img.photobucket.com/albums/v600/IanBryant/Screenshot.png[/IMG]

[http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz:) 404 Not Found
[http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.46 80]

---

### Post by miguel_mips on 2009-05-01
I have exactly the same thing with gutsy 7.10

---

### Post by redoscar3 on 2009-05-05
I suspect that the Gutsy repositories have been removed and are no longer available.  The last updates I saw for Gutsy were posted maybe a week to 10 days before Jaunty was released.  I have two Gutsy machines and tried to get everything I wanted installed and updated before the repositories disappeared.

---

### Post by SolarisSDK on 2009-05-06
And what should we do? Same problem. Gutsy.
Installing/Updating manually is like hell. 
Wipe OS and install 9.04 ? NO WAI!!!

---

### Post by anonymousnobody on 2009-06-11
I have the same problem. I can't seem to update my repositories. I am running Ubuntu 7.10 Gutsy Gibbon.

I have looked at other threads and then mention a problem with proxy servers, but I don't have a /etc/apt/apt.conf file. I do have a /etc/apt/apt.conf.d directory though.

From the error message below, I think the servers no longer exist?

Any help would be appreciated. Thanks.

Error message when I try to update or change repository servers via GUI:
```

http://ubuntu.media.mit.edu/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz: 404 Not Found
http://ubuntu.media.mit.edu/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz: 404 Not Found
http://ubuntu.media.mit.edu/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz: 404 Not Found
http://ubuntu.media.mit.edu/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz: 404 Not Found
http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz: 404 Not Found
http://ubuntu.media.mit.edu/ubuntu/dists/gutsy/main/binary-i386/Packages.gz: 404 Not Found
http://ubuntu.media.mit.edu/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz: 404 Not Found
http://ubuntu.media.mit.edu/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz: 404 Not Found
http://ubuntu.media.mit.edu/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz: 404 Not Found
http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz: 404 Not Found
http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz: 404 Not Found
http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz: 404 Not Found

```


/etc/apt/sources.list file:
```
deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted
deb http://ubuntu.media.mit.edu/ubuntu/ gutsy-updates universe main multiverse restricted
deb http://ubuntu.media.mit.edu/ubuntu/ gutsy main universe restricted multiverse

```

Error message via command line apt-get update:
```
$  sudo apt-get update
[sudo] password for lawrence:
Ign http://ubuntu.media.mit.edu gutsy Release.gpg
Ign http://ubuntu.media.mit.edu gutsy/main Translation-en_US
Ign http://ubuntu.media.mit.edu gutsy/universe Translation-en_US
Ign http://ubuntu.media.mit.edu gutsy Release
Ign http://ubuntu.media.mit.edu gutsy/main Packages
Ign http://ubuntu.media.mit.edu gutsy/universe Packages
Err http://ubuntu.media.mit.edu gutsy/main Packages
  404 Not Found
Err http://ubuntu.media.mit.edu gutsy/universe Packages
  404 Not Found
Failed to fetch http://ubuntu.media.mit.edu/ubuntu/dists/gutsy/main/binary-i386/Packages.gz  404 Not Found
Failed to fetch http://ubuntu.media.mit.edu/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz  404 Not Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by Claus7 on 2009-07-23
Hello,

I had exactly the same problem with ubuntu gutsy 7.10. I wanted to install a new package from synaptic, and always I was not able to do so.

I had install gutsy since it was out and I had never tried to do (almost) any update.

In the control panel (the menu bar) I always had an orange mark witch prompted me to update my system. I went there, and I tried to update my system. Yet, the error that it could not fetch the requested packages, popped up.

The errors I faced in general were: either the title of the thread or the fact that it could not fetch the requested packages.

So I decided, while hitting the same icon, to update my system to hardy heron 8.04.3 (this was the latest one). It was easy to do so, because I had that option available. The update went ok and I have not faced any problem since.

Regards!

---

### Post by peachtree195 on 2009-09-10
I have a similar problem when updating my system

System could not download all repository indexes

and then the detailed info:

Failed to fetch [ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/source/Sources](ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/source/Sources)  Unable to fetch file, server said 'Failed to open file.  '
Some index files failed to download, they have been ignored, or old ones used instead.

How to fix this?

---

### Post by trellis2 on 2009-09-13
For peachtree 195 (Atlanta???) If you're not using mysql workbench, you can comment out the entry in your sources.list file. (here are the steps for newbies or my grandmother.)
1. open a terminal
[INDENT]Applications/Accessories/Terminal[/INDENT]

2. open a text editor
[INDENT]usrnam@urcomputr:~$ sudo gedit /etc/apt/sources.list[/INDENT]

3.Using the search function in gedit find mysql workbench.
[INDENT]# MySQL Workbench
deb [ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/](ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/) binary/
deb-src [ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/](ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/) source/[/INDENT]

4. Comment out the  binary and the source entries with a "#" sign at the beginning of each entry.
[INDENT]# MySQL Workbench
#deb [ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/](ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/) binary/
#deb-src [ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/](ftp://ftp.mysql.com/pub/mysql/download/gui-tools/ubuntu/) source/[/INDENT]

5. Save the file. Close gedit and update your repos.
[INDENT]usrnam@urcomputr:~$ sudo apt-get update && sudo apt-get upgrade[/INDENT]

let everyone know if this works.

---

### Post by neeraj_schrody on 2009-10-10
> **aKidNamedStoney said:**
> Just installed an older version of ubuntu in an emergency, 7.04 feisty fawn I think. I get this message trying to install or update anything.

[IMG]http://img.photobucket.com/albums/v600/IanBryant/Screenshot.png[/IMG]

[http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz:) 404 Not Found
[http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-security/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-security/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.46 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/feisty-security/multiverse/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.88.46 80]
after lots of googling i found sumthin...may b dis one help......
go to software source panel...


[LIST]
[*]Software Sources: System > Administration > Software Sources. 
[*]*Synaptic*: System > Administration > *Synaptic* >> Settings >> Repositories. 
[*]You will have to enter your password to gain access to the page.
[/LIST]
or else u can access it frm openin update manager n den click on settings..
now change the server to main server in ubuntu software tab..

this has worked for me..
realted link:[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by rmohan80 on 2010-01-10
Anybody figured this out yet? The last reply isn't of much use. I'm using "Main Server" and I tried to switch to a local server, but still same issue. Getting 404 file not found whenever I try to update or download some software

---

### Post by rmohan80 on 2010-01-10
Ok, I did some research. Change your /etc/apt/sources.lst file's all [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) to [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) (including the ones in #).

This should work

---

### Post by darkknight85 on 2010-01-10
Hay I have a similar problem mine says 
E: Malformed line 60 in source list /etc/apt/sources.list (dist parse)
can anyone tell me what to do.

---

### Post by k64 on 2010-01-10
```
sudo apt-get dist-upgrade
``` 5 times!

---

### Post by darkknight85 on 2010-01-11
Oh hey I also need to know how to remove the following /usr/lib/codecs and /usr/lib/libdvdcss2.so 
No matter what i try even sudo rm --no-preserve-root   all I get is "Operation not permitted"

---

### Post by Fons van der Plas on 2010-02-07
I've got the same problem, with the following error messages:

Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch [http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/binary-i386/Packages.gz](http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/source/Sources.gz](http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/source/Sources.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

Can anyone help?

---

### Post by jsibauste on 2010-05-05
I am having the same problem. I also have access to the internet but I am running the Ubuntu Desktop 10.04 on Sun's Virtual Box. I have no idea what the problem is. I am not new to Ubuntu but is not an OS that I use all the time and I would like to learn more but it's difficult since is not as intuitive as Windows 7.
[http://archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz)
[http://archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.bz2)
[http://archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.bz2)
[http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.bz2)
[http://archive.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.lzma](http://archive.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.lzma)
[http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.lzma](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.lzma)
[http://archive.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/lucid-security/Release.gpg)
[http://archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.gz)
[http://archive.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-i386/Packages.gz)
[http://archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.lzma](http://archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.lzma)
[http://archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.gz)
[http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.bz2)
[http://archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.lzma](http://archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.lzma)
[http://archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.bz2)
[http://archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.gz)
[http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.lzma](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.lzma)
[http://archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.gz)
[http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz)
[http://archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/lucid/Release.gpg)
[http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/binary-i386/Packages.bz2)
[http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz)
[http://archive.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.gz)
[http://archive.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.bz2)
[http://archive.ubuntu.com/ubuntu/dists/lucid/Release](http://archive.ubuntu.com/ubuntu/dists/lucid/Release)
[http://archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.lzma](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.lzma)
[http://archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/Release.gpg)
[http://archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz)
[http://archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.lzma](http://archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.lzma)
[http://archive.ubuntu.com/ubuntu/dists/lucid-updates/Release](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/Release)
[http://archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.bz2)
[http://archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.bz2)
[http://archive.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-security/main/source/Sources.gz)
[http://archive.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-i386/Packages.lzma](http://archive.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-i386/Packages.lzma)
[http://archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.gz)
[http://archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.bz2)
[http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.bz2)
[http://archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.bz2)
[http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.lzma](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.lzma)
[http://archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid/main/binary-i386/Packages.gz)
[http://archive.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.lzma](http://archive.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.lzma)
[http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.gz)
[http://archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.lzma](http://archive.ubuntu.com/ubuntu/dists/lucid/universe/binary-i386/Packages.lzma)
[http://archive.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.bz2)
[http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/main/source/Sources.gz)
[http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.lzma](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/restricted/source/Sources.lzma)
[http://archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.lzma](http://archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.lzma)
[http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.lzma](http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.lzma)
[http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.bz2)
[http://archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/source/Sources.bz2)
[http://archive.ubuntu.com/ubuntu/dists/lucid-security/Release](http://archive.ubuntu.com/ubuntu/dists/lucid-security/Release)
[http://archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz)
[http://archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.lzma](http://archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.lzma)
[http://archive.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid-security/universe/binary-i386/Packages.bz2)
[http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz)
[http://archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.lzma](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.lzma)
[http://archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.bz2)
[http://archive.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.gz)
[http://archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.lzma](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.lzma)
[http://archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.bz2)
[http://archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz)
[http://archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.gz)
[http://archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.bz2)
[http://archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.gz)
[http://archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.lzma](http://archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.lzma)
[http://archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.lzma](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.lzma)
[http://archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.bz2)
[http://archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.lzma](http://archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.lzma)
[http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.lzma](http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.lzma)
[http://archive.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid-security/main/binary-i386/Packages.bz2)
[http://archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid/main/source/Sources.bz2)
[http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/binary-i386/Packages.bz2)
[http://archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.gz)
[http://archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid-security/multiverse/source/Sources.gz)
[http://archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.lzma](http://archive.ubuntu.com/ubuntu/dists/lucid/universe/source/Sources.lzma)
[http://archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.lzma](http://archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.lzma)
[http://archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.bz2)
[http://archive.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.lzma](http://archive.ubuntu.com/ubuntu/dists/lucid-security/universe/source/Sources.lzma)
[http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/lucid/restricted/source/Sources.gz)

---

### Post by Shay Guy on 2010-06-17
I've been getting the following today when I try to check for updates:

**Could not download all repository indexes**

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch [http://76.73.4.58/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://76.73.4.58/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://76.73.4.58/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz](http://76.73.4.58/ubuntu/dists/lucid/restricted/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://76.73.4.58/ubuntu/dists/lucid/main/source/Sources.gz](http://76.73.4.58/ubuntu/dists/lucid/main/source/Sources.gz)  404  Not Found
Failed to fetch [http://76.73.4.58/ubuntu/dists/lucid/restricted/source/Sources.gz](http://76.73.4.58/ubuntu/dists/lucid/restricted/source/Sources.gz)  404  Not Found
Failed to fetch [http://76.73.4.58/ubuntu/dists/lucid/universe/binary-i386/Packages.gz](http://76.73.4.58/ubuntu/dists/lucid/universe/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://76.73.4.58/ubuntu/dists/lucid/universe/source/Sources.gz](http://76.73.4.58/ubuntu/dists/lucid/universe/source/Sources.gz)  404  Not Found
Failed to fetch [http://76.73.4.58/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz](http://76.73.4.58/ubuntu/dists/lucid/multiverse/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://76.73.4.58/ubuntu/dists/lucid/multiverse/source/Sources.gz](http://76.73.4.58/ubuntu/dists/lucid/multiverse/source/Sources.gz)  404  Not Found
Failed to fetch [http://76.73.4.58/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz](http://76.73.4.58/ubuntu/dists/lucid-updates/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://76.73.4.58/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz](http://76.73.4.58/ubuntu/dists/lucid-updates/restricted/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://76.73.4.58/ubuntu/dists/lucid-updates/main/source/Sources.gz](http://76.73.4.58/ubuntu/dists/lucid-updates/main/source/Sources.gz)  404  Not Found
Failed to fetch [http://76.73.4.58/ubuntu/dists/lucid-updates/restricted/source/Sources.gz](http://76.73.4.58/ubuntu/dists/lucid-updates/restricted/source/Sources.gz)  404  Not Found
Failed to fetch [http://76.73.4.58/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz](http://76.73.4.58/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://76.73.4.58/ubuntu/dists/lucid-updates/universe/source/Sources.gz](http://76.73.4.58/ubuntu/dists/lucid-updates/universe/source/Sources.gz)  404  Not Found
Failed to fetch [http://76.73.4.58/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz](http://76.73.4.58/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://76.73.4.58/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz](http://76.73.4.58/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz)  404  Not Found
Failed to fetch [http://76.73.4.58/ubuntu/dists/lucid-security/main/binary-i386/Packages.gz](http://76.73.4.58/ubuntu/dists/lucid-security/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://76.73.4.58/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.gz](http://76.73.4.58/ubuntu/dists/lucid-security/restricted/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://76.73.4.58/ubuntu/dists/lucid-security/main/source/Sources.gz](http://76.73.4.58/ubuntu/dists/lucid-security/main/source/Sources.gz)  404  Not Found
Failed to fetch [http://76.73.4.58/ubuntu/dists/lucid-security/restricted/source/Sources.gz](http://76.73.4.58/ubuntu/dists/lucid-security/restricted/source/Sources.gz)  404  Not Found
Failed to fetch [http://76.73.4.58/ubuntu/dists/lucid-security/universe/binary-i386/Packages.gz](http://76.73.4.58/ubuntu/dists/lucid-security/universe/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://76.73.4.58/ubuntu/dists/lucid-security/universe/source/Sources.gz](http://76.73.4.58/ubuntu/dists/lucid-security/universe/source/Sources.gz)  404  Not Found
Failed to fetch [http://76.73.4.58/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.gz](http://76.73.4.58/ubuntu/dists/lucid-security/multiverse/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://76.73.4.58/ubuntu/dists/lucid-security/multiverse/source/Sources.gz](http://76.73.4.58/ubuntu/dists/lucid-security/multiverse/source/Sources.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by TGAKO on 2010-09-08
Hi All the problem that you encounter is so easy to solve and it happens because of some users unmanaged action like playing with system things that he don't know what is it .
And the Way to solve it :
1- go to System=>Administration=>Software Sources
2-Uncheck the (Installable From CD-Rom/DVD) its like (Cdrom with Ubuntu 10.04 'Lucid Lynx) uncheck it remove it from using and chuck (apply) Source Code and all above it or   Make your choices as like as this photo and make the download from : (Main Server)
[ATTACH]168845[/ATTACH]
  3-Close the Software Sources and you can Use YOUR updates now try typing (Sudo apt-get update) and see thats the problem has been solved .

And thats all :p.
And remember to don't miss with system things you don't know what you will change.
And for further help ask me on my Email: [EMAIL="TGAKO.SOT@Gmail.com"]TGAKO.SOT@Gmail.com[/EMAIL]
):P

---

### Post by akila1989 on 2010-09-29
hai

help!
I'm using ubuntu 10.04
I get this message
"*The repository might be no longer available or could not be contacted  because of network problems. If available an older version of the  failed index will be used. Otherwise the repository will be ignored.  Check your network connection and the correct writing of the repository  address in the preferences.*"

when type in terminal sudo apt-get update

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid/multiverse/source/Sources.bz2)  Hash Sum mismatch

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid/multiverse/binary-i386/Packages.bz2)  Hash Sum mismatch

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.bz2)  Hash Sum mismatch

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/source/Sources.bz2)  Hash Sum mismatch

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/universe/binary-i386/Packages.bz2)  Hash Sum mismatch

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.bz2)  Hash Sum mismatch

E: Some index files failed to download, they have been ignored, or old ones used instead.

I guess this is happen because of a network problem(not sure!)
I'm using [cache.mrt.ac.lk]("http://cache.mrt.ac.lk/") wi-fi network to update.
i'm not not very confident about network configuration
i did some configurations but i'm not sure.
i'm also unable to intall software from "ubuntu software center"  :mad:

would you please be kind enough to help for this matter

thank you.

---

### Post by TGAKO on 2010-10-01
I think you should copy your important data and format your harddisk and reinstall ubuntu and install it correct maybe your problem happened while installing in ubuntu reinstall it and report .

---

### Post by rirchse on 2013-05-03
Hello All,
When I want to try this command 
"**head -38 /etc/apt/sources.list | tail -1**" in terminal, then show the message **##developers who want to ship their latest software.**

Is it possible to solved **(could not download all repository indexes) **this problem?

---

### Post by matt_symes on 2013-05-03
Hi

> **rirchse said:**
> Hello All,
When I want to try this command 
"**head -38 /etc/apt/sources.list | tail -1**" in terminal, then show the message **##developers who want to ship their latest software.**

Is it possible to solved **(****could not download all repository indexes)**this problem?

No. The command ```
head -n38 /etc/apt/sources.list | tail -1
```does not fix this error > could not download all repository indexes

What it does is print the line at line number 38 in the file /etc/apt/sources.list.

If there is a problem on line 38 then the above command will display the line.

sarvan.rb's error was...
> 
E: Malformed line 38 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

...and that is why that command was used; to see what the problem with line 38 actually was.

I prefer to use sed to do the same thing.

Take a look at this.
```

matthew-S206:/home/matthew/BACKUP % cat -n /etc/apt/sources.list | head  
     1    # deb http://packages.linuxmint.com/ maya main upstream import
     2    # deb cdrom:[Xubuntu 12.10 _Quantal Quetzal_ - Release amd64 (20121017.1)]/ saucy main multiverse restricted universe
     3    
     4    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     5    # newer versions of the distribution.
     6    deb http://gb.archive.ubuntu.com/ubuntu/ saucy main restricted
     7    deb-src http://gb.archive.ubuntu.com/ubuntu/ saucy main restricted
     8    
     9    ## Major bug fix updates produced after the final release of the
    10    ## distribution.
matthew-S206:/home/matthew/BACKUP % sed -n '6p' /etc/apt/sources.list
deb http://gb.archive.ubuntu.com/ubuntu/ saucy main restricted
matthew-S206:/home/matthew/BACKUP % head -n6 /etc/apt/sources.list | tail -1
deb http://gb.archive.ubuntu.com/ubuntu/ saucy main restricted
matthew-S206:/home/matthew/BACKUP % 
 
```

*sed -n '6p' /etc/apt/sources.list* prints out the 6th line and so does *head -n6 /etc/apt/sources.list | tail -1*

This is a really old thread though so **Thread Closed**.

Kind regards

---

