---
title: "For Users wanting to upgrade from 9.04 to 9.10 Karmic"
date: 2009-09-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by BAMF1501 on 2009-09-25
Here is the howto i find to work the best ...


[LIST]
[*]Open a terminal (Applications | Accessories | Terminal)
[*]Enter the following command to update the package list:
[/LIST]
 > sudo apt-get update


Then make sure Update Manager is installed and up to date:

> sudo apt-get install update-manager


Lauch Update Manager:

> sudo update-manager -d


[LIST]
[*]You will see an option “New distribution release ‘9.10&#8242; is available”.  Click the Upgrade button to upgrade and follow the prompts to upgrade your distribution.
[/LIST]
 Now, seat back and relax because Update Manager will take a while to download all the required packages from the Internet and to install them.



---

### Post by Clonito on 2009-09-25
> **BAMF1501 said:**
> Here is the howto i find to work the best ...


[LIST]
[*]Open a terminal (Applications | Accessories | Terminal)
[*]Enter the following command to update the package list:
[/LIST]
 

Then make sure Update Manager is installed and up to date:



Lauch Update Manager:
Wouldn't easier just to download the current alpha? :confused:

---

### Post by BAMF1501 on 2009-09-25
this does all that for you

---

### Post by lovinglinux on 2009-09-25
I don't think it's a good idea to post this on the General Help forum, at least without a warning, because Karmic is still alpha and expected to break things as already reported in some threads. Despite the fact that this isn't the Absolute Beginner Talk forum, some newcomers that also visit the General Help might think it's time to upgrade, while it isn't.

Just my opinion.

---

### Post by overdrank on 2009-09-25
Moved to  Karmic Koala Testing and Discussion

---

### Post by FuturePilot on 2009-09-25
No need for launching update-manager with sudo.

---

### Post by SunnyRabbiera on 2009-09-25
This is a bad idea, Karmic is still beta/alpha.

---

### Post by llamakc on 2009-09-25
It isn't a bad idea provided any users upgrading via `update-manager -d` are well aware of any possible breakage that could and/or WILL occur prior to the proper release of 9.10. 

This method of upgrading must also be vetted for those of us who prefer the method over downloading an ISO.

---

### Post by DougieFresh4U on 2009-09-25
Should I also add that after they do there update, should they also via terminal run** sudo update-grub2** before restarting  to make sure their grub menu is in order.
**Beware of 'partial updates' don't do them**

---

### Post by Cuddles McKitten on 2009-09-25
Stupid upgrade question: does the updater install packages that I might not want (like Empathy) or does it just upgrade existing packages adding only what's necessary?

---

### Post by FuturePilot on 2009-09-25
> **Cuddles McKitten said:**
> Stupid upgrade question: does the updater install packages that I might not want (like Empathy) or does it just upgrade existing packages adding only what's necessary?

It will install new packages, such as Empathy, upgrade existing packages, and also (optionally) remove old obsolete packages.

---

### Post by Cuddles McKitten on 2009-09-25
Well, poop.  I guess I'll have to do some uninstalling when I upgrade then (assuming there's no menu beforehand).

---

### Post by Neobuntu on 2009-09-25
This is indeed a very bad idea. It's a bad idea simply because, most people are not technical. They (most) do not need to evaluate this, while undone. Sure, anyone is invited to test, if they will; but we have to remember, we (individually) are not everyone.

What is the purpose of (x)Ubuntu? For whom, are the developers (and their leaders), developing?

---

### Post by llamakc on 2009-09-25
Correct. Which is why this discussion is in the Testing Forum, and Karmic is still in Alpha.

---

### Post by chargersfan420 on 2009-09-25
Quick newb question:  If I move to some form of kernel 2.6.30, but stay on Jaunty, what percentage would you say I have upgraded towards Karmic?

---

### Post by FuturePilot on 2009-09-25
> **chargersfan420 said:**
> Quick newb question:  If I move to some form of kernel 2.6.30, but stay on Jaunty, what percentage would you say I have upgraded towards Karmic?

0% Karmic uses 2.6.31. Besides that, every single package on your system gets upgraded.

---

### Post by sgosnell on 2009-09-25
Pretty much zero.  Karmic will have the .31 kernel, AFAIK, not the .30.  The .30 does work wonderfully for me under Jaunty, but the .31 will not boot at all.  It does boot under Karmic, but I can't live with breakages on my computer, so I will wait for Karmic to be released and vetted before I jump on it.  I have installed Karmic on an SD card, and so far am not greatly impressed.  But then, it is still in the alpha stage.

---

### Post by VMC on 2009-09-25
> **chargersfan420 said:**
> Quick newb question:  If I move to some form of kernel 2.6.30, but stay on Jaunty, what percentage would you say I have upgraded towards Karmic?

You wouldn't be even close. Totally different on many levels.

---

### Post by BAMF1501 on 2009-09-25
whats empathy ??

and what yall mean no menu ??

---

### Post by VMC on 2009-09-26
> **BAMF1501 said:**
> whats empathy ??

Sorry, but I don't have much empathy for those that don't make use of search function. :)

---

