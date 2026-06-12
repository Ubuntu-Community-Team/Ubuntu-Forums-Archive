---
title: "Root PW (I'm sure you get this alot...)"
date: 2005-09-06
forum: Installation &amp; Upgrades
---

### Post by XiroMisho on 2005-09-06
I got a few CD's of Ubuntu and I just finished my install.  For some reason I thought that Ubuntu just used the primary user's password would be the root... but it's not.  I tired entering nothing into the password prompt and still invalid - then also my primary user password - invalid.  

so i'm not sure what to do at the moment.

---

### Post by bored2k on 2005-09-06
Ubuntu = [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by robins_web on 2005-09-06
[QUOTE=XiroMisho]I got a few CD's of Ubuntu and I just finished my install.  For some reason I thought that Ubuntu just used the primary user's password would be the root... but it's not.  I tired entering nothing into the password prompt and still invalid - then also my primary user password - invalid.  

so i'm not sure what to do at the moment.[/QUOTE]
 Ubuntu comes with no password for root.

Open a console and type:
     sudo passwd root<RET>

You'll be prompted for your own password. Enter that, then you'll be prompted for a new password for root.

---

### Post by rafakl on 2005-09-06
Or simply use the command "sudo" before all the operation that require root.

---

