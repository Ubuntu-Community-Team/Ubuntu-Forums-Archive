---
title: "Can't boot after Distro Upgrade!!!"
date: 2017-07-17
forum: Installation &amp; Upgrades
---

### Post by spencer2 on 2017-07-17
I have Ubuntu 16 & got the dist-upgrade message today (like just a couple hours ago), so I ran the upgrade, rebooted & now my laptop won't boot up. It just keeps blinking over & over again like its trying to boot but then the screen goes black & it just does it again. 
Help me please please please. 
I have an acer aspire f15.

The "Ubuntu Studio" screen comes on like normal, a single line of sda stuff pops up counting files but then it just blinks black & keeps repeating the line reading & goes black again.

even when I try to boot into safe mode, it wont boot that way. i am able to get into BIOS by way of F2, but no F8, 10 & 12 gets out of the loop.

I did get into safe mode but don't know what to run from there

---

### Post by BenginM on 2017-07-17
Salutations!

from recovery (safe) mode drop to a root shell , and type:

```

[COLOR=#000080]mount -o remount,rw /
dpkg --configure -a
apt-get -f install
[COLOR=#000080]fsck -f[/COLOR]
mount -o remount,ro /
sync
reboot[/COLOR]

```

##
[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

---

### Post by spencer2 on 2017-07-17
I ran the 'dpkg --configure' command and it seemed to have timed out and is reading 

"Dependency failed for Swap"

there are 2 files that I keep seeing when running upgrades --

"all/all"
"all/allfiles"

1) how long do I need to let the dpkg configure command run & what should I see if it does (or doesn't work)?
2) any thoughts about the 'all' files?

nothing seems to happen after dependency fail & running the apt-get doesn't do anything (a prompt is not returned after failed swap)

---

### Post by spencer2 on 2017-07-18
I fiddled around some & am back into my main Ubuntu, but when I do updates I'm getting some error messages. 

```
W: The repository 'http://deb.bitmask.net/debian trusty Release' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/bitmask.list:1 and /etc/apt/sources.list.d/bitmask.list:2
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list.d/bitmask.list:1 and /etc/apt/sources.list.d/bitmask.list:2
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/bitmask.list:1 and /etc/apt/sources.list.d/bitmask.list:2
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/bitmask.list:1 and /etc/apt/sources.list.d/bitmask.list:2
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/bitmask.list:1 and /etc/apt/sources.list.d/bitmask.list:2
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/bitmask.list:1 and /etc/apt/sources.list.d/bitmask.list:2
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list.d/bitmask.list:1 and /etc/apt/sources.list.d/bitmask.list:2
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/bitmask.list:1 and /etc/apt/sources.list.d/bitmask.list:2
W: The repository 'http://archive.ubuntu.com/ubuntu stable Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/stable/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/stable/main/binary-i386/Packages)  404  Not Found [IP: 91.189.88.149 80]
E: Some index files failed to download. They have been ignored, or old ones used instead.
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/bitmask.list:1 and /etc/apt/sources.list.d/bitmask.list:2
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list.d/bitmask.list:1 and /etc/apt/sources.list.d/bitmask.list:2
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/bitmask.list:1 and /etc/apt/sources.list.d/bitmask.list:2
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/bitmask.list:1 and /etc/apt/sources.list.d/bitmask.list:2
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/bitmask.list:1 and /etc/apt/sources.list.d/bitmask.list:2
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/bitmask.list:1 and /etc/apt/sources.list.d/bitmask.list:2
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list.d/bitmask.list:1 and /etc/apt/sources.list.d/bitmask.list:2
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/bitmask.list:1 and /etc/apt/sources.list.d/bitmask.list:2


```

there is also an error message in the package manager notification along my appelet panel: error opening a cache, permission denied for ifstream in the /etc/apt/sources.list

help pretty please.

---

### Post by BenginM on 2017-07-18
Well, it is as it says: you have sources configured multiple times in /etc/apt/sources.list 

Is your /etc/apt/sources.list not readable or something... you didn't disabled unofficial sources before the upgrade, right! 

if you do $ ls -l /etc/apt/sources.list , what permissions do you see! mine is :
```

[COLOR=#000080]sm@tru:/$ ls -l /etc/apt/sources.list
-rw-r--r-- 1 root root 3097 Jul 13 23:21 /etc/apt/sources.list
sm@tru:/$ [/COLOR]

```

which Ubuntu you're flyin' .. here is the official repo sources list from my system Ubuntu 16.04

[http://sprunge.us/BZHH](http://sprunge.us/BZHH)

you need to adjust it to your Ubuntu version/codename . after that run apt update .

---

### Post by spencer2 on 2017-07-18
I've actually gotten the duplicate message a couple times & have  looked for the duplicate multiple times and maybe I just don't know what  I'm looking at (which is a distinct possibility). Th  is is what I get  when use the "ls -l" command in the /etc/apt directory.

> Aspire-F5-571T:/etc/apt$ ls -l
total 76
drwxr-xr-x 2 root root  4096 Jul 18 09:46 apt.conf.d
drwxr-xr-x 2 root root  4096 Apr 14  2016 preferences.d
-rw------- 1 root root   236 Jul 17 18:29 sources.list
drwxr-xr-x 2 root root  4096 Jul 17 18:29 sources.list.d
-rw-rw-r-- 1 root root  3008 Jun 12 20:52 sources.list.save
-rw-r--r-- 1 root root 22538 Jul 18 08:36 trusted.gpg
-rw-r--r-- 1 root root 25348 Jul 18 08:36 trusted.gpg~
drwxr-xr-x 2 root root  4096 Jul 18 08:36 trusted.gpg.d



1,2,4 & 8 are the folders; the others are just files.

---

### Post by deadflowr on 2017-07-18
It says you have two lines that are duplicates in the same file
look at
```
cat /etc/apt/sources.list.d/bitmask.list
```
but I think that's part of the problem.
The other problem is that archive doesn't seem to be properly signed.
And then there is the only actual error which is for the failed to fetch for the Ubuntu archives...
I do not think the archive that fails actually exists.
Post the out for
```
cat /etc/apt/sources.list
```

---

### Post by spencer2 on 2017-07-18
ran cat /etc/apt/sources.list and it says "No such file or directory"
and on cat /etc/apt/sources.list.d/bitmask.list returns 
deb [http://deb.bitmask.net/debian](http://deb.bitmask.net/debian) trusty main
deb [http://deb.bitmask.net/debian](http://deb.bitmask.net/debian) trusty main

---

### Post by deadflowr on 2017-07-18
Run
```
sudo chmod 755 /etc/apt/sources.list
```

Also open a text editor as root (sudo) and delete one of those lines in the /etc/apt/sources.list.d/bitmask.list file.
(You only need one line)
Easiest way is to run
```
sudo nano /etc/apt/sources.list.d/bitmask.list
```
then go to the end and use backspace to delete the line.
Then press ctrl + X to save and exit,
(press Y to accept the changes and then double check that the file is correct (the same as what it was when you opened, usualy is) and press enter to exit.)

Then post the output for the 
```
cat /etc/apt/sources.list
```
again.

---

### Post by spencer2 on 2017-07-18
a couple of quick questions (forgive me please) -- the "nano" command is just the 'in-terminal' text editor? does the same as gedit filename except all within the terminal {doesn't open gedit externally}? (and does "nano" do that for all the files?) These are all the same as the GUI side of just going to the apt folder & deleting the 2nd url? 

Thank you again: it is greatly appreciated. I'll run commands update.

---

### Post by spencer2 on 2017-07-18
ran the commands: here's the cat output

Aspire-F5-571T:/etc/apt/sources.list.d$ cat /etc/apt/sources.list
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) stable main # auto generated by ubuntu-release-upgrader
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty main # auto generated by ubuntu-release-upgrader

---

### Post by spencer2 on 2017-07-18
ran commands: the output for "cat"

```
Aspire-F5-571T:/etc/apt/sources.list.d$ cat /etc/apt/sources.list
deb http://archive.ubuntu.com/ubuntu yakkety main
deb http://archive.ubuntu.com/ubuntu stable main # auto generated by ubuntu-release-upgrader
deb http://archive.ubuntu.com/ubuntu trusty main # auto generated by ubuntu-release-upgrader
```

---

### Post by deadflowr on 2017-07-18
> **spencer2 said:**
> a couple of quick questions (forgive me please) -- the "nano" command is just the 'in-terminal' text editor? does the same as gedit filename except all within the terminal {doesn't open gedit externally}? (and does "nano" do that for all the files?) These are all the same as the GUI side of just going to the apt folder & deleting the 2nd url? 

Thank you again: it is greatly appreciated. I'll run commands update.
Yes, nano is a command-line based text editor, and will do the same thing as using gedit would.
If you want to use gedit to remove the lines in these files you need to gui sudo app known as gksu, or
use sudo -H like
```
sudo -H gedit /etc/apt/sources.list
```
sudo does not play well with graphical apps, so using option like -H help it not break things.
If that makes sense.
> **spencer2 said:**
> ran the commands: here's the cat output

Aspire-F5-571T:/etc/apt/sources.list.d$ cat /etc/apt/sources.list
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) stable main # auto generated by ubuntu-release-upgrader
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty main # auto generated by ubuntu-release-upgrader
hmm, odd.
well, what release is it suppose to be, 14.04 or 17.04?
I'm guessing 17.04(yakkety), and if so you can delete the entries for the other two lines 
(the ones for stable and trusty)
You should never mix releases.

You can also simply comment out the other entries by adding a # to the front so they look like
```
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) yakkety main
#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) stable main # auto generated by ubuntu-release-upgrader
#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty main # auto generated by ubuntu-release-upgrader
```
this will allow you to keep the entries in case they weren't the right ones to remove and also it sets them as not readable by the system and so they'll be ignored.

Sorry, I meant 16.10 is yakkety.

---

### Post by spencer2 on 2017-07-18
Thank you very very much. I did the edits through nano & am content  with that. thank you for the answer. I've actually just started studying  for lpic 1 & 2 tests, so I greatly appreciate your help. I was  trying to upgrade to the yakkety & the upgrade stalled in the middle  & I'm assuming I just had stuff out of whack. I commented out the  lines as you showed, ran "cat" & got:

```
Aspire-F5-571T:/etc/apt/sources.list.d$ cat /etc/apt/sources.list
deb http://archive.ubuntu.com/ubuntu yakkety main
#deb http://archive.ubuntu.com/ubuntu stable main # auto generated by ubuntu-release-upgrader
#deb http://archive.ubuntu.com/ubuntu trusty main # auto generated by ubuntu-release-upgrader


```

should this take care of things?

---

### Post by spencer2 on 2017-07-18
I ran update & upgrade and got:

```
Aspire-F5-571T:/etc/apt/sources.list.d$ sudo apt-get update && sudo apt-get upgrade
Ign:1 http://deb.bitmask.net/debian trusty InRelease
Ign:2 http://dl.google.com/linux/chrome/deb stable InRelease               
Hit:3 http://deb.bitmask.net/debian trusty Release                         
Hit:4 http://dl.google.com/linux/chrome/deb stable Release                 
Ign:5 http://deb.bitmask.net/debian trusty Release.gpg                   
Hit:7 http://archive.ubuntu.com/ubuntu yakkety InRelease                 
Reading package lists... Done
W: The repository 'http://deb.bitmask.net/debian trusty Release' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
spencerownside@spencerownside-Aspire-F5-571T:/etc/apt/sources.list.d$ 

```

also, do you know anything about a couple of files called?

```
/all/all
/all/allfiles
```

---

### Post by deadflowr on 2017-07-18
Looking at bitmask it seems there are no packages for it for either 14.04 trusty or 16.10 yakkety
(I added an apology at the end of my previous post for calling yakkety 17.04)
You might need to comment out the line in that file, or follow theuir how-to remove it from their install page:
[https://bitmask.net/en/install/linux]("https://bitmask.net/en/install/linux")

I think the /all files are related to the packaging and installation structure of said packages.

---

