---
title: "mkdtemp: private socket dir: Permission denied"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by yage on 2006-10-29
I don't know how this happend but after using edgy a while and rebooting i came to the usual gdm screen. Trying to log in i got a error message. /etc/gdm/Xsession: Beginning session setup... mkdtemp: private socket dir: Permission denied. Hammerd google and the ubuntu forums all i found was changing the permissions on /tmp to 777 and then try again. It worked, but should the permission be set to 777 ?

---

### Post by davidmoffatt on 2007-01-24
Just today (1/24/07) I upgraded edgy and got this same problem.  A quick sudo chmod a+w /tmp fixed it.  Thank good for google.  This would have been a real pain to track down.  Not something you want to do when the boss is breathing down you neck to get something done.

---

### Post by ntom-taylor on 2007-10-12
Thank you so much, the prospect of being stuck out my ubuntu box all day was looking like the future, but now thanks to your posts the issue is resolved.

Much appreciation. :-({|=

---

### Post by Wavelett on 2007-10-17
This also happened to me today, and the chmod fixed it.

This error has been around over a year. Does any one know what causes it? I'm sure I didn't tough the permissions on it.

Wavelett

---

### Post by cobold on 2007-10-30
Exactly the same problem, I was installing something with sudo, but near that I did a lot of other thing too, my notebook freezed, couldn't restart, luck that I was near my other pc and could oslve the problem in 5 minutes. Hovere it was strange ...

---

### Post by Nutone718 on 2008-03-11
This is weird. I was installing cpanel on this machine and after I rebooted it gave me this error. I have the same question that Yage has, should 777 be the permissions for /tmp ?

Thanks in advance.

---

### Post by johnnycakes79 on 2008-06-13
Thanks David, dunno what caused this but the chmod solution saved my *** this weekend.

J.

---

### Post by ram4nd on 2008-06-18
Ty, worked for me. I got this problem by trying to get MEDUSA work.

---

