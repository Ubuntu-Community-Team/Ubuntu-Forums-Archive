---
title: "administration tasks or apps fail under 8.04"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by togo59 on 2008-04-29
Viglen, P4 dual-core, 3.2Ghz, 2Gb RAM

Ubuntu 8.04 installed OK but cannot launch any of the admin apps (including login window). Symptom: The "Starting Administration.." message appears for a short while and then disappears - nothing else happens. Some other apps work some don't. Everything VERY slow.

Anyone know what I need to tweak?

---

### Post by finite9 on 2008-04-30
i have exactly the same issue on a newly installed 8.04 amd64 using the alternate CD.  the only admin app that fails for me though is the login window app.  After starting it, the hard drive just goes mental, trying to load it.

---

### Post by togo59 on 2008-04-30
Please let me know if you fix it. Otherwise I am completely screwed.:(

BTW: I installed 8.04 on my Toshiba laptop with no such problems.

---

### Post by thedoorguy on 2008-04-30
Check System > Administration >  System Log > auth.log right after you attempt to open one of the admin applications "tasks" you are having problems with.

Look for a line that contains ":unable to resolve host~" (your host name follows the tildi) If you find it,,, that is probably your problem. It is a bug that is being worked.  See [http://ubuntuforums.org/showthread.php?t=773851](http://ubuntuforums.org/showthread.php?t=773851) for more info.  They suggest a work around but it didn't work for me... the following did....

Goto System > Administration > Network... unlock and goto Host tab of your network connection... if the Alias by IP Address 127.0.1.1 is not your host name .... add a new line using your host name and IP Address 127.0.1.1 then delete the old line.

Worked for me anyway.

Hope this helps.

thedoorguy  aka  Richard

---

### Post by Akt on 2008-04-30
I edited my localhost line, it contained an extra bit of information ".Goodnight" that I had to remove.  I think that was a remnant of a Windows domain I had set up somewhere.  Works fine now.  Thanks for the pointer!

---

### Post by togo59 on 2008-04-30
Many thanks! That worked.:)

---

### Post by finite9 on 2008-04-30
damndest thing happened.  I didnt change anything, but looked at the listed links and then did a tail -f auth.log anf got the following errors, but it worked!!!  Now it just works??  Btw, my 127.0.1.1 was already set to just my hostname.

```
Apr 30 20:12:07 everest sudo: PAM unable to dlopen(/lib/security/pam_smbpass.so)
Apr 30 20:12:07 everest sudo: PAM [error: /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory]
Apr 30 20:12:07 everest sudo: PAM adding faulty module: /lib/security/pam_smbpass.so
Apr 30 20:12:33 everest sudo:   andrew : TTY=unknown ; PWD=/home/andrew ; USER=root ; COMMAND=/usr/sbin/gdmsetup
Apr 30 20:12:33 everest sudo: pam_unix(sudo:session): session opened for user root by (uid=0)
Apr 30 20:12:33 everest sudo: pam_unix(sudo:session): session closed for user root
```

---

### Post by Dyqik on 2008-05-07
Hi,

I just managed to fix the exact same problem (same log errors as finite9) on my newly installed machine by installing the missing libpam-smbpass package.

I now have thinkfinger (fingerprint sudo and login authentication) on my thinkpad!

---

