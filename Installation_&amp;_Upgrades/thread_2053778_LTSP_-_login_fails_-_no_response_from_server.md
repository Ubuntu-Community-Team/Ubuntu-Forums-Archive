---
title: "LTSP - login fails - no response from server"
date: 2012-09-06
forum: Installation &amp; Upgrades
---

### Post by fusionp on 2012-09-06
I've just built my first LTSP, and have pxe booted my first client, I receive the login screen, but after putting in my user and password I get "ltsp login no response from server restarting" and I'm presented again with the login portal.

What I've done:
I've enabled password authentication in the ssh config.
I've tested the login account via SSH and can successfully login to the server via a putty session.

I've run the following commands on the server:
sudo ltsp-update-sshkeys
sudo ltsp-update-image

However the issue continues.

Does anyone have any pointers, I've searched but the steps I've tried above are the only fixes I can find and I've already tried them.

thanks

---

### Post by fusionp on 2012-09-06
bump...anyone?

---

### Post by fusionp on 2012-09-06
Anyone in the know?

---

### Post by fusionp on 2012-09-07
Have I posted in the wrong forum here? I'll try the Microsoft forum, they might know.](*,)](*,)](*,)[-o<

---

### Post by viniciusferrao on 2012-10-24
I'm having the exactly same issue.

---

### Post by forkandles on 2012-12-25
The later steps in this link *may* provide a solution:
[http://www.linuxquestions.org/questions/blog/beachboy2-315980/ltsp-setting-up-from-scratch-35204/](http://www.linuxquestions.org/questions/blog/beachboy2-315980/ltsp-setting-up-from-scratch-35204/)

LTSP is great when it works but you need to clear several hurdles first. Believe me, I have been there.

Good luck with your efforts.

---

