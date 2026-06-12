---
title: "Newbie: How to updrade from 7.10 to 8.04.1 with live cd?"
date: 2008-08-07
forum: Installation &amp; Upgrades
---

### Post by silvestros on 2008-08-07
I have Ubuntu 7.10 on my laptop and I want to upgrade to 8.04.1 with the 8.04.1 live cd, without internet connection. Is that possible? Does the cd have to be alternate cd or live cd is ok? 

If upgrading with live cd is not possible, can you tell me how to do it with internet connection?

Thanks for your help!
Ubuntu rocks!:guitar:

---

### Post by Partyboi2 on 2008-08-07
You will need to use the alternate cd to upgrade not the live cd. Or the other method is to 
make sure you are up to date with all the updates for gusty then open a terminal and type
```
 update-manager -d
``` or
Press Alt-F2 and type update-manager -d then press enter. [FONT=monospace]T[/FONT]his should open update manager with the option to upgrade.

[http://www.ubuntugeek.com/upgrade-ubuntu-710-gutsy-gibbon-to-ubuntu-804-lts-hardy-heron.html](http://www.ubuntugeek.com/upgrade-ubuntu-710-gutsy-gibbon-to-ubuntu-804-lts-hardy-heron.html)

---

### Post by silvestros on 2008-08-07
Thanks a lot for the reply, but how can I do the upgrade?
Could you tell me how to do it step by step if possible?

---

### Post by silvestros on 2008-08-07
I mean which commands should I use with the alternate cd if my Gutsy is not fully updated?
thanks again!

---

### Post by Partyboi2 on 2008-08-07
open a terminal (applications>accessories>terminal) then type
```
sudo apt-get update
sudo apt-get upgrade
```this will update your system if it is not already. Also make sure all 3rd party repo's are disabled in Software Sources before upgrading.

---

### Post by silvestros on 2008-08-07
ok. thanks

---

