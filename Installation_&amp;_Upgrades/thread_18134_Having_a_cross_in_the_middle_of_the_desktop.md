---
title: "Having a cross in the middle of the desktop"
date: 2005-03-04
forum: Installation &amp; Upgrades
---

### Post by popeye on 2005-03-04
Hello,

Just installed ubuntu freshly as a dual boot. Everything is starting well only i keep looking at a quit big black cross in the middle of the screen. I think it has something to do with the xfree driver but don't know how to solve the problem.

Thanks  for the help.

---

### Post by Gary Powers on 2005-03-04
Popeye, add the following line to your /etc/X11/XF86config-r in device section ...

Code

   Option                "SWcursor"             "true"

Reboot or relogin and you should be OK.

Gary

---

### Post by Gary Powers on 2005-03-04
Whoops, don't add the word "code"

---

### Post by HJB on 2005-03-05
Hi there. Same thing happend to me when I installed **Hoary**. Grey screen with only a cross. I then reinstalled this time using Warty and upgraded to **Hoary**. Had a few probleblems right after the install with **message bus** but after some apt-get upgrade's I was fine and everything is working well now.

In my N00by opinion it was all to do with some packages not updated... BUT have a look here: [Support](http://www.ubuntulinux.org/support/documentation/faq/hwcursor) 


Bye
H

---

### Post by popeye on 2005-03-11
[QUOTE=Gary Powers]Popeye, add the following line to your /etc/X11/XF86config-r in device section ...

Code

   Option                "SWcursor"             "true"

Reboot or relogin and you should be OK.

Gary[/QUOTE]

Hi, thanks it works, however my XF86config is named: /etc/X11/XF86config-4

I could not find how to edit the file in gedit, because it opens readonly. 

In a rootterminal with the command root@....:/# vi /etc/X11/XF86config-4  did the trick for me. 

Anyway. thanks for the quick response. Unfortunately i'm not so quick.

---

