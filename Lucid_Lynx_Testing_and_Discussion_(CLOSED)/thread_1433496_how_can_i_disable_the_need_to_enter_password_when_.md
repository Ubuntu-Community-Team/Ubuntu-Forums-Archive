---
title: "how can i disable the need to enter password when opening empathy?"
date: 2010-03-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-03-19
every time i open empathy i need to enter a password i canceled it in the past but i can't find it now and i don't want to use pidgin because of its "privacy problem" so if there is a solution or a better multi protocols chat software that would be great and thanks in advance.

---

### Post by meborc on 2010-03-19
> **aviramof said:**
> every time i open empathy i need to enter a password i canceled it in the past but i can't find it now and i don't want to use pidgin because of its "privacy problem" so if there is a solution or a better multi protocols chat software that would be great and thanks in advance.

edit-accounts maybe?!

---

### Post by godhika on 2010-03-19
That might be not the solution you are after but disabling autologin for your desktop session resolves this ;)

---

### Post by aviramof on 2010-03-19
> **meborc said:**
> edit-accounts maybe?!
 
it's has nothing to do with accounts it's just to open the software itself.
 
and i want my autologin i don't see no reason to type in password every time i open my computer when i'm the only user of this computer i'll try uninstall and reinstall empathy maybe then i would be able to do it if not i would uninstall it completly and find my self a better software.

---

### Post by kurros on 2010-03-19
Since you are using autologin, I believe if you set your login keyring password to blank it wont prompt you anymore. 

Applications->Accessories->Passwords and Encryption Keys

right click on the Passwords: login keyring and choose Change Password.

At least I remember doing for my parent's autologin accounts so it wouldn't ask to unlock they keyring for the wireless password. Dont know if that was a special case for network-manager or if the blank password will work elsewhere.

---

### Post by SevenMachines on 2010-03-19
i think adding something like

session optional pam_keyring.so

to /etc/pam.d/gdm-autologin (and logging out and in) does for the network-manager keyring thing on autologin if i remember correctly (unlocking the keyring by default). Obviously, make sure your happy with the zero security implications of this first.

---

### Post by SevenMachines on 2010-03-19
> **SevenMachines said:**
> i think adding something like

session optional pam_keyring.so

to /etc/pam.d/gdm-autologin (and logging out and in) does for the network-manager keyring thing on autologin if i remember correctly (unlocking the keyring by default). Obviously, make sure your happy with the zero security implications of this first.

EDIT: I must be mistaken, doesnt seem to work so totally ignore what i said!!

---

### Post by aviramof on 2010-03-19
> **kurros said:**
> Since you are using autologin, I believe if you set your login keyring password to blank it wont prompt you anymore. 

Applications->Accessories->Passwords and Encryption Keys

right click on the Passwords: login keyring and choose Change Password.



thank you it's working maybe next time i want put any password when i install ubuntu will see if it let's me.

thanks for your help.

---

