---
title: "Am i really toasted?"
date: 2009-12-23
forum: Installation &amp; Upgrades
---

### Post by ububaba on 2009-12-23
Have several SATA HDs. After having tackled the ICEauthority problem, 
on one of them, I noticed that sound was completely gone. No streams 
were present. Nvidia driver was OK, when I expanded different mixers that
I had loaded, they showed only a blank page, had neither any figures 
nor text on it. 

After a restart I was pushed to the shell where I was prompted to login,
which was an impossibility as the screen was [COLOR="Red"]flickering[/COLOR] madly. Hence other
harddisks could not be accessed. 

If I make the healthy HD as the sda1, I do get to see the login icon but it 
stops at that, no possibility to actually login. And then after a few minutes 
the screen turns blank black.

[COLOR="Red"]Has anyone been through this?[/COLOR] There is so much on the HD that I would 
not like to lose.

Am I really toasted? Naturally, I can furnish more details.[COLOR="Red"][/COLOR]

---

### Post by K.J. on 2009-12-23
I'm not exactly sure what your problem might be. You can try logging in as single user and reconfiguring your X. You probably haven't lost any data. I would boot in with a live cd and copy data to an external drive.

---

### Post by HeadHunter00 on 2009-12-23
Ooh, you're toast.

---

### Post by ububaba on 2009-12-23
> **K.J. said:**
> I'm not exactly sure what your problem might be. You can try logging in as single user and reconfiguring your X. You probably haven't lost any data. I would boot in with a live cd and copy data to an external drive.

1 If the problematic disk is sda then it keeps on flickering no further
  action is possible.

2 If the good one is made sda then the login screen is incomplete and 
after a little wait it becomes totally black. 

I hope it is clearer now. I will try out with live CD. 

Thanks

---

### Post by ububaba on 2009-12-23
> **HeadHunter00 said:**
> Ooh, you're toast.

Thanks for making me realise!

---

### Post by ububaba on 2009-12-23
I had to autoclean and corect ext3 and ext4 in /etc/fstab 
that fixed everything. Thanks anyway.

---

