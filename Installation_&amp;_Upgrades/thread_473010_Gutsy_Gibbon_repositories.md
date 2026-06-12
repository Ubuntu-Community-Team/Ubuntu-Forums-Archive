---
title: "Gutsy Gibbon repositories"
date: 2007-06-13
forum: Installation &amp; Upgrades
---

### Post by skymera on 2007-06-13
Few of you might already seen these.

!WARNING!
THESE ARE SUPER PRE-RELEASED.
YOU AT YOUR OWN WILL! IF YOU NOT AFRAID OF BREAKAGE!
THESE ARE NOT RECOMMENDED TO BE USED!

```
How to upgrade from Feisty Fawn -> Gutsy Gibbon

    * Use these repos if you are /not/ afraid of breakage. 

Add the following lines to your feisty /etc/apt/sources.list

deb http://us.archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse

deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse

deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main universe restricted multiverse

deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main universe restricted multiverse

deb http://us.archive.ubuntu.com/ubuntu/ gutsy-security main universe restricted multiverse

deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-security main universe restricted multiverse

deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main universe restricted multiverse

deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main universe restricted multiverse

deb http://us.archive.ubuntu.com/ubuntu/ gutsy-proposed main universe restricted multiverse

deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-proposed main universe restricted multiverse

Run "sudo apt-get update && sudo apt-get dist-upgrade" 
```

ONCE INSTALLED, GOOD LUCK

---

### Post by skymera on 2007-06-13
not one comment?

---

### Post by allforcarrie on 2007-06-13
thank you.

---

### Post by zvacet on 2007-06-14
Thanks,but I will wait until october.

---

### Post by skymera on 2007-06-14
i will wait until october aswell.
dont wanna risk anything :)

---

### Post by eentonig on 2007-06-14
Now that I have VMWare setup, I'll give it a try one of these days.

---

### Post by skymera on 2007-06-14
you can wait till october when its officially released :)
these are 'use at your will' repos

---

### Post by redas23 on 2007-07-14
Haloo thanks for repository

---

### Post by mhenriday on 2007-07-15
> **redas23 said:**
> Haloo thanks for repositoryHow did the repositories work out for you, **redas** ? Did you have any problems getting **Gutsy** to work ? If so, could you describe them ? And last but not least, what sort of computer setup do you employ ?...

Henri

---

### Post by louieb on 2007-07-15
> Add the following lines to your feisty /etc/apt/sources.listI don't use my Feisty install on my desktop so I don't care if it breaks or not. (I still use Dapper its works well and its stable.)
But a quick question. Do you **add** the Gutsy repositories to the Feisty ones or do you **replace** them.

---

### Post by skymera on 2007-07-15
i bwelieve you replace them.

---

### Post by skymera on 2007-07-15
i believe you replaxce them

---

### Post by jlc on 2007-07-15
You could just tell people to do the following to make it easier.

```

$ cd /etc/apt
$ sudo cp /etc/apt/sources.list /etc/apt/sources.list.feisty

```

then:

```

$ sudo sed -i s/feisty/gutsy/g /etc/apt/sources.list

```

---

### Post by louieb on 2007-07-15
> **jlc said:**
> You could just tell people to do the following to make it easier.
```

$ sudo sed -i s/fiesty/gutsy/g /etc/apt/sources.list

```

I tried to cut and paste the  **sed**  but the  way you have it didn't do a thing, because**   feisty** is misspelled. Fixed the spelling and sed did its thing.
I'll let you know how the upgrade goes.

---

### Post by louieb on 2007-07-16
For some odd reason I backed up my Feisty install and ran 
```
sudo apt-get update && sudo apt-get dist-upgrade
```Downloaded 500+mg of packages upgrade stopped about 1/2 way problem with dependencies for gedit. Rebooted logon screen was fine but when i logged on all i got was a gray blank screen w a cursor.  used Ctrl+alt+f1 to get a command line Ran apt-get -f install started and finished. 
Rebooted again logon screen is fine. Logged in, Gnome starts up I have my desktop with one major problem: Fonts are all messed up can't hardly read a thing. Thunderbird's fonts really messed up to. 

Oh well another dist-upgrade gone bad. Think I'll stick with Dapper till the alternated CD comes out and do a fresh install then.

---

### Post by mhenriday on 2007-07-16
> **louieb said:**
> ... Fixed the spelling and sed did its thing.
I'll let you know how the upgrade goes.

And how did the upgrade go, **louieb** ? Did you find yourself in **Gutsy** after running ```
cd /etc/apt
$ sudo cp /etc/apt/sources.list /etc/apt/sources.list.feisty
sudo sed -i s/feisty/gutsy/g /etc/apt/sources.list
```and then re-booting, did the new kernel work as expected ?...

Henri

---

### Post by jlc on 2007-07-16
> **louieb said:**
> I tried to cut and paste the  **sed**  but the  way you have it didn't do a thing, because**   feisty** is misspelled. Fixed the spelling and sed did its thing.
I'll let you know how the upgrade goes.

fixed typo.

---

