---
title: "apt-get problem with MergeList"
date: 2007-01-06
forum: Installation &amp; Upgrades
---

### Post by cmire on 2007-01-06
I'm running Kubuntu 6.06 and getting issues with apt-get.  It used to work fine, but I'm not sure what happened to cause this error.  I think the last thing I installed was gnomad2 -- and had to remove and reinstall due to some initial errors.  I checked /var/lib/dpkg/status for the gnomad2 entry and didn't see anything obvious indicating that is the problem.

When I run 'sudo apt-get update' or 'sudo apt-get install' I get this error:

Fetched 7B in 13s (1B/s)
Reading package lists... Error!
E: Problem parsing dependency Conflicts
E: Error occurred while processing konqueror (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.

I was getting some 404 Not Found errors for some of the repositories in my list, so I commented those out, but the error still shows up.  There's nothing in /var/lib/dpkg/status for konquerer, so that message line puzzles me.

I searched the other posts I could find with apt-get issues, but they all seemed to point to a specific offending package, none of which really matched my specific error (the konquerer part).

As it stands now, I can't upgrade or install anything new -- so my system is basically frozen unless I fix this issue or reinstall.
[http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)

---

### Post by taurus on 2007-01-06
Can you post your /etc/apt/sources.list here from a terminal to make sure it is good?

```
cat /etc/apt/sources.list
```

---

### Post by cmire on 2007-01-06
Here is what I have in sources.list:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

#deb [http://lprod.org/deb/dapper/](http://lprod.org/deb/dapper/) ./ ####404 not found####
#deb-src [http://lprod.org/deb/dapper/](http://lprod.org/deb/dapper/) ./ ####404 not found####
#deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper free non-free ####404 not found####

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe multiverse
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse

---

### Post by cmire on 2007-01-14
O.k. -- finally resolved the problem.  Somewhere during my various 'apt-get install's for stuff I wanted on my system, something updated my /var/lib/dpkg/status file in such a way as to cause severe syntax issues the next time I ran apt-get.

Here are the specific problems that were in my /var/lib/dpkg/status file:

1 -- dpkg: parse error, in file `/var/lib/dpkg/status' near line 3777 package `kdemultimedia-kio-plugins':
 `Replaces' field, invalid package name `kdebase-aud)olibs': character `)' not allowed - only letters, digits and -+._ allowed

2 -- dpkg: parse error, in file `/var/lib/dpkg/status' near line 3778 package `kdemultimedia-kio-plugins':
 `Depends' field, reference to `libogg0': version contains `('

here's the text that caused error #2 -- look at the libogg0 entry:
Depends: kdelibs4c2a (>= 4:3.5.2), libartsc0 (>= 1.5.2-0), libasound2 (>> 1.0.10), libc6 (>= 2.3.4-1), libcdparanoia0 (>= 3a9.8-11), libflac7, libgcc1 (>= 1:4.0^H2), libglib2.0-0 (>= 2.10.0), libkcddb1 (>= 4:3.5^H2), libogg0 (>= 1.1(3), libstdc++6 (>= 4.0.2-4), libtag1c2a (>= 1.4), libvorbis0a (>= 1.1.2), libvorbisenc2 (>= 1.1.2), libvorbisfile3 (>= 1.1.2)

3 -- dpkg: parse error, in file `/var/lib/dpkg/status' near line 26331 package `konqueror':
 `Replaces' field, invalid package name `kdebase-aud)olibs': character `)' not allowed - only letters, digits and -+._ allowed

I really wish apt-get had some sort of 'debug extra verbose mode' to reveal specific errors like this.

I only figured this out after trying to run 'dpkg' directly on a .deb file I downloaded, as that gave me the output I posted here.

---

### Post by rendral on 2007-12-25
CMIR: I have the exact same problem with Ubuntu, and as I am an absolute beginner, could please tell me what I should do to fix my problem (I assume I must edit my var/lib/dpkg/status file? But, what to remove and what to replace - this is where I need the help. Any advice you are able to give me would be very much appreciated.

---

### Post by cmire on 2007-12-25
Hi rendral,

You are correct -- you will have to edit the /var/lib/dpkg/status file.  I used vi, but you can use the text editor of your choice.

First, make a backup copy of the file.

The error messages should tell you some line numbers, like in my post ("near line 3777", etc.).  The manual correction of this file will be a bit piecemeal.

So start by going to the first line indicated in the error message, and look at the line versus what the error says.  In my case, the error said "invalid package name `kdebase-aud)olibs': character `)' not allowed - only letters, digits and -+._ allowed" -- so there was a syntax error, with the offending text quoted: the odd parenthesis in "kdebase-aud)olibs".

I removed the ) from "kdebase-aud)olibs", saved the file, and continued down the list of error messages until I finished with all the lines noted.

Then I reran 'apt-get update' to see if there were any more errors.  If there are, just repeat the process of going down the list, and rerun apt-get once you are done.  Eventually, all the corrections needed should be there and you will no longer get the error, and apt-get will work properly from that point on.

Hope this helps!

---

### Post by cmire on 2007-12-25
Hi rendral,

One more detail I overlooked -- in the quoted text with the odd parenthesis, "kdebase-aud)olibs" -- the ) character had to be replaced by the letter 'i'.  Otherwise it would spell "kdebase-audolibs" -- which is still incorrect, just no longer a syntax error.

Just pay attention to stuff like that, so the corrections make some kind of linguistic sense versus something strange.

Cheers,
Charles

---

### Post by waterspider on 2008-03-14
please how can i open the dpkg file? help i have the same problem too

---

### Post by plucky on 2008-03-14
> please how can i open the dpkg file? help i have the same problem too


First make a copy of the file ```
sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.old
``` just in case something goes wrong.

Then open the file with your favourite editor,I have used gedit ```
gksudo gedit /var/lib/dpkg/status
```

Good Luck

---

### Post by waterspider on 2008-03-17
whenever i run the command i got this error message 


Could not open the file /var/lib/dpkg/status using the Unicode (UTF-8) character coding.

---

### Post by Jeremy23 on 2008-07-08
I fixed mine by doing:

```
sudo rm /var/lib/apt/lists/*
```

---

