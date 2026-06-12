---
title: "copy the configuration from one version of ubuntu to another"
date: 2012-03-15
forum: Installation &amp; Upgrades
---

### Post by groveman on 2012-03-15
Hello everybody,

I have been using Ubuntu 10.10 for over a year. Now when it is at the end of life I started thinking about an update to 11.10 or 12.04.

What I remember was a big problem a year back is configuration of my Kworld tv tuner card to work with tvtime. At the end, after trying this and that, tv card just started working. Needless to say I don't know what exactly did I do to make it work.

So, my question is: Is it possible to somehow copy configurations of tv card and tvtime so it could just work under new version?

I'd appreciate any help you have to offer.[I]
Thanks.
[/I]

---

### Post by papibe on 2012-03-16
Hi groveman. Welcome to the forums!

I'm not familiar with Kworld, but almost every desktop application that I know stores its settings in files inside your home directory.

For instance, Skype keep its setting under ~/.Skype/

There are several applications that save its settings under the ~/.config  For example, VLC uses ~/.config/vlc/

I hope that help you to find Kworld's settings so you can better prepare for the upgrade.
Regards.

---

### Post by jerrrys on 2012-03-16
look what i found

[http://tvtime.sourceforge.net/usage.html#configfile](http://tvtime.sourceforge.net/usage.html#configfile)

[http://linux.die.net/man/5/tvtime.xml](http://linux.die.net/man/5/tvtime.xml)

---

### Post by groveman on 2012-03-17
> **jerrrys said:**
> look what i found

[http://tvtime.sourceforge.net/usage.html#configfile](http://tvtime.sourceforge.net/usage.html#configfile)

[http://linux.die.net/man/5/tvtime.xml](http://linux.die.net/man/5/tvtime.xml)

> **papibe said:**
> Hi groveman. Welcome to the forums!

I'm not familiar with Kworld, but almost every desktop application that I know stores its settings in files inside your home directory.

For instance, Skype keep its setting under ~/.Skype/

There are several applications that save its settings under the ~/.config  For example, VLC uses ~/.config/vlc/

I hope that help you to find Kworld's settings so you can better prepare for the upgrade.
Regards.



Thank you very much guys.
Any idea how to copy tv card configuration?

---

### Post by jerrrys on 2012-03-17
> **groveman said:**
> Thank you very much guys.
Any idea how to copy tv card configuration?

Open a terminal and enter:

gksudo nautilus

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

Navigate to the following folders:

[I]~/.tvtime/tvtime.xml
/etc/tvtime/tvtime.xml

Then right click on folder and make a copy.  Be sure tvtime is off to insure no corruption happens.

[/I]*post back if I have not been clear on anything*

---

### Post by groveman on 2012-03-18
> **jerrrys said:**
> Open a terminal and enter:

gksudo nautilus

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

Navigate to the following folders:

[I]~/.tvtime/tvtime.xml
/etc/tvtime/tvtime.xml

Then right click on folder and make a copy.  Be sure tvtime is off to insure no corruption happens.

[/I]*post back if I have not been clear on anything*

That would be tvtime configuration, right?
Are there any tv card specific configuration files.

---

### Post by jerrrys on 2012-03-18
I don't have a tv card so cant say for sure.  The link given to you was found by google and I just provided you with further instructions.  You can explore the link below for tv card configure files and post back if needed if you find something you need help with.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=tv++card+configuration+file&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=tv++card+configuration+file&sa=Search&cof=FORID:9)

---

