---
title: "xfce install in edgy - not working."
date: 2007-11-05
forum: Installation &amp; Upgrades
---

### Post by mavicdog on 2007-11-05
Once upon a time I had xubuntu installed and removed it due to some lacking functionality. now that 4.4 is out I want to try it again. I am using kubuntu edgy currently. I tried to reinstall several ways. 1) Xubuntu-desktop via apt and 2) adept, 3) with xfce installer and xfce4 only via apt. In all cases I get a blank desktop with no panel and no mouse click options. I have tried uninstalling and reinstalling - no change. This seems to be a config problem where the appropriate files are not located.....how do I fix this?

I have search and found logs of this problem - those solutions did not work for me. thanks for helping.
S.

---

### Post by zvacet on 2007-11-05
[http://www.psychocats.net/ubuntu/xubuntu]("http://www.psychocats.net/ubuntu/xubuntu")

---

### Post by mavicdog on 2007-11-05
Hmmm....same result. I figured it would be since I had done this already but I repeated it as per the instructions on the page, for the sake of being thorough. thanks though - other ideas? maybe related to getting kdm to run the correct desktop?

---

### Post by mavicdog on 2007-11-06
Just realized this may not be the best category to post this in. reposting to desktop environments. Moderators: feel free to move/remove this.

---

### Post by creeco on 2007-11-06
I have a couple non technical solutions for you:

1: If you dare, try upgrading to gutsy gibbon (7.10). That might solve you problem.

2: Download the Xubuntu 7.10 live CD and boot from it.

3: Reinstall Ubuntu (any version) and try installing XFCE again.

---

### Post by Netor on 2007-11-18
hey mavicdog I had the same problem when installed xfce and killed the panels.
the reason this is still happening is because of sessions being saved in xfce.

try deleting all files that start with Thunar or Xfce in ~/.cache/sessions
try this without login in to X. meaning switch terminals (ie Ctrl + Alt + F1) login with user name and password, then delete those files (remember cd to change directories and rm to remove files) after logout (exit) then switch back to X (Ctrl + Alt + F7) and login again.

let me know if it worked for you or not...it worked for me and gave me a fresh desktop next login.

---

### Post by mavicdog on 2007-12-10
sorry for the big lag to follow-up.

thanks netor. I'll give this a shot. will post outcome.

Creeco - I did upgrade to gutsy (i had to anyway) - no change after reinstalling xfce.

---

