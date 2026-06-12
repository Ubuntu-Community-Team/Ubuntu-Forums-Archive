---
title: "Ubunto doesn't recognize xp during install"
date: 2008-02-23
forum: Installation &amp; Upgrades
---

### Post by guysh on 2008-02-23
After a long long time of thinking about it, I decided to give linux a try, and tried to install ubuntu.
For different reasons I can't give up my xp so I want to use the double boot option. The problem is that the installation cd doesn't seems to recognize the installed xp on my system and only offers to either use all the cd or one partition. 
I thought about letting it use the other partition but - then I'm afraid I won&#8217;t have the option to chose an OS when booting. 

Any soultions , anyone ? 

Thanks

---

### Post by taurus on 2008-02-23
Do you already have an empty partition to install Ubuntu on?  Try picking the Manual option when you get to the partition screen.

Otherwise, open a terminal from the LiveCD and post the output of this command here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by penguinv on 2008-02-23
Yes, I too posted about this in another thread. 

I got no good help either only further obscuration, see FUD for details.

---

### Post by wolfen69 on 2008-02-23
you must have an empty partition to install ubuntu to. if you do, dont worry, it will give you the option to boot into ubuntu or xp when you're done. here is a how to about dual booting. [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by guysh on 2008-02-23
Wolfen :
The only result I get from the terminal is : Unable to open 1

penguinv  : What did you do in the end & what is fud ?

---

### Post by guysh on 2008-02-23
> **wolfen69 said:**
> you must have an empty partition to install ubuntu to. if you do, dont worry, it will give you the option to boot into ubuntu or xp when you're done. here is a how to about dual booting. [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
 
O.K - I can crate an empty one. Altough the I've read a review about ubuntu which specficly said that ubunto automaticly recognaized win and offered to install itsefl next to it.

---

### Post by taurus on 2008-02-23
> **guysh said:**
> Wolfen :
The only result I get from the terminal is : Unable to open 1

penguinv  : What did you do in the end & what is fud ?

That is a lower case letter L, not number 1!

```
sudo fdisk -**[COLOR="Blue"]l[/COLOR]**
```

---

### Post by guysh on 2008-02-23
LOL - I'll give a try later

---

