---
title: "Please display output apt-get instal..."
date: 2006-12-14
forum: Installation &amp; Upgrades
---

### Post by scrooch on 2006-12-14
On a /clean/ edgy install, could you guys please tell me what the content of file.txt is when you do a 

apt-get -y --print-uris install vlc |grep http |awk '{print $1}'|tr -d "'" > file.txt
(tx to Yota for that line)

I would like to know that because this file enables me to wget all the dependencies of vlc which I need.

Thanks!

---

### Post by taurus on 2006-12-14
You mean

```
cat file.txt
```

---

### Post by pandu.rs on 2006-12-14
i dont use edgy, so i cannot tell the output of that command

But why dont you use the edgy live cd and find it out yourself? (i have done this for dapper)

---

### Post by scrooch on 2006-12-14
I can´t get online with the livecd at work, at home the computer is only offline so I can´t add reps like multiverse to see what the deps for vlc are...

It´s really important to get this information, please.

---

