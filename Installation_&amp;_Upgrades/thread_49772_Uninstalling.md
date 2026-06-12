---
title: "Uninstalling"
date: 2005-07-17
forum: Installation &amp; Upgrades
---

### Post by johnsorc on 2005-07-17
Here's the situation:  I installed Ubuntu on my 2nd HD, but now I want to remove it.  I tried just reformatting the drive, but received the Grub 17 error.  To avoid that, I reinstalled ubuntu on the same drive so I could get back into windows.  I'm not sure what to do though.  I don't have a windows cd, as the other uninstall posts advise using.  Is it possible to change the grub, then uninstall ubuntu?  Oh, I'm running windows XP Home on my machine.

---

### Post by damonw5 on 2005-07-17
[QUOTE=johnsorc]Here's the situation:  I installed Ubuntu on my 2nd HD, but now I want to remove it.  I tried just reformatting the drive, but received the Grub 17 error.  To avoid that, I reinstalled ubuntu on the same drive so I could get back into windows.  I'm not sure what to do though.  I don't have a windows cd, as the other uninstall posts advise using.  Is it possible to change the grub, then uninstall ubuntu?  Oh, I'm running windows XP Home on my machine.[/QUOTE]
 You could configure GRUB, or you could install a different boot manager. Try installing this to your MBR (master boot record):

[http://www.ranish.com/part/xosl.htm](http://www.ranish.com/part/xosl.htm)

That will let you boot from any partition of any hard drive. The same page also has a good partitioning tool.

---

### Post by johnsorc on 2005-07-17
Thanks!  I'll try those and see if I can get things to work

---

### Post by WildTangent on 2005-07-17
this is how to solve the problem:
You can do this before or after uninstalling Ubuntu, it really doesnt matter. what you need to do is get the disk you installed XP with (it has to be the same version and service pack) and boot it, when it gives you a menu, type R to repair windows. it will ask you what windows installation you want to repair, itll list them (if you have more than one, but ill assume you dont), just press 1 and then enter. if you have an administrator password, youll have to enter it now. now youll have a command prompt, type "fixmbr" without the quotes, itll say something about this could damage your partition table (and it may, but its EXTREMELY unlikely, in any case, i will not be held responsible) type "y" and then hit enter and its done. type "exit" and take the cd out, your computer is now rebooting.

ive posted this same solution in here 3 times now, all for the same reason, uninstalling/reformatting the linux partition. can i make a HOWTO?

-LLM

---

