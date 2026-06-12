---
title: "APT dying or dead"
date: 2007-12-07
forum: Installation &amp; Upgrades
---

### Post by hanksims on 2007-12-07
APT, Update Manager and Synaptic are all broken on my system right now. Here's the output when I try to install a common program from the command line. I've bolded what seems to be the key phrase:

> Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe xchat-common 2.8.4-0ubuntu5 [1050kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe xchat 2.8.4-0ubuntu5 [308kB]
Fetched 1358kB in 7s (177kB/s)                                                 
Selecting previously deselected package xchat-common.
(Reading database ... dpkg: error processing /var/cache/apt/archives/xchat-common_2.8.4-0ubuntu5_all.deb (--unpack):
** files list file for package `coreutils' is missing final newline**
Errors were encountered while processing:
 /var/cache/apt/archives/xchat-common_2.8.4-0ubuntu5_all.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

I get some version of this error message whatever I try to do with apt-get or Synaptic or Update Manager -- "file for package coreutils in missing final newline."

Any ideas?

---

### Post by MrFSL on 2007-12-07
perhaps:
```

sudo apt-get update
sudo apt-get -f install
```

will fix your problem

---

### Post by hanksims on 2007-12-07
MrFSL: No joy. 

It looks like what I've got is a [version of this right here]("http://groups.google.com/group/lolug/browse_thread/thread/62c52aa0923994b4#9f4f5aff216f6b14"), only worse because the error is popping up in coreutils. I can't just purge coreutils, can I?

---

### Post by PmDematagoda on 2007-12-07
Try this:-

```
sudo rm /var/cache/apt/archives/xchat-common_2.8.4-0ubuntu5_all.deb
```

After that is removed do:-

```
sudo apt-get update
```

Then see if the problem is solved.

---

### Post by hanksims on 2007-12-08
PmDematagoda: That's not it. The problem is with coreutils, not xchat. Xchat was just an example; apt was broken before I tried to install it.

---

### Post by bapoumba on 2007-12-08
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/108189](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/108189) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Please have a look at the bug report. There are references to threads with fixes that worked at least for some users. Not simple.

---

### Post by hanksims on 2007-12-08
bapoumba: Yes, that looks like it. Thanks.

Guess I gotta roll up my sleeves...

---

### Post by bapoumba on 2007-12-08
Okay, I googled the error " files list file for package ` ' is missing final newline" which I think is the central one.

[http://www.linuxquestions.org/questions/debian-26/apt-get-dpkg-error-files-list-file-...-missing-final-newline-271118/](http://www.linuxquestions.org/questions/debian-26/apt-get-dpkg-error-files-list-file-...-missing-final-newline-271118/)
[https://lists.ubuntu.com/archives/ubuntu-users/2007-January/104520.html](https://lists.ubuntu.com/archives/ubuntu-users/2007-January/104520.html)

Hope this helps. Good luck :)

---

### Post by hanksims on 2007-12-09
OK, this turned out to be a fairly major problem. I'm amazed that I recovered from it, but somehow I have. So I'll note how I did it here, in case others someday find themselves in the same boat.

Turns out that the root problem was that I had very serious filesystem errors, probably due to a bad shutdown. This I figured out when my computer refused to reboot last night. I booted into recovery mode, and the automatic fsck check failed.

So I booted up the Live CD and manually fsck'd my filesystem. Fsck fixed what seemed to be 1000 errors, and I was able to boot into my system again.

That still didn't fix my APT issue, though. It turned out that a whole bunch of (package).list files had been corrupted -- maybe 10 or so. Here's how I figured this out. I tried to employ the solution suggested by bapoumba in the following link:

 [http://www.linuxquestions.org/questions/debian-26/apt-get-dpkg-error-files-list-file-...-missing-final-newline-271118/](http://www.linuxquestions.org/questions/debian-26/apt-get-dpkg-error-files-list-file-...-missing-final-newline-271118/)

In other words, I deleted the offending .list file, figuring I'd purge the package and reinstall it. But APT wouldn't let me purge the package, because now another package was getting in the way. I then identified all of the screwed-up (package).list files using "Search For Files..." in the Places menu. I searched the /var/lib/dpkg/info/ folder with "*.list", then sorted by filetype. All the screwed-up files showed at the bottom -- their filetype was "unknown" -- while all the working .list files showed up as either text files (usually) or bash scripts (occassionally).

So now I had a list of all my problem packages. Perhaps I could have tried to purge them all and reinstall, as above, but I was hesitant to purge some of them -- like coreutils -- because I was afraid that it would screw up my system for good. So instead I set out to rebuild the screwed-up .list files from the .deb packages, using the instructions found here (under Q5.19):

[http://finkproject.org/faq/usage-fink.php](http://finkproject.org/faq/usage-fink.php)

I went through the bad .list files one my one and rebuilt them according to this recipe. It worked. Of course you have to adapt it to the Ubuntu filesystem. In Ubuntu, the cached APT packages are in /var/cache/apt/archives/ and the dpkg .list files are in /var/lib/dpkg/info/.

> dpkg -c /var/cache/apt/archives/debfile.deb  | awk '{if ($6 == "./"){ print "/."; } \
else if (substr($6, length($6), 1) == "/")\
{print substr($6, 2, length($6) - 2); } \
else { print substr($6, 2, length($6) - 1);}}'\ 
> /var/lib/dpkg/info/packagename.list

You've gotta do it from a root shell (run "sudo bash"). If you don't have the DEB package in your cache, you can use ... 

sudo apt-get install --reinstall --download-only packagename

...to get it. Remember that the name of the .deb file probably isn't exactly the same as the package name. (The .deb file's name will include version numbers, etc.)

Rebuild all the screwed-up .list files one by one. Get to the finish. Voila! APT is back up and running.

Thanks, world!

---

### Post by bapoumba on 2007-12-09
Wow.. Warmest congratulations, and thanks for coming back to post a solution! Impressive.

---

### Post by hanksims on 2007-12-09
bapoumba: I stand on the shoulders of giants. Thanks for your help!

---

