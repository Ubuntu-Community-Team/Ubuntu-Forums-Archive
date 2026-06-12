---
title: "no support for en.CA-utf8 -- is it serious? or just annoying?"
date: 2017-01-11
forum: MINT
---

### Post by ineuw on 2017-01-11
I am using Linux Mint Cinnamon 18, Sara and with each kernel update I get the message "no support for en.CA-utf8" I know that it's a lowercase/uppercase issue. I checked the locale with ```
sudo dpkg-reconfigure locales
``` which doesn't even list "EN.CA-UTF8", although being in Canada it is correct. Also used ```
 sudo locale-gen --purge --no-archive 
``` which indicates it does exist and is is properly upper case, The warning repeats itself on the next kernel update, so I think that the problem is in the kernel update file and not my installation. How serious is this?

---

### Post by Irihapeti on 2017-01-11
*Thread moved to **MINT**.*

---

### Post by ineuw on 2017-01-11
Thanks for your help, but I am not sure what you meant by "Mint" since I am new to Mint. Did you mean the Linux Mint forums, or something else? Isn't Mint also based on Ubuntu? I was wondering because it is missing from the flavours' tags.
From now on, do I post my questions to the Mint Forum? Please advise.

P.S: Must change my signature, since I am a renegade and no longer using xubuntu:-)

---

### Post by Irihapeti on 2017-01-11
The main Official Flavours Support (and Specialised Support) are, as the name suggests, for official Ubuntu variants. Threads relating to other OSes, regardless of what they are based on, get moved to the Other OS Support and Projects area.

It's entirely over to you whether you post here or over at the Linux Mint forums. But if you post here and your question is about a Mint issue, you need to post in this area.

---

### Post by ineuw on 2017-01-11
Much thanks for the clarification.

---

### Post by jeremy31 on 2017-01-11
See [this post](https://forums.linuxmint.com/viewtopic.php?f=47&t=231518&p=1227663&hilit=support+utf8#p1227666) for a possible solution

---

### Post by ineuw on 2017-01-12
Thanks jeremy31. This solved my problem. The latest kernel update no error was reported.

---

