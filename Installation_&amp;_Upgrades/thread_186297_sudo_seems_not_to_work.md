---
title: "sudo seems not to work"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by denisl on 2006-06-01
I am running Breezy Badger (amd64 generic) and when I try the posted recipes to update the update-manager (0.37.1) to 0.42 so that I can do the update,](*,)  the sudo command replies that permission denied after I enter my password as per instructions in the manual. I have tried all of the sudo commands with apt-get they also fail - I am now at a loss.

---

### Post by pellgarlic on 2006-06-05
does "sudo su" work? type that, then it will ask for your password. enter it, then the prompt should change from something like this:

username@ubuntu:/$ 

to something like this:

root@ubuntu:/#

and switches to super-user, so you don;t need to keep issuing "sudo" prefixes to commands. if this way works, it might shed some light on why the other way doesn't. and at the very least, it might help you get those updates going...

---

### Post by taurus on 2006-06-05
Or what is the output of this command from a terminal?
```

id

```

---

