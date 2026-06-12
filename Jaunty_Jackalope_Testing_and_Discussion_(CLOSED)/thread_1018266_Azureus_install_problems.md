---
title: "Azureus install problems"
date: 2008-12-21
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by LordVeovis on 2008-12-21
I am told different errors depending on where I try to install from... If I try from Add/Remove Applications I am told it will remove other packages and I should use Synaptic... In synaptic if I try to install Vuze (thats what I tried first) it tells me:
```

vuze:
 Depends: azureus but it is not going to be installed

```
So when I try to install azureus:
```

azureus:
 Depends: libseda-java  but it is not installable
 Recommends: vuze but it is not going to be installed

```
In command line 
```

sudo apt-get install azureus
[sudo] password for me:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  azureus: Depends: libseda-java but it is not installable
E: Broken packages

```

What's broken? Is it something I can work arround?

---

### Post by LordVeovis on 2008-12-23
Still having problems.  Has anyone been able to install this?

I read arround and found this [http://ubuntuforums.org/showthread.php?t=80647](http://ubuntuforums.org/showthread.php?t=80647)  But it wasn't able to help me as it was 3+yrs old

---

### Post by BwackNinja on 2008-12-24
libseda-java does not exist in the jaunty repos. You can get it from here: [https://launchpad.net/ubuntu/jaunty/i386/libseda-java/3.0-3](https://launchpad.net/ubuntu/jaunty/i386/libseda-java/3.0-3)

Its status is "deleted" so there might be a reason why it isn't in the repos, try it and see :P

---

### Post by gfang on 2009-03-24
I got Vuze/Azureus to work like this.

Open the Azureus script and edit the line 

 "[COLOR="DarkGreen"]JAVA='/usr/lib/jvm/[COLOR="Red"]java-6-openjdk[/COLOR]/jre/bin/java -Xmx1024M'[/COLOR]"

to look like this

"[COLOR="DarkGreen"]JAVA='/usr/lib/jvm/[COLOR="Red"]java-6-sun[/COLOR]/jre/bin/java -Xmx1024M'[/COLOR]"


Works fine!

---

