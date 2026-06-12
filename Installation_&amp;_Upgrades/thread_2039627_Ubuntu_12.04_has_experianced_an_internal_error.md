---
title: "Ubuntu 12.04 has experianced an internal error"
date: 2012-08-09
forum: Installation &amp; Upgrades
---

### Post by Graham C Williams on 2012-08-09
Good morning.

System: 64bit Ubuntu 12.04.

The warning: 'System Program problem detected'
Eventually followed by the attached screen shots.

What does it all mean?
Should I do anything?

Graham.

---

### Post by 2F4U on 2012-08-09
Do you experience any problems because of this error? I have one machine which also gets an error every time after I login. It says that my GPU hung. The first time I was worried, but since I found no negative effects due to this error, I am now ignoring it.

---

### Post by unevenflow on 2012-08-09
Hey if you don't have any problems as i and i have been pestered by this you could turn off this by typing in terminal
**sudo gedit /etc/default/apport**
a text editor will appear and type this:
enabled=0

My understanding is that devs didn't turn this off after beta.

---

### Post by Graham C Williams on 2012-08-11
Hi all. Apologies for late reply (family business). There does not appear to be any problem as a result of this. I'll try your suggestion and let you know.

Thanks
Graham.

---

