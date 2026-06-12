---
title: "aptitude vs apt-get?"
date: 2006-06-28
forum: Installation &amp; Upgrades
---

### Post by Jessehk on 2006-06-28
I was used to previously using apt-get (and related tools) to do package management in the terminal. Recently though, I've seen many tutorials that use the command-line mode of aptitude instead. 

Which, if any, is preferred for command-line package management?

---

### Post by aysiu on 2006-06-28
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by Jessehk on 2006-06-28
[QUOTE=aysiu][http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)[/QUOTE]

Thanks. I'll be sure to use aptitude from now on. :)

---

### Post by Drakkor on 2006-06-29
Say you installed programs via Synaptic or Easy Ubuntu, how to remove them and all their dependences ?  Thanks :)

---

### Post by rai4shu2 on 2006-06-29
Drakkor, take a look at gtkorphan.

---

### Post by Drakkor on 2006-06-29
Ok,think I got it now Thanks ! :D

---

### Post by FredB on 2006-06-30
[QUOTE=aysiu][http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)[/QUOTE]

Thanks. I think my apt-get will get long long long holidays ;)

---

### Post by slimg on 2007-01-17
The apt-get version in the ubuntu edgy release has the same functionality as aptitude regarding the removal of unused dependencies:
```
sudo apt-get autoremove applicationname
```

---

### Post by mannheim on 2007-01-17
> **slimg said:**
> The apt-get version in the ubuntu edgy release has the same functionality as aptitude regarding the removal of unused dependencies


Yes, and so does the version of Synaptic in edgy (though some other features of edgy's synaptic are broken, pending a bug fix which is in progress).

In Synaptic, if the installing kword (for example) pulls in some dependent packages,  then when you remove kword, you will see the dependencies of kword flagged as "Auto removable". You can then choose to remove the auto-removable packages. This also works if you install kword with apt-get on the command line and remove it with Synaptic.

I think it just comes down to what you are used to and what you like.

---

### Post by nphx on 2007-08-06
So what's the best way to install deb packages you've downloaded that are not in the repositories? Should we use GDebi Package Installer or command line dpkg -i or are they the same thing or an alternative method?

---

### Post by aysiu on 2007-08-06
They are the same thing, more or less. One is point-and-click; the other is a terminal command.

I _think_ gDebi might be a bit more sophisticated. As far as I know, gDebi will pull in needed dependencies, and *sudo dpkg -i* will just tell you the dependencies are missing.

---

### Post by motin on 2007-12-09
Aptitude basically does the same that most apt-* tools (-get, -cache, -listchanges) as well as many dpkg-* and other tools do, but using ONE program with sane default parameters instead. 

Read more in this great article: [http://www.pthree.org/2007/08/12/aptitude-vs-apt-get/](http://www.pthree.org/2007/08/12/aptitude-vs-apt-get/)

---

### Post by ubuntu-freak on 2008-01-10
I think it's confusing to newbies and pointless when people post 'sudo aptitude' commands when they know full well that most use 'apt-get'. It's best to use one or the other and not mix.
 
Apt-get has 'autoremove' now anyway. and there was always deborphan if you really hated left over packages.
 
Nathan

---

### Post by Kivech on 2008-03-17
I'd like to add to that that sometimes aptitude has unwanted results.

Take my situation for example. I have the nspluginwrapper for Ubuntu 7.10 x64 installed. In one case someone wrote in a HOWTO to use the command "sudo aptitude update && sudo aptitude safe-upgrade".... Bye bye macromedia player plugin.....

However when I use "sudo apt-get update && sudo apt-get upgrade" all works fine and leaves my manually installed stuff alone.

So also for that reason I would always recommend to use "apt-get". Just to make sure you don't get unwanted results.

Kivech

---

