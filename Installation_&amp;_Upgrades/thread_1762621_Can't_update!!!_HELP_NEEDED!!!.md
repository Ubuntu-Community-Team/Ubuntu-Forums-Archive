---
title: "Can't update!!! HELP NEEDED!!!"
date: 2011-05-19
forum: Installation &amp; Upgrades
---

### Post by 3xp10r3r|X13 on 2011-05-19
[FONT=Courier New]Hello there, 
I've got this really annoying problem:

I just can't get any updates from:

[http://ppa.launchpad.net/dists/natty/main/Sources/binary-amd64/Packages](http://ppa.launchpad.net/dists/natty/main/Sources/binary-amd64/Packages)

AND

[http://ppa.launchpad.net/dists/natty/main/Sources/source/Sources](http://ppa.launchpad.net/dists/natty/main/Sources/source/Sources)  

In both cases it says "404 not found"

Here's the code out of the terminal after typing "sudo apt-get update"

W: Failed to fetch [http://ppa.launchpad.net/dists/natty/main/Sources/source/Sources](http://ppa.launchpad.net/dists/natty/main/Sources/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/dists/natty/main/Sources/binary-amd64/Packages](http://ppa.launchpad.net/dists/natty/main/Sources/binary-amd64/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

--> what's going on?


any help or advice is really appreciated (and needed) :(


[/FONT]

---

### Post by dino99 on 2011-05-19
these address are borked, copy/paste the lines below to:

sudo gedit /etc/apt/sources.list

#******************************
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) natty partner
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) natty restricted main multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) natty-updates restricted main multiverse universe
  
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) natty-security restricted main multiverse universe

deb [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu) natty main

deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) natty contrib

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) natty-proposed restricted main multiverse universe
#******************************

(remove all other lines before to paste)
then update:
sudo apt-get update
sudo apt-get install -f

---

### Post by ajgreeny on 2011-05-19
Can I please also ask you to use the standard fonts when entering any text into the input boxes here.

I find your small, gray text very difficult to read easily!

---

### Post by 3xp10r3r|X13 on 2011-05-19
Thanks for your quick replies, I will try it out (finally someone offered a solution --> :D--> I posted this thread three times already, if this works, I will link this one to the other ones).

"Can you please use..."
Well I thought it would look nicer, but if there are some people who have difficulties to read my selected font I will use the standard font from now on.

I'll tell you if it solved my problems, so please check this thread from time to time.

Thanks again:)

---

### Post by 3xp10r3r|X13 on 2011-05-19
Hope this doesn't sound stupid, but should I delete all of them or just the main sources ones???

--> I still want to get updates for vlc etc. so i would probably be better if I would leave those

---

### Post by ajgreeny on 2011-05-19
> **3xp10r3r|X13 said:**
> Hope this doesn't sound stupid, but should I delete all of them or just the main sources ones???

--> I still want to get updates for vlc etc. so i would probably be better if I would leave those
No; delete all the others as dino99 says.  If you don't you will still get those error messages and go nowhere.  VLC should still update from those standard repos, along with all other packages.  You can add other ppa repos after if needed.

PS:  Thanks for the font change; much better!

---

### Post by 3xp10r3r|X13 on 2011-05-20
Worked out just fine :D
I just had to delete those, which weren't on your list.

Just one question left:

How am I meant to get PPA updates now?

---

### Post by 3xp10r3r|X13 on 2011-05-20
" You can add other ppa repos after if needed."
Sry missed that part :D

So thanks very much

---

### Post by ajgreeny on 2011-05-20
Just for information, there is a great site at [http://repogen.simplylinux.ch/generate.php](http://repogen.simplylinux.ch/generate.php) which allows you to start again with a new sources.list file.  You simply fill in the various blanks for country and some of the non-standard repos you want, and the site generates the list for you.  You can then just edit the sources.list file with ```
gksu gedit /etc/apt/sources.list
``` delete everything in it, and copy in all the new generated text.

---

### Post by 3xp10r3r|X13 on 2011-05-20
Hey, that seems useful :)

---

