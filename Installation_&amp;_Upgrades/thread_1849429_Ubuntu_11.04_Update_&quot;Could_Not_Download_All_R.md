---
title: "Ubuntu 11.04 Update: &quot;Could Not Download All Repository Indexes&quot;"
date: 2011-09-24
forum: Installation &amp; Upgrades
---

### Post by jmk08 on 2011-09-24
Hello all,

     For thee days now, the red exclamation point triangle has been showing on the top right task bar of my 11.04 classic. Upon attempting to update, I receive:
------------
Failed to fetch [http://ppa.launchpad.net/n-muench/bur/ubuntu/dists/natty/main/source/Sources](http://ppa.launchpad.net/n-muench/bur/ubuntu/dists/natty/main/source/Sources)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/n-muench/bur/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/n-muench/bur/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found
Some index files failed to download. They have been ignored, or old ones used instead.
------------
     This error has essentially stupefied me lol. Help ye wise ones!

General System:
Ubuntu 11.04
Asus U36SD with Ubuntu Nvidia drivers installed.

---

### Post by dino99 on 2011-09-24
you are trying to get packages from links that does not exist :(

[http://ppa.launchpad.net/n-muench/](http://ppa.launchpad.net/n-muench/)

---

### Post by Old_Grey_Wolf on 2011-09-24
Read my next post before you do this.

```
gksudo gedit /etc/apt/sources.list
```

Change the lines with [http://ppa.launchpad.net/n-muench/bur/](http://ppa.launchpad.net/n-muench/bur/)... to [http://ppa.launchpad.net/n-muench/burg/](http://ppa.launchpad.net/n-muench/burg/)...
The "g" is missing.

---

### Post by Old_Grey_Wolf on 2011-09-24
Hello again jmk08,

With Calculus+Biology+Chemistry you still have time to play with the Burg boot loader?

[COLOR="DarkRed"]You may want to read about reinstalling Grub2 from the Live USB or CD before messing with the boot loader. If something goes wrong with the Burg install you may have troubles getting the computer to boot.
[/COLOR]
[I]For future reference this is how I derived the solution to the Repository Index problem:

1.  I clicked on the link in your post ://ppa.launchpad.net/n-muench/bur/ubuntu/dists/natty/main/source/Sources and got a 404 error

2.  I removed part of the link a /blahblah/ one at a time until i did not get a 404 error
[INDENT]://ppa.launchpad.net/n-muench/bur/ubuntu/dists/natty/main/source/
://ppa.launchpad.net/n-muench/bur/ubuntu/dists/natty/main/
://ppa.launchpad.net/n-muench/bur/ubuntu/dists/natty/
...
://ppa.launchpad.net/n-muench/bur[/INDENT]

3.  When the link was only ://ppa.launchpad.net/n-muench/ I got a list of files and directories where burg (not bur) was listed
[INDENT]Index of /n-muench
[ICO]	Name	Last modified	Size
[DIR]	Parent Directory	 	-
[DIR]	[COLOR="Red"]burg/[/COLOR]	28-Apr-2011 03:36 	-
[DIR]	bzr/	15-Feb-2011 04:25 	-
[DIR]	bzr2/	15-Feb-2011 04:35 	- 
...
__________________________________________
Apache/2.2.14 (Ubuntu) Server at ppa.launchpad.net Port 80[/INDENT]

4.  I put the g on the end of bur in the original link (://ppa.launchpad.net/n-muench/bur[COLOR="Red"]g[/COLOR]/ubuntu/dists/natty/main/source/Sources) and a file was displayed rather that the 404 error
[INDENT]Package: burg
Binary: burg, burg-common, burg-pc, burg-emu
Version: 1.98+20100623-1
...

Package: burg-themes
Binary: burg-themes, burg-themes-common
Version: 1.98+20100623-1
...
[/INDENT]



I hope this helps you in the future.[/I]

---

### Post by klein8 on 2011-10-05
> **Old_Gray_Wolf said:**
> Hello again jmk08,

With Calculus+Biology+Chemistry you still have time to play with the Burg boot loader?

[COLOR=DarkRed]You may want to read about reinstalling Grub2 from the Live USB or CD before messing with the boot loader. If something goes wrong with the Burg install you may have troubles getting the computer to boot.
[/COLOR]
[I]For future reference this is how I derived the solution to the Repository Index problem:

1.  I clicked on the link in your post ://ppa.launchpad.net/n-muench/bur/ubuntu/dists/natty/main/source/Sources and got a 404 error

2.  I removed part of the link a /blahblah/ one at a time until i did not get a 404 error[INDENT]://ppa.launchpad.net/n-muench/bur/ubuntu/dists/natty/main/source/
://ppa.launchpad.net/n-muench/bur/ubuntu/dists/natty/main/
://ppa.launchpad.net/n-muench/bur/ubuntu/dists/natty/
...
://ppa.launchpad.net/n-muench/bur[/INDENT]3.  When the link was only ://ppa.launchpad.net/n-muench/ I got a list of files and directories where burg (not bur) was listed[INDENT]Index of /n-muench
[ICO]    Name    Last modified    Size
[DIR]    Parent Directory         -
[DIR]    [COLOR=Red]burg/[/COLOR]    28-Apr-2011 03:36     -
[DIR]    bzr/    15-Feb-2011 04:25     -
[DIR]    bzr2/    15-Feb-2011 04:35     - 
...
__________________________________________
Apache/2.2.14 (Ubuntu) Server at ppa.launchpad.net Port 80[/INDENT]4.  I put the g on the end of bur in the original link (://ppa.launchpad.net/n-muench/bur[COLOR=Red]g[/COLOR]/ubuntu/dists/natty/main/source/Sources) and a file was displayed rather that the 404 error[INDENT]Package: burg
Binary: burg, burg-common, burg-pc, burg-emu
Version: 1.98+20100623-1
...

Package: burg-themes
Binary: burg-themes, burg-themes-common
Version: 1.98+20100623-1
...
[/INDENT]

I hope this helps you in the future.[/I]

I tried this way ,but it does nothing. I mean it doesn't work in my system.:(

---

### Post by klein8 on 2011-10-05
> **Old_Gray_Wolf said:**
> Hello again jmk08,

With Calculus+Biology+Chemistry you still have time to play with the Burg boot loader?

[COLOR=DarkRed]You may want to read about reinstalling Grub2 from the Live USB or CD before messing with the boot loader. If something goes wrong with the Burg install you may have troubles getting the computer to boot.
[/COLOR]
[I]For future reference this is how I derived the solution to the Repository Index problem:

1.  I clicked on the link in your post ://ppa.launchpad.net/n-muench/bur/ubuntu/dists/natty/main/source/Sources and got a 404 error

2.  I removed part of the link a /blahblah/ one at a time until i did not get a 404 error[INDENT]://ppa.launchpad.net/n-muench/bur/ubuntu/dists/natty/main/source/
://ppa.launchpad.net/n-muench/bur/ubuntu/dists/natty/main/
://ppa.launchpad.net/n-muench/bur/ubuntu/dists/natty/
...
://ppa.launchpad.net/n-muench/bur[/INDENT]3.  When the link was only ://ppa.launchpad.net/n-muench/ I got a list of files and directories where burg (not bur) was listed[INDENT]Index of /n-muench
[ICO]    Name    Last modified    Size
[DIR]    Parent Directory         -
[DIR]    [COLOR=Red]burg/[/COLOR]    28-Apr-2011 03:36     -
[DIR]    bzr/    15-Feb-2011 04:25     -
[DIR]    bzr2/    15-Feb-2011 04:35     - 
...
__________________________________________
Apache/2.2.14 (Ubuntu) Server at ppa.launchpad.net Port 80[/INDENT]4.  I put the g on the end of bur in the original link (://ppa.launchpad.net/n-muench/bur[COLOR=Red]g[/COLOR]/ubuntu/dists/natty/main/source/Sources) and a file was displayed rather that the 404 error[INDENT]Package: burg
Binary: burg, burg-common, burg-pc, burg-emu
Version: 1.98+20100623-1
...

Package: burg-themes
Binary: burg-themes, burg-themes-common
Version: 1.98+20100623-1
...
[/INDENT]

I hope this helps you in the future.[/I]


.:(
And I want to know how can open the file which contain the above statements.

---

### Post by Old_Grey_Wolf on 2011-10-05
> **klein8 said:**
> .:(
And I want to know how can open the file which contain the above statements.

Are you having the same problem as jmk08 or are you trying to get the Burg boot loader?

---

### Post by subehsharma on 2011-11-10
Best method to getaway from this problem is to install fix404. You can read about it more here:

Under Ubuntu, the APT package index is a database containing all packages of repositories (PPAs) defined in the /etc/apt/sources.list file. To update this database after adding some repositories, we need to use this command from the Terminal:

sudo apt-get update

Sometimes, when running the command given above, we get error messages (404 Not Found) that are the result of wrong PPAs, which may slow down the update process via the Terminal. In fact, this 404 Not Found error messages are not harmful at all, but you can use Fix404 to detect and remove these PPAs.

To install Fix404 on Ubuntu 11.04, launch the Terminal and run these commands:

sudo apt-add-repository ppa:lkjoel/fix404
sudo apt-get update
sudo apt-get install fix404

To install on Ubuntu 10.10/10.04, download this deb package here.

To start using Fix404, run this command (root privileges required):

sudo fix404

Then follow displayed instructions to disable PPAs causing the 404 Not Found Error.

[http://www.upubuntu.com/2011/07/remove-ubuntu-ppas-that-cause-404-not.html](http://www.upubuntu.com/2011/07/remove-ubuntu-ppas-that-cause-404-not.html)

---

### Post by subehsharma on 2011-11-10
[http://www.upubuntu.com/2011/07/remove-ubuntu-ppas-that-cause-404-not.html](http://www.upubuntu.com/2011/07/remove-ubuntu-ppas-that-cause-404-not.html)

---

