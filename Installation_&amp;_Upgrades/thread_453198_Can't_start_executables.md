---
title: "Can't start executables"
date: 2007-05-24
forum: Installation &amp; Upgrades
---

### Post by bibbi on 2007-05-24
Hi,

When i try to start an executable from the shell, I always get a 'command not found'! How come?

Example is here:
[http://www.rainlendar.net/cms/index.php?option=com_joomlaboard&Itemid=27&func=view&catid=2&id=3171#3171]("http://www.rainlendar.net/cms/index.php?option=com_joomlaboard&Itemid=27&func=view&catid=2&id=3171#3171")

where I discuss running Rainlendar.

Any help, please?

B

p.s. just tried it with sunbird, with the same result: 'command not found'

---

### Post by bibbi on 2007-05-24
I get this error message:

[IMG]http://i8.tinypic.com/6f6tvyo.png[/IMG]


But on 'Control Center' there is no entry for 'File types and programs'

:-(

This is the directory listing:
[img]http://i18.tinypic.com/5zegwmh.png[/img]

---

### Post by bibbi on 2007-05-26
Anyone that can help...?:(

---

### Post by dodgePT on 2007-05-26
They got their own [support forum]("http://www.rainlendar.net/cms/index.php?option=com_joomlaboard&Itemid=27&func=showcat&catid=3"), ask the same question there, they'll help you for sure :)

edit: Ooops, sorry, you done it already...

Place the extracted folder in your home/'username' directory, cd into it and start the executable.

---

### Post by dodgePT on 2007-05-26
I downloaded it and ran it with no problems

---

### Post by bibbi on 2007-05-27
Yes, I ran Rainlendar before without problems. But it seems I get a 'command not found' when trying to run an executable. The same thing happens when I try to run Sunbird.

So the problem is not with the application I'm trying to start, but more likely with my Ubuntu system. Someone with a suggestion how to tackle this, how to find out what is wrong or how to restore it? Or should I just reinstall Ubuntu?

B

---

### Post by taurus on 2007-05-27
Are you trying to run 32bit apps in 64bit environment by any chance?

---

### Post by bibbi on 2007-05-29
ehhmmm.... yes. 
The creator of Rainlendar opted that it would not be a problem, so I tried it out. But as stated without positive results. 

So is this purely due to it being a 32bit program which I'm trying to run in a 64bit environment?

---

### Post by taurus on 2007-05-29
You need to install all those 32bit libraries first before you can run 32bit apps in 64bit environment.  Search for them with synaptic.

---

### Post by bibbi on 2007-05-30
Thanks Taurus, for pointing me in the right direction! But how do I find out which libraries I should get?

---

### Post by Kobalt on 2007-05-30
```
sudo apt-get install ia32-libs*
```
That should install you most of what you need.

---

### Post by bibbi on 2007-05-31
GREAT!
That did indeed work. Rainlendar2 now runs as expected. I&#314;l report this back to the Rainlendar forum.

Thanks Kobalt.

B

---

