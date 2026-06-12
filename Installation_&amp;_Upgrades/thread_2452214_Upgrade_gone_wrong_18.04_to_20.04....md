---
title: "Upgrade gone wrong 18.04 to 20.04..."
date: 2020-10-18
forum: Installation &amp; Upgrades
---

### Post by abillybob94 on 2020-10-18
[COLOR=#333333]Hey All[/COLOR]

[COLOR=#333333]Hopefully someone can help, I have a home server running Ubuntu 18.04 Desktop which has my plex server installed on it.[/COLOR]

[COLOR=#333333]I tried to update it to 20.04 as I was sick of the prompt and since then I've been having issues with it. At first it restarted and put me back to the login page, so when I logged in it would just freeze and wouldn't go to my desktop.[/COLOR]

[COLOR=#333333]I then entered the terminal and used commands to reinstall desktop and Unity I think, found it on a forum and since then it's doing the following.[/COLOR]

[https://youtu.be/d6MrpepAsmU](https://youtu.be/d6MrpepAsmU)

[COLOR=#333333]It's strange because when it gets to the end screen I can access my plex library so it is loading things I just can't do anything, type anything or see the gui it's just stuck at a black screen with a white text marker at the top.[/COLOR]

[COLOR=#333333]I'd rather not have to reinstall ubuntu from scratch it took me ages to configure it how I wanted and as I'm just a novice it'll take me ages again![/COLOR]

[COLOR=#333333]Any help would be most appreciated! [/COLOR][IMG]https://awscdn.cdngeek.com/images/smilies/smile.png[/IMG]

---

### Post by ActionParsnip on 2020-10-19
Is the Plex server just a plex server or does it also play the media on its own system using the Plex UI?

---

### Post by abillybob94 on 2020-10-19
> **ActionParsnip said:**
> Is the Plex server just a plex server or does it also play the media on its own system using the Plex UI?

It's just a Plex server. I can't get to the UI of it anymore but when accessing Plex from my phone it's working fine.

---

### Post by grahammechanical on 2020-10-19
May I ask a question? During the upgrade process did it ask you to confirm the removal of obsolete packages. That is what I got and as I had Unity installed and was using LightDM as the display manager that controls the log in screen I also ended up with a black screen on reboot.

For myself I reinstalled LighDM and was asked to configure it. I also had GDM (Gnome Display Manager) installed so I choose to load with GDM and not LightDM and I got a desktop top that way.

Regards.

---

### Post by abillybob94 on 2020-10-19
> **grahammechanical said:**
> May I ask a question? During the upgrade process did it ask you to confirm the removal of obsolete packages. That is what I got and as I had Unity installed and was using LightDM as the display manager that controls the log in screen I also ended up with a black screen on reboot.

For myself I reinstalled LighDM and was asked to configure it. I also had GDM (Gnome Display Manager) installed so I choose to load with GDM and not LightDM and I got a desktop top that way.

Regards.

Yes it did, it removed a bunch of obsolete packages and then continued.

How would I go about reinstalling lightdm and getting it to boot using gdm? I can't access the terminal via ctrl + alt + f2.

---

### Post by CelticWarrior on 2020-10-19
Try CTRL+ALT+F3

---

