---
title: "System monitoring via Web browser"
date: 2020-07-23
forum: Installation &amp; Upgrades
---

### Post by optimusprime11 on 2020-07-23
Hi,

I'm looking for a relatively light weight system monitoring program so I view the current stats such as:

CPU
RAM
Storage space 
etc, etc 

This is purely for my own benefit on my home server as i'm interested to know what's happening.

Ideally, I would love to have an iPad/iPhone app but there isn't many available that I could find (let me know if you know otherwise). Therefore a web browser based GUI is fine with me.

on my short list in no particular order I have:
- Zenoss
- Zabbix
- Cockpit.

I would appreciate your input with your experiences. Typically the most used one will probably be the best for me. Problem is I don't know what that is!

I all most forgot to add, i'm looking for a free program. Like i said, this is a home use machine. I would not have the requirement for a subscription based monitoring tool.

Thank you

---

### Post by TheFu on 2020-07-23
I've used munin and sysusage. They create web pages for performance stats.  When I used sysusage, I had to rsync the stats for a centralized view.  Munin has an collection agent and server to generate the graphs. I liked this because SysUsage was impacting the CPU on each machine. By offloading that work to a different system, the data was clearer.

Be warned, they still use the "master" terminology, so sensitive people may want to skip the project.

---

### Post by optimusprime11 on 2020-07-24
thanks for the suggestions! after looking into this further i find Zabbix and Zenoss very powerful but they depend on Apache and SQL etc. all of the additional overhead just seems too much for my needs. Cockpit looks like it can run on it's own and I think I read somewhere that Htop can be ran on a web interface.

---

### Post by optimusprime11 on 2020-07-24
bit of a curve ball but I've gone with Glances. [https://nicolargo.github.io/glances/#](https://nicolargo.github.io/glances/#)

easy to setup:

```
sudo apt-get install glances
```

open UFW on port 61208

run the following to start the web interface:

```
glances -w
``` 

navigate to the server IP: Port

I'm now working on the auto run script from boot

---

### Post by TheFu on 2020-07-24
Can glances show what has been happening the last 3, 6, 12 months?  When you server gets hacked, seeing when the use pattern changed is a huge help.  Having a list of running processes available from 17 days ago can be a big help.

---

### Post by mIk3_08 on 2020-07-24
Try brainypdm, creates a custom graph using various important performance data from Nagios.

---

### Post by ActionParsnip on 2020-07-24
We use a combination of Zabbix and OpsView. Works well.

---

