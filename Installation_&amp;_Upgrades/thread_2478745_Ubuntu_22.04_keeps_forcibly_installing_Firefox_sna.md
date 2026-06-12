---
title: "Ubuntu 22.04 keeps forcibly installing Firefox snap"
date: 2022-09-04
forum: Installation &amp; Upgrades
---

### Post by regs4 on 2022-09-04
So I completely uninstall snap with **snap remove firefox**, then **apt remove firefox**.

I do have **/etc/apt/preferences.d/mozillateam.pref** with
```
Package: firefox
Pin: release o=LP-PPA-mozillateam
Pin-Priority: 1001
```

It does install firefox from PPA, but a day or a few later it silently reinstalls the snap.
[IMG]https://i.imgur.com/GJzGSrE.png[/IMG]

then **apt policy firefox says**
```
firefox:
  Installed: 1:1snap1-0ubuntu2
  Candidate: 104.0.1+build1-0ubuntu0.22.04.1~mt1
  Version table:
 *** 1:1snap1-0ubuntu2 500
        500 http://archive.ubuntu.com/ubuntu jammy/main amd64 Packages
        100 /var/lib/dpkg/status
     104.0.1+build1-0ubuntu0.22.04.1~mt1 1001
        500 https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu jammy/main amd64 Packages
```


and **apt upgrade** says 
```
The following packages will be DOWNGRADED:
  firefox

```

What else could be done to stop the snap reinstalling the firefox? The snap version has very bad cursors on high DPI screens and it's still slower.

---

### Post by &amp;KyT$0P# on 2022-09-04
You need to do [FONT=Courier New]sudo apt-get **purge firefox***[/FONT] , and then pin more than just the "firefox" package (for example, [this guide how to use Mozillateam PPA]("https://ubuntuhandbook.org/index.php/2022/04/install-firefox-deb-ubuntu-22-04/") pins [FONT=Courier New]firefox*[/FONT] ).

---

### Post by regs4 on 2022-09-04
It was Package: * at some point. Didn't help either.

---

### Post by &amp;KyT$0P# on 2022-09-04
Do you have unattended-upgrades or some other method of automatically updating apt packages?  If so, is it aware of the Mozillateam PPA?  I seem to recall that unattended-upgrades requires explicitly adding each PPA as an "allowed origin" or something like that.

You could also try blocking the installer for snap Firefox in the same pinning file -
```
Package: firefox*
Pin: release o=Ubuntu
Pin-Priority: -1
```

---

### Post by oldfred on 2022-09-04
I have this:

[FONT=monospace][COLOR=#54ff54]**fred@z690-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ cat /etc/apt/preferences.d/mozilla-firefox [/COLOR]

Package: * 
Pin: release o=LP-PPA-mozillateam 
Pin-Priority: 1001

Not this:
[/FONT][FONT=monospace][COLOR=#54ff54]**fred@z690-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ cat /etc/apt/preferences.d/mozillateam.pref [/COLOR]
cat: /etc/apt/preferences.d/mozillateam.pref: No such file or directory

And this:
```
[FONT=monospace][COLOR=#54ff54]**fred@z690-jammy**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ apt policy firefox [/COLOR]
firefox: 
  Installed: 104.0.1+build1-0ubuntu0.22.04.1~mt1 
  Candidate: 104.0.1+build1-0ubuntu0.22.04.1~mt1 
  Version table: 
     1:1snap1-0ubuntu2 500 
        500 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 Packages 
 *** 104.0.1+build1-0ubuntu0.22.04.1~mt1 1001 
       1001 https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu jammy/main amd64 Packages 
        100 /var/lib/dpkg/status


[/FONT]
```

I followed these instructions:
[https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04)

[/FONT][FONT=monospace][/FONT]

---

### Post by regs4 on 2022-09-07
I have feeling /usr/bin/firefox wasn't being deleted. Tried to start over with purge. Third day is ok, will see where it goes. Also changed to firefox*.

---

### Post by oldfred on 2022-09-07
Did you change the priority as above.
Otherwise the snap version will be the priority and reinstalled.

---

