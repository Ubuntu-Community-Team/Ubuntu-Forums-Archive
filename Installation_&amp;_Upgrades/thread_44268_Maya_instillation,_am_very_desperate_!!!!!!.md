---
title: "Maya instillation, am very desperate !!!!!!"
date: 2005-06-25
forum: Installation &amp; Upgrades
---

### Post by abs on 2005-06-25
hello all,

I am loving ubuntu and this is my first time using a Linux system, now a week in, i
 am using my first instillation as a tester, i would love to get my all time fav program
 running on it Maya 6.5, the problem i have is that i don't know how to install it, 

i have converted the openmotif.rpm to .deb. 

however, when i convert the maya6.5.rpm to a .deb file i don't get a .deb file, i get an extracted folder,  any ideas!!!!

iv read other forums but they all seem to mis the point, and stray away from the 
core subject, if any one has gotten maya to work on there box, please, please, let me know how, its killing me that such an amazing OS cant be used with one of my 
passions of MAYA, i love this program and just wont it to work.

i hope someone can help me in my mission of fulfillment, :confused: 

thanks for looking.


---system----
dual athlone 1800MP
quadro FX 500
1gb mem,
60GB harddrive IDE
160GB harddrive Sata
-----------------------------------------

/Abs

3d crazy

---

### Post by mingus on 2005-06-25
and you have googled the question? . . .

I found the following which may be useful . . .

[http://www.highend2d.com/boards/showflat.php?Cat=1,6,7,8,9&Board=linuxforum&Number=189551&page=1&view=collapsed&sb=5&o=&fpart=](http://www.highend2d.com/boards/showflat.php?Cat=1,6,7,8,9&Board=linuxforum&Number=189551&page=1&view=collapsed&sb=5&o=&fpart=)

[http://www.highend2d.com/boards/showflat.php?Cat=&Board=linuxforum&Number=177772&page=&view=&sb=&o=&fpart=2&vc=1](http://www.highend2d.com/boards/showflat.php?Cat=&Board=linuxforum&Number=177772&page=&view=&sb=&o=&fpart=2&vc=1)

---

### Post by abs on 2005-06-25
i have googled it!!!

i manage to get the maya application config window, but nothing seems to be in that window i.e. no tasks to select to allow me to press next.

also i get an error in the shell, "Failed to load m5opa from .:lib:../lib:/usr/aw/maya6.5/bin:/usr/aw /maya6.5/bin/../lib:/usr/aw/maya6.5/bin/lib"

which i have'nt a clue what it means, if only installing it was stright forward. ](*,) 

please can any one shed some light on this,

thanks for your help pal, ;)

abs

---

### Post by Boggles3 on 2005-07-19
i have that exact same error... someone help please  ](*,)

---

### Post by abs on 2005-07-19
helllo,

i am not sure what problem your having now, but i must say its all working now and got my alt key disabled,

ubuntu, window manager and change the alt key to windows key

 :)  :smile: 

[3dnuta.com](http://www.3dnuta.com)

---

### Post by Boggles3 on 2005-07-19
hmm.. how did you solve the m5 error??? do you remember

---

### Post by Boggles3 on 2005-07-21
ok i wound up reinstalling maya..  i didnt convert them to bed's right..


i dont like the bulky symbols for the curser in maya... any way to get rid of them??? 

also i thought maya wa sapposed to use your theme for its settings .. 
i have a dark theme and it has white text..
in maya the white text crosses over but the panels are all still grey and did not darken at all....??

this makes it really hard to read the text in maya..
why is the text changing according to my scheme but not the interface..
??
any quike fixes?? 
thanx

---

### Post by carina on 2005-08-09
> ok i wound up reinstalling maya..  i didnt convert them to bed's right..


i dont like the bulky symbols for the curser in maya... any way to get rid of them??? 


if you mean the way it turns into a default x cross after certain operations alias's solution to the problem is to set the variable MAYA_MMSET_DEFAULT_XCURSOR to something other than zero.

Now this didn't work for me, I am using fluxbox and I still got the big chunky default x cross. An easy fix is to replace the default x cursor with something else. There are cursors you can pick up at themes.freshmeat.net.

> 
also i thought maya wa sapposed to use your theme for its settings .. 
i have a dark theme and it has white text..
in maya the white text crosses over but the panels are all still grey and did not darken at all....??

this makes it really hard to read the text in maya..
why is the text changing according to my scheme but not the interface..
??
any quike fixes?? 
thanx

The Maya theme file in linux is called MayaScheme. You can find it under
/usr/aw/mayax.x/app-defaults

---

