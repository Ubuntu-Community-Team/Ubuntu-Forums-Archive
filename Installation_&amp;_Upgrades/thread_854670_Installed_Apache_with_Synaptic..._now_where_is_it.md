---
title: "Installed Apache with Synaptic... now where is it?"
date: 2008-07-09
forum: Installation &amp; Upgrades
---

### Post by brnetonboy on 2008-07-09
I need to install the latest version of Apache, so in Synaptic, I did "mark for installation" on 'apache2'. It automatically marked some other ones for me too.

It seemed to have installed correctly, since it told me "Changes applied. Successfully applied all changes..."

How can that be? :-k I've set up Apache on Windows, and it asks TONS of questions. It never asked what directory to install to, what network domain, what admin email... nothing! Furthermore, Apache doesn't exist anywhere in the menu... "apache" in a terminal does nothing... what am I missing?

Also... I have no idea what exact version of Apache I installed. Was it 2.2? Also, someone told me I needed to install it as root. Is there a way to do this through synaptic? Thanks to anyone who can help!

---

### Post by NTolerance on 2008-07-09
Apache is already installed and running as a daemon with sensible default settings.  That's the beauty of apt-get.  Just type "localhost" into your browser and you should see the default test page.  The webroot is at /var/www and the config files are located at /etc/apache2.  Synaptic should tell you what version of Apache you have installed.  Also, anytime you install anything with Synaptic you will be prompted for to enter your password for root access.

---

### Post by brnetonboy on 2008-07-09
> **NTolerance said:**
> Apache is already installed and running as a daemon with sensible default settings.  That's the beauty of apt-get.  Just type "localhost" into your browser and you should see the default test page.  The webroot is at /var/www and the config files are located at /etc/apache2.  Synaptic should tell you what version of Apache you have installed.  Also, anytime you install anything with Synaptic you will be prompted for to enter your password for root access.

Awesome. That was just what I needed. Synaptic really should have told me those crucial pieces of information as soon as it finished installing... I really have no idea why Synaptic isn't more helpful post-install. Every time I install something I am stuck with the question "now what?"

Fortunately, the forums are extremely awesome! Thanks so much! BTW, If anyone knows of useful guides to configuring Apache, I'd love to see them.

---

### Post by NTolerance on 2008-07-10
I think the reason why Synaptic doesn't give you information about each program post-install is due to the fact that it's designed to install multiple packages at once.  Could get too verbose and clunky to have dialogs pop up after each program installs.  

After you install a package with Synaptic there's a couple of command line utilities which can give you more info about what you just installed.  To find where the executable for a program is located, do this (using apache2 as an example)

```
which apache2
```

If you want to get a small amount of info about a program, use the --help option (using ls as an example)

```
ls --help
```

If you want to get a lot of info about a program use man

```
man apache2
```

---

