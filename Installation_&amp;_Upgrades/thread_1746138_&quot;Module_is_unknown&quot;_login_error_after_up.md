---
title: "&quot;Module is unknown&quot; login error after update to 11.04"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by denrix on 2011-05-01
Hi everyone,

I've just upgraded to Natty and lost ability to login through the Gnome login screen - "Module is unknown" message appears after I enter the correct password and hit "Enter".

I'm still able to switch to a text console and login there, both as root and as a restricted user.

Here is an excerpt from my /var/log/auth.log file:

```
May  1 14:12:09 HomeServer gdm-session-worker[1948]: PAM unable to dlopen(/lib/security/pam_listfile.so): /lib/security/pam_listfile.so: cannot open shared object file: No such file or directory
May  1 14:12:09 HomeServer gdm-session-worker[1948]: PAM adding faulty module: /lib/security/pam_listfile.so
May  1 14:12:09 HomeServer gdm-session-worker[1948]: pam_succeed_if(gdm:auth): requirement "user ingroup nopasswdlogin" not met by user "deadrix"
```

This appears after each attempt to login at Gnome login screen.

I've reinstalled libpam-modules, but with no avail.

Please help to solve this.

---

### Post by denrix on 2011-05-02
Anybody?

---

### Post by cowguru2000 on 2011-05-04
Try:
pam_tally --reset --user <username>
sudo pam-auth-update --force

[http://ubuntuforums.org/showthread.php?t=1150786](http://ubuntuforums.org/showthread.php?t=1150786)

---

### Post by cowguru2000 on 2011-05-04
Btw, bump. I got those commands from another thread but they didn't work for me.

---

### Post by odp on 2011-05-15
I am experiencing the exact same thing.

I have used the above mentioned commands with no result.

Further I have tried to reinstall X and gdm, no luck!

I am currently looking into problems with pam. I will post results asap.


No solutions yet, but as far as i can see people have been having this sort of problem before.
So maybe the updater fails to install/update/configure/sanitize from 10.10 to 11.04 ?

Now I just need to figure out how to check for those errors?

---

### Post by extensa-5420 on 2011-05-25
I had the same problem in Ubuntu 11.04 (32-bit).  I found out that pam_listfile.so was not in /lib/security.  I did a search and found it.  Then I went to /etc/pam.d/gdm and changed the path from:

/lib/security/pam_listfile.so

to:

/lib/i386-linux-gnu/security/pam_listfile.so

and that fixed the problem.

---

### Post by floatingworld on 2013-01-23
I ran into this in 12.04 32-bit.  In my case, for some reason [FONT="Courier New"]/lib/security[/FONT] was completely absent from the system, the folder didn't exist at all.  My solution was to create it and copy all of the .so files from [FONT="Courier New"]/lib/i386-linux-gnu/security[/FONT] into it.

---

### Post by oldos2er on 2013-01-24
Old thread closed.

---

