---
title: "[SOLVED] I WANT TO CRYYYY, bluetooth sucks..."
date: 2008-11-22
forum: Installation &amp; Upgrades
---

### Post by dj_ee3 on 2008-11-22
I don't know what to say ... I am on the computer 7 hours already and no result... my ubuntu instalation doesn't want to pass the bluetooth starting... I don't know what to do and I feel very bad ... I waste my whole saturday for nothing..... can you please please please help me solve this one.. I will be very thankful.](*,)](*,)](*,)](*,)](*,)

---

### Post by lswb on 2008-11-22
I cannot tell from your post whether your system is failing to finish booting after it gets to the point where bluetooth starts, or whether you are trying to get bluetooth working on a system that is otherwise working OK.

---

### Post by dj_ee3 on 2008-11-22
> **lswb said:**
> I cannot tell from your post whether your system is failing to finish booting after it gets to the point where bluetooth starts, or whether you are trying to get bluetooth working on a system that is otherwise working OK.
The first one the system is failing to finish booting after it gets to the point where bluetooth starts..

---

### Post by lswb on 2008-11-22
OK, most likely the problem is not bluetooth, but whatever follows it in your boot process is failing. Bluetooth generally generally starts pretty late in the boot process, often just a step or 3 from where a graphic login would start.

When the system appears to have stopped, try pressing Control+Alt+F1 and see if it switches to a vt with a login: prompt. If so, you can go ahead and log in, then check your log files ( /var/log/syslog to start also if you are expecting a gui/graphic login, /var/log/Xorg.0.log) and see if there are any obvious errors or warnings present.

I would suggest posting a new request with a title that more accurately describes the problem. In the post include what distro & version you are running and what kind of system (processor & speed, video adapter, installed memory, etc.) This will make it more likely to attract attention from people who can help solve your problem.

---

