---
title: "Lost Synaptic after upgrade to 8.04"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by glendavee on 2008-04-27
After upgrading to 8.04 from 7.10 I can no longer open most of the applications in the System>Administration menu. The programs are all listed, but when I try to open them, nothing happens. Means I can't open Synaptic, Update Manager,Simple Backup, amongst others. I'm sure they are still in there somewhere, problem is, how do I find them??

---

### Post by IT-Joker on 2008-04-27
This is probably caused by the /etc/hosts problem that I had as well.
Read the first post in this thread: [http://ubuntuforums.org/showthread.php?t=769338](http://ubuntuforums.org/showthread.php?t=769338)
it's section 1.

Or for short:
- Try opening terminal and type sudo anything, for example:
sudo synaptic
Normally it should ask you for password and then run Synaptic. If you get error message from sudo instead, something about that it can't reach [your computer name], then it's propably this problem.

What you can do:
1. From the error message, remember [your computer name] (remember letter case too)
2. Restart, enter the boot menu and choose the recovery mode
3. You should end up in the command line. Now type:
nano /etc/hosts
It should open the /etc/hosts file in a simple text editor.
4. You should see something like this:
```
127.0.0.1 localhost

# The following lines are desirable for IPv6 capable hosts
(some stuff)
```
Now you must add the following line to the file:
127.0.1.1 [your computer name]
instead of [your computer name] type your computer name that I told you to remember from the sudo error message ;)
Now quit nano (ctrl+X) and when asked to save the file, choose YES.
5. Restart and it should be working correctly.

---

### Post by glendavee on 2008-04-27
Thanks,IT-Joker  worked like a charm

---

