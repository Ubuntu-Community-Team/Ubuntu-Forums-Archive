---
title: "Partial upgrade - Both 12.04 &amp; 12.10?"
date: 2012-07-23
forum: Installation &amp; Upgrades
---

### Post by Albury_Boy on 2012-07-23
Hi all,

I seem to have had a strange partial upgrade. When logging into my laptop, the login screen shows 12.10. The 'About this computer' shows 12.04 LTS. 

When running sudo apt-get update I see that it is using 'quantal' repositories mostly, with a couple of 'precise' ones thrown in. A heap of them are now broken.  

My linux kernel is 3.5.0-5-generic

I'd recently upgraded my distro from 11.10 to 12.04 (on purpose). After the usual problems with X server settings, everything seemed to have settled down. 

A couple of reboots later, I ran sudo apt-get update && sudo apt-get upgrade, went to get a coffee, and when I got back, I found this Frankenstein machine.

<<- HE GETS TO THE QUESTION HERE ->> 

So... I was wondering if I could force the system into totally 'believing' that it is 12.04??

My repositories are all precise or lower. There are no quantal sources in the list.

Any suggestions?

---

### Post by sectio aurea on 2012-09-23
This is still a relevant question, as the Quantal beta was just released. 

One method, which worked for me and my extremely crufty upgrade partition when I experienced the OP's problem, is to try forcing aptitude to fix the problem:

[LIST=1]
[*]Boot to safe mode, then run:

[*]```
sudo aptitude -f

```
[*]In aptitude, type "u" to update, then "g" to install updates. 

[*]Reboot when it won't take any more updates. 

[*]Repeat steps 1-4 until you can get to your graphical login screen on a 3.5.0 kernel.
[/LIST]

---

