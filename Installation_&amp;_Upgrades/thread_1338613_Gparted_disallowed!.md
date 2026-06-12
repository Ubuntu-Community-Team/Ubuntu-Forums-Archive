---
title: "Gparted disallowed!"
date: 2009-11-26
forum: Installation &amp; Upgrades
---

### Post by Hopalong on 2009-11-26
Gparted in 9.10. I have an operational 9.10 going well so far. However it was installed from a download (copied to a CD) and got written into the whole of the largest remaining partition of the hard drive. (My standard system 8.10 is still there.) I would like to try and tidy up these huge partitions with Gparted, which I have installed from the repository. (The hard disk is 320 GB.) However starting Gparted give a note that "The underlying authorisation mechanism (sudo) does not allow you to run this program. Contact the system administrator." That's me! So what do I have to do to allow myself to use my own system?

---

### Post by mhgsys on 2009-11-26
have you tried opening a terminal and typing 
```

gksudo gparted

```
?

---

### Post by pastalavista on 2009-11-26
You can't make changes to a mounted partition. Right-click the drive and unmount it before you can change anything. No way will you be able to unmount the / directory while it is running. Best bet is to use Gparted from the live CD.

---

### Post by mhgsys on 2009-11-26
@ pastalavista 
well,. Please correct me if i'm wrong>
 
but hopalong could also resize / erase whatever partition which isn't his os that time right?

meaning; he could also use gparted in 8.10 f.e to resize his 9.10 and visa versa using sudo unmount or gkduso gparted to unmount the non-booted partition.




edit; lol,. .. the usernames in this topic so far.

---

### Post by pastalavista on 2009-11-26
> **mhgsys said:**
> have you tried opening a terminal and typing 
```

gksudo gparted

```
?

> **mhgsys said:**
> well,. Please correct me if i'm wrong>
 
but hopalong could also resize / erase whatever the partition which isn't his os that time right?

meaning; he could also use gparted in 8.10 f.e to resize his 9.10 and visa versa using sudo unmount or gkduso gparted to unmount.

yes, but if he doesn't have any free space, he'll have to shrink one to expand the other... resizing both of them

---

### Post by mhgsys on 2009-11-26
Ah, did not think of that. 

I stand corrected, using live disk would indeed be the best

---

### Post by Hopalong on 2009-11-27
For the record gksudo gparted gets the same message. I'm still trying.  (My mother used to say "you're always very trying!")

---

### Post by coffeecat on 2009-11-27
It sounds as though you've lost administrative privileges in 9.10 - there's something wrong with your sudoers file. What happens when you try to open another app for which you need root privileges? Synaptic?

Anyway, as others have said you'll be better of using the live CD - you won't have authorisation problems with that - but you'll still be left with an issue in 9.10.

---

### Post by Hopalong on 2009-12-02
The same thing. My user name is "not in the sudoers file". Since I am the only user of this machine (and it doesn't stay connected to the net unattended), how do I get all the rights I am entitled to, and whatever others there are?

Whoa! I've just played with Users and Groups and got myself elevated. I can now 'sudo gparted' successfully! Thanks for your patience and advice.

---

### Post by Hopalong on 2009-12-02
The same thing. My user name is "not in the sudoers file". Since I am the only user of this machine (and it doesn't stay connected to the net unattended), how do I get all the rights I am entitled to, and whatever others there are?:confused:

---

### Post by darkod on 2009-12-02
Post #5
[http://ubuntuforums.org/showthread.php?t=668421](http://ubuntuforums.org/showthread.php?t=668421)

---

### Post by coffeecat on 2009-12-02
Fix broken sudo:

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

