---
title: "Enter password for default keyring to unlock"
date: 2009-10-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by erikla2002 on 2009-10-08
I recently installed Karmic and every time I boot I get an annoying popup window saying Enter password for default keyring to unlock. The application XXX wants access to the default keyring but it is locked. First the application was Empathy but then I uninstalled it and it complained about some other application instead. 
I googled some but all threads are related to the Ntework manger in Ubuntu 6.X or so...

---

### Post by meborc on 2009-10-08
> **erikla2002 said:**
> I recently installed Karmic and every time I boot I get an annoying popup window saying Enter password for default keyring to unlock. The application XXX wants access to the default keyring but it is locked. First the application was Empathy but then I uninstalled it and it complained about some other application instead. 
I googled some but all threads are related to the Ntework manger in Ubuntu 6.X or so...

this happened to me too when i had both ubuntu and kubuntu-desktop installed... as i did a fresh install of ubuntu beta, i can't advise you on how to get rid of that annoyance ;)

---

### Post by berthiggins on 2009-10-08
do you by any chance have auto login enabled?

---

### Post by anders_c_ on 2009-10-08
have you uninstalled the entire telepathy framework? or only empathy? i think its telepathy mission-control that asks for password.
[https://bugs.launchpad.net/ubuntu/karmic/+source/indicator-applet/+bug/437065](https://bugs.launchpad.net/ubuntu/karmic/+source/indicator-applet/+bug/437065)

---

### Post by dro0g on 2009-10-08
> **erikla2002 said:**
> I recently installed Karmic and every time I boot I get an annoying popup window saying Enter password for default keyring to unlock. The application XXX wants access to the default keyring but it is locked. First the application was Empathy but then I uninstalled it and it complained about some other application instead. 
I googled some but all threads are related to the Ntework manger in Ubuntu 6.X or so...

For some inexplicable reason the default keyring password still doesn't automatically sync with the user password after a password change. If you go into Application -> Accessories -> Passwords and Encryption Keys, then right-click on the Passwords folder and select Change Password, Set the password to be the same as your login password and then it should stop prompting. If that doesn't work you may need to modify PAM so it will use the login password to unlock the keyring, however I think it's set that way by default now.

---

### Post by erikla2002 on 2009-10-08
> **berthiggins said:**
> do you by any chance have auto login enabled?


Yes. I changed the password accrding to the last post. Will see if that works on next reboot. Thanks for the answers.

---

### Post by VMC on 2009-10-08
Try moving ~/home/.gnome/keyring somewhere and see if that changes things. You can always bring it back. logout and log back in.

---

### Post by scradock on 2009-10-08
> **VMC said:**
> Try moving ~/home/.gnome/keyring somewhere and see if that changes things. You can always bring it back. logout and log back in.
This happens to me - NetworkManager is asking for its wifi secret, and the default keyring needs to be unlocked to get it. I tried VMC's idea, which left NM itself asking me for its wifi secret instead of the key to unlock the default keyring. 

So I put the default.keyring back in /home/sc/.gnome2/keyrings, and noticed next time I logged in that there is a little checkbox under the space for the password saying "Unlock default keyring when I log in", or somesuch. I checked it, and logged in without the annoying popup.

That's been bothering me for weeks - thanks for the clues!

---

### Post by erikla2002 on 2009-10-09
I still have problems when I boot the computer. The application that needs to access the keyring is 'Do' /user/bin/mono

I moved the default and default.keyring from /home/.gnome2/keyrings to another folder and that didnt help.

---

### Post by _sAm_ on 2009-10-11
Same problem here, even after changing the password it ask for it when I reboot.

---

### Post by mcduck on 2009-10-11
Are you using automatic login?

If yes, the only option is to remove the keyring password (which means storing your keys and passwords unprotected). The keyring is unlocked automatically only when the keyring password is same as your login password and you use normal login.

Here's how to change/remove keyring password:

1.Open the keyring manager (Applications/Accessories/Passwords and Encryption Keys)

2. Go to Passwords-tab

3. Right-click the "Passwords:login"-keyring & select "Change Password"

Now you can change the keyring password. If you use normal login set the password to same as your login password to unlock the keyring automatically. If you use automatic login leave the new password fields empty to remove the keyring password.

---

### Post by 16sinker on 2009-10-11
Thank you MCDuck. That worked for me-finally. By leaving the "new password" choice blank I no longer have to provide my password to unlock the keyring when I reboot. I use auto login to speedup boot time and it was really aggravating to be challenged for that same password to unlock the keyring. I understand this is unsafe security wise, but this is a project machine only and I don't keep any important data on it.:)


> **mcduck said:**
> Are you using automatic login?

If yes, the only option is to remove the keyring password (which means storing your keys and passwords unprotected). The keyring is unlocked automatically only when the keyring password is same as your login password and you use normal login.

Here's how to change/remove keyring password:

1.Open the keyring manager (Applications/Accessories/Passwords and Encryption Keys)

2. Go to Passwords-tab

3. Right-click the "Passwords:login"-keyring & select "Change Password"

Now you can change the keyring password. If you use normal login set the password to same as your login password to unlock the keyring automatically. If you use automatic login leave the new password fields empty to remove the keyring password.

---

### Post by magneze on 2009-10-12
Thanks for the tips. I recently changed my login password and this message kept coming up to enter the old password in the keyring! Really annoying.

I was looking for the place to change it - Accessories really isn't the right place for this. The System menu feels like a better home for this sort of thing.

When login password is changed then the keyring needs to also be updated..

Is this changing in Karmic? Little details like this really make a difference..

---

