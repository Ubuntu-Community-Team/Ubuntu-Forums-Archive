---
title: "how can i install java?"
date: 2010-02-19
forum: Installation &amp; Upgrades
---

### Post by infla on 2010-02-19
Hello,

I've formatted my whole computer (because i had a few linux distro's on it. and i'd like to reinstal my ubuntu aswell.

but on some sites, I need Java. but I don't got that installed. I don't know how I have to install it. any ideas?

greetings,

Infla

---

### Post by ratcheer on 2010-02-19
Which Java do you want? I downloaded mine from java.sun.com, but others are available.

Tim

---

### Post by infla on 2010-02-19
oh? I don't know :P

just a normal java version i guess :P

---

### Post by infla on 2010-02-19
well, i've downloaded something there, but how can i install it?

---

### Post by infla on 2010-02-19
oh, wait, I think that I got it.

---

### Post by gjoellee on 2010-02-19
you can just install this:
```
sudo atp-get install ubuntu-restricted-extras
```

it installs java, flash, media codecs and fonts.

---

### Post by San_SS! on 2010-02-19
Well, it depends on what you want, but personally I like the Sun java package:

If you want the Java Runtime Envirnoment:

```

$sudo aptitude install sun-java6-jre

```

If you need the Development Kit:

```

$sudo aptitude install sun-java6-jdk

```

If you want the plugin for your browser:
```

$sudo aptitude install sun-java6-plugin

```

I hope this is useful for you.

---

### Post by infla on 2010-02-19
San_SS,


i can't do that, because:
/var/lib/dpkg/lock

that is locked (i'm not permitted to do that)

so I think that i have to unlock it with chmod?  but what was the code for that?

greetings,

Infla

---

### Post by gjoellee on 2010-02-19
> **infla said:**
> San_SS,


i can't do that, because:
/var/lib/dpkg/lock

that is locked (i'm not permitted to do that)

so I think that i have to unlock it with chmod?  but what was the code for that?

greetings,

Infla
 
Are you already installing something? Is synaptic running?  If not, just reboot, and it should be solved.

---

### Post by infla on 2010-02-19
> **gjoellee said:**
> Are you already installing something? Is synaptic running?  If not, just reboot, and it should be solved.


okay, i'll try

---

### Post by infla on 2010-02-19
no, i still can't.

```
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

```

---

### Post by infla on 2010-02-20
anyone?

---

### Post by Soul-Sing on 2010-02-20
> **infla said:**
> anyone?

if all other -apt/software manager/synaptic etc is closed

```
sudo rm /var/cache/apt/archives/lock
```
```
sudo apt-get update
```

Did you sign the license that comes with sun java? If not sometimes linux comes with this errors....

---

### Post by ubantu_user on 2010-02-24
I tried installing using the commands....I get the following error

$ sudo aptitude install sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Couldn't find any package whose name or description matched "sun-java6-plugin"
Couldn't find any package whose name or description matched "sun-java6-plugin"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done



> **San_SS! said:**
> Well, it depends on what you want, but personally I like the Sun java package:

If you want the Java Runtime Envirnoment:

```

$sudo aptitude install sun-java6-jre

```If you need the Development Kit:

```

$sudo aptitude install sun-java6-jdk

```If you want the plugin for your browser:
```

$sudo aptitude install sun-java6-plugin

```I hope this is useful for you.

---

### Post by oldos2er on 2010-02-24
Check System, Administration, Software Sources, and make sure you have the multiverse repository enabled.

---

### Post by QIII on 2010-02-24
The version of Java you can install from the repos is dated.

You may want to either install OpenJDK or follow the instructions here:

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

