---
title: "download ubuntu packages"
date: 2009-12-14
forum: Installation &amp; Upgrades
---

### Post by alimooghashang on 2009-12-14
Hi all,
how can i download all of these packages in order to write them into several DVDs and keep it for my self?

[http://packages.ubuntu.com/karmic/](http://packages.ubuntu.com/karmic/)

I'm using ubuntu 9.10.
thanks all
:popcorn:

---

### Post by lewisforlife on 2009-12-14
I am not at an Ubuntu box right now, but I believe you can do something like:
 
```
 
apt-get --download-only [package name]

```
 
You might be able to put a * in place of [package name] to download everything, I assume this will take a long time, hope you have a lot of space.

---

### Post by alimooghashang on 2009-12-14
> **lewisforlife said:**
> I am not at an Ubuntu box right now, but I believe you can do something like:
 
```
 
apt-get --download-only [package name]

```
 
You might be able to put a * in place of [package name] to download everything, I assume this will take a long time, hope you have a lot of space.
thanks
is there any way to retrieve the links of these files which meant to be downloaded via this command?
i mean , i want to give these packages links to a download manager program , which would download these packages ;)
although i'm not in ubuntu , but in windows.
is there any ISO image file which i could download it instead?
thanks

---

### Post by lewisforlife on 2009-12-14
I don't know of an iso that you can download containing all of the packages, but if you are able to get to an Ubuntu box, you can run the following:

```
apt-cache dumpavail | grep Package > file.txt
```

This will give you a list of all of the Packages and put them in file.txt.  It will give them in the following format:

Package: apache2
Package: mysql

You can then do a text replace of Package: and change it to say [http://packages.ubuntu.com/karmic/](http://packages.ubuntu.com/karmic/).  Then you would have a list in the file that looks like the following:

[http://packages.ubuntu.com/karmic/apache2](http://packages.ubuntu.com/karmic/apache2)
[http://packages.ubuntu.com/karmic/mysql](http://packages.ubuntu.com/karmic/mysql)

etc...  Then you can move the text file to your windows machine, and load the links into your download manager.

---

### Post by mikewhatever on 2009-12-14
Check out this howto -> [http://ubuntuforums.org/showthread.php?t=352460&highlight=repo+cds](http://ubuntuforums.org/showthread.php?t=352460&highlight=repo+cds)

---

### Post by alimooghashang on 2009-12-15
> **mikewhatever said:**
> Check out this howto -> [http://ubuntuforums.org/showthread.php?t=352460&highlight=repo+cds](http://ubuntuforums.org/showthread.php?t=352460&highlight=repo+cds)

is it just working in linux OS ?
i want to get the links and download them in windows with IDM
please tell me if it's possible
thanks

---

### Post by lewisforlife on 2009-12-15
> **lewisforlife said:**
> I don't know of an iso that you can download containing all of the packages, but if you are able to get to an Ubuntu box, you can run the following:

```
apt-cache dumpavail | grep Package > file.txt
```

This will give you a list of all of the Packages and put them in file.txt.  It will give them in the following format:

Package: apache2
Package: mysql

You can then do a text replace of Package: and change it to say [http://packages.ubuntu.com/karmic/](http://packages.ubuntu.com/karmic/).  Then you would have a list in the file that looks like the following:

[http://packages.ubuntu.com/karmic/apache2](http://packages.ubuntu.com/karmic/apache2)
[http://packages.ubuntu.com/karmic/mysql](http://packages.ubuntu.com/karmic/mysql)

etc...  Then you can move the text file to your windows machine, and load the links into your download manager.

This solution requires Linux, but once you have all of the packages in a file, you can move it to your Windows box.  Just out of curiosity, why do you want to do this in Windows so bad?

---

### Post by alimooghashang on 2009-12-16
could you please do this for me?
i do that, and the result is not what i need.
i need all of the packages links in a text file.
thanks

---

### Post by lewisforlife on 2009-12-16
I wouldn't mind running it for you, but I am on Jaunty, and you are looking for the Karmic packages, if I ran the script it would give me all of the Jaunty packages.  Just out of curiousity, what do you get when you run:
 
```
 
apt-cache dumpavail | grep Package > file.txt

```
 
Just look in file.txt, and paste a couple of lines into this forum so I can see what you are getting.  I should be able to help you troubleshoot this.

---

### Post by fhage on 2011-09-06
The above examples won't work if the packages have already been installed.
One can reload packages into the apt cache with:

```
sudo apt-get --download-only --reinstall install *packagename*

```

The package files end up in /var/cache/apt/archives/. Copy them into the /var/cache/apt/archives/ on a target host and run apt-get install* packagename* to complete the install of the packages.

---

