---
title: "Ubuntu Wont Let me Update!"
date: 2009-07-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by CompizDoDo on 2009-07-16
ok so i am really eager to try out ubuntu 9.10 i don't know why but i just am and know matter how hard i try i cannot get my ubuntu to update to it on the ubuntu website it sais to run alt plus f2 to run update manager but it sais no such command and when i go to system preferences and click on update manager there is no option to update i am caught in a bind and really want 9.10 please help

---

### Post by nhasian on 2009-07-16
looks like you forgot the hyphen.  it should be:

```
sudo update-manager -d
```

Click on System Menu -> Administrator -> Software Source -> Click on Updates TAB ->, which will display the Software Source dialogue box.

Set the value in the &#8220;Show new distribution releases&#8221; drop-down list to &#8220;Normal releases&#8221; as shown below.

---

### Post by MontelEdwards on 2009-07-16
uh, yeah. 
You probably don't need to be on Karmic if you are asking this lol, it is really, really buggy.
I just got done switching back. I did a clean install but iirc yeah just press the ALT key and F2 together, and you will see a prompt. Type in ```
update-manager -d
```


but again,
i would really advise you to wait till the beta comes out.

---

### Post by MontelEdwards on 2009-07-16
> **nhasian said:**
> looks like you forgot the hyphen.  it should be:

```
sudo update-manager -d
```Click on System Menu -> Administrator -> Software Source -> Click on Updates TAB ->, which will display the Software Source dialogue box.

Set the value in the &#8220;Show new distribution releases&#8221; drop-down list to &#8220;Normal releases&#8221; as shown below.
hah beat me to it.
OH, and dont use sudo, its a graphical program :)
gksudo :)

---

### Post by nhasian on 2009-07-16
your right.  it should be

```
gksu update-manager -d
```

but either will work i guess.  I'm just used to doing everything from a terminal:

```
sudo apt-get dist-upgrade
```

anyway, i've been running karmic alpha2 since it came out with only a couple of minor hiccups there were corrected easily.  alpha3 should be out in a few days now.

> **MontelEdwards said:**
> 
You probably don't need to be on Karmic if you are asking this lol, it is really, really buggy.


---

### Post by MontelEdwards on 2009-07-16
> **nhasian said:**
> your right.  it should be

```
gksu update-manager -d
```but either will work i guess.  I'm just used to doing everything from a terminal:

```
sudo apt-get dist-upgrade
```anyway, i've been running karmic alpha2 since it came out with only a couple of minor hiccups there were corrected easily.  alpha3 should be out in a few days now.
Well have you tried to build any source code on it?
dosent work that good :)

oh, the dist-upgrade will not show early development releases.

it usually gets good around alpha3, ill try it on my net-book. I did love the new log in screen though.

oh, btw if you want to try the new Grub2 i would reccomend doing a clean install. just download the ISO.
and, ext4 is default.

---

### Post by CompizDoDo on 2009-07-16
thanks guys! but before i do it is it really that buggy im not looking to do no hacking or anything ?

---

### Post by CompizDoDo on 2009-07-16
ok, so i tryed the command
gksu update-manager -dand it worked but when it opens up update manager it sais im up to date? there is no indication that i can upgrade please help

---

### Post by MontelEdwards on 2009-07-16
Well i dont do any hacking either! 
well i hack my own **** just to see if i can.

but it depends on what you are going to be doing.
I personally, hate it.
I only did it to help out and file a couple of bugs on Launchpad. Just wait a couple months for Beta.

---

### Post by MontelEdwards on 2009-07-16
> **CompizDoDo said:**
> ok, so i tryed the command
gksu update-manager -dand it worked but when it opens up update manager it sais im up to date? there is no indication that i can upgrade please help
hmm. go to system>administration> software sources
then go to updates, and then make Show distribution releases to 'normal releases' and try again :)

---

### Post by philcamlin on 2009-07-16
> **MontelEdwards said:**
> hmm. go to system>administration> software sources
then go to updates, and then make Show distribution releases to 'normal releases' and try again :)

yeah that shoulld so it

---

### Post by CompizDoDo on 2009-07-16
still nothing

---

### Post by philcamlin on 2009-07-16
sudo apt-get dist-upgrade

---

### Post by MontelEdwards on 2009-07-16
> **CompizDoDo said:**
> still nothing
thats gayy
hmmph.
uh... im outa ideas. hopefully else knows.

---

### Post by MontelEdwards on 2009-07-16
> **philcamlin said:**
> sudo apt-get dist-upgrade
those wont show development releases :)

---

### Post by CompizDoDo on 2009-07-16
this is the result
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by MontelEdwards on 2009-07-16
uhhhhh,
idfk but lets try to run the update manager without gksudo, 
i tried it and it works so..

```
 update-manager -d 
```

OHH!
make sure you press the "check" button!

---

### Post by CompizDoDo on 2009-07-16
PSHHHHH i always press[SIZE=1] check[/SIZE] all i did was run the command
 update-manager -din terminal and it worked thanks so much!!!!:guitar:u rock!

---

### Post by CompizDoDo on 2009-07-16
it is updating now i cant wait untill full release i hope there inst too many bugs!

---

### Post by philcamlin on 2009-07-16
thats good :)

---

### Post by Crunchy the Headcrab on 2009-07-16
> **CompizDoDo said:**
>  i hope there inst too many bugs!

Pssshh....there's still a ton of bugs in Jaunty!  It's my favorite distro and the only one that doesn't play nice with my computer.

---

### Post by CompizDoDo on 2009-07-16
:lolflag:

---

### Post by nhasian on 2009-07-16
the only issues with upgrading from a previous release instead of a fresh install is that you'll still be running on EXT3 partitions when EXT4 is the default now and you wont have grub2 yet.

---

### Post by philinux on 2009-07-16
> **CompizDoDo said:**
> ok so i am really eager to try out ubuntu 9.10 i don't know why but i just am and know matter how hard i try i cannot get my ubuntu to update to it on the ubuntu website it sais to run alt plus f2 to run update manager but it sais no such command and when i go to system preferences and click on update manager there is no option to update i am caught in a bind and really want 9.10 please help

If you are having trouble now you'll regret updating to 9.10. It's still at alpha 2 and things break regularly.  See the forum. Read the stickies there.
[http://ubuntuforums.org/forumdisplay.php?f=359](http://ubuntuforums.org/forumdisplay.php?f=359)

If you really want it I'd advise dual booting. At least have one stable system running.

---

### Post by MontelEdwards on 2009-07-16
Glad i could help :)

---

