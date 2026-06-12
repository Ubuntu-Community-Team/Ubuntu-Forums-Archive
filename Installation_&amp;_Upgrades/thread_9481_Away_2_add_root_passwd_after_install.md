---
title: "Away 2 add root passwd after install"
date: 2004-12-29
forum: Installation &amp; Upgrades
---

### Post by LatterDaySaint on 2004-12-29
Does anybody know how to add root passwd to Ubuntu after installation

---

### Post by rbran100 on 2004-12-29
Just create any user you want to then add root privledges.  There are plenty of tutorials for that, i think you should have no problem finding them.  Why do you need a root account?

You know that "sudo -s" will log you in as sudo root?

---

### Post by tokemaster on 2004-12-29
[QUOTE=LatterDaySaint]Does anybody know how to add root passwd to Ubuntu after installation[/QUOTE]

1, $ sudo passwd root
2. Computer -> System Configuration -> Login Screen Setup
Login Screen Setup
Security Tab -> Options -> Allow root to login with GDM (Checked)

---

### Post by LatterDaySaint on 2004-12-30
Thanks fellows ,The reason I wanted a root account Is I installed KDE ect ,and found I could not use certain tools like lisa in control panel ect with out root account, so it seemed,    or can I use sudo with Kde as well ,Im still picking up on all the sudo commands. .Any help will be good help. Thankyou ,Jason.

---

