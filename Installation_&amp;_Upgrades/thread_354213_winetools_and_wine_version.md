---
title: "winetools and wine version"
date: 2007-02-05
forum: Installation &amp; Upgrades
---

### Post by wxnker on 2007-02-05
I installed the newest wine and afterwards the newest winetools which should work with the new wine versions. 

I have setup wine like always by running "winecfg". I have also changed the default windows to "win 98".

When I start winetools in the terminal with "wt" I get a weird error:
[COLOR="Olive"]"Winetools cannot run with a Wine version older than 20050628"[/COLOR]

_Here are the lines from the terminal:_
:~$ wt
detecting Wine version... done.
Drive C: is /home/novak/.wine/drive_c
**Wine 0**
wine is executed as wine
Parameters are --noexit
Browser is /usr/bin/firefox.
**WINEVER is "0".**

Winetools detects Wine as version "**0**"

_Checking Wine version from terminal shows I have the new version:_
:~$ wine --version
wine-0.9.30

What could be wrong? 

(I have seen an old post regarding the same problem without finding a solution. The discussion there was about kernel-versions)
[http://www.ubuntuforums.org/showthread.php?t=128067](http://www.ubuntuforums.org/showthread.php?t=128067)

---

### Post by divague on 2007-02-05
which version of wineools are you using?

---

### Post by wxnker on 2007-02-05
Winetools version: wt0.9jo

---

### Post by divague on 2007-02-05
there's a version winetools 0.9.4, download it from here

[http://fly5.pp.fi/misc/winetools-0.9.4.tar.gz](http://fly5.pp.fi/misc/winetools-0.9.4.tar.gz)

---

### Post by wxnker on 2007-02-06
Thank you. This version seems to work

But I get all kinds of permission denied when running the different options in winetools.

like these examples:
wineserver: could not save registry branch to /home/novak/.wine/system.reg : Permission denied
wineserver: could not save registry branch to /home/novak/.wine/userdef.reg : Permission denied
wineserver: could not save registry branch to /home/novak/.wine/user.reg : Permission denied

Problem is that the .wine directory is write protected. (it did not use to be. I don't know if it's something done by the new wine versions).

So I tried getting permissions by using chgrp -R and chmod -R 775 but it does not work.

[COLOR="Olive"]**Edit: FIXED the permissions.**[/COLOR]

---

### Post by tjtansey on 2007-02-10
I had the same problem, so I downloaded the newer version of wt, but i got an error that I had installed another version of wt and I needed to uninstall it.  I did ./uninstall and I still get th error.  I tried deleting the old dir but that didn't help either?

---

### Post by willc0de4food on 2007-02-18
this solution worked for me:
> sudo gedit /etc/profile

/* append to the end of the file */
WINEVER=wine-0.9.30
export WINEVER

save & exit

source /etc/profile

wt

---

### Post by xodeus on 2007-02-26
I can confirm this solution...

---

### Post by jmspiers on 2007-10-14
> 
sudo gedit /etc/profile

/* append to the end of the file */
WINEVER=wine-0.9.30
export WINEVER

save & exit

source /etc/profile

wt


I can confirm that this solution works for 7.10 RC1 (the version is 0.9.46, just modify that parameter).

---

### Post by zvacet on 2007-10-14
It is good to see that you find solution for your question.I just want to say that you can use winedoors.It comes in deb package.

[http://www.wine-doors.org/wordpress/?page_id=3]("http://www.wine-doors.org/wordpress/?page_id=3")

---

### Post by alexc2 on 2007-12-19
Hello! I've done that, still I'm getting this error when a try to run wt.

[I]acampos@AC2-Ubuntu:~/Desktop/Downloads/winetools-0.9jo-III$ wt
bash: /usr/local/bin/wt: Permission denied
[/I]

And I asure you, I've follow the steps mentioned above one by one...
:confused:
Thanks for your help.
AlexC2

---

