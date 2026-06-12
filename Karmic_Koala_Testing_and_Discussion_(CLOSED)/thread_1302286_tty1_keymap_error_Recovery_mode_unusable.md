---
title: "tty1 keymap error? Recovery mode unusable"
date: 2009-10-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by FormerSlacker on 2009-10-26
Long post, bare with me please.

Basically, tty1 is unusable. This includes recovery mode as well.

Steps to reproduce:
1)Change to tty1 with ALT+CTRL+F1
2)Login
3)Use an app that requires PAGE UP/DOWN ie)nano /var/log/messages
4)Randomly scroll up and down, after 10 seconds or so your screen will be unusable and you'll see a message about "Maintenance mode" and a root prompt!

All other tty's function properly, only tty1 is affected.

It seems that another program, perhaps the "recovery console" menu, is reading tty1 input as well, leading to odd behavior when using PAGE UP/DOWN etc.

That's the only explanation for the "Maintenance mode" being invoked eventually.

Any ideas?

---

### Post by FormerSlacker on 2009-10-28
Success! After much searching, I've stumbled onto this bug report.

[https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/458352](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/458352)

Definitely the same problem.

---

### Post by FormerSlacker on 2009-10-28
Another bug related to this issue:
[https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/456806](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/456806)

Sadly, they seemed to have marked the bug as fixed. It still affects me.

---

### Post by VMC on 2009-10-28
> **FormerSlacker said:**
> Basically, tty1 is unusable. This includes recovery mode as well.
Steps to reproduce:
1)Change to tty1 with ALT+CTRL+F1
2)Login
3)Use an app that requires PAGE UP/DOWN ie)nano /var/log/messages
4)Randomly scroll up and down, after 10 seconds or so your screen will be unusable and you'll see a message about "Maintenance mode" and a root prompt!

All other tty's function properly, only tty1 is affected.

It seems that another program, perhaps the "recovery console" menu, is reading tty1 input as well, leading to odd behavior when using PAGE UP/DOWN etc.

That's the only explanation for the "Maintenance mode" being invoked eventually.Any ideas?I had no problems at all. I first used 'vim' then byobu along with 'vim' to see the time I was going up/down and around. Severals minutes later it still works, no messages. Maybe 'nano'. I don't have that installed for some reason.

---

### Post by FormerSlacker on 2009-10-28
For vim, the magic combination for me is simply ESC and I'm greeted with a mountall root prompt.

---

### Post by FormerSlacker on 2009-10-28
I've read that this is may only be a issue for an hour or two after you've booted up.

---

