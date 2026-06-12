---
title: "firewall installed-where did it go?"
date: 2008-06-11
forum: Installation &amp; Upgrades
---

### Post by tksee55 on 2008-06-11
hi, i'm a newbie in linux. have ubuntu 8.04 and decided to install a firewall from the repository. marked a program called fiaif and installed it. it downloaded 2 files and everything seems to have gone well, except, where did it go?

looking through the whole menu structure and it's not there? and there's no icon anywhere on the desktop to suggest that it's running in the background. it's as though nothing just happened :p

btw synaptic package manager now indicates that fiaif is installed.

can someone shed some light here? thanks.

---

### Post by iaculallad on 2008-06-11
FIAF is automaticall started when you boot your machine. Visit their [FAQ]("http://www.fiaif.net/faq.php") page for more information regarding FIAF (FIAIF Is An Intelligent Firewall).

---

### Post by mikewhatever on 2008-06-11
It seems fiaif firewall has no GUI, hence the lack of icons and menu entries. Please consult their web site for more [http://www.fiaif.net/configuration.php](http://www.fiaif.net/configuration.php).

> firewall installed-where did it go?

Obviously, a program does not live in a menu icon. If you want to find out where the packages are, try <locate fiaif>. That should only find things if fiaif is installed.

---

### Post by tksee55 on 2008-06-11
hmm...ok...a bit of reading to do then. wasn't what i was expecting. too use to windows i guessed :)

tried to look into /etc/fiaif/fiaif.cong: and there's a "x" on the folder. clicked on it and it says i do not have permission to look at it :(

so basically it's loaded automatically when the os starts up anyway.

thanks.

---

### Post by Lantesh on 2008-06-11
I'm not familiar with this particular program, but I'd imagine you should be able to change settings in the terminal.  Just because it doesn't have a GUI does not mean you shouldn't learn how to properly adjust the settings.

---

### Post by mikewhatever on 2008-06-11
> **tksee55 said:**
> hmm...ok...a bit of reading to do then. wasn't what i was expecting. too use to windows i guessed :)

tried to look into /etc/fiaif/fiaif.cong: and there's a "x" on the folder. clicked on it and it says i do not have permission to look at it :(

so basically it's loaded automatically when the os starts up anyway.

thanks.

May I ask why you picked that particular program and why you think you need a firewall. Did you know about alternatives? Firestarter is a nice GUI for IPtables, very user friendly and easy to use.
[https://help.ubuntu.com/community/Firestarter?highlight=%28firestarter%29](https://help.ubuntu.com/community/Firestarter?highlight=%28firestarter%29)

---

