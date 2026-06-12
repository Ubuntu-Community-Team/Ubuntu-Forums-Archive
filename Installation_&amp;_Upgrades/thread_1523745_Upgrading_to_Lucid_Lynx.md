---
title: "Upgrading to Lucid Lynx"
date: 2010-07-04
forum: Installation &amp; Upgrades
---

### Post by suddentwigs on 2010-07-04
Hi there. I have just upgraded the OS on my laptop to lucid lynx using the update manager. It successfully went through everything, but when the system rebooted it asked me for a password. I've never set a password for it, so I just pressed enter. It then seemed to freeze, and returned me to the login screen. Is there anything I can do, or will I need to reinstall from scratch?

---

### Post by Rubi1200 on 2010-07-04
> **suddentwigs said:**
> Hi there. I have just upgraded the OS on my laptop to lucid lynx using the update manager. It successfully went through everything, but when the system rebooted it asked me for a password. I've never set a password for it, so I just pressed enter. It then seemed to freeze, and returned me to the login screen. Is there anything I can do, or will I need to reinstall from scratch?

That is not possible; when you originally installed Ubuntu you created a user account with a password.

That is the password you need to enter now; what you just experienced is an authentication failure (security measure on Ubuntu).

What may have happened is that you originally set things up to log in automatically but the upgrade somehow changed things.

---

### Post by ajgreeny on 2010-07-04
If you have forgotten your password having been using autologin, see [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by SisterNotes on 2010-07-19
Thanks ajgreeny - this solved my authentication failure issue. I didn't forget my password - they all stopped working except for the auto login. I suspect the problem may have started with a power outage. I had a similar problem when I first started using ubuntu and accidentally pulled out the power cord. The lack of shutdown procedure seemed to have messed up the password/login function. At that time I did a fresh install. But this time, I was able to reset my password and avoid the reinstall trouble. Thanks!

---

