---
title: "problem running live disc"
date: 2009-09-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by joshuapbell on 2009-09-09
trying to run the live disc for karmic, and i have this issue with both 32 bit and 64... but anyways it will load to the first screen and i hit try ubuntu, it will load the first flash screen go through then eventually i will see a verbose screen, then it will go to a screen that says "ubuntu login" then i can do nothing... any ideas what is going on

---

### Post by cariboo on 2009-09-10
What do you mean when you say you can do nothing at the login screen?

Do you try to enter a user name and password? Do you wait for the time out?

Is it a graphical login, or command line ?

---

### Post by executorvs on 2009-09-10
if it's the same issue I was having with tuesday's build the gdm appears to get stuck in a loop from which the only way to exit is to power down as alt+ctrl+sysRq+K doesn't work

for clarification it's the auto login and not a command prompt

edit2: upon further reading it's a known bug affecting all ATI cards from r600 and up.

---

### Post by joshuapbell on 2009-09-10
> **executorvs said:**
> if it's the same issue I was having with tuesday's build the gdm appears to get stuck in a loop from which the only way to exit is to power down as alt+ctrl+sysRq+K doesn't work

for clarification it's the auto login and not a command prompt

edit2: upon further reading it's a known bug affecting all ATI cards from r600 and up.

yes this seems to be the issue, but i have a nvidia chipset with integrated nvidia graphics (i assume this is what you are reffering to by ati), don't remember off the top of my head exactly what model, as i am not at my computer. Maybe the bug effects nvidia too.

---

### Post by executorvs on 2009-09-10
if you have an Nvidia card make sure to file a report on launchpad as all the errors of that type I read were for ATI cards from the R600 series and up.

---

### Post by kestal on 2009-09-10
do you mean.... that its hitting a tty1 screen and asking for login/password for the live cd? (without you actually entering in a user/password?) rather than going through to the live desktop?

I have this problem on Karmic, but only on my laptop (nvidia). Desktop was fine (nvidia) -_-

---

### Post by executorvs on 2009-09-10
it opens the gdm and then tries to proceed to the desktop and.. reopens the gdm

---

### Post by joshuapbell on 2009-09-10
> **executorvs said:**
> if you have an Nvidia card make sure to file a report on launchpad as all the errors of that type I read were for ATI cards from the R600 series and up.

if this is indeed the case, then how do I go about filing a report? Obviously i can not do it now as i am not at my computer. but please do tell me how so i can when I get home. Thanks

---

### Post by joshuapbell on 2009-09-10
> **kestal said:**
> do you mean.... that its hitting a tty1 screen and asking for login/password for the live cd? (without you actually entering in a user/password?) rather than going through to the live desktop?

I have this problem on Karmic, but only on my laptop (nvidia). Desktop was fine (nvidia) -_-

Yes this is the problem

---

### Post by executorvs on 2009-09-10
karmic bug list: [https://bugs.launchpad.net/ubuntu/karmic/+bugs?start=75](https://bugs.launchpad.net/ubuntu/karmic/+bugs?start=75)
GDM loop related bug: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/419126](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/419126)

you may want to tag a related project like the xserver-xorg-video-nv package if that's what your card uses... I'm not really sure, but I'm sure if you ask someone can give you some clarification.

---

