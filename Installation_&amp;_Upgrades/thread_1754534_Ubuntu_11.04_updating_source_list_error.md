---
title: "Ubuntu 11.04 updating source list error"
date: 2011-05-10
forum: Installation &amp; Upgrades
---

### Post by raviainani on 2011-05-10
i have using ubuntu 10.10 from past 3 months and about a week before upgraded to 11.04. The upgrade was a successful one and everything was back to normal, was enjoying unity.

upgrading disabled most of the ppa's in the source list and later i enabled them and still everything was okay. yesterday suddenly when i clicked on the ubuntu software center it was just showing as if it was still processing the source list but after sometime it started giving me the below error: 
**"E:Type 'rc' is not known on line 3 in source list /etc/apt/sources.list.d/geod-ppa-geod-natty.list"** 

could anyone please help me with this??? 

thanks in advance
ravi

---

### Post by plucky on 2011-05-10
> **raviainani said:**
> i have using ubuntu 10.10 from past 3 months and about a week before upgraded to 11.04. The upgrade was a successful one and everything was back to normal, was enjoying unity.

upgrading disabled most of the ppa's in the source list and later i enabled them and still everything was okay. yesterday suddenly when i clicked on the ubuntu software center it was just showing as if it was still processing the source list but after sometime it started giving me the below error: 
**"E:Type 'rc' is not known on line 3 in source list /etc/apt/sources.list.d/geod-ppa-geod-natty.list"** 

could anyone please help me with this??? 

thanks in advance
ravi

Post output of ```
cat /etc/apt/sources.list.d/geod-ppa-geod-natty.list
```

---

### Post by raviainani on 2011-05-10
deb [http://ppa.launchpad.net/geod/ppa-geod/ubuntu](http://ppa.launchpad.net/geod/ppa-geod/ubuntu) natty main
deb-src [http://ppa.launchpad.net/geod/ppa-geod/ubuntu](http://ppa.launchpad.net/geod/ppa-geod/ubuntu) natty main
rc [http://ppa.launchpad.net/geod/ppa-geod/ubuntu](http://ppa.launchpad.net/geod/ppa-geod/ubuntu) natty main # disabled on upgrade to natty disabled on upgrade to natty

the above is the output

thanks plucky :)

---

### Post by iponeverything on 2011-05-10
change line 3 to start with:

#

---

### Post by raviainani on 2011-05-10
> **iponeverything said:**
> change line 3 to start with:

#

sorry... could you pls explain it a little more.. i'm a n00b :(

thanks

---

### Post by plucky on 2011-05-10
> **raviainani said:**
> deb [http://ppa.launchpad.net/geod/ppa-geod/ubuntu](http://ppa.launchpad.net/geod/ppa-geod/ubuntu) natty main
deb-src [http://ppa.launchpad.net/geod/ppa-geod/ubuntu](http://ppa.launchpad.net/geod/ppa-geod/ubuntu) natty main
rc [http://ppa.launchpad.net/geod/ppa-geod/ubuntu](http://ppa.launchpad.net/geod/ppa-geod/ubuntu) natty main # disabled on upgrade to natty disabled on upgrade to natty

the above is the output

thanks plucky :)

You need to edit the file with ```
gksudo gedit /etc/apt/sources.list.d/geod-ppa-geod-natty.list
``` and remove the line```
rc http://ppa.launchpad.net/geod/ppa-geod/ubuntu natty main # disabled on upgrade to natty disabled on upgrade to natty

``` as it is not needed.

Good Luck

---

### Post by raviainani on 2011-05-10
> **plucky said:**
> You need to edit the file with ```
gksudo gedit /etc/apt/sources.list.d/geod-ppa-geod-natty.list
``` and remove the line```
rc http://ppa.launchpad.net/geod/ppa-geod/ubuntu natty main # disabled on upgrade to natty disabled on upgrade to natty

``` as it is not needed.

Good Luck

thanks a lot plucky... you saved me.... :guitar:

i've one question, though it is out of this thread topic but i believe you answer this.... is it possible to get a 3d (stero) output from my laptop to my 3d monitor??? 

MY GRAPHICS CARD IS INTEL 945 GME, thanks again for the help

regards
ravi

---

### Post by plucky on 2011-05-11
Well done,can you please mark the thread as **[Solved]** using the [color=red]Thread Tools[/color] icon at the top of the page.



> i've one question, though it is out of this thread topic but i believe you answer this.... is it possible to get a 3d (stero) output from my laptop to my 3d monitor???

MY GRAPHICS CARD IS INTEL 945 GME, thanks again for the help

I doubt it as you need to have HDMI video card to get 3D output.

Good Luck

---

