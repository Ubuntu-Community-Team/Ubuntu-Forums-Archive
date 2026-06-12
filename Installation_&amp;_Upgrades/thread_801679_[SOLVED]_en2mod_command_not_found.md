---
title: "[SOLVED] en2mod: command not found"
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by cjtjamandra on 2008-05-20
i have an apache2 installed, when i run the command:

```
en2mod mod_evasive
```

it generates an error:


```
en2mod: command not found
```


please help thanks..

---

### Post by iaculallad on 2008-05-20
Try this [link]("http://advosys.ca/viewpoints/2006/08/installing-mod_evasive-in-ubuntu/") for the procedure in installing the mod_evasive in your Apache.

---

### Post by cjtjamandra on 2008-05-20
that's the guide iam using but i cant continue on the

en2mod mod_evasive

because it generates an error

---

### Post by iaculallad on 2008-05-20
Post the generated error.

---

### Post by cjtjamandra on 2008-05-20
i mean the command is not executed because:

```
en2mod: command not found
```

---

### Post by wickid on 2008-06-19
I'm having the same problem...I followed the guide but when it comes to running en2mod evasive, I get the same output.  I am not sure where to find en2mod...have you had any luck since posting your thread?

---

### Post by cjtjamandra on 2008-06-26
i have installed en2mod by executing:

```
apt-get install apache2-prefork-dev 
```

and everything was fixed.

---

