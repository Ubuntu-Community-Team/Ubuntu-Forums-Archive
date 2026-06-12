---
title: "No X11 on new Ubuntu Server installation"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by nonyadb on 2007-04-23
I downloaded ubuntu-7.04-server-i386.iso and installed it on my old PII 550. After the base install, I chose the LAMP software package.

When I rebooted, it just stuck at "Running local boot scripts". If I press "Enter" it goes to a command prompt after I log in.

If I boot in recovery mode the last line before the command prompt (no login this time) is "Setting up console fonts and keymap".

If I go to the /ect/X11/ directory the only thing listed is another directory named "xkb".

---

### Post by haricharan on 2007-04-23
i dont think the server edition comes with X11...you got to download the desktop edition..

---

### Post by uberNoobZA on 2007-04-23
You have 2 options.....

Install Ubuntu 7.04 Server and then use the following to download and install desktop components -

sudo aptitude install ubuntu-desktop

Alternatively install Ubuntu 7.04 Desktop and use the following to install LAMP -

sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server

Note - I have simply mined the above info from other threads on this forum, so cannot assist if they don;t work. I am VERY new to Ubuntu and Linux, but experienced the same issues as you, so thought I'd post the info I found.

---

### Post by nonyadb on 2007-04-23
> **uberNoobZA said:**
> Install Ubuntu 7.04 Server and then use the following to download and install desktop components -

sudo aptitude install ubuntu-desktop

I tried this after your recommendation and it downloaded the kitchen sink. I saw libraries for games and office productivity being downloaded and decompressed. I'm installing this on an old computer with a 2GB hard drive, 128MB of which is used for swap.

Is there a way to install only the desktop, network management software, and any dependencies?

Also, does anyone have any idea why a LAMP installation would be able to download files but not accept incoming connections?

---

### Post by nonyadb on 2007-04-25
Nobody?

Nothing?

---

### Post by haricharan on 2007-04-29
i m not sure abt how much size it occupies...but it definitely can fit in 2 GB i guess....

---

