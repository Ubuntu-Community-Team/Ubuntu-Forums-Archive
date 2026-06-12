---
title: "Ati Radeon 7000 and Genius Netscroll PS2"
date: 2005-02-21
forum: Installation &amp; Upgrades
---

### Post by galder on 2005-02-21
Hello everybody,

My problem started when I tried to change of videocard. I changed the XFConfig86-4 file and now, with that configuration I have not achieve to get a proper configuration.

My screen has a very low resolution, and I can change it in the configuration file but it does not work. In the Gnome I can't get any other choice in the Monitor configuration screen. 

According to the mouse problem,  it works well the pointer, but when I use the left button, it goes really bad.

Can anybody post his/her XF86Config-4 file in order to copy it to my Ubuntu?

Thank you very much,

Galder

---

### Post by subbia on 2005-03-05
[QUOTE=galder]Hello everybody,

My problem started when I tried to change of videocard. I changed the XFConfig86-4 file and now, with that configuration I have not achieve to get a proper configuration.

My screen has a very low resolution, and I can change it in the configuration file but it does not work. In the Gnome I can't get any other choice in the Monitor configuration screen. 

According to the mouse problem,  it works well the pointer, but when I use the left button, it goes really bad.

Can anybody post his/her XF86Config-4 file in order to copy it to my Ubuntu?

Thank you very much,

Galder[/QUOTE]


If you use Xfree86 as X server you can do xf86config from bash.
If you use X.org you can do xorgconfig. 

This commands are wizards that helps you to configure XF86Config-4 file, and are very simply to use. Give them a try ;)

---

