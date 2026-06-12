---
title: "System Program Problem on startup"
date: 2013-08-25
forum: Installation &amp; Upgrades
---

### Post by angel mike on 2013-08-25
I am getting the following message soon after startup - 'System Program Problem'. I have sent the report but can anyone suggest a fix!
 It happened after I deleted my password - which I later retrieved through the Terminal.
 I thought I could do without a password but obviously not !

Thanks Mike

---

### Post by angel mike on 2013-08-25
Solved the problem by removing Apport using the Software centre. It should have been disabled when Ubuntu 12.04 LTE was released anyway.
Mike

---

### Post by ibjsb4 on 2013-08-25
Is there an option in that window to click on to see details?  Are you having any system problems?

---

### Post by deadflowr on 2013-08-25
> **angel mike said:**
> Solved the problem by removing Apport using the Software centre. It should have been disabled when Ubuntu 12.04 LTE was released anyway.
Mike

Prior to 12.04, when the release came out, apport was indeed disabled.
However, when 12.04 came out, they kept apport enabled to help Ubuntu's error tracking
[https://wiki.ubuntu.com/ErrorTracker](https://wiki.ubuntu.com/ErrorTracker)

Though, removing it is an alternative, you can also just simply disable it.
Just open an editor in root on go to /etc/default/apport and change enabled to 0(zero).

And also, even if you never use it, always keep your password.
And never disable it.
Disabling the password can, and almost always does, cause trouble later.

---

