---
title: "Medibuntu broken in Update Manager?"
date: 2010-04-20
forum: Installation &amp; Upgrades
---

### Post by grikdog on 2010-04-20
9.04
Dell Inspiron 1525

Update Manager fails to retrieve database info for Medibuntu.  Is this a phase error with Adobe swf or reader?  What should I do?

TY

---

### Post by jaco223 on 2010-04-20
> **grikdog said:**
> 9.04
Dell Inspiron 1525

Update Manager fails to retrieve database info for Medibuntu.  Is this a phase error with Adobe swf or reader?  What should I do?

TY


I know there is a problem with the website at the moment. The site appears to be down.
Maybe this is why you can't update. 


Jaco

---

### Post by Morbius1 on 2010-04-20
[https://bugs.launchpad.net/medibuntu/+bug/565810](https://bugs.launchpad.net/medibuntu/+bug/565810)

Read the bug report for a list of mirrors until the main medibuntu site is restored.

---

### Post by grikdog on 2010-04-20
The mirrors refer to lucid, but I have jaunty.  If the main site is still down on Wednesday (tomorrow), is it wise to put a lucid mirror in my jaunty sources?

Thanks the confirmation about medibuntu is (or was) actually down.

---

### Post by wojox on 2010-04-20
> **grikdog said:**
> The mirrors refer to lucid, but I have jaunty.  If the main site is still down on Wednesday (tomorrow), is it wise to put a lucid mirror in my jaunty sources?

Thanks the confirmation about medibuntu is (or was) actually down.

It's down for everybody, regardless of what version your using.

---

### Post by Morbius1 on 2010-04-20
jeesh,

Change
[http://packages.medibuntu.org/](http://packages.medibuntu.org/)

To 
         [http://mirrors.ucr.ac.cr/medibuntu/](http://mirrors.ucr.ac.cr/medibuntu/)

Keep all the other parameters that identify your version and free / non free stuff the same.

---

### Post by polly1 on 2010-04-21
Morius1,

Thanks.

It solved the problem for me.

Regards

polly1

:guitar:

---

### Post by Morbius1 on 2010-04-21
Actually, I may have found an explanation of why this has gone one for so long. 
> **Morbius1 said:**
> I read in another forum somewhere that the problem is not that medibuntu.org is down - it's a DNS problem. "packages.medibuntu.org" can't be converted to an ip address. This might explain why it's been going on for so many days now. Medibuntu can't fix it because it's not their problem.

Anyway, to fix it add the following line to your **/etc/hosts** file:

```
88.191.101.8 packages.medibuntu.org
```That's the ip address of the repository so it doesn't have to use DNS to convert it.

I changed it to use the hosts file workaround and it works for me.

---

### Post by bance on 2010-04-21
Thanks Morbius 1,

am just about to try your solution.........

---

### Post by goldshirt9 on 2010-04-21
could you be a little more precise on where what i change. please :)

---

### Post by Morbius1 on 2010-04-21
Open **Terminal**
Type **gksu gedit /etc/hosts**

Add the following line to the end of the file:
```
88.191.101.8 packages.medibuntu.org
```
Save the file and then do an update as usual.

---

