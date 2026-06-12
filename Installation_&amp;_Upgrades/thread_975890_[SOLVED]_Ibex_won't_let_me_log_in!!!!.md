---
title: "[SOLVED] Ibex won't let me log in!?!?!?!"
date: 2008-11-08
forum: Installation &amp; Upgrades
---

### Post by rbradt on 2008-11-08
Hey folks,

I have a rather weird situation.  After upgrading from 8.04 to 8.10, things were going well.  Until recently when I restarted my system, the log in screen comes up fine; however, after I put in my username and password, it just goes right back to the log in screen even if I put in the correct information.  The same goes for the terminal modes as well.

I am able to login when in root recovery mode, but I have no idea what's going on.  Right now, my plan is to get an external hard disk and move all my docs and what not over, and then just do a clean install.  Unless anyone can give me any suggestions...?

-rbradt

---

### Post by taurus on 2008-11-08
Boot into recovery mode from GRUB menu and change your password.

```
passwd **your_login_name**
shutdown -r now
```
Can you log in with your new password now?

---

### Post by rbradt on 2008-11-08
When I try to execute the command:

```
passwd **login_name**
```

I get a segmentation fault.

---

### Post by taurus on 2008-11-08
You need to replace **login_name** with your _actual_ login name!

---

### Post by rbradt on 2008-11-08
Yes, I'm aware of that.  And I get a segmentation fault when I try to execute.

---

### Post by bigmac8298 on 2008-11-10
The same problem is currently happening to me as well.  Was there ever a fix found for this or will I have to reinstall?  Is there something that causes this type of error??

---

### Post by frodon on 2008-11-10
This may help ;) :
[https://bugs.launchpad.net/ubuntu/+source/pam/+bug/292791](https://bugs.launchpad.net/ubuntu/+source/pam/+bug/292791)

---

### Post by rbradt on 2008-11-12
That's amazing!!!  That fixed it.  Thanks a lot.

Just out of curiosity.  Do you happen to know why this bug occurs?

Thanks again!
-rbradt

---

### Post by frodon on 2008-11-12
You should post in the bug report your experience, maybe it could help making the bug report more active.

As for the root cause i have no idea.

Anyway glad to know you're back to normal ubuntu experience, such issues are really a pain.

---

### Post by ricksterinps on 2008-11-13
Thank you so much.  I've been banging my head against the desk for the last 5 hours trying to figure this out.  I upgraded to 8.10 last week and everything was running fine and I even was able to do the update this morning, but afterwards I was stuck.  This solved my problem as well.

---

### Post by OsNo on 2008-11-18
Got the same problem with a clean 8.10 install

worked fine for a couple of days (with almost nothing extra then a LAMP config)
But when i started installing and configuring samba, vsftpd and cups with a reboot aftherwards it all went wrong.

Thanks for the link to the bugreport, it helped me out, so that led me to believe the bug has something to do with samba.

---

### Post by evolutionx on 2008-11-19
I'm getting the exact same issue after setting up Cups and Samba. Not sure if they are related but in my case everything trying to use PAM segfaults.

This is my dmesg;

```
[74553.572975] cupsd[4536]: segfault at 0 ip b7079abb sp bff6c5a0 error 4 in pam_smbpass.so[b701d000+12a000]
[74748.747900] sshd[10231]: segfault at 0 ip b7889abb sp bffe64f0 error 4 in pam_smbpass.so[b782d000+12a000]
[74828.318587] login[26776]: segfault at 0 ip b7c58abb sp bfe58770 error 4 in pam_smbpass.so[b7bfc000+12a000]
[75102.607384] sudo[11095]: segfault at 0 ip b7d72abb sp bf9816d0 error 4 in pam_smbpass.so[b7d16000+12a000]
```

---

### Post by Silver Streak on 2008-12-02
I'd like to chime in and say that this bug has also affected me. I was playing around with CUPS, when suddenly the server stopped responding. Attempting to restart it resulted in a segfault. Upon reboot I was stuck in a login loop, both graphically and on the command line.

The fix in the launchpad topic (commenting out one line in two specific PAM config files) seems to have worked for me: I can now login through GDM (and likely via command line).

---

### Post by gali98 on 2008-12-14
wow... so weird.. Same exact thing as above. I was messing with the cups at localhost:631, and I reloaded it a bunch of times to see if a job was doing something, then the webserver crashed (as did cupsd) so I restarted and the login loop started. Problem is I need the smb auth to work as I use a printer connected to a windows machine... any help? I'll post back with any info I find...
Kory

---

### Post by gali98 on 2008-12-14
all I did was:
sudo apt-get purge libpam-smbpass
sudo apt-get purge libpam-smbpass

and that fixed it for me. 
(I first had to change the config files like in the bug report, but after logging in and running these commands, it was fixed.)
One thing I have noticed though is from some apps (like gimp and the pdf viewer) it just won't print to the printer (the one shared on a windows machine), but in open office and scribus it will. It's strange. anyway, that's what I did.
Kory

---

