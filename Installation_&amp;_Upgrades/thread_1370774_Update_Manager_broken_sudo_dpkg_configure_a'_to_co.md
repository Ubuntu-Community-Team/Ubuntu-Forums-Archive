---
title: "Update Manager broken sudo dpkg configure a' to correct the problem."
date: 2010-01-02
forum: Installation &amp; Upgrades
---

### Post by jman11 on 2010-01-02
Error messege:

sudo dpkg configure a' to correct the problem.






I used synaptic package manager to install WIne....It stalls on "ttf-mscorefonts-installer (3.0". So, I try update manager and it asked me to restart computer which I do. When I try to re-run synaptic manager I get the above error.

---

### Post by sisco311 on 2010-01-02
Open a terminal (Applications -> Accessories -> Terminal)
and paste the following code into the terminal window:
```
sudo dpkg --configure -a
```
press Enter. You will be prompted for your password, type it and press Enter again. 

NOTE:
When you type your password the terminal doesn't offer any visual feedback.

---

### Post by jman11 on 2010-01-02
I've done this already in terminal. It just recycles and recycles like its not downloading from the website, and I do have a Internet connection.

---

