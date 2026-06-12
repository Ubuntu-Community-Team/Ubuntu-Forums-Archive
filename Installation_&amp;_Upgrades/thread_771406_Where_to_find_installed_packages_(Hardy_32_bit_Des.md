---
title: "Where to find installed packages (Hardy 32 bit Desktop version)?"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by hannah187 on 2008-04-27
Hi all,
I cannot post in [COLOR="Red"]**Absolute Beginner Talk forum**[/COLOR]. Any particular reason. I have been a good boy…

I am running Hardy 32 bit Desktop version fresh install. I have got 2 questions.

1.	I have installed few extra packages through Synaptic however do not seem to find them. Can you please give me a pointer re: how to find them easily and put in under Application menu?
2.	I also have downloaded these packages in my computer before installing. I would like to keep these packages in my flash drive for future use. Where can I find these packages in my directory to copy from, please?
Thanks for the help

---

### Post by martrn on 2008-04-27
> **hannah187 said:**
> Hi all,
I cannot post in [COLOR="Red"]**Absolute Beginner Talk forum**[/COLOR]. Any particular reason. I have been a good boy&#8230;  I am running Hardy 32 bit Desktop version fresh install. I have got 2 questions. 

1.	I have installed few extra packages through Synaptic however do not seem to find them. Can you please give me a pointer re: how to find them easily and put in under Application menu?


To find firefox open a terminal and type
> whereis firefox

> **hannah187 said:**
> 
2.	I also have downloaded these packages in my computer before installing. I would like to keep these packages in my flash drive for future use. Where can I find these packages in my directory to copy from, please?
Thanks for the help


If you are talking about applications fetched via apt then
From
```
man aptitude
```
> 
Enviroments....

       TMP
           If TMPDIR is unset, aptitude will store its temporary files in TMP if that variable is set.
           Otherwise, it will store them in /tmp.

If you are talking about downloading debian packages from [getdeb]("http://www.getdeb.net/") or other simular sites then that will depend on the browser you are using and will usually be at /home/name or /home/name/desktop  where /name is your login name.

---

### Post by hannah187 on 2008-04-27
thanks ..will try this eve.. appreicate the promptness

---

