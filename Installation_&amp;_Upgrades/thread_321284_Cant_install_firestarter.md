---
title: "Cant install firestarter"
date: 2006-12-18
forum: Installation &amp; Upgrades
---

### Post by Acturbo on 2006-12-18
Hello all, I am new to the whole ubuntu thing.  I am using 6.06.  Firestarter is the first program I have tried to install.  I was under the impression all I had to do was go to the terminal and type sudo apt-get install firestarter however I get this message: 
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package firestarter

So I figure maybe its not on the system so I go to the website to download it.  After downloading it wont install and I get the message: 

Error: Dependency is not satisfiable: libgnutls11

What am I doing wrong?  This is very frustrating.  Can someone please help me?

---

### Post by ciscosurfer on 2006-12-18
> **Acturbo said:**
> Hello all, I am new to the whole ubuntu thing.  I am using 6.06.  Firestarter is the first program I have tried to install.  I was under the impression all I had to do was go to the terminal and type sudo apt-get install firestarter however I get this message: 
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package firestarter

So I figure maybe its not on the system so I go to the website to download it.  After downloading it wont install and I get the message: 

Error: Dependency is not satisfiable: libgnutls11

What am I doing wrong?  This is very frustrating.  Can someone please help me?Firestarter is the Universe repository.  [Check here]("http://psychocats.net/ubuntu/sources") to enable that repository and then install with the method you used in the beginning ```
sudo aptitude install firestarter
```

---

### Post by Acturbo on 2006-12-18
> **ciscosurfer said:**
> Firestarter is the Universe repository.  [Check here]("http://psychocats.net/ubuntu/sources") to enable that repository and then install with the method you used in the beginning ```
sudo aptitude install firestarter
```

Thanks for the help it is much appreciated.  That seems to have worked.  Would you be willing to give a more in depth explanation of what exactly I just did there.  Thanks again

---

### Post by ciscosurfer on 2006-12-18
> **Acturbo said:**
> Thanks for the help it is much appreciated.  That seems to have worked.  Would you be willing to give a more in depth explanation of what exactly I just did there.  Thanks againAbsolutely.  Basically what you did was enable a software archive (aka repository) to allow you to download that specific app.  In this case, Firestarter.  To learn more about repositories, [this page]("https://help.ubuntu.com/community/Repositories/Ubuntu") will provide you with a detailed explanation of the differences between different type of repositories, which ones are enabled by default, how to go about changing them, etc.

When you used Aptitude (a front-end for apt...[you can read more about Aptitude vs Apt-get here]("http://www.psychocats.net/ubuntu/aptitude")), it decides which dependencies are necessary for any given app that you want to either install or remove (and there are many other functions as well).  When you tried to download via the web, it may or may not have listed the specific apps (read: dependencies) upon which Firestarter depends.  Aptitude, apt-get, synaptic, adept, etc. will all resolve those dependencies for you (each app has a specific syntax to use -- Synaptic and Adept are GUI programs and do not use the command line, and thusly do not require you to learn how to resolve dependencies manually).  So, what you did was call on Aptitude to do the dependency resolution for you.

Hope that made sense.  If you need any more assistance, please let me know, and either myself or someone else here on the Forums will be glad to lead you on the correct path. :D

Cheers,
ciscosurfer

---

