---
title: "E: Could not perform immediate configuration on 'util-linux'.Please see man 5 apt.con"
date: 2010-03-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by tehk on 2010-03-25
E: Could not perform immediate configuration on 'util-linux'.Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)


Any idea what to do here? This happened after I switched all my repositories over to lucid and did a dist-upgrade...

---

### Post by dino99 on 2010-03-25
> **tehk said:**
> E: Could not perform immediate configuration on 'util-linux'.Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)


Any idea what to do here? This happened after I switched all my repositories over to lucid and did a dist-upgrade...

what do you mean by "switched all my repositories over" ?

---

### Post by tehk on 2010-03-25
That's how I've been upgrading since 8.04, find and replace all "karmic" strings in /etc/apt/sources.lst with "lucid"

---

### Post by tehk on 2010-03-25
solved. see first post.

---

### Post by tehk on 2010-03-25
Nevermind, cant edit posts, chrome crashes with an... 

Aww Snap! 

message, when I try to edit any post on this thread.

So, the solution was to use synaptic and upgrade util-linux and all dependencies. Then the dist-upgrade completed.

---

### Post by avantgardist on 2010-04-22
Hey, I've got exactly the same error message. But I'm unable to fix it with synaptic because I've no gui, there is only the command line!

so what can I do to solve the problem?

thx

---

### Post by mibrahim74 on 2010-04-23
I got around this error first by upgrading apt and apt-utils, then upgrading util-linux using synaptic, then did dist-upgrade from the shell and it worked.

---

### Post by mox69 on 2010-04-29
I also was having the same issue while upgrading from karmic to lucid, using the replace the work karmic with lucid method. 
 
After running safe-upgrade and rebooting I was dropped into console mode. When attempting a full-upgrade, I started getting this error.
 
Turns out that while I had previously updated apt and aptitude, I did not upgrade "dpkg" (because of some other random mountall errors while doing so).

 
 
Solution was to first upgrade dpkg (apt-get install dpkg) then run a full upgrade (aptitude full-upgrade). This caused the util-linux error to go away and full-upgrade to hum along like normal.

---

### Post by cariboo on 2010-04-29
> **avantgardist said:**
> Hey, I've got exactly the same error message. But I'm unable to fix it with synaptic because I've no gui, there is only the command line!

so what can I do to solve the problem?

thx

At the prompt depending on which prompt if you are at a root prompt type:

```
apt-get -f install
```

then

```
aptitude update && aptitude -y safe-upgrade
```

If you are at your user prompt just add sudo at the beginning of the command.

---

