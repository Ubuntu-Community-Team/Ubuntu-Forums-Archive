---
title: "Sabayon app in Lucid"
date: 2010-01-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by SnowRider on 2010-01-03
Sabayon app in Lucid..What is this all about? While poking around the menu this app asked for sabayon password.I gave it my password,but nothing opened.It just disappeared..Strange..Any ideas?

---

### Post by k3lt01 on 2010-01-03
[http://packages.ubuntu.com/lucid/sabayon](http://packages.ubuntu.com/lucid/sabayon)

---

### Post by ronacc on 2010-01-03
try starting it from term with sudo . the menu iten calls gksudo sabayon and that fails , it starts with just plain sudo . starting from term with gksudo shows it fails opening up a dialog box, file a bug on it.

---

### Post by SnowRider on 2010-01-04
[HTML]k3lt01  	
Re: Sabayon app in Lucid
http://packages.ubuntu.com/lucid/sabayon[/HTML]k3lt01--Thank you for the link I didn't know Lucid and Sabayon shared the same libs.                  [HTML]ronacc  	
Re: Sabayon app in Lucid
try starting it from term with sudo . the menu iten calls gksudo sabayon and that fails , it starts with just plain sudo . starting from term with gksudo shows it fails opening up a dialog box, file a bug on it.[/HTML] ronacc--Will try opening it with sudo when I get back to my Lucid installation.Didn't file a bug report yet because I wanted to find out if anybody else had the same problem.

---

### Post by lavinog on 2010-01-05
> **SnowRider said:**
> I didn't know Lucid and Sabayon shared the same libs.

Sabayon is just the name of the application.  It isn't referring to the distribution.

---

### Post by ranch hand on 2010-01-05
The distro is debian based though so a lot of stuff is the same.

---

### Post by k3lt01 on 2010-01-05
> **SnowRider said:**
> [HTML]k3lt01  	
Re: Sabayon app in Lucid
http://packages.ubuntu.com/lucid/sabayon[/HTML]k3lt01--Thank you for the link I didn't know Lucid and Sabayon shared the same libs.                  [HTML]If you had taken a look at the page you would have seen, as has already been pointed out, that Sabayon is an application that is in the Lucid Repostories. Sabayon isn't a separate distribution.

The page I linked for you tells you about Sabayon as it is within Lucid and answers your question as to what it is for.

---

### Post by ranch hand on 2010-01-06
> **k3lt01 said:**
> If you had taken a look at the page you would have seen, as has already been pointed out, that Sabayon is an application that is in the Lucid Repostories. Sabayon isn't a separate distribution.

The page I linked for you tells you about Sabayon as it is within Lucid and answers your question as to what it is for.
The confusion comes due to the fact that there is a Sabayon distro;

[http://sabayonlinux.org/](http://sabayonlinux.org/)

There is also somesort of salad dressing by that name but no one seems to be confusing that with the app or the distro.  Beats me.

---

### Post by k3lt01 on 2010-01-06
> **ranch hand said:**
> The confusion comes due to the fact that there is a Sabayon distro;

[http://sabayonlinux.org/](http://sabayonlinux.org/)Two different links showing two different things. There should be no confusion if the links supplied are actually read. The most important thing I have found with Linux, specifically Ubuntu, is the need to be prepared to do alot of reading. If your not willing to put in the work to read you aren't going to get a grip on things.

> **ranch hand said:**
> There is also somesort of salad dressing by that name but no one seems to be confusing that with the app or the distro.  Beats me.And this has what to do with the current discussion?

---

### Post by SnowRider on 2010-01-08
> k3lt01   If you had taken a look at the page you would have seen, as has already been pointed out, that Sabayon is an application that is in the Lucid Repostories. Sabayon isn't a separate distribution.

The page I linked for you tells you about Sabayon as it is within Lucid and answers your question as to what it is for.                         I have finally returned home and had time to read your link.Yes,Iwas confusing the app with the Distro.Thank you for helping straightening it out.                                                                        > ronacc  	
Re: Sabayon app in Lucid
try starting it from term with sudo . the menu iten calls gksudo sabayon and that fails , it starts with just plain sudo . starting from term with gksudo shows it fails opening up a dialog box, file a bug on it.    You are quite right.It opens with sudo.gksu gives a broken pipe error.I will file a bug report if I can't fix it myself.             > ranch hand   There is also somesort of salad dressing by that name but no one seems to be confusing that with the app or the distro. Beats me.                                                               Next time I'm at the Supermarket,I will look for it.I'm always game to try something new.

---

### Post by SnowRider on 2010-01-09
Sabayon working fine with todays updates.

---

