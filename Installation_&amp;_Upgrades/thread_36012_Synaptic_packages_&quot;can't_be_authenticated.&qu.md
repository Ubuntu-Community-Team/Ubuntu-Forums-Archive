---
title: "Synaptic packages &quot;can't be authenticated.&quot;"
date: 2005-05-21
forum: Installation &amp; Upgrades
---

### Post by Chunk of Earth on 2005-05-21
I upgraded from Warty to Hoary by changing my sources.list file to:

 ```
# deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted 

## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu/ hoary main restricted 
deb-src http://us.archive.ubuntu.com/ubuntu/ hoary main restricted 

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hoary-updates main restricted 
deb-src http://us.archive.ubuntu.com/ubuntu/ hoary-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hoary universe 
deb-src http://us.archive.ubuntu.com/ubuntu/ hoary universe 

deb http://security.ubuntu.com/ubuntu/ hoary-security main restricted 
deb-src http://security.ubuntu.com/ubuntu/ hoary-security main restricted 

deb http://security.ubuntu.com/ubuntu/ hoary-security universe 
deb-src http://security.ubuntu.com/ubuntu/ hoary-security universe 

deb http://archive.ubuntu.com/ubuntu/ hoary multiverse 
deb-src http://archive.ubuntu.com/ubuntu/ hoary multiverse 

deb http://backports.ubuntuforums.org/backports/ hoary-backports main universe multiverse restricted	
deb http://backports.ubuntuforums.org/backports/ hoary-extras main universe multiverse restricted	

deb ftp://ftp.nerim.net/debian-marillat/ stable main 
deb ftp://ftp.nerim.net/debian-marillat/ unstable main 
deb ftp://ftp.nerim.net/debian-marillat/ testing main 

# deb http://debian.lcs.mit.edu/debian/ unstable main 
# deb-src http://debian.lcs.mit.edu/debian/ unstable main 

# deb http://debian.lcs.mit.edu/debian/ unstable contrib non-free 
# deb-src http://debian.lcs.mit.edu/debian/ unstable contrib non-free

``` ...then running  ```
sudo apt-get update
sudo apt-get dist-upgrade
```The Debian repositories are there so I could install xml-tv on Warty -- they were pinned so as not to override my Ubuntu packages and have been commented out since I installed xml-tv.
Here's my apt preferences file:
 ```
Package: *
Pin: release o=Debian 
Pin-Priority: 200
``` My upgrade to Hoary went great and I had no problems until new packages were added to the repositories. Now, when I run Synaptic I get this error when I try to upgrade the packages: ```
**Warning**
You are about to install software that **can't be authenticated!**
Doing this could allow a malicious individual to damage or
take control of your system.
``` The packages being flagged are common packages like Firefox, aMule, gimp, and gaim.
I found the section in the unofficial starter guide about updating the keys for the marillat repositories and I've done that. I also found another post for adding a different key but it turned out to be for a Debian repository. Here is the output of a **sudo gpg --list-keys** command: ```
/home/*userid*/.gnupg/pubring.gpg
------------------------------
pub  1024D/1F41B907 1999-10-03 Christian Marillat <marillat@debian.org>
uid						 Christian Marillat <marillat@free.fr>
uid						 Christian Marillat <marillat.christian@wanadoo.fr>
sub  1536g/C28DCC42 1999-10-03
sub  1024D/5D3877A7 2002-08-26

pub  1024D/4F368D5D 2005-01-31 Debian Archive Automatic Signing Key (2005) <ftpmaster@debian.org>

```Does anyone know how to determine which repository is untrusted by apt and how to import its key?
Thanks for reading this far.

---

### Post by Xian on 2005-05-21
[QUOTE=Chunk of Earth]Does anyone know how to determine which repository is untrusted by apt and how to import its key?
[/QUOTE]
AFAIK this has nothing to do with an unsigned key. 
It is just a common warning on those marillat repo packages.

---

### Post by Chunk of Earth on 2005-05-21
[QUOTE=Xian]AFAIK this has nothing to do with an unsigned key. 
It is just a common warning on those marillat repo packages.[/QUOTE]So that must mean I'm getting Firefox, gimp, gaim, gnome-menus and some others from Marillat? Would that be right? I'd rather get them from the Hoary repositories or the backports. If I pin the Marillat repositories it should resolve the error then, right?

---

### Post by Xian on 2005-05-21
[QUOTE=Chunk of Earth]So that must mean I'm getting Firefox, gimp, gaim, gnome-menus and some others from Marillat? Would that be right? I'd rather get them from the Hoary repositories or the backports. If I pin the Marillat repositories it should resolve the error then, right?[/QUOTE]
No, I get that message from the Hoary backport repos as well.
Like I said, it's just a common warning.

The backport repos are _relatively_ safe and so I'd just proceed.
I wouldn't advise that you pin any of those repos (just create other troubles).

---

### Post by Chunk of Earth on 2005-05-21
OK. I'll press on. I wish it wouldn't do that, though.

Thanks for the help.

---

