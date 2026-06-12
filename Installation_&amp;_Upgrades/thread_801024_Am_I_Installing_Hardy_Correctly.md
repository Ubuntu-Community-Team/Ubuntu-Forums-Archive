---
title: "Am I Installing Hardy Correctly?"
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by Jenga-kun on 2008-05-20
I've installed Hardy Heron 7 times now and I've had the same problem every time. You can read my previous thread to see what that problem is: [http://ubuntuforums.org/showthread.php?p=4982599#post4982599](http://ubuntuforums.org/showthread.php?p=4982599#post4982599)

My question now is whether or not I'm even installing it correctly. I've recorded my installation process and uploaded it onto youtube here: [http://www.youtube.com/watch?v=S7_nekiw_Xo](http://www.youtube.com/watch?v=S7_nekiw_Xo)

It's only 7 minutes long since I only recorded the important steps. I'd really appreciate it if someone would watch my video and help me. Thanks a lot.

---

### Post by PmDematagoda on 2008-05-20
When you are trying login, try doing this:-
1) Press Options.
2) Press Sessions.
3) Select GNOME fail-safe.
4) Login.

See if that would allow you to login.

---

### Post by VMC on 2008-05-20
> **Jenga-kun said:**
> I've installed Hardy Heron 7 times now and I've had the same problem every time. You can read my previous thread to see what that problem is: [http://ubuntuforums.org/showthread.php?p=4982599#post4982599](http://ubuntuforums.org/showthread.php?p=4982599#post4982599)

My question now is whether or not I'm even installing it correctly. I've recorded my installation process and uploaded it onto youtube here: [http://www.youtube.com/watch?v=S7_nekiw_Xo](http://www.youtube.com/watch?v=S7_nekiw_Xo)

It's only 7 minutes long since I only recorded the important steps. I'd really appreciate it if someone would watch my video and help me. Thanks a lot.

I watched most of the video. My question is did you do the CTRL+ALT+F1 to get another login prompt and type you password there? See if maybe your password is wrong.

Also output fdisk -l . Check fstab and make sure it matches. You could also try the "recovery mode" . Hit ESC right when you see the 3 second count down.

---

### Post by Jenga-kun on 2008-05-20
> **PmDematagoda said:**
> When you are trying login, try doing this:-
1) Press Options.
2) Press Sessions.
3) Select GNOME fail-safe.
4) Login.

See if that would allow you to login.

This worked but it's the only way I can get in. How can I fix this?

---

### Post by PmDematagoda on 2008-05-20
Try making a new user and then see if you can login to the account under a normal GNOME session.

---

### Post by Jenga-kun on 2008-05-20
> **PmDematagoda said:**
> Try making a new user and then see if you can login to the account under a normal GNOME session.

Didn't work either.

---

