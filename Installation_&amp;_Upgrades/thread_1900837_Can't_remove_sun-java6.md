---
title: "Can't remove sun-java6"
date: 2011-12-27
forum: Installation &amp; Upgrades
---

### Post by Davis Bre on 2011-12-27
Hi all!

I have problem with sun-java6. I can't remove it, and when I try to install another program from Ubuntu Software Center, computer shoot out an error that I need to reinstall Java package. When I  tried to remove Java in terminal, my computer still demand to reinstall Java.
davis@ubuntu:~$ sudo apt-get --purge remove sun-java6
[sudo] password for davis: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package sun-java6-bin needs to be reinstalled, but I can't find an archive for it.

And, if it makes matter, my computer is Lenovo B560

Hope to hear solution for this problem.

Davis Bre

---

### Post by Davis Bre on 2011-12-28
???

---

### Post by dabl on 2011-12-28
```
sudo dpkg --configure -a
```

```
sudo apt-get purge sun-java6-jre sun-java6-plugin
```


Any errors?

---

### Post by sammiev on 2011-12-28
Read [this]("http://sites.google.com/site/easylinuxtipsproject/java") near the bottom. :)

---

### Post by Davis Bre on 2011-12-29
Still nothing, I need to reinstall java. But now I will try sammiev's advice.

---

### Post by Davis Bre on 2011-12-29
> **sammiev said:**
> Read [this]("http://sites.google.com/site/easylinuxtipsproject/java") near the bottom. :)


Still nothing. I have deleted folder of java some time ago, and maybe it's the reason why I can't remove it, but thanks anyway. Actually, I don't care about that , that java isn't working and it just exists on my computer but, what makes me care, is that I can't install or remove other software and, of course, install Ubuntu updates. Is there any suggestions how can I remove that block, what makes unable to install new software?

---

### Post by sammiev on 2011-12-29
It will delete all versions of java if you follow all directions. You will need some version of java for the internet. :)

---

### Post by Davis Bre on 2011-12-30
Now my Java application is working. So now I don't want to remove it, but now I have a new problem, I'm unable to install new updates, because of the error:
An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/ferramroberto-java-oneiric.list'

Where do I need to send report?

---

### Post by sammiev on 2011-12-30
> **Davis Bre said:**
> Now my Java application is working. So now I don't want to remove it, but now I have a new problem, I'm unable to install new updates, because of the error:
An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/ferramroberto-java-oneiric.list'

Where do I need to send report?

You need to remove that line from your sources.list. 
Ubuntu Tweak is a great program for that. You can also do it from System Settings then Software Sources.

---

### Post by Davis Bre on 2011-12-30
> **sammiev said:**
> You need to remove that line from your sources.list. 
Ubuntu Tweak is a great program for that. You can also do it from System Settings then Software Sources.
I follow to your advice, but it only changed text in the error. I forgot to mention that I have Ubuntu 11.10. I went in Software Sources -> Other Software and removed all, one by one, but it only changed text in error.

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'ain' is not known on line 1 in source list /etc/apt/sources.list.d/ferramroberto-java-oneiric.list, E:The list of sources could not be read., E:The package lists or status file could not be parsed or opened.'

Any ideas what else I can do? I have tried sudo gedit... command, but it shoots out an empty page, where isn't any line at all.

---

### Post by spacecheck on 2011-12-30
> **Davis Bre said:**
> I follow to your advice, but it only changed text in the error. I forgot to mention that I have Ubuntu 11.10. I went in Software Sources -> Other Software and removed all, one by one, but it only changed text in error.

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'ain' is not known on line 1 in source list /etc/apt/sources.list.d/ferramroberto-java-oneiric.list, E:The list of sources could not be read., E:The package lists or status file could not be parsed or opened.'

Any ideas what else I can do? I have tried sudo gedit... command, but it shoots out an empty page, where isn't any line at all.

Yes, I suggest you correct that line (or each line with that error) to add the missing -m- from the word -main- and see if it solves your problem.

Good luck!

---

### Post by sammiev on 2011-12-30
> **Davis Bre said:**
> Now my Java application is working. So now I don't want to remove it, but now I have a new problem, I'm unable to install new updates, because of the error:
An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/ferramroberto-java-oneiric.list'

Where do I need to send report?

Please also run the following command:

sudo rm /etc/apt/sources.list.d/ferramroberto-java-oneiric.list

Also see [this]("https://answers.launchpad.net/ubuntu/+source/apt/+question/177618") Bug Report.

---

### Post by Davis Bre on 2011-12-31
Thanks a lot! That Bug Report were very helpful, and my Ubuntu again works properly.

---

### Post by Davis Bre on 2011-12-31
My Ubuntu seemed working properly, until I restarted it to complete updates. I think, that it would be easier to reinstall OS. But how can I do it? I have tried: sudo dpkg-reconfigure -phigh -a , it works for a wile and then stops with this error: 

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop cron
cron stop/waiting
dpkg-maintscript-helper: error: couldn't identify the package

And, when I tried: sudo apt-get install -f it shoot again error. 

How can I reinstall Ubuntu. Mother google almost always shows only the ways how to install Ubuntu. And my Ubuntu is in dual boot with Windows 7.

I can use Ubuntu in Xubuntu and XFCE sessions, because in Ubuntu session isn't start menu and menu toolbar on the left side.

---

### Post by sammiev on 2011-12-31
You have errors in your updates? So likely it's in your source list. When you run a update post the error here.

---

### Post by Davis Bre on 2011-12-31
davis@ubuntu:~$  apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by sammiev on 2011-12-31
Start a new thread with that info and I'm sure one of the devs will be by to answer your question. PM the link after as well as I want to follow this one. I'm hoping to learn from this one as well. :)

---

### Post by spacecheck on 2011-12-31
> **Davis Bre said:**
> davis@ubuntu:~$  apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
<br />
You need to add "sudo" before the command

---

