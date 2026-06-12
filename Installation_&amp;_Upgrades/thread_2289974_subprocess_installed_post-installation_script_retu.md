---
title: "subprocess installed post-installation script returned error exit status 2"
date: 2015-08-08
forum: Installation &amp; Upgrades
---

### Post by arunsingh.in on 2015-08-08
I wanted to run my program in Python, due to some reasons it was not working on Python2.7.6, I read on some forum there must be compatibility issue, Hence I used the command "sudo apt-get autoremove python2.7"  

This command removed several packages like full gnome-desktop environment, unity, ubuntu software centre, vlc +------- 50 other softwares/utilities-----.

After that i tried to manually install from terminal these programs, Ubuntu software centre, gnome-desktop environment, but it is giving some error, the detailed have been posted in pastebin, Kindly visit and see : [http://pastebin.com/1LSRYHke](http://pastebin.com/1LSRYHke)


I am desperately seeking solution, Kindly provide valuable suggestions. Any leads and help is much appreciated. Thanks in advance.:D


PS: I have tried following commands to fix it but nothing worked to rescue me.

sudo apt-get install -f


sudo apt-get clean    


sudo apt-get autoremove    

sudo dpkg --configure -a    


sudo dpkg --remove -force --force-remove-reinstreq package name

---

### Post by bapoumba on 2015-08-08
The bottom of the error message is missing from your pastebin.

What does **sudo apt-get install ubuntu-desktop **return ?

---

### Post by arunsingh.in on 2015-08-08
sudo apt-get install ubuntu-desktop > Read this pastebin  :[http://paste.ubuntu.com/12033004/](http://paste.ubuntu.com/12033004/)

---

### Post by arunsingh.in on 2015-08-08
Full Text after running "sudo apt-get install ubuntu-desktop" > Read this pastebin:[http://paste.ubuntu.com/12033052/](http://paste.ubuntu.com/12033052/)

---

### Post by bapoumba on 2015-08-08
Please first try and post the outputs to :
```
sudo apt-get update
sudo dpkg --configure -a
sudo apt-get -f install
```

---

### Post by arunsingh.in on 2015-08-08
[FONT=Verdana]sudo apt-get update > Read this post: [http://paste.ubuntu.com/12036934/](http://paste.ubuntu.com/12036934/)[/FONT]

sudo dpkg --configure -a > [http://paste.ubuntu.com/12036960/](http://paste.ubuntu.com/12036960/)


sudo apt-get -f install  >  [http://paste.ubuntu.com/12036973/](http://paste.ubuntu.com/12036973/)

When I tried to install from Ubuntu software center, At last after downloading it states common message for any download, "package operation failed"

Tried removing ntop manually but on the same page again > Read output: [http://paste.ubuntu.com/12038690/](http://paste.ubuntu.com/12038690/)

Though I have already used them but no solution, problem remains unresolved.

---

### Post by v3.xx on 2015-08-09
I see you tried to remove ntop with apt-get.  Try removing it with dpkg.
```
sudo dpkg --purge ntop
```

---

### Post by arunsingh.in on 2015-08-09
sudo dpkg --purge ntop >[http://paste.ubuntu.com/12042316/](http://paste.ubuntu.com/12042316/)

---

### Post by arunsingh.in on 2015-08-09
```
sudo dpkg --remove --force-all ntop
```

This solved my sub process error code problem, though now I want to install and re install all the packages removed while removing Python 2.7.6. For this I did this,

```
cat /var/log/apt/history.log | nc termbin.com 9999
```

```
nano ~/packages
``` and go to [http://termbin.com/5z5c](http://termbin.com/5z5c) and copy and paste the packages there{in nano}, then type ```
xargs -a ~/packages sudo apt-get install --reinstall
```

Now its giving error, [http://paste.ubuntu.com/12045252/](http://paste.ubuntu.com/12045252/)

Kindly suggest measure to resolve this, I am just one step away from my final solution. Any leads and help is much appreciated.

---

### Post by arunsingh.in on 2015-08-10
I removed this content from nano ~/package file and pasted only packages.

```
[COLOR=#B8860B]content[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]width[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#000000]device-width,initial-scale[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#000000]1.0,maximum-scale[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#000000]1.0/><style>body[/COLOR][COLOR=#666666]{[/COLOR][COLOR=#000000]margin:0px;padding:0px;[/COLOR][COLOR=#666666]}[/COLOR][COLOR=#000000]iframe[/COLOR][COLOR=#666666]{[/COLOR][COLOR=#000000]width:100%;height[/COLOR][COLOR=#BB4444]'[/COLOR][COLOR=#BB4444]E: Unable to locate package src=http://182.79.218.37[/COLOR] [COLOR=#BB4444]E: Couldn'[/COLOR][COLOR=#000000]t find any package by regex [/COLOR][COLOR=#BB4444]'src=http://182.79.218.37:8080/webadmin/deny/index.php?dpid=1&dpruleid=3&cat=107&ttl=0&groupname=-&policyname=-&username=-&userip=122.177.134.134&connectionip=127.0.0.1&nsphostname=policy05-Chennai&protocol=policyprocessor&dplanguage=-&url[/COLOR]
```

After posting I used ```
[COLOR=#000000][FONT=Ubuntu Mono]xargs -a ~/packages sudo apt-get install --reinstall[/FONT][/COLOR]
```

Issue stands resolved, I conquered the fight with the system. I learned my hard lesson when I read some random thread and decided to remove python 2.7.6 and install python 3.0. Lesson I learned > don't remove python and specially using "sudo apt-get autoremove python2.7.6" It will devastate the system beyond repair due to several dependencies of python on other programs  

I learned my lesson and I was able to conquer the system difficulties and pull my system back to normal. Use any linux command with great caution, first learn its Pros and cons.

---

