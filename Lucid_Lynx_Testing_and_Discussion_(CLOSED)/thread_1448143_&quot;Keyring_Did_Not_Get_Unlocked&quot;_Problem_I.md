---
title: "&quot;Keyring Did Not Get Unlocked&quot; Problem In 10.04"
date: 2010-04-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by tomcatjosh on 2010-04-06
I got Ubuntu 10.04, But after this update i seem to be having a problem: Every time I Log On, I Get The Message "Please Unlock The Login Keyring""The Login Keyring Did Not Get Unlocked When You Logged On'
Does anyone know a fix? 
Thanks,
Josh

---

### Post by philinux on 2010-04-06
Moved to lucid testing forum.

---

### Post by Golf_a_Little on 2010-04-06
I too had this problem and found this solution. You need to set the keyring password to a null. Try this - Applications - Accessories - Passwords and Encryption Keys.  Right click on the highlighted line "Passwords:login". Click the "Change Password". Then set the new password to a blank (null).

---

### Post by Killigrew on 2010-04-07
that is unsave because than, your passwords will be saved without encryption.

instead look at your /etc/pam.d/gdm-autologin file, it should look like this:
```

#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale
auth    required        pam_permit.so
auth    optional        pam_gnome_keyring.so
@include common-account
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so close
session required        pam_limits.so
session optional        pam_gnome_keyring.so auto_start
@include common-session
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so open
@include common-password
```greetings

---

### Post by mrdoob on 2010-04-10
Hopefully they fix that. I installed Beta 2 today on a computer I use as server. I usually control it from VNC and it won't connect to the wireless without unlocking the keyring, which means I can't restart the machine without having a screen/keyboard plugged :/

---

### Post by _uli_ on 2010-04-20
I have the same problem. 

Editing gdm-autologin, as Killigrew suggested, didn't fix it: Instead of the keyring asking for a password, it is now the network manager asking. 

The situation is similar to what mrdoob wrote: My machine also connects to a wireless network at boot. I use autologon so I don't have to enter a password to login.

With Karmic this worked, with Lucid (Beta2, all updates since) it doesn't. Any more ideas are welcome.

---

### Post by Erlander on 2010-04-21
I had this problem too after I had a look at Ubuntu-One.

In System/Preferences/Startup Applications I removed it and all is well now.

---

### Post by bangmalley on 2010-04-24
> **Golf_a_Little said:**
> I too had this problem and found this solution. You need to set the keyring password to a null. Try this - Applications - Accessories - Passwords and Encryption Keys.  Right click on the highlighted line "Passwords:login". Click the "Change Password". Then set the new password to a blank (null).

This will cause empathy refuse to add account.

---

### Post by Podex on 2010-04-24
Is there already a bugreport on this? Because I have the same problem.

---

