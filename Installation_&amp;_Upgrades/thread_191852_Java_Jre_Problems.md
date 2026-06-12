---
title: "Java Jre Problems"
date: 2006-06-08
forum: Installation &amp; Upgrades
---

### Post by CameronCalver on 2006-06-08
hey i would like to install java runtime environment i did it on one computer with
 sh jre-1_5_0_07-linux-i586.bin and the fakeroot make-jpkg one it worked on one computer with all the lines going past the terminal it also did it on the other comuputer but i worked on on but not the other ? can i copy it from one comp to the other i dunno can some1  help

---

### Post by ajgreeny on 2006-06-08
Look for sun-java in synaptic and you will find it there so don't need to do it the way you intended.

Make sure you have multiverse repos active and it's there as version 1.5.0-06-1, rather than 1.5.0-07 as you spoke of, but what a saving of time and trouble!

---

### Post by CameronCalver on 2006-06-09
hey thanks for a good quick response and it worked very well and it was so easy

---

### Post by DC@DR on 2006-06-09
Hello, I have Kubuntu Dapper 6.06 installed in my laptop, and I wanna install jsdk1.5.0 via downloading from multiverse repositories, but I couldn't find the right package? Are these steps correct to enable the universe/multiverse repositories:
1- Start up the Adept Manager
2- View -> Manage Repositories
3- Right-click -> Enable the links for universe/multiverse repositories

But when I tried to search for keyword 'java' to find the package, I couldn't see it there? Any ideas? Thanks in advance :)

---

### Post by CameronCalver on 2006-06-09
search sun-jave 


did it work?

---

### Post by DC@DR on 2006-06-09
No luck, dude :-( ...Any other ideas, plz? I did enable the multiverse repositories, that's why it's so weird....

---

### Post by FredB on 2006-06-09
[QUOTE=DC@DR]No luck, dude :-( ...Any other ideas, plz? I did enable the multiverse repositories, that's why it's so weird....[/QUOTE]

Erh...

I looked in Synaptic, and it is : "sun-java5-jre"

Try this so ;)

---

### Post by craftbrewer on 2006-06-09
[QUOTE=FredB]Erh...

I looked in Synaptic, and it is : "sun-java5-jre"

Try this so ;)[/QUOTE]

I've also been working on this without any luck.  Fresh install of Ubuntu 6.06, enabled multiverse, reloaded, and this package does not exist.

See [http://ubuntuforums.org/showthread.php?t=193018](http://ubuntuforums.org/showthread.php?t=193018) for more...

---

### Post by ajgreeny on 2006-06-09
It is definitely there in the multiverse/libs section so I'm a bit baffled why you can't find it. Double check your repos and don't forget to update them (ie download the new repository db by clicking on reload, top left of the window.)

---

### Post by craftbrewer on 2006-06-09
[QUOTE=ajgreeny]It is definitely there in the multiverse/libs section so I'm a bit baffled why you can't find it. Double check your repos and don't forget to update them (ie download the new repository db by clicking on reload, top left of the window.)[/QUOTE]

Been there a dozen times since installing Ubuntu wednesday evening.  I've enabled every repo available in a virgin install.  ie.  I havn't added anything to my sources, just enabled all thats there.  Followed all the various wiki documents to the letter to no avail.

I'm baffled too!  :)

---

### Post by FredB on 2006-06-09
[QUOTE=craftbrewer]Been there a dozen times since installing Ubuntu wednesday evening.  I've enabled every repo available in a virgin install.  ie.  I havn't added anything to my sources, just enabled all thats there.  Followed all the various wiki documents to the letter to no avail.

I'm baffled too!  :)[/QUOTE]

Gnnnn ? :cry: 

Something is weird here. :mad: 

Maybe a problem with the repository you're targetting ?!

What does your /etc/apt/sources.list look like ?

---

### Post by craftbrewer on 2006-06-09
I'm mobile atm, so I'll have to post my sources.list in a couple hours...

---

### Post by FredB on 2006-06-09
[QUOTE=craftbrewer]I'm mobile atm, so I'll have to post my sources.list in a couple hours...[/QUOTE]

I will go to bed in one hour - ah, living in Europe - so I cannot help until 10 hours after...

---

### Post by snellgrove on 2006-06-09
Java seems to be gone in my repo's too.

big problems with java here (as always, it seems... :( ) and I cant find blackdown, sun's or anyones runtime environment here.

---

### Post by craftbrewer on 2006-06-09
Here's my sources.list with comments removed.  Problems with the Canuck repos prehaps?

> deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe


---

### Post by FredB on 2006-06-10
[QUOTE=craftbrewer]Here's my sources.list with comments removed.  Problems with the Canuck repos prehaps?[/QUOTE]

Maybe. Try removing ca. and test again. Some repos seems to be lazy :(

---

### Post by afx on 2006-06-10
I had the same problem with "at."...
I just removed it and it works fine now...
Thanks for the hint!

---

### Post by craftbrewer on 2006-06-10
[QUOTE=FredB]Maybe. Try removing ca. and test again. Some repos seems to be lazy :([/QUOTE]

Tried that , then ran **sudo aptitude update** but I still had no sun-java5-jre.  Then I substituted my entire sources.list with SD-Plissken's as posted in the other thread, ran update again and everything is now as it should be.

Thanks everybody for your input!

---

### Post by CameronCalver on 2006-06-11
I just have to say one thing 

i made the thread and you took over so you should try not to do that ok

---

### Post by craftbrewer on 2006-06-11
[QUOTE=CameronCalver]I just have to say one thing 

i made the thread and you took over so you should try not to do that ok[/QUOTE]

Personally, I don't see this as off topic or hijacking.  The solution may have worked for you, but not for everybody, which prompted further discussion.  

If having the information in your thread regarding problems with the repos helps someone else who's having trouble installing java5, then its all good.

---

### Post by cpudney on 2006-06-12
[QUOTE=craftbrewer]Been there a dozen times since installing Ubuntu wednesday evening.  I've enabled every repo available in a virgin install.  ie.  I havn't added anything to my sources, just enabled all thats there.  Followed all the various wiki documents to the letter to no avail.[/QUOTE]
I'm in a similar situation too.  Clean Dapper Drake installation, all repositories enabled but no sign of sun-java5.  E.g.
```

$ sudo apt-get install sun-java5-jre
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-java5-jre
```

My /etc/apt/sources.list are all mainly [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com)

I wonder whether sun-java5 might actually have been [pulled due to licensing problems]("http://ubuntuforums.org/showthread.php?t=178436&highlight=sun-java5") :confused: 

Chris.

---

### Post by cpudney on 2006-06-12
G'day,

For the time being I'm going with the old-fashioned approach of [downloading from Sun and manually installing the JRE]("http://ubuntu-linux-dell-inspiron-9400.blogspot.com/2006/06/installing-suns-java_12.html").  FWIW, here are the steps I used:
[LIST=1]
[*]download the self-extracting bin file from [Sun's web-site]("http://java.sun.com/j2se/1.5.0/download.jsp")
[*]make executable
*chmod +x jre-1_5_0_07-linux-i586.bin*
[*]run the executable (requires acceptance of the terms of the license)
*sudo ./jre-1_5_0_07-linux-i586.bin*
[*]move the extracted file-tree to a suitable location
*sudo mv jre1.5.0_07/ /opt*
[*]configure the browser plug-in, e.g. for Firefox:
[I]cd /usr/lib/firefox/plugins/
sudo ln -s /opt/jre1.5.0_07/plugin/i386/ns7/libjavaplugin_oji.so[/I]
[*]set your JAVA_HOME environment variable and put it into your PATH variable e.g. in $HOME/.bash_profile add
[I]JAVA_HOME=/opt/jre1.5.0_07
PATH="${PATH}:${JAVA_HOME}/bin"[/I]
[*]To run the Control Panel
*ControlPanel*
[/LIST]

HTH,
Chris.

---

### Post by smilelover on 2006-06-13
Same problem here!

---

### Post by müller on 2006-06-13
had same problem

recheck your sources.list for multiverse

---

### Post by cpudney on 2006-06-14
G'day,

[QUOTE=müller]had same problem
recheck your sources.list for multiverse[/QUOTE]

```
deb http://**au**.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://**au**.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

```

What's yours?

Regards,
Chris.

---

### Post by izvit on 2006-06-14
Had the same issue.

this seems to solve it:
[https://jdk-distros.dev.java.net/ubuntu-dev.html](https://jdk-distros.dev.java.net/ubuntu-dev.html)

hope that helps,   :) 

Vitaliy

---

### Post by craftbrewer on 2006-06-15
izvit, that won't help if multiverse is enabled and java5 still cannot be found.  
It appears some repos's are culprit in this problem.  Here again is what solved the repo problem for me:

[http://ubuntuforums.org/showthread.php?t=193018](http://ubuntuforums.org/showthread.php?t=193018)

---

### Post by cpudney on 2006-06-18
G'day,

[QUOTE=izvit]
this seems to solve it:
[https://jdk-distros.dev.java.net/ubuntu-dev.html](https://jdk-distros.dev.java.net/ubuntu-dev.html)
[/QUOTE]

THANKS - indeed it does =D> 

It turns out I [hadn't properly referenced the multiverse repository in Synaptic]("http://ubuntu-linux-dell-inspiron-9400.blogspot.com/2006/06/installing-suns-java-problem-solved.html") #-o 

Please forgive my earlier false lead on this one - I'm still a n00buntu.

BTW, it's also worth doing the following post-installation:

```
$ sudo update-alternatives --config java
Password:

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.1
*+    2        /usr/lib/jvm/java-gcj/jre/bin/java
      3        /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 3
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/java' to provide `java'.
```

Regards,
Chris.

---

