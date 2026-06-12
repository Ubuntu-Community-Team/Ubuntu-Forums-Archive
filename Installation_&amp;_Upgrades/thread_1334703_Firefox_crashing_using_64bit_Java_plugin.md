---
title: "Firefox crashing using 64bit Java plugin"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by Bobhuber on 2009-11-22
Firefox Crashing using 64 bit Java Plugin
64 Bit Java Install in Karmic 9.10 64 bit using Firefox 3.5.5 - AMD Athalon
I hope this post saves someone else all the hassle.

After pulling my hair out for 3 days I was finaly able to get the newest Java JRE (version 17) working in Firefox 3.5.5. Java would work when Firefox was loaded from the terminal but immediately crash when accesing a java site if loaded from the desktop.
Follow the instructions found at [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)
for the basic install which will allow you to access firefox within the terminal.Then create a second link to be able to use Firefox from the desktop                                                  [SIZE=3][COLOR=#000000][COLOR=#0000ff]ln -s /opt/java/64/jre1.6.0_17/lib/amd64/libnpjp2.so /usr/lib64/firefox-addons/plugins 

[/COLOR][/COLOR][/SIZE]

---

