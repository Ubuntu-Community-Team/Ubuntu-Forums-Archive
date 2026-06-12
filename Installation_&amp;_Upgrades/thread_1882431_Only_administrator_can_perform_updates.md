---
title: "Only administrator can perform updates"
date: 2011-11-17
forum: Installation &amp; Upgrades
---

### Post by robin_s on 2011-11-17
After upgrading to Ubuntu 11.10, and then performing an update, the update manager now demands authentication from the original administrator in order to perform updates.  I have sudo privileges, but am not the original administrator.  What do I do to persuade the update manager also to accept me as an authorised updater?

---

### Post by plucky on 2011-11-17
> **robin_s said:**
> After upgrading to Ubuntu 11.10, and then performing an update, the update manager now demands authentication from the original administrator in order to perform updates.  I have sudo privileges, but am not the original administrator.  What do I do to persuade the update manager also to accept me as an authorised updater?

Have you  tried inputting your login password? What happens if you do?

What output do you get from ```
sudo apt-get update && sudo apt-get upgrade
``` in a terminal.

Does your user have **admin** group privileges?

From a terminal post the output of ```
id
```

---

### Post by robin_s on 2011-11-17
If I input my login password, the update manager replies "Sorry, that didn't work.  Please try again".

The result of using the command line commands:
 	Code:
 	sudo apt-get update && sudo apt-get upgrade 
 appears to be a normal update and upgrade (quite long, there were 218 updates to do, so I guess you do
not want to see the whole thing).

The output from id is:
 	Output:
 	[SIZE=2]uid=500(robin) gid=500(robin) 
groups=500(robin),4(adm),20(dialout),24(cdrom),46(plugdev),111(lpadmin),119(admin),
122(sambashare)[/SIZE]
 
The problem seems to be in the GUI-based update manager, which only seems to know about the original administrator who set up the system.   It just presents me with a pop-up window containing the name and atavar of the administrator, and a box in which to type the (administrator's) password.

I shall have to restart the computer to see whether the above update+upgrade affected this behaviour.

---

### Post by robin_s on 2011-11-17
After restarting the computer:

The command line update+upgrade seems to have been completed successfully, but it had no effect on the behaviour of the Update Manager GUI, which consistently demands authentication from the original administrator rather than the current user.

Interestingly enough, I could restart the computer from the Update Manager GUI without problems (and without giving any authentication).  This doesn't sound very secure (even though it helped me on my way).

---

### Post by plucky on 2011-11-17
> The output from id is:
Output:
uid=500(robin) gid=500(robin)
groups=500(robin),4(adm),20(dialout),24(cdrom),46( plugdev),111(lpadmin),119(admin),
122(sambashare)


I am not sure if this is relevant,but uid and gid between 100 and 999 are allocated on Debian systems to dynamically allocated **system** users.

The account created at installation time allocates a uid=1000 and gid=1000 as the start for **user** accounts.

See [Debian Policy Manual](http://www.debian.org/doc/debian-policy/ch-opersys.html)

Perhaps this is the reason you are getting the strange behaviour on your system.

You could try changing the uid and gid of your user account to above the 1000 mark.

Good Luck

---

