---
title: "Help upgrading to Edgy"
date: 2006-12-25
forum: Installation &amp; Upgrades
---

### Post by qtrey on 2006-12-25
I am new to Ubuntu, and I can't upgrade from Dapper to Edgy by the update manager. It says
```
Failed to fetch http://ubuntu.compiz.net/dists/dapper/Release.gpg Temporary failure resolving 'ubuntu.compiz.net'

```
what does it mean, how do I solve that?

---

### Post by Spin Doctor on 2006-12-25
Did you upgrade by using:
```

gksu "update-manager -c" 
```

---

### Post by qtrey on 2006-12-25
Yes, also tried ```
sudo update-manager -c
``` with the same result.

---

### Post by Spin Doctor on 2006-12-25
I am not 100% sure what is causing it...but I am guessing something could be wrong with your /etc/apt/sources.list

Go into software sources, and see if you have any odd entries in there. If so uncheck or delete these entries and try again. 

You can also open sources.list by gedit and see if you have any formatting errors. If you see that error URL you have on your previous post, delete it from your sources.list.

Before you do this, backup your sources.list just incase it does not solve it...

---

### Post by qtrey on 2006-12-25
Thank you very much :D 
that solved it.

---

### Post by Spin Doctor on 2006-12-25
Your welcome! Glad it worked as I suspected the sources.list to be part of the problem =) Have a great day!

Hope you have broadband...or it will be a loooooooooooooong download =)

---

### Post by qtrey on 2006-12-25
Already downed it... gotta love broadband :D

---

### Post by d7thstring on 2007-01-05
Thanks , this really helped me.

---

