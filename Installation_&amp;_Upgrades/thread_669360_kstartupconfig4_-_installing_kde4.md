---
title: "kstartupconfig4 - installing kde4"
date: 2008-01-16
forum: Installation &amp; Upgrades
---

### Post by Jense on 2008-01-16
Hi,
I tried to install kde4. Now I get this errormsg. 'could not start kstartupconfig4. Check your installation'.

I googled and tried the 

'chown -R username:users /home/username'

I also tried to set a symlinc to 

'ln -s /usr/lib/kde4/bin/kstartupconfig4 /usr/bin/kstartupconfig4' 

to no succes yet.
I would really like to check out kde4 but I would be nearly just as happy having my old kde3 back. Does anyone have a solution or maybe I did something wrong with the commands above. 
Thx for your help

---

### Post by br4ndo on 2008-01-31
It would have been sufficient with:
chown -R username /home/username/.kde4
worked for me
Overkill to change ownership of the whole home folder.
Might explain your problems to get KDE3 back.

---

