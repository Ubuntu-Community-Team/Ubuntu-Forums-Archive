---
title: "After upgrade to 13.04 system crashes at xubuntu desktop..."
date: 2013-05-07
forum: Installation &amp; Upgrades
---

### Post by twgray on 2013-05-07
Xubuntu 64-bit, after upgrade to 13.04, returns to login screen after bringing up Xubuntu desktop.  After I enter password, Xubuntu desktop comes up and starts loading apps from some previous session (not the last session I ran and I'm not sure how to stop it from doing that), and then immediately goes back to the login screen.  Syslog says there was a segfault in xfce, but nothing else.  

So, 2 questions:  What key xfce files should I delete and reinstall, or just reinstall to hopefully overwrite the corrupted image, and
                           How do I stop Xubuntu from loading a previous session?  As I mentioned above, the session it is loading is not the last session used.

Thanks in advance.

Oh, by the way, I can boot into an Enlightenment session successfully.  Who knew Enlightenment would end up being the more stable one?

---

### Post by Toz on 2013-05-07
> **twgray said:**
> Xubuntu 64-bit, after upgrade to 13.04, returns to login screen after bringing up Xubuntu desktop.  After I enter password, Xubuntu desktop comes up and starts loading apps from some previous session (not the last session I ran and I'm not sure how to stop it from doing that),
From either the working Enlightenment session or from a console login (Ctrl+Alt+F1), delete the files in **$HOME/.cache/sessions**. This will stop the loading of previously saved session apps.
> and then immediately goes back to the login screen.  Syslog says there was a segfault in xfce, but nothing else.  
Can you post back the exact wording in the message? You might also find some more relevant information in the **$HOME/.xsession-errors** (or **$HOME/.xsession-errors.old** if you log in with another X session like Enlightenment to view the file.

---

### Post by twgray on 2013-05-07
Thanks for the info...I am away from that machine until later today but will post more log info when I get back to it.

---

### Post by twgray on 2013-05-07
Well, it seems that removing the ~/.cache/sessions files solved the problem.  As I said, the session it was loading was not a previous session I recognized so perhaps one of the files in .cache/sessions got corrupted and was causing the return to login screen.  But all working great now.  Thanks for the help.

---

### Post by wybo2 on 2013-11-09
> **twgray said:**
> Well, it seems that removing the ~/.cache/sessions files solved the problem.  As I said, the session it was loading was not a previous session I recognized so perhaps one of the files in .cache/sessions got corrupted and was causing the return to login screen.  But all working great now.  Thanks for the help.

I have this problem after upgrading to 13.10 and removing  ~/.cache/sessions helped, but only temporarily. After the next login I got the same problem again. 
I finally solved it by editing (as root) /etc/rc.local and adding:

   ```
rm -rf /home/myhomedir/.cache/sessions
```

Not really nice of course, but at least I can now wait for the real solution without this daily frustration.

---

### Post by Toz on 2013-11-09
> **wybo2 said:**
> I have this problem after upgrading to 13.10 and removing  ~/.cache/sessions helped, but only temporarily. After the next login I got the same problem again. 
I finally solved it by editing (as root) /etc/rc.local and adding:

   ```
rm -rf /home/myhomedir/.cache/sessions
```

Not really nice of course, but at least I can now wait for the real solution without this daily frustration.

Hello @wybo2 and welcome to the forums. 

Sessions are saved if during logout, you check the "Save session for future logins" checkbox or if "Settings Manager -> Session and Startup -> General tab -> Automatically save session on logout" is checked.

---

