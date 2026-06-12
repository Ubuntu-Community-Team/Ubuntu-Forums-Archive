---
title: "What components of MySQL do I need to install?"
date: 2010-01-13
forum: Installation &amp; Upgrades
---

### Post by rpaskudniak on 2010-01-13
Greetings.

I need to come up to speed on MySQL.  When I installed my OS, I skipped this part, though I see that many MySQL-related components are already installed, mainly libraries and modules eg. for Perl/DBI::mysql.  However, I clearly do not have mysqld running.

My problem is the size of the haystack: If I go into Synaptic and search for mysql, I get a godzillion packages, simply because the description mentions mysql.  Constraining the search ([Name] for example) helps very little because none of the names mean anything.  I also know there is more than one GUI interface but the only one I know off-hand is gmysqlcc; I would have to know the name of every blessed component before getting started.

I want the server, obviously, and every shell-runnable front-end, GUI or not, plus the libraries for C, C++, Perl, PHP, Ruby etc. Hence, my question: (Yeah, I figure you wondering when I would get around to that. :P  )

As I step down the list in synaptic, what packages must I install?

Thanks.

---

### Post by plusnplus on 2010-01-14
Hi rpaskudniak,

mostly what you need is: (in terminal)

sudo apt-get install mysql-server

---

### Post by phillw on 2010-01-14
Why not do this ....

> 
A quick word on **LAMP**, yes all you wannabe programmers & web-designers !!!

As of 9.10 the **correct** way to put on a LAMP server is as follows
```
sudo tasksel
```Arrow dowm to LAMP, press the space bar to put an * in the box, press the tab bar to get to <OK> and press enter. Then do as it says & **make a note of your MySQL root password**

Then, go into System --> Administration --> Synaptic Package Manager
Type in phpmyadmin in the search window, right click on the little box to the left of phpmyadmin in the results area, select install, then click on 'Apply'. Do as it says.

Then reboot. You now have a full LAMP installation with PhpMyAdmin on it - all configured up. Do **not** do it the long way round - it causes much grief and takes me ages to fix it for you all !!!
That will put all the dependant packages on for you & pop on phpMyAdmin for playing with your MySQL installation.

Regards,

Phill.

---

### Post by rpaskudniak on 2010-01-14
Thanks, Guys.

I went with plusnplus's simpler suggestion.  I actually had seen this command in the forum but the poster was having such grief therefrom, I guessed (incorrectly, I now see) it would not the the path to take.  Thus, for mysql, my issue is basically solved. I will download/install gmysqlcc later.

On the other hand, phillw has opened my eyes in two ways:
[LIST]
[*]Introducing me to tasksel, which I have never heard of.
[*]Introducing me to the LAMP, sort of.  I have seen this acronym before, in the context of googgling for MySQL info.
[/LIST]

That tasksel seems like a pre-packaged menu, but it provided no exit button; I had to kill [-1] it from another window.  I hope I haven't damaged my file system in the process.  And despite the contents of the man page for tasksel, I am left confused about just what constitutes a "task", though it certainly appears to be an installation.

But what in blazes is the LAMP server?  Why would I want this installed?

This looks like a matter for a whole new thread.  I will re-post this question in a new thread to avoid muddling the issue.

Thanks to you both.

---

