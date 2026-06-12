---
title: "lost root"
date: 2005-05-17
forum: Installation &amp; Upgrades
---

### Post by vanaedium on 2005-05-17
i've checked ubuntu after 2 weeks and I forgot what i did before but nothing wrong I think. Actually every operation by root is not permitted!!!
I've tried to do 

sudo passwd root

but I can't use root, no synaptic, no su!! What happens and especially what have I to do?
Thanx

---

### Post by Xian on 2005-05-17
Read the wiki article ["RootSudo"](http://www.ubuntulinux.org/wiki/RootSudo/view?searchterm=sudo) and see if it is of assistance.
You may need to re-add your user to the sudoers group.

---

### Post by vanaedium on 2005-05-17
ok but i'll need root permission to do that? or I have to change with knoppix? Which file does contain the group indications?

---

### Post by Xian on 2005-05-17
Look at [THIS](http://www.ubuntuforums.org/showthread.php?t=34184&page=2&pp=10&highlight=sudo) thread. It should be helpful.
Be sure to read the last post by azz.

---

### Post by vanaedium on 2005-05-17
sorry I miss something:
when I type su and the password the answer is 
setgid: Operation not permitted
In particular I find that /etc/sudoers is setted as 0666 but must be 0440 (?)
When I type sudo "something" the answer is
sudo: must be setuid root
 ](*,)

---

### Post by hammett111 on 2005-05-18
I just hammered this problem. This is what I did.

Find the sudoers file /etc/sudoers using file navigator. Then click on properties and look at permissions. There change all the permissions so that only the top two selections are ticked to read, and nothing else is ticked. This changes the permissions to the setting 440 or in your case 0440.

Clear as mud?

---

