---
title: "Media Player package Problem &amp; VLC not installing"
date: 2010-07-03
forum: Installation &amp; Upgrades
---

### Post by cpcpcp on 2010-07-03
[SIZE=2]Fresh Newly installed 10.04 but Totem seems not to want to install packages for .avi .mp3 or .wmv and VLC just will not install. Finding the packages to install for say AVI into Totem and getting ready it comes up with message corrupt packages cannot install 'til fixed.
According to Synaptic Package Manager there are no corrupt packages.

[COLOR=Navy]I have removed and reinstalled Totem  through package manager.
I have removed and installed TOTEM using 
*sudo apt-get install totem-gstreamer*
but still I cannot install what it takes to play any file.
[/COLOR]
Trying to Install VLC through the Ubuntu software centre I was told 
"Package dependencies could not be resolved"
details :- vlc

And I thought Ubuntu would be simple.
**Where do I start, what do I do?**[/SIZE]

---

### Post by wookieshaver on 2010-07-04
The first step would be get the codecs needed for mp3/avi/wmp play. Heres a simple guide to get these (its in step three):
 
[http://www.omgubuntu.co.uk/2010/04/10-things-to-do-after-installing-ubuntu.html](http://www.omgubuntu.co.uk/2010/04/10-things-to-do-after-installing-ubuntu.html)
 
Then if the package manager is still giving you grief trying to install vlc. You can manually get the packages needed following the advice here:
 
[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)
 
Or, if you are tired of links, you can open up a console and type:
 
sudo apt-get update
 
( hit enter and then)
 
sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc

Hopefully this gets you back where you want to be!

---

### Post by efflandt on 2010-07-05
Normally you would install **ubuntu-restricted-extras** using Synaptic package manager, which installs most codecs and other things that you need for media playing, and the package description also tells you what to do for DVD's to work.

Then likewise you would install **vlc** using Synaptic.

Otherwise if you do it in bits and pieces and do not really know what you need, you might be missing something.

---

### Post by cpcpcp on 2010-07-05
> **wookieshaver said:**
> The first step would be get the codecs needed for mp3/avi/wmp play. Heres a simple guide to get these (its in step three):
 
[http://www.omgubuntu.co.uk/2010/04/10-things-to-do-after-installing-ubuntu.html](http://www.omgubuntu.co.uk/2010/04/10-things-to-do-after-installing-ubuntu.html)
 
Then if the package manager is still giving you grief trying to install vlc. You can manually get the packages needed following the advice here:
 
[http://www.videolan.org/vlc/download-ubuntu.html](http://www.videolan.org/vlc/download-ubuntu.html)
 
Or, if you are tired of links, you can open up a console and type:
 
sudo apt-get update
 
( hit enter and then)
 
sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc

Hopefully this gets you back where you want to be!

Afraid not.

I followed your first link and was told the packages were aleady installed.
So I trustingly went off and clicked on an .AVI file and was told it needed a plugin so I agreed to install what it wanted
gstreamer0.10-ffmpg
and then when it tried to do whatever it does the same old box came up - "
" Could not apply changes. Fix broken packages first."

I decided not waste my time and yours trying to install VLC again as one refusal a night is enough for me.


[SIZE=3]I do not know if there is any relevance here but in windows (I have dual boot) I have seen today that all my files folders etc have suddenly bee marked Read Only ( and it does not seem to want to change that attribute).
Could the Ubuntu stuff somehow also have become read only? How do I check this and if it is how do I change it back?

Chris
[/SIZE]

---

### Post by cpcpcp on 2010-07-05
> **efflandt said:**
> Normally you would install **ubuntu-restricted-extras** using Synaptic package manager, which installs most codecs and other things that you need for media playing, and the package description also tells you what to do for DVD's to work.

Then likewise you would install **vlc** using Synaptic.

Otherwise if you do it in bits and pieces and do not really know what you need, you might be missing something.

Er I had (I thought) been using the package manager thing and following the instructions and got nothing - same with VLC installation.

[SIZE=3]But see my comment above on the windows file system files system[/SIZE] and let me know in simple terms if it may be the cause of the problems and if so how do I check it and  fix it.
Thanks

Chris

---

### Post by efflandt on 2010-07-05
You might try the following to attempt to fix broken packages:

**sudo apt-get -f install**

Are you running Ubuntu from a separate partition, or did you use Wubi to install it within a Windows partition?  The latter may make a difference if you are saying that Windows files are showing as "read only" when you boot Windows.

To see if directories or files have write permission in Linux from a terminal in a particular directory you can do:

**ls -l** (small L for long listing) or **ls -al** (to also show hidden files)

For a dir the first letter will be **d** then **rwx** would indicate if it has read/write permission for the owner, but **x** for a directory is not for execute permission, it means that you can access the dir for a directory listing.  The 2nd group of letters, typically r-x would be permissions for group, and 3rd set would be for others. A dir with drwx------ would only have permissions for the owner.

For files rwx are for read, write, or execute.  At least the owner should have read and write permission (-rw------- as a minimum).

---

### Post by cpcpcp on 2010-07-06
> **efflandt said:**
> You might try the following to attempt to fix broken packages:

**sudo apt-get -f install**

.

did that  and got this

```
 user@user-desktop:~$ sudo apt-get -f install
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 49 not upgraded.

```>  Are you running Ubuntu from a separate partition, or did you use Wubi to  install it within a Windows partition?  The latter may make a  difference if you are saying that Windows files are showing as "read  only" when you boot Windows.

To see if directories or files have write permission in Linux from a  terminal in a particular directory you can do:

**ls -l** (small L for long listing) or **ls -al** (to also show  hidden files)

For a dir the first letter will be **d** then **rwx** would  indicate if it has read/write permission for the owner, but **x** for  a directory is not for execute permission, it means that you can access  the dir for a directory listing.  The 2nd group of letters, typically  r-x would be permissions for group, and 3rd set would be for others. A  dir with drwx------ would only have permissions for the owner.

For files rwx are for read, write, or execute.  At least the owner  should have read and write permission (-rw------- as a minimum)Ah you assumed I knew what I was doing:p

can run terminal 
can do what you say
can change directories
but  have not yet figured out how to change drives:confused: and who knows what "dirs -clpv" does ;- NOT ME and I was too timid to try (and create another problem - no thanks).

[SIZE=3]I can hear the laughter but am new and lost here guys[/SIZE].
 

I did try and help myself and perhaps the answer was here [http://https://help.ubuntu.com/9.10/basic-commands/C/]("http://https//help.ubuntu.com/9.10/basic-commands/C/") but I could not find it.

Enough I am off to bed but one last question - what is going on here?? no Public directory when I see it!

```
 user@user-desktop:~$ ls
Desktop    Downloads         Music     Public     Videos
Documents  examples.desktop  Pictures  Templates
user@user-desktop:~$ cd/Public
bash: cd/Public: No such file or directory

```(None of this, "interesting" as it might be, solves my original problem it just gets me more frustrated)
Chris

---

### Post by cpcpcp on 2010-07-06
[SIZE=3]IT GETS WORSE.

I tried to install clamav-demon and just like trying to install VLC up popped the message:-

"Package dependencies cannot be resolved"
"[SIZE=2]This error could be caused by requiring additional software packages which are missing or not installable. Alternatively, there could be a conflict between software packages which are not allowed to be installed at the same time."
Details
"clamav-demon"
[SIZE=3]
A mirror of the problem message I had when trying to install VLC

[SIZE=1]I wish I had gone to bed when I said I would

Chris
[/SIZE][/SIZE][/SIZE][/SIZE]

---

