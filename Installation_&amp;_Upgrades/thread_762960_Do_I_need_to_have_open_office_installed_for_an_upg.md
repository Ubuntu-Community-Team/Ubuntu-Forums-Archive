---
title: "Do I need to have open office installed for an upgrade?"
date: 2008-04-22
forum: Installation &amp; Upgrades
---

### Post by dsiembab on 2008-04-22
I was wondering if I need to have open office installed on my desktop for an upgrade install. I barely use open office and usually delete it after an Install from cd. Right now I am running a partial install because being an impatient idiot I didn't wait for k3b to verify the alternative cd before upgrading. Dohh!! Do i have to boot with an older linux kernel for this to work every time I try to upgrade it asks for the gutsy cd and all I have is the alternative cd should I just make a gutsy cd? I think I am answering my own questions. Never mind it started installing the packages again. Anywho, how's the weather?

---

### Post by martrn on 2008-04-22
You can remove opejn office, and it will not upgrade open office and save a little bandwidth.

To remove the cd from your soucrces list do the following :-
```
sudo nano /etc/apt/sources.list
 // or 
sudo kate /etc/apt/sources.list
```

search for a line looing like this :-

> deb cdrom:[Ubuntu-Server 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted


and delete it.
No more will apt or other installers ask for your installation cd.

---

### Post by Wazoot on 2008-04-22
nah, for an upgrade you dont have to have OpenOffice installed. It's just there if you need it

---

