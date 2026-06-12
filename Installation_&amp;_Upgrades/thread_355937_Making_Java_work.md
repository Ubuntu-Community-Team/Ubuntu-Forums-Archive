---
title: "Making Java work"
date: 2007-02-07
forum: Installation &amp; Upgrades
---

### Post by Neko_D on 2007-02-07
So I am new to the structure of Ubuntu.  I am trying to install the java JRE plugin for my Mozilla Firefox.

So I was following your guide and whenever I type sudo aptitude install sun-java5-jre sun-java5-plugin.  I got this message
> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "sun-java5-jre"
Couldn't find any package whose name or description matched "sun-java5-plugin"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.


I was a bit conused needless to say.  Anyway I decided that I need the JDK because I program java for school.  So I went to your JDK installation instructions and had the same result.  Then I said screw it and went and manually installed JDK1.6.0 like I did on my Fedora.  Problem is that when I pasted over my symoblic link it did not work.  So HOW do I get my Java plugin to work on this OS?

-- MORE --
What is the deal here guys?  NOTHING is being found in your database.  I MEAN NOTHING and I a getting pissed off.  I try to install multimedia codecs NOTHING.  I try to install flash NOTHING I try to install anything using your guide and NOTHING IS EVER FOUND](*,) :confused: What am I doing wrong I added your extra repositories, and I copy and paste your commands.  I just want this stuff to work.  I do not want to go back to fedora because it has been pissing me off but if I must I will.

---

### Post by scrooge_74 on 2007-02-07
Hi, to your first question about java and packages, it did not install any package since it is not in the repositories.  

to install Java for your browser you need first to download it from the [Java website]("http://www.java.com") and then jsut follow the instructions there.  I am not a programmer and I manage to install JAVA by following the instructions.

For installing flash is the same you have to follow instructions from the [Adobe website]("http://www.adobe.com")

To installa codecs since those are restricted formats following the instructions on the [website]("https://help.ubuntu.com/community/RestrictedFormats") should be enough 

It would be a good idea to know which version of Ubuntu are you using and what are those steps you try and did not work. Been more specific will help others help you

---

### Post by meng on 2007-02-07
> **scrooge_74 said:**
> Hi, to your first question about java and packages, it did not install any package since it is not in the repositories.  

to install Java for your browser you need first to download it from the [Java website]("http://www.java.com") and then jsut follow the instructions there.  I am not a programmer and I manage to install JAVA by following the instructions.

For installing flash is the same you have to follow instructions from the [Adobe website]("http://www.adobe.com")

To installa codecs since those are restricted formats following the instructions on the [website]("https://help.ubuntu.com/community/RestrictedFormats") should be enough 

It would be a good idea to know which version of Ubuntu are you using and what are those steps you try and did not work. Been more specific will help others help you

Not quite true. If you enable multiverse repositories, you will be able to install sun-java5-jre and -plugin using those same commands. [https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)

EDIT: saw your postscript and I have two comments:
1. Did you "sudo aptitude update" in order for the extra enabled repositories to be registered?
2. If you must go back to Fedora, then I for one am not going to try to stop you. Heck, Fedora 7 might (eventually) be a big improvement. I will say that I personally am less inclined to make an effort to help when members cajole, threaten or just vent their frustration. It's not a threat, it's just a personal observation and I don't think I'm the only one here who feels that way.

---

### Post by scrooge_74 on 2007-02-08
I was tempted not to offer any advice, but in the spirit of the forum I offered some

---

### Post by Neko_D on 2007-02-08
> **scrooge_74 said:**
> Hi, to your first question about java and packages, it did not install any package since it is not in the repositories.  

to install Java for your browser you need first to download it from the [Java website]("http://www.java.com") and then jsut follow the instructions there.  I am not a programmer and I manage to install JAVA by following the instructions.

For installing flash is the same you have to follow instructions from the [Adobe website]("http://www.adobe.com")

To installa codecs since those are restricted formats following the instructions on the [website]("https://help.ubuntu.com/community/RestrictedFormats") should be enough 

It would be a good idea to know which version of Ubuntu are you using and what are those steps you try and did not work. Been more specific will help others help youSorry it took me so long to get back it has been a busy day/week for me.  Playing with Linux Oses was probably not the best idea this week.

But as far as following the insturctions I did, I skipped the first one and went onto the second one.  But my terminal said that "fakeroot" was not an official command.

> **scrooge_74 said:**
> I was tempted not to offer any advice, but in the spirit of the forum I offered someI am grateful you offered advice.  I am just being slow this week it has been a long stressful week.
> **meng said:**
> Not quite true. If you enable multiverse repositories, you will be able to install sun-java5-jre and -plugin using those same commands. [https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)

EDIT: saw your postscript and I have two comments:
1. Did you "sudo aptitude update" in order for the extra enabled repositories to be registered?
2. If you must go back to Fedora, then I for one am not going to try to stop you. Heck, Fedora 7 might (eventually) be a big improvement. I will say that I personally am less inclined to make an effort to help when members cajole, threaten or just vent their frustration. It's not a threat, it's just a personal observation and I don't think I'm the only one here who feels that way.No I went in and manually edited the file myself like it says to in the guide.

---

### Post by phossal on 2007-02-08
I recommend you install Java directly from SUN, rather than the repositories. Both JDK5 and JDK6 are available via the repositories, but I've always felt more comfortable getting it direct and placing it wherever I want it. The plugin .so can't just be *copied.* If you're using firefox, for example, you want to make a sym link from the JRE/plugin to /usr/lib/firefox/plugin. All the instructions you need are at SUN's site, but I've broken them down further in a tutorial linked in my signature.

---

### Post by meng on 2007-02-08
So the process of updating/adding repositories is this:
1. you edit the /etc/apt/sources.list (either directly or indirectly, e.g. through Synaptic)
2. you update (either directly by "sudo apt-get update" or "sudo aptitude update", or else indirectly, e.g. through Synaptic)
3. you install the program of interest (either directly though the terminal or indirectly through synaptic)

If you're still at a loss, please post your sources.list here:

cat /etc/apt/sources.list

---

### Post by scrooge_74 on 2007-02-09
> **phossal said:**
> I recommend you install Java directly from SUN, rather than the repositories. Both JDK5 and JDK6 are available via the repositories, but I've always felt more comfortable getting it direct and placing it wherever I want it. The plugin .so can't just be *copied.* If you're using firefox, for example, you want to make a sym link from the JRE/plugin to /usr/lib/firefox/plugin. All the instructions you need are at SUN's site, but I've broken them down further in a tutorial linked in my signature.


I second Phossal recomendation, I did the same myself (but mostly because I had to do it when I was using Debian Sarge) since  I got use to doing that

---

