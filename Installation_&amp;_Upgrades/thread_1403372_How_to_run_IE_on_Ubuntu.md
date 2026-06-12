---
title: "How to run IE on Ubuntu?"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by badaveil on 2010-02-10
In Malaysia, govt depts have to use certain e-govt applications, that were designed to run on IE. The best compromise I know is to dual-boot the computer and select Windows when IE and Windows based applications are required and select Ubuntu when they want to surf the internet, use their email and eventually use OpenOffice.org more efficiently and effectively. If IE could be easily installed on Ubuntu, that would enable e-govt applications to run on an open source platform. 

My question is "What and how is the most simplest way to install IE on Ubuntu?"#-o

---

### Post by MelDJ on 2010-02-10
try IE with wine [http://www.winehq.org/](http://www.winehq.org/)
or try: [http://www.psychocats.net/ubuntu/ies4linux](http://www.psychocats.net/ubuntu/ies4linux)

do the sites use silverlight? if they do, you can try installing moonlight so that they can be viewed in firefox [http://www.mono-project.com/Main_Page](http://www.mono-project.com/Main_Page)

---

### Post by Mark Phelps on 2010-02-10
Relying on using IE in Linux is a major mistake.

Take a look at the link below to the WinHQ page for Internet Explorer:

[http://http://appdb.winehq.org/objectManager.php?sClass=application&iId=25]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=25")

You will notice nearly ALL the versions are rated Garbage -- which means that those versions of IE will NOT work -- no matter what you do.

---

### Post by badaveil on 2010-02-10
I installed IE 7 and IE 8 exe files but double-clicking either I get extraction failed message "Unable to find a volume for file extraction. Please verify that you have proper permission"

As I am sudo can anyone advice how to go about this?

---

### Post by MelDJ on 2010-02-21
> **badaveil said:**
> I installed IE 7 and IE 8 exe files but double-clicking either I get extraction failed message "Unable to find a volume for file extraction. Please verify that you have proper permission"

As I am sudo can anyone advice how to go about this?

have you tried the ways me and the other poster have shown?

---

### Post by NightwishFan on 2010-02-21
By sudo if you mean you ran Wine as root that is not how Wine is supposed to be used. Wine is meant to be run as a standard user and you will gain no permission benefits by running wine with sudo.

---

### Post by dandnsmith on 2010-02-21
I seem to remember that there is a FireFox addon which allows it to pretend to be IE. I don't remember whether this is only Windows platform (but would expect it to be less specific).

Any mileage from going this route?

---

### Post by Mark Phelps on 2010-02-21
[QUOTE=dandnsmith;8859169]I seem to remember that there is a FireFox addon which allows it to pretend to be IE. I don't remember whether this is only Windows platform (but would expect it to be less specific)./QUOTE]

Nope -- that's not how it works.  I have such extendions in FF and all they do is launch IE and pass it the URL of the current page.  You still require IE installed and working.

---

### Post by Mark Phelps on 2010-02-21
> **badaveil said:**
> I installed IE 7 and IE 8 exe files but double-clicking either I get extraction failed message "Unable to find a volume for file extraction. Please verify that you have proper permission"

As I am sudo can anyone advice how to go about this?

Did you even LOOK at the link I posted? It clearly shows IE8 as GARBAGE -- meaning, it will NOT work -- no matter what yo do!

---

### Post by nexx on 2010-02-21
You can try ie4linux at [http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)

Install it from the console since there is some bugs when using the graphical installer that ie4linux uses.

---

### Post by nos09 on 2010-02-21
> **badaveil said:**
> I installed IE 7 and IE 8 exe files but double-clicking either I get extraction failed message "Unable to find a volume for file extraction. Please verify that you have proper permission"

As I am sudo can anyone advice how to go about this?

well its exe file so of course it'll not gonna work on ubuntu. you have to install wine.. ( tell me if i m misunderstanding something )

---

### Post by badaveil on 2010-02-21
Thanks you guys.

I solved the problem via another way, i.e. install PlayonLinux and subsequently use it to install IE7 which it does very well after it installed the latest wine file. I must say, it's not bad.

---

### Post by nos09 on 2010-02-21
> **badaveil said:**
> Thanks you guys.

I solved the problem via another way, i.e. install PlayonLinux and subsequently use it to install IE7 which it does very well after it installed the latest wine file. I must say, it's not bad.

i told you its windows application. and wine would done the job. but its fine with plyaonlinux.

---

### Post by harry2006 on 2010-02-21
As far as testing on IE6 is concerned you can pretty much do the same using IE6 on wine...you can try ie4linux...i have tried it earlier and it does work quite good...

---

