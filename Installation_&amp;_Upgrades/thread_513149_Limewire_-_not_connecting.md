---
title: "Limewire - not connecting"
date: 2007-07-30
forum: Installation &amp; Upgrades
---

### Post by zaffod on 2007-07-30
Hi, 
Installed limewire on fiesty. Install went fine. Limewire launches with no problems. No errors in konsole... I just don't seem to get connected to any hosts. Not a java issue....

This is not firewall related as other machines on my LAN can connect fine. I tried gtk-gnutella on my feisty machine but the same issue exists. 

I'm guessing there is something with the feisty install that is causing this problem, but I am not aware of any firewall software running. 

Can anyone assist me with troubleshooting this issue?

I'm running the 64bit version. Recent download.

---

### Post by MikeAlmere on 2007-07-30
It probably is your firewall, because port forwarding is usually to a specific IP adress. This would explain why it works on one machine, but not on the other. I had the same problem, adding an extra IP adress in the list of my firewall for port forwarding did the trick.

---

### Post by zaffod on 2007-07-30
Thanks for your answer Mike, but the issue is certainly not (external) firewall related. My firewall rules are based on the whole LAN, not host specific. 

I turned on logging on my firewall and I'm not seeing any limewire data hit it, so I suspecting something in the feisty install.

---

### Post by zaffod on 2007-07-30
Also, with regards to port forwarding....
I set it up on the firewall to forward 6346 to the feisty machine.
Call me paranoid, but I don't usually do that. I don't have such a rule set up for the other machine (XP) that does successfully connect.

---

### Post by zaffod on 2007-08-06
It's like limewire does not even try to connect. The Connections windows remains blank.

---

### Post by zaffod on 2007-08-15
This is still any issue - any ideas?

---

### Post by Steveway on 2007-08-15
You should use Frostwire.
It's the same as Frostwire but doesn't limit your connection or shows ads and it is free.

---

### Post by cbiere on 2007-08-15
What version of gtk-gnutella did you try? There should be no such issues at least with the latest 0.96.4 unless your firewall (or something else) prevents outgoing connections to arbitrary ports. If it cannot connect on itself, you can always manually to connect some other peers. Just pick a couple from this list:

[http://tsubasa.ghostwhitecrab.de/?client=nobody&hostfile=1](http://tsubasa.ghostwhitecrab.de/?client=nobody&hostfile=1)

---

### Post by fmonjaraz on 2007-08-25
Im using frostwire, I went to the connections tab. I clicked the "add" button and put one of the ip's from the latter list.  It should work after one does this.

---

### Post by fmonjaraz on 2008-04-11
For frostwire and limewire you need to get a new gnutella.net file and place in your home/.limewire or .frostwire file...which is hidden.. and it should connect.  I believe this was a bug which has been fixed by now.

---

