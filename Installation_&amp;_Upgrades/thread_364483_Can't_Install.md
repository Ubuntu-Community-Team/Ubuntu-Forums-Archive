---
title: "Can't Install"
date: 2007-02-18
forum: Installation &amp; Upgrades
---

### Post by Dollar00 on 2007-02-18
First of all, I am completely new to Ubuntu/Linux, but have had it for a day and was able to install programs previously.
But now when I open up Synaptic Package Manager or try to install something (like Geany) through Add/Remove Programs, I get this error:
> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

Honesty, I am not completely sure what it means, but I assume it means type that in the terminal. When I do type "dpkg --configure -a" in the terminal, I get this message:
> dpkg: requested operation requires superuser privilege


Please help. Thank you.

---

### Post by highneko on 2007-02-18
sudo dpkg --configure -a

---

### Post by Dollar00 on 2007-02-18
Thanks. Now that I've typed in the correct line, here is what I get:
> Password:
Setting up java-common (0.25ubuntu1) ...

Setting up libltdl3 (1.5.22-4) ...

Setting up odbcinst1debian1 (2.2.11-13) ...

Setting up clamav-base (0.88.4-1ubuntu2.1) ...
chown: cannot access `/var/run/clamav': No such file or directory
dpkg: error processing clamav-base (--configure):
 subprocess post-installation script returned error exit status 1
Setting up unixodbc (2.2.11-13) ...

Errors were encountered while processing:
 clamav-base

Any help?

---

### Post by Dollar00 on 2007-02-19
I keep trying to install updates, but instead of saying "Done" next to each update, it says "Failed" or "Hit". I've "installed" the same 41 updates through Update Manager many times now and they have not actually been installed still.

I also often get an error dealing with clamav-base. I have no idea what this is.

Please help.

EDIT: Through the Synaptic Package Manager, I tried to reinstall clamav-base, which is apparently some anti-virus thing, and got an error. Then beryl-xgl crashed. Now I think beryl may be causing the problems. I don't think this site allows discussion on beryl: is there another site I can go to for help?

---

