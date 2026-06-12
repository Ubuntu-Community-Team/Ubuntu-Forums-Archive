---
title: "upgrade fails - &quot;Failed to read mirror file&quot; @ security.ubuntu.com"
date: 2008-01-07
forum: Installation &amp; Upgrades
---

### Post by silvari on 2008-01-07
Attempting an upgrade from Edgy to Feisty (hoping to get it to Gutsy eventually).  Note dates below.

Using: System \ Administration \ Update Manager

The update fails with:

"Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)"

in /var/log/dist-upgrade/apt.log , I see:

[INDENT]bzip2: Compressed file ends unexpectedly;
	perhaps it is corrupted?  *Possible* reason follows.
bzip2: Inappropriate ioctl for device
	Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

bzip2: (stdin) is not a bzip2 file.
bzip2: (stdin) is not a bzip2 file.
bzip2: (stdin) is not a bzip2 file.
bzip2: (stdin) is not a bzip2 file.
bzip2: (stdin) is not a bzip2 file.
WARNING: **Failed to read mirror file**[/INDENT]

So, I first tried this (with failure) on 1/1/08. Have tried several times since, same result. However, if I browse to the following URL, the timestamp has changed:

[INDENT][http://**security.ubuntu.com**/ubuntu/dists/feisty-security/main/binary-i386/](http://**security.ubuntu.com**/ubuntu/dists/feisty-security/main/binary-i386/)[/INDENT]

And, if I 'manually' download it, I'm able to **_successfully_** unzip / expand the file 'Packages.bz2' with no problems.

Any ideas?

---

### Post by zvacet on 2008-01-07
Try to refresh your source list with 

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by silvari on 2008-01-07
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/102511](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/102511) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				zvacet,

First, a big THANK YOU for replying to the post - and for suggesting something that works.

I've run the command 

[INDENT]sudo apt-get update && sudo apt-get upgrade[/INDENT]

... as you suggested, and then re-ran the Update Manager GUI, and it's now working.  :)

Can you provide any insight about why it was necessary to do this step? My understanding has been that using the GUI Update Manager (Ubuntu's "recommended method) would obviate the performing of any CLI commands, for doing upgrades. But instead, it seems to be a critical step. What did this do, that Update Manager did not / could not do, on its own?

Thanks again.
- Rick

---

### Post by Partyboi2 on 2008-01-07
To have done the same thing with Synaptic you would have pressed "Reload" then "Mark all upgrades"

---

### Post by zvacet on 2008-01-07
To use update manager your distro must be up-to-date.With CLI commands you just make sure that is the case (you are refreshing your source list).After that you can use update manager to upgrade to new version.

---

### Post by jthiel on 2008-06-03
Ok, I am totally missing something.

I have kept my 6.10 up to date for almost 2 years.  Figured its time to move up.  I know i have to go to 7.04.  So I ran my update manager and clicked the update now button.  I am getting this error (the first in a list of similar errors):

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz) 404 Not Found

I've been searching through forums etc for several hours now.  I managed to get the partial answer above and ran:
sudo apt-get update && sudo apt-get upgrade

The sudo apt-get update appears to fail with a bunch of 404 errors including this one:
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz)  404 Not Found

Using firefox, I browsed to [http://security.ubuntu.com/ubuntu/dists/](http://security.ubuntu.com/ubuntu/dists/) and lo and behold, NO edgy directory.  

What gives?  Is edgy no longer supported?  How do i get this darn update manager to work?

If I run update manager and hit the check button, I get something very similar (bunch of 404s with the security.ubuntu.com, archive.ubuntu.com, etc).  

Oh, my network connection is obviously fine as I'm on this site now!
Thanks for any insight.

---

### Post by drazel on 2008-06-04
Hello!

I am having the same problem when trying to run apt-get update on  ubuntu 6.10 server.

I got 404 error messages, and when I checked [http://fr.archive.ubuntu.com/ubuntu/dists/](http://fr.archive.ubuntu.com/ubuntu/dists/)

i cannot find any edgy directory. :confused:

Can someone tell me what is going on ?

---

