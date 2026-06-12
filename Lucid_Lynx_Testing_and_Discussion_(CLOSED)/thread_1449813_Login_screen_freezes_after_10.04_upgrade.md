---
title: "Login screen freezes after 10.04 upgrade"
date: 2010-04-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by iris_v on 2010-04-08
Hello,

I just upgraded to 10.04. All went well on my laptop, but my desktop is proving more troublesome. 

When I start up as normal, the login screen appears. I can choose which user I want to log in as, or select 'Other' and type my username. So far so good. However, as soon as I select the user and progress to the  screen where you enter your password, everything freezes for about 5 seconds, then the screen blinks black, and then it's back to the first login screen where you select the user. It's a loop I cannot get out of, other than restarting. 

When I circumvent the login screen by starting in recovery mode, then selecting 'Resume normal boot', entering my username & pw when prompted and then running startx, everything works fine.

---

### Post by TeoBigusGeekus on 2010-04-08
Never had any luck with upgrades - for one reason or the other I could never get a working system after an upgrade. That's why I've always done a fresh install (and I've learned to keep a separate /home partition the hard way).

---

### Post by iris_v on 2010-04-10
> **TeoBigusGeekus said:**
> Never had any luck with upgrades - for one reason or the other I could never get a working system after an upgrade. That's why I've always done a fresh install (and I've learned to keep a separate /home partition the hard way).

OUch, that sounds messy! I've been running Ubuntu on two computers since 2007, so this problem occurred on what I think is my 12th upgrade. Not every upgrade has gone entirely smoothly, but then I usually upgrade to the beta, so that is to be expected. And besides, I've never ended up with a completely unworkable situation. 
And this issue also isn't unworkable, but because of the total lack of error messages, I haven't yet been able to solve it. So, any help will be much appreciated!

---

### Post by macstevejb on 2010-04-10
this is a known problem, particularly when using nvidia graphics.

See bug #553200

Until fixed, try the following workaround:

upon arrival @ gdm login scree,n do nothing, then:
ctrl+alt+F2
Login with your username and password
sudo service gdm stop
insert your password again
startx

regards

---

### Post by iris_v on 2010-04-10
Thanks! And indeed, nvidia graphics there...

Update: the problem resolved itself with subsequent updates

---

### Post by jv2112 on 2010-04-25
Anybody hear of any permanent fix ?

---

### Post by Opettaja on 2010-04-27
Same problem here! Any luck finding a permanent fix?

---

### Post by 4Orbs on 2010-04-27
The nvidia legacy driver that I use was upgraded to 96.43.17 when Lucid RC was released. That fixed the login loop for me. Maybe if you run the update manager then deactivate your driver, then reactivate it.

---

### Post by jv2112 on 2010-04-28
No dice here with that method.......:(

---

