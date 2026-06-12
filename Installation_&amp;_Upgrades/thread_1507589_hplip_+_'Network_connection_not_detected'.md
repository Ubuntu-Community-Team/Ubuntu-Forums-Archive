---
title: "hplip + 'Network connection not detected'"
date: 2010-06-11
forum: Installation &amp; Upgrades
---

### Post by RH9R on 2010-06-11
'tried 5 or 6 solutions on the different threads on hplip - none seem to affect the download of the plugin - always 'no network connection detected'.
 
'Running Lucid on a Dell Optiplex 755 w/ an HP1020. The printer appears to be recognized - show up on admin/printer. Anyone else having this heartburn?

---

### Post by RH9R on 2010-06-15
Is everyone else's HP's just connecting and loading the drivers?

---

### Post by RH9R on 2010-07-02
Whine alert: I have to fire up an XP box to print. Lucid resolved the dual monitor driver issue, but at the expense of printing.

---

### Post by hopllit on 2010-08-04
I have the same problem. Ubuntu 10.04, HP LaserJet 1018, HPLip 3.10.2 returns this error: Network connection not detected. Any suggestions? Thank you in advance.

---

### Post by ma2k1 on 2010-09-25
> **hopllit said:**
> I have the same problem. Ubuntu 10.04, HP LaserJet 1018, HPLip 3.10.2 returns this error: Network connection not detected. Any suggestions? Thank you in advance.

See also this launchpad bug [https://bugs.launchpad.net/hplip/+bug/573971](https://bugs.launchpad.net/hplip/+bug/573971)

I have an hp 1005, so I've launched hp-plugin for installing firmware (as reported here [https://bugs.launchpad.net/ubuntu/+source/foo2zjs/+bug/96454/comments/67](https://bugs.launchpad.net/ubuntu/+source/foo2zjs/+bug/96454/comments/67)) but "network connection not detected" error was raised :(

So, I' ve relaunched with this two options:
sudo hp-plugin -g -i
-g debug mode
-i interactive

Hp-plugin try to wget [www.google.com](www.google.com) but probably because my network was slowly it fail and give me the error above.
If I launch wget from terminal, without the option --timeout=10, [www.google.com](www.google.com) was resolved so, I've just added to my /etc/hosts
ip_google [www.google.com](www.google.com) *

Next, I relaunched sudo hp-plugin -g -i and this time [www.google.com](www.google.com) was resolved ;) and hp-plugin continue to the next steps (download some configuration/driver/firmware from various site) and in five minutes my printer have a new firmware :)

Have fun, bye
:popcorn:

* to retrieve ip from hostname, just digit on terminal host [www.google.com](www.google.com)

---

### Post by hopllit on 2010-10-16
> **ma2k1 said:**
> See also this launchpad bug [https://bugs.launchpad.net/hplip/+bug/573971](https://bugs.launchpad.net/hplip/+bug/573971)

I have an hp 1005, so I've launched hp-plugin for installing firmware (as reported here [https://bugs.launchpad.net/ubuntu/+source/foo2zjs/+bug/96454/comments/67](https://bugs.launchpad.net/ubuntu/+source/foo2zjs/+bug/96454/comments/67)) but "network connection not detected" error was raised :(

So, I' ve relaunched with this two options:
sudo hp-plugin -g -i
-g debug mode
-i interactive

Hp-plugin try to wget [www.google.com](www.google.com) but probably because my network was slowly it fail and give me the error above.
If I launch wget from terminal, without the option --timeout=10, [www.google.com](www.google.com) was resolved so, I've just added to my /etc/hosts
ip_google [www.google.com](www.google.com) *

Next, I relaunched sudo hp-plugin -g -i and this time [www.google.com](www.google.com) was resolved ;) and hp-plugin continue to the next steps (download some configuration/driver/firmware from various site) and in five minutes my printer have a new firmware :)

Have fun, bye
:popcorn:

* to retrieve ip from hostname, just digit on terminal host [www.google.com](www.google.com)

Thank you so much, it worked!! :)

---

### Post by jobutane on 2010-11-23
Hello (sorry for my english, I'm French)
I have the same problem with HPLIP, but I don't understand your solution, because I'm a newbie in terminal use.
pleas can you explain me step by step how to edit  /etc/hosts
thanks a lot

---

### Post by jobutane on 2010-11-26
I try to edit etc/hosts like this: 
```
79.118.175.79     www.google.com
```and it doesn't work.
the ip it's find but it's make new try of connection every 10 s.

---

### Post by ma2k1 on 2010-11-29
> **jobutane said:**
> I try to edit etc/hosts like this: 
```
79.118.175.79     www.google.com
```and it doesn't work.
the ip it's find but it's make new try of connection every 10 s.

Have you digitized " sudo hp-plugin -g -i " in the terminal?
What version of Ubuntu are you using?

Pleas report also the output of hp-plugin for better understanding the problem.

Bye

---

### Post by jobutane on 2010-11-29
yes I digitized " sudo hp-plugin -g -i " in terminal
my ubuntu is the 10-10
the probleme is this  --timeout=10 option, may be we can delet it somwhere?

yes it's work with your solution, thanks

---

### Post by Sedrikov on 2011-01-23
I had same problem as you (I am also french); to solve your problem try to add/replace "ip_google [www.google](www.google).**com**" by "ip_google [www.google](www.google).**fr**"; it suceeded in downloading the drivers and then my printer woke up and printed successfully a test page when I asked it.

---

### Post by jobutane on 2011-01-24
> try to add/replace "ip_google [www.google]("http://www.google/").**com**" by "ip_google [www.google]("http://www.google/").**fr**"
i did something like this and it works
thanks

---

