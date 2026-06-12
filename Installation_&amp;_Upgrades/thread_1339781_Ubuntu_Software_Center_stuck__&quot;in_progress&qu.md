---
title: "Ubuntu Software Center stuck  &quot;in progress&quot;"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by mark555 on 2009-11-27
I just tried to install the adobe flash plug-in through the Ubuntu Software Center and it stopped at 82% complete.  I then closed the software center and relaunched it.  It says that the flash plug-in is installed, but if I try to remove it, it says "Waiting for other software manager to quit.". It also says the same thing if I try to install any other software.  I tried using synaptic, but I get and error box that says "Unable to get exclusive lock."  I used the system monitor to kill the software center process, but when I relaunch it, it still says "In progress(1)" in the left pane.

---

### Post by PRC09 on 2009-11-27
Just try  rebooting the system and try again.I had the same problem about 2 hours ago and a reboot solved it...

---

### Post by mark555 on 2009-11-27
I tried rebooting and shutting down and rebooting, but it didn't help.

---

### Post by jake0391 on 2009-12-05
I am having the same exact issue. Every time I try to install the adobe flash plug-in it locks up. I need to load another package now and can not get it installed. This time it started from an auto update. Prior to that it was when I was installing from Firefox. Would love to know the solution.

---

### Post by jake0391 on 2009-12-05
I resolved it by doing the following command:

sudo dpkg --configure -a

It finished downloading the package that seemed to be stuck and everything else started to work.

---

### Post by needhelppeeps on 2009-12-10
I'm having the same issue, also on flash.

---

### Post by needhelppeeps on 2009-12-16
I fixed this problem by using the .deb installer package.

---

### Post by uffe.hellum on 2010-05-30
I fixed mine by killing the right "dpkg" thread:


uffeh@toshi1:~$ ps ax | grep dpkg
 8191 pts/0    Ss+    0:00 /usr/bin/dpkg --status-fd 26 --configure -a --force-confdef --force-confold
 8194 pts/0    S+     0:00 /usr/bin/perl -w /usr/share/debconf/frontend /var/lib/dpkg/info/mysql-server-5.1.postinst configure 
 8200 pts/0    S+     0:00 /bin/bash -e /var/lib/dpkg/info/mysql-server-5.1.postinst configure 
 8326 pts/2    S+     0:00 grep --color=auto dpkg
uffeh@toshi1:~$ sudo kill 8191


uffeh@toshi1:~$ sudo dpkg --configure -a
Setting up mysql-server-5.1 (5.1.41-3ubuntu12.1) ...
(Failed to set mysql root password, but happily continuing)


uffeh@toshi1:~$ sudo tasksel install lamp-server
uffeh@toshi1:~$ 
(Seemed happy. )

Now I just need to repair mysql root password and folder access...  But I think that's explained in other threads, so I'm optimistic.

---

### Post by senthilss on 2011-06-09
No need to reboot. 

Because it's a Linux, not windows :)

Just kill the dpkg process running for the moment. Whenever a package is to be installed, dpkg will be called for install and configure. It usually get stuck in configuration step (for whatever reason). So just killing the dpkg process will end up the app install and go for next one waiting in the queue. 

Again, don't reboot. B'cos it's not needed :)

---

### Post by JosephKirubakaran on 2011-12-25
> **uffe.hellum said:**
> I fixed mine by killing the right "dpkg" thread:


uffeh@toshi1:~$ ps ax | grep dpkg
 8191 pts/0    Ss+    0:00 /usr/bin/dpkg --status-fd 26 --configure -a --force-confdef --force-confold
 8194 pts/0    S+     0:00 /usr/bin/perl -w /usr/share/debconf/frontend /var/lib/dpkg/info/mysql-server-5.1.postinst configure 
 8200 pts/0    S+     0:00 /bin/bash -e /var/lib/dpkg/info/mysql-server-5.1.postinst configure 
 8326 pts/2    S+     0:00 grep --color=auto dpkg
uffeh@toshi1:~$ sudo kill 8191


uffeh@toshi1:~$ sudo dpkg --configure -a
Setting up mysql-server-5.1 (5.1.41-3ubuntu12.1) ...
(Failed to set mysql root password, but happily continuing)


uffeh@toshi1:~$ sudo tasksel install lamp-server
uffeh@toshi1:~$ 
(Seemed happy. )

Now I just need to repair mysql root password and folder access...  But I think that's explained in other threads, so I'm optimistic.
Worked for me :)
thanks

---

### Post by Oesipower on 2012-06-12
> **uffe.hellum said:**
> I fixed mine by killing the right "dpkg" thread:


uffeh@toshi1:~$ ps ax | grep dpkg
 8191 pts/0    Ss+    0:00 /usr/bin/dpkg --status-fd 26 --configure -a --force-confdef --force-confold
 8194 pts/0    S+     0:00 /usr/bin/perl -w /usr/share/debconf/frontend /var/lib/dpkg/info/mysql-server-5.1.postinst configure 
 8200 pts/0    S+     0:00 /bin/bash -e /var/lib/dpkg/info/mysql-server-5.1.postinst configure 
 8326 pts/2    S+     0:00 grep --color=auto dpkg
uffeh@toshi1:~$ sudo kill 8191


uffeh@toshi1:~$ sudo dpkg --configure -a
Setting up mysql-server-5.1 (5.1.41-3ubuntu12.1) ...
(Failed to set mysql root password, but happily continuing)


uffeh@toshi1:~$ sudo tasksel install lamp-server
uffeh@toshi1:~$ 
(Seemed happy. )

Now I just need to repair mysql root password and folder access...  But I think that's explained in other threads, so I'm optimistic.

I had the same problem: Ubuntu Software Center got stuck in applying changes of Flash Player.So I killed the dpkg process as you said and installed the Flash Player update manually and Flash works now. Only problem is that everytime I run "sudo dpkg --configure -a" it wants to update Flash Player, although it works, and gets stuck. Same thing happens when I want to update the system with the normal updating tool. So, how can I stop the dpkg process from wanting to update Flash Player?

---

### Post by David Andersson on 2012-06-12
(off topic)
> **Oesipower said:**
> I had the same problem: 
**Dear Oesipower**: You hijacked thread [http://ubuntuforums.org/showthread.php?t=2001577](http://ubuntuforums.org/showthread.php?t=2001577) "Adobe Flash Player plugin from Ubuntu Software Center" with your problem. You was told to start your own thread. Now a few hours later you hijack this thread with seemingly the same problem. Please **start a new thread**!

---

