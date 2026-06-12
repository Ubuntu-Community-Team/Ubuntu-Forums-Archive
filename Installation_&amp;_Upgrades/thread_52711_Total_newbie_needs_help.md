---
title: "Total newbie needs help \/  \/  \/  \/"
date: 2005-07-28
forum: Installation &amp; Upgrades
---

### Post by Schmoozer3348 on 2005-07-28
For some reason I can't seem to install anything. I got to the terminal and type in the command but there is always the same problem:

logan@dhcp123:~$ sudo apt-get install mplayer-386
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package mplayer-386

I always get the "E: Couldn't find package....." (except for update and upgrade) I went [http://www.ubuntuguide.org](http://www.ubuntuguide.org) and looked around. I got the sudo apt-get upgrade and sudo apt-get update. A friend told me in passing that I may need to "edit my apt list" or to search for "more upgrade sources." So far no luck, any ideas?

Also in rhythembox 0.8.8 when I entered my defualt library folder I was told "There is no plugin installed to handle a MP3 file." about 4000 times in a row. How do I get those plugins?

Thanks guys, sorry for newb-ness ](*,)

---

### Post by Sam on 2005-07-28
Did you [add the extra repositories](http://ubuntuguide.org/#extrarepositories) ?

After that, do```
$ sudo apt-get update
```

To search a package:```
$ apt-cache search <pattern>
```

---

### Post by angkor on 2005-07-28
Please post you /etc/apt/sources.list

And check the [UbuntuGuide](http://www.ubuntuguide.org/#repositories)

---

### Post by Schmoozer3348 on 2005-07-28
[QUOTE=Sam]Did you [add the extra repositories](http://ubuntuguide.org/#extrarepositories) ?

After that, do```
$ sudo apt-get update
```

To search a package:```
$ apt-cache search <pattern>
```[/QUOTE]

Ok here is what I get:

logan@dhcp123:~$ $sudo apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
logan@dhcp123:~$ $ apt-cache search <pattern>
bash: syntax error near unexpected token `newline'



And here is my source list:

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe


Thanks for the quick response
-Logan

---

### Post by angkor on 2005-07-28
Uncomment the Universe repos and save the file. (you'll need to be root, so sudo gedit /etc/apt/sources.list will do).

sudo apt-get update

sudo apt-get install mplayer-386

Don't write <pattern>

write something like apt-cache search mplayer-386

---

### Post by Schmoozer3348 on 2005-07-28
[QUOTE=angkor]Uncomment the Universe repos at the bottom and save the file.[/QUOTE]

I'm sorry I don't understand, do you mean deleteing the number sighs (#) infront of the bottom two lines?

---

### Post by Sam on 2005-07-28
[quote="Schmoozer3348"]E: Unable to lock the list directory[/quote]
This mean that Synaptic is open and you're using apt or vice-versa. Close any package application and try again.

---

### Post by angkor on 2005-07-28
*nods* there's 4 universe repos, remove all #'s in front of em.

---

### Post by Schmoozer3348 on 2005-07-28
Angkor,
Hmmmm, well easier said than done. It won't let me delete the '#'s. When I double clicked it, it opened in Gedit 2.10.2 do I need some type of editing program?

Sam,
I don't have synaptic open, all I'm using is GAIM, Firefox, terminal, and gedit(source.list)

---

### Post by Schmoozer3348 on 2005-07-28
Ok i opened it in a different folder, now its telling me it is a write protected folder when i try to save it. How do I 'un write protect' it?

---

### Post by angkor on 2005-07-28
Open up a terminal and type:

sudo gedit /etc/apt/sources.list     

This will open the gedit editor in root mode, which you need to be able to write to the file.

You will be prompted for your **user** password.

---

### Post by Schmoozer3348 on 2005-07-28
Ok I did the update and upgrade again and it got some new stuff, but still having the same problem:

logan@dhcp123:~$ apt-cache mplayer-386
E: Invalid operation mplayer-386

logan@dhcp123:~$ sudo apt-get install mplayer-386
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package mplayer-386


 ](*,)

---

### Post by Sam on 2005-07-28
Don't copy the '$', it means that your must run the following command in a terminal.

---

### Post by Sam on 2005-07-28
[QUOTE=Schmoozer3348]logan@dhcp123:~$ apt-cache mplayer-386
E: Invalid operation mplayer-386[/QUOTE]
```
$ apt-cache search mplayer-386
```
You forgot the 'search' argument.

Could you please copy the output of the command 'uname -a' ? Maybe you're using an AMD64, which has not the mplayer-386 package...

---

### Post by angkor on 2005-07-28
:)

Yeah, listen to Sam

:)

It's:

```
apt-cache search [type-desired-packagename-here]
```

```
sudo apt-get install [type-desired-package-name-here]
```  

Note that you need 'sudo' (which is 'do as root') to install software, but you don't need sudo to search for a package

---

### Post by Schmoozer3348 on 2005-07-28
OK....

logan@dhcp123:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release [16.9kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release.gpg [189B]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release [16.8kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Sources
Fetched 34.1kB in 3s (9075B/s)
Reading package lists... Done

logan@dhcp123:~$ apt-cache search <pattern>
bash: syntax error near unexpected token `newline'

logan@dhcp123:~$ apt-cache search mplayer-386

logan@dhcp123:~$ apt-get install mplayer-386
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

and....

logan@dhcp123:~$ uname -a
Linux dhcp123 2.6.10-5-386 #1 Tue Apr 5 12:12:40 UTC 2005 i686 GNU/Linux

is that what you meant???? sorry for the confusion


Edit: Oops sorry forgot that

logan@dhcp123:~$ apt-cache search mplayer-386
logan@dhcp123:~$ sudo apt-get install mplayer-386
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package mplayer-386

---

### Post by Sam on 2005-07-28
[QUOTE=Schmoozer3348]logan@dhcp123:~$ apt-get install mplayer-386
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?[/QUOTE]
Listen to angkor :wink:, you need 'sudo' to install a package !
```
$ sudo apt-get install mplayer-386
```
However, the package wasn't found with 'apt-cache search'...

I don't have this package on my box (I've an AMD64), so I don't know on which repository it can be found.

---

### Post by angkor on 2005-07-28
```
#deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary universe multiverse
deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) hoary universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

## Skype repository
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free
```

This is my list. You'll need the **multiverse** repos as well, because:

```
apt-cache search mplayer-386
mplayer-386 - The Ultimate Movie Player For Linux
```

It _is_ in my repos.

:D  You're getting there...and you'll know a _lot_ more about apt and your repositories when this is done.

---

### Post by angkor on 2005-07-28
Note btw that I use the nl repositories because I'm in Holland, you'll probably want mirrors closest to your location.

Click the link in the second and third post to check out the Ubuntu Guide repositories section for which ones to add.

---

### Post by Sam on 2005-07-28
To find out in which repository is a package, do
```
$ apt-cache show <package> |grep Section
```

---

### Post by Schmoozer3348 on 2005-07-28
Ok I found someone here (at my college) in the IT department that was able to sort all this out for me. Thanks for the help guys, i really did learn a lot.
-Logan :grin:

---

### Post by Sam on 2005-07-28
[QUOTE=Schmoozer3348]Ok I found someone here (at my college) in the IT department that was able to sort all this out for me. Thanks for the help guys, i really did learn a lot.
-Logan :grin:[/QUOTE]
You're welcome ! :wink:

---

### Post by angkor on 2005-07-28
Cool, welcome.

Did you manage to install and run mplayer?

Now you will probably want to install all the available codecs...just go to the UbuntuGuide and search for codecs

---

