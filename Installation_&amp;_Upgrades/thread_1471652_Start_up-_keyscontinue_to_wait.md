---
title: "Start up- keys:continue to wait  ?"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by Professor IllDog43 on 2010-05-03
Alrighty,
Upgraded Xubuntu 10.04 using my motorola backflip teathered to my dell inspiron 2650 ( I know why but thats what I have and I live in the sticks )

Older problem
So everything looks good a few hickup now and then but still have the same shut down issue I had in xubuntu9.10 shuts down all the way then hangs on final splash screen. (anyone found fix?)

New Problem 
At start up everything is good till I get to xubuntu splash screen with (keys:Continue to wait; or Press S to skip mounting or M for manual recovery) now if I press S it boot just fine and everything works great. I just no sure what is going on this point so I have no where to turn for help...:confused:

Thanks for information and if you would like linux to your smart phone look here...
[http://www.humans-enabled.com/2009/12/how-to-tether-your-verizon-droid-as.html](http://www.humans-enabled.com/2009/12/how-to-tether-your-verizon-droid-as.html)

---

### Post by blueridgedog on 2010-05-11
I had this issue as well and had to add the option "nobootwait" to a few entries in my /etc/fstab file for drives that are not always plugged in.

If that is not familiar to you, I can make suggestions if you post the contents of your /etc/fstab file with:

```
cat /etc/fstab
```

---

### Post by bilgee0629 on 2010-05-14
Hey buddy! have you found solution??? :P

---

### Post by Tshann on 2010-05-16
Yeah, the solution is here: [http://ubuntuforums.org/showthread.php?t=1467638]("http://ubuntuforums.org/showthread.php?t=1467638")

Peace

---

### Post by Professor IllDog43 on 2010-06-14
I installed [COLOR="Red"]Pysdm[/COLOR] to solve disk issue.

---

### Post by aditya3098 on 2012-01-01
sudo gedit /etc/fstab
delete the line which has the error(look at it and you WILL find out what has the problem).

---

