---
title: "apt-get search"
date: 2006-04-01
forum: Installation &amp; Upgrades
---

### Post by podollb on 2006-04-01
I was wondering how to go about doing a search for software using apt-get? I have been a Gentoo user for many years and have always utelized the "emerge --search" or "emerge --searchdesc" feature. Hence, looking for something to do with ssh I could just do "emerge --searchdesc ssh" and see all the 100's of packages that are related to ssh. There must be a way using apt-get to do something similar, right?

---

### Post by aysiu on 2006-04-01
Try this. If you're looking for an FTP program, for example: ```
apt-cache search ftp
```

---

### Post by shinygerbil on 2006-04-01
If you feel like using aptitude, you can ```
sudo aptitude search
``` just fine.

Steve

---

### Post by Sutekh on 2006-04-01
The one I like.  Not really a search, but makes things easier.  This will allow you to use TAB to auto-complete package names in apt-get.

Edit your .bashrc
```
sudo nano ~/.bashrc
```
and where you see this part (near the end of the file)
```
# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
#if [ -f /etc/bash_completion ]; then
#    . /etc/bash_completion
#fi
```
Add this line
```

source /etc/bash_completion
```
Save (Ctrl+O) and exit (Ctrl+X).  If you close and re-open a terminal you should be able to install using apt-get and the autocompletion power of TAB.

Start typing and use TAB to get the prompt to finish the typing for you

An example
```
sudo apt-g<TAB> i<TAB> rhyt<TAB>
```
becomes
```
sudo apt-get install rhythmbox
```

---

### Post by podollb on 2006-04-02
Ok so thoese are a few ways and they seem to work, thanks. Now how do I go about expanding the options available? I read a little about universe and mulituniverse, but I'm not sure how to expand my possible install options...

---

### Post by Sutekh on 2006-04-02
It's easy.  All you need to do is edit the file that contains the list of repositories.  
```
sudo nano /etc/apt/sources.list
```

You need to uncomment the lines that contain 'universe' to enable the universe repository.  To enable the multiverse repository add 'multiverse' to the same lines.

Should look something like this when you are done.
```
deb http://archive.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy universe multiverse

deb http://security.ubuntu.com/ubuntu breezy universe multiverse
deb-src http://security.ubuntu.com/ubuntu breezy universe multiverse
```
Then if you refresh the apt-get repository lists using
```
sudo apt-get update
```You are ready to grab software from those repositories.

---

