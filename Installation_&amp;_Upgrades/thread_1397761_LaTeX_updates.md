---
title: "LaTeX updates"
date: 2010-02-03
forum: Installation &amp; Upgrades
---

### Post by virsto on 2010-02-03
I have been able to install LaTeX and Texmaker and it seems to be working ok. However, I then started working with LyX (1.6.4) and found that some LaTeX *.sty and/or *.cls files were missing in my installation.
 
**How can I install/update LaTeX *.sty and *.cls files?**
 
I have vers. 9.10 of Ubuntu and the LaTeX installation was done today.
 
--Thank you,
V.

---

### Post by Abdus on 2010-02-03
You may check this thread:

As far as I know for now there is no way to update your default Ubuntu TeX installation en masse, and installing packages by hand is quite tedious. This is why I chose to reinstall TeX from scratch using much newer version. This occurred to be very easy, you will find details in the thread [Is LaTeX in Ubuntu very outdated?](http://ubuntuforums.org/showthread.php?p=8761147#post8761147) <== click.

If you choose to update every package you need by hand, it is strongly recommended to build an independent TeX tree for your manually installed packages.

Remember to add the path to such a new handmade tree to your Path variable:
```
sudo [any text editor] /etc/environment
```
for example
```
sudo nano /etc/environment
```
Add the path to the tree in the PATH line:
```
PATH="[COLOR="Red"]/usr/local/texlive/2009/bin/x86_64-linux[/COLOR]:[COLOR="Navy"]/home/mylogin/myprivatetexttree[/COLOR]:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
```

This way anything you install will be seen by TeX, and it will not spoil its auto updates... if it does them anyway. :)

---

### Post by virsto on 2010-02-04
Thanks for this information. However, I now have another question --- How do I edit the PATH variable?:P

---

### Post by virsto on 2010-02-04
This is from the successful installation of TexLive a few hours ago.

Add /usr/local/texlive/2009/texmf/doc/man to MANPATH.
 Add /usr/local/texlive/2009/texmf/doc/info to INFOPATH.

 Most importantly, add /usr/local/texlive/2009/bin/i386-linux
 to your PATH for current and future sessions.

However, I do not know how to do this? Where are MANPATH, INFOPATH, PATH and how do I create/edit them?

--V

---

### Post by Abdus on 2010-02-04
In my previous post I showed you how to open a file containing your various paths:

```
sudo [any text editor] /etc/evironment
--------for example--------
sudo nano /etc/environment
--------or if you prefer editor named gedit--------
sudo gedit /etc/environment
```
[LIST]
[*]sudo is a command that gives you admin privileges needed to edit the file
[*]nano/gedit are the names of the applications you will use to edit the file
[*]/etc/environment is the name of the file to edit
[/LIST]

"Add the path" means just: "copy and paste the path to your TeX directory to the appropriate line in the file you just opened". Example below shows the very first line in my /etc/evironment with 2 paths added: red one is for the TeX-Live installation tree, the green one is the one I added by hand later.

 to the tree in the PATH line:
```
PATH="[COLOR="Red"]/usr/local/texlive/2009/bin/x86_64-linux[/COLOR]:[COLOR="Navy"]/home/mylogin/myprivatetexttree[/COLOR]:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
```

After you edit the file just save it - after reboot the path will be added. You can check this by issuing the command:
```
echo $PATH
```
which means "show me what is the value of the $PATH variable".

EDIT: The commands in the frames are what you are supposed to type in your console.

---

### Post by virsto on 2010-02-04
> **Abdus said:**
> In my previous post I showed you how to open a file containing your various paths:

```
sudo [any text editor] /etc/evironment
--------for example--------
sudo nano /etc/evironment
--------or if you prefer editor named gedit--------
sudo gedit /etc/evironment
```
[LIST]
[*]sudo is a command that gives you admin privileges needed to edit the file
[*]nano/gedit are the names of the applications you will use to edit the file
[*]/etc/evironment is the name of the file to edit
[/LIST]

"Add the path" means just: "copy and paste the path to your TeX directory to the appropriate line in the file you just opened". Example below shows the very first line in my /etc/evironment with 2 paths added: red one is for the TeX-Live installation tree, the green one is the one I added by hand later.

 to the tree in the PATH line:
```
PATH="[COLOR="Red"]/usr/local/texlive/2009/bin/x86_64-linux[/COLOR]:[COLOR="Navy"]/home/mylogin/myprivatetexttree[/COLOR]:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
```

After you edit the file just save it - after reboot the path will be added. You can check this by issuing the command:
```
echo $PATH
```
which means "show me what is the value of the $PATH variable".

EDIT: The commands in the frames are what you are supposed to type in your console.
But I do not have a file: 
/etc/evironment

---

### Post by virsto on 2010-02-04
Ok Abdus,
This procedure to change the PATH variable worked! Thanks!
But, how do I add 

/usr/local/texlive/2009/texmf/doc/man

to MANPATH 

and 
 
/usr/local/texlive/2009/texmf/doc/info 

to INFOPATH

Neither of these variables exist in my environment!

--V

---

### Post by Abdus on 2010-02-04
> **virsto said:**
> But I do not have a file: 
/etc/evironment

This is my typo, sorry, it should say /etc/environment

EDIT:

> **virsto said:**
> Ok Abdus,
This procedure to change the PATH variable worked! Thanks!
But, how do I add 

/usr/local/texlive/2009/texmf/doc/man

to MANPATH 

and 
 
/usr/local/texlive/2009/texmf/doc/info 

to INFOPATH

Neither of these variables exist in my environment!


Add the two lines to your /etc/environment file. Here you have what mine says:
```
MANPATH="/usr/local/texlive/2009/texmf/doc/man"
INFOPATH="/usr/local/texlive/2009/texmf/doc/info"
```

These were added by the installer I used (Ailurus), so I didn't have to paste them myself. If you don't have them, just paste them as new lines, this will do as well (after reboot).

---

### Post by virsto on 2010-02-04
> **Abdus said:**
> This is my typo, sorry, it should say /etc/environment

EDIT:


Add the two lines to your /etc/environment file. Here you have what mine says:
```
MANPATH="/usr/local/texlive/2009/texmf/doc/man"
INFOPATH="/usr/local/texlive/2009/texmf/doc/info"
```

These were added by the installer I used (Ailurus), so I didn't have to paste them myself. If you don't have them, just paste them as new lines, this will do as well (after reboot).
This works fine!
Thanks again Abdus!

--V

---

