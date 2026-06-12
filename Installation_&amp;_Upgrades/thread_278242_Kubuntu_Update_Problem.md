---
title: "Kubuntu Update Problem"
date: 2006-10-16
forum: Installation &amp; Upgrades
---

### Post by keyo on 2006-10-16
](*,) I have not been able to update the repositories after disabling ipv6(no luck with it on either) and trying different mirrors in sources.list. I've had no success with either Terminal or Adept on kubuntu 6.06(from shipit cd). Konqueror and kopete connect to the internet just fine.
If i can sort this out nearly everything will be fixed, please help.

Thanks, Ben ;)

---

### Post by keyo on 2006-10-16
Guess this should be in another forum, sorry if any admin or mods would be kind enough to move it that would be great.

I have tried
[http://ubuntuforums.org/showthread.php?t=185758](http://ubuntuforums.org/showthread.php?t=185758)
[http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2)

---

### Post by NeoLithium on 2006-10-16
I'll try to give you a hand. Can you please pose the printout of this command: ```
cat /etc/apt/sources.list
```

Hopefully we'll be able to get you up and running :)

---

### Post by keyo on 2006-10-17
So I found out that the problem seems to be DNS based, someone suggested i change the dns server to my ISPs server instead of my router, that failed. The updates only work after I have been to the address before during the same session. I have managed to install quite a few things including automatix, which is useless at the moment unless I can resolve this dns problem. 

Cheers :D

---

### Post by keyo on 2006-10-17
Ok after looking again it seems the dns settings have somehow been reset back to 10.1.1.1 (Dlink router). Is this a common problem?

---

