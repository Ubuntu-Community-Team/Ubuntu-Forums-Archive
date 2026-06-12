---
title: "[SOLVED] Google Earth"
date: 2008-06-15
forum: Installation &amp; Upgrades
---

### Post by Lorna on 2008-06-15
Hi all you amazing programmers!

I love google earth to spy on my husband, see where his car is...lol anyway I downloaded the new GoogleEarthLinux.bin file from Google but can't for the life of me work out how to install it?  Any brainy boy able to assist me with my little problem?

Lorna

---

### Post by iaculallad on 2008-06-15
Say GoogleEarthLinux.bin is downloaded on your Desktop:

Change directory to your desktop:

```
cd ~/Desktop
```

Change the file permission so you could execute it:

```
sudo chmod +x GoogleEarthLinux.bin
```

Run the executable:

```
sudo ./GoogleEarthLinux.bin
```

*sudo - just in case

---

### Post by ChameleonDave on 2008-06-15
I imagine that you just have to put the file on your desktop, open a command-line terminal, and type this:
```

sudo ~/Desktop/GoogleEarthLinux.bin

```

Google Earth is also simply available in the Ubuntu repositories.  Providing that you have the correct repositories enabled, the following command will download and install Google Earth automatically:

```

sudo apt-get install google-earth

```

I'm actually on Windows today, so I can't check.

---

### Post by sbungay on 2008-06-15
While on the topic of Google Earth...
Latest update of xorg 3:1.2.0-3 seems to break Google earth :(. Each time the Google earth app loads the X server restarts, rather nasty this. Downloaded the latest version of the Google app to see if there was a fix on their end and so far there is no joy.  
Is there a way to back out an "upgrade"?

---

### Post by Sabata on 2008-06-15
> **sbungay said:**
> While on the topic of Google Earth...
Latest update of xorg 3:1.2.0-3 seems to break Google earth :(. Each time the Google earth app loads the X server restarts, rather nasty this. Downloaded the latest version of the Google app to see if there was a fix on their end and so far there is no joy.  
Is there a way to back out an "upgrade"?
So it's not only me... ](*,) 

I just ran into this problem as well and even downloaded the beta version a minute ago to try, but figured it best to stop in here first. Looks like there's no use installing it until someone smarter than me comes up with a solution. :(

---

### Post by vishzilla on 2008-06-15
Google Earth is available in the Medibuntu repos.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

after enabling the repos, ```
sudo apt-get install googleearth
```

---

### Post by sbungay on 2008-06-16
> **vishzilla said:**
> Google Earth is available in the Medibuntu repos.
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

after enabling the repos, ```
sudo apt-get install googleearth
```

  I'm not sure who that post was targeted at, but the mediubuntu version of Google Earth also does not work with the "upgrade" to xorg that came down last week.
  Solution so far.. run Google Earth in XP in VirtualBox using OpenGL Emulation... this is just SO  wrong.

---

### Post by Lorna on 2008-06-17
Thank you to everyone for your help....You Rock!

---

### Post by Patch87 on 2008-06-19
What Lorna said!!! you guys:guitar::guitar: double Rock!!!

---

