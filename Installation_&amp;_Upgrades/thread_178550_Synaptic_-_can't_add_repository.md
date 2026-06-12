---
title: "Synaptic - can't add repository"
date: 2006-05-17
forum: Installation &amp; Upgrades
---

### Post by alfh on 2006-05-17
I have been banging my head against a strange problem for several hours. No luck searching the forums or the net. Hope someone here can help.
](*,) 
Running Norwegian Ubuntu 5.10
1. I open Synaptic then do Settings --> repositories (Innstillinger --> Arkiv)
2. Click Add (legg til)
3. Check all four boxes, click Ok.
4. Click Ok again.
5. Start over. The Universe and multiverse boxes are now NOT checked. ArrGGhH!

Any ideas? Thanks in advance!

---

### Post by zhoux on 2006-05-17
[QUOTE=alfh]I have been banging my head against a strange problem for several hours. No luck searching the forums or the net. Hope someone here can help.
](*,) 
Running Norwegian Ubuntu 5.10
1. I open Synaptic then do Settings --> repositories (Innstillinger --> Arkiv)
2. Click Add (legg til)
3. Check all four boxes, click Ok.
4. Click Ok again.
5. Start over. The Universe and multiverse boxes are now NOT checked. ArrGGhH!

Any ideas? Thanks in advance![/QUOTE]

What do you mean by start over? and did you hit "Reload" after editing the repositories?

---

### Post by Sutekh on 2006-05-17
How about we try this from the command line?  It's very easy to do this.
 
 
Start by opening a Terminal Window (Appications -> Accessories Menu) and then backing up your current sources using this command
 ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
``` Then edit it with your preferred editor, I am using **nano** in this example.  You may prefer **gedit**. If so just swap nano for gedit in the next command.
 ```
sudo nano /etc/apt/sources.list
``` When the editor opens you need to find these lines (they may have a **no.** in front of them, for Norway)
 ```

 # deb http://archive.ubuntu.com/ubuntu breezy universe
 # deb-src http://archive.ubuntu.com/ubuntu breezy universe
 
 ...
 
 # deb http://security.ubuntu.com/ubuntu breezy-security universe
 # deb-src http://security.ubuntu.com/ubuntu breezy-security universe
``` You need to uncomment them - remove the # signs. This enables the universe repository. To enable the multiverse repository, add multiverse to the end of these lines.
 
 It would look something like this when you finish making the changes
 ```

 deb http://archive.ubuntu.com/ubuntu breezy universe **multiverse**
 deb-src http://archive.ubuntu.com/ubuntu breezy universe **multiverse**
  
 ...
 
 deb http://security.ubuntu.com/ubuntu breezy-security universe **multiverse**
 deb-src http://security.ubuntu.com/ubuntu breezy-security universe **multiverse**
``` If you save the file (Ctrl +O if you are using nano) and exit (Ctrl + X iin nano) you can then update the repositories with
 ```
sudo apt-get update
``` Then you are set, and can use Synaptic.

---

### Post by alfh on 2006-05-18
[QUOTE=zhoux]What do you mean by start over? and did you hit "Reload" after editing the repositories?[/QUOTE]

I meant doing the procedure again from the top. And yes, I did reload.

Sutekh; thanks for your advice, it put me on the right track. After backup I did
```
sudo gedit /etc/apt/sources.list
```
and removed everything. Then I started Synaptic and added everything. Now everything works fine

Except,of course, for the repositories dialog in Synaptic:
The main dialog says 'main restricted universe multiverse' like I want it to but if I enter the 'add' dialog universe and multiverse tickboxes are still not checked

Seems like a minor bug I can live with :D

---

### Post by Sutekh on 2006-05-18
I'm glad you got it working.  The problem you are having is why I prefer to do things from the command line.  The GUI's don't make sense to me sometimes, and things like this add to the confusion

---

### Post by no way on 2006-05-25
i have the same problem as alfh.

opened sources.list and get the following:

 [COLOR="DarkRed"][INDENT]deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
 deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe main restricted multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse[/COLOR][/INDENT]

so, everything seems to be activated just fine.... but still i cannot instal apps that need the multiverse repository (i.e. real player). ](*,) 

any ideas?

cheers
fred

---

### Post by Sutekh on 2006-05-25
Ok, so what is the error you are recieving when you try to install something (realplayer)?

```
sudo apt-get update
sudo apt-get install realplayer
```

---

### Post by no way on 2006-05-27
the message i get is:

fred@Fred:~$ sudo apt-get install realplayer
Reading package lists... Done
Building dependency tree... Done
Package realplayer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package realplayer has no installation candidate


what can that be?
i am using ubuntu 5.10 amd64

cheers
fred

---

### Post by Sutekh on 2006-05-27
Realplayer in the Ubuntu repositories is only i386 sorry

[Ubuntu Packages - Realplayer]("http://packages.ubuntu.com/breezy/net/realplayer")

I think you will need to install it this way

[Ubuntu Wiki - Realplayer Installation Methods]("https://wiki.ubuntu.com/RealplayerInstallationMethods")

---

### Post by no way on 2006-05-28
oh shoot, i did not think about this. it's just a pain in the neck all the time with the 64 version, i wish i had chosen the 32bit one.

thanx anyway :-)

fred

---

