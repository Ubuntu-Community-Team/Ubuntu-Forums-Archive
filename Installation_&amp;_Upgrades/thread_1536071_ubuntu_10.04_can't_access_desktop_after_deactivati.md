---
title: "ubuntu 10.04 can't access desktop after deactivating user password for log in"
date: 2010-07-21
forum: Installation &amp; Upgrades
---

### Post by AstroPhysik on 2010-07-21
Hi,
**ubuntu 10.04 can't access desktop after deactivating user password for log in.**

i installed ubuntu studio 64bit, all was fine, and for starting, the user password is now necessary.
But at home i don't want to type every time the user password, so i deactivated it in the Control Center (user needs no password for logging in..)

the next start up, there were various messages, that ubuntu has no writing privileges, and the desktop could not be loaded anymore.
Messages:
> 
1) could not update ICEauthory  file /home/user/ .ICEauthory
2) there is a problem with the configuration server  /usr/lib/libgconf2-4/gconf-sanity-check-2  exited with status 256
3)nautilus could not create following directories:
     /home/user/Desktop
     /home/user/.nautilus

please create this dirs or add writing privileges    // yes i'll do , but how if it froze up...
So i left ubuntu studio AMD64bit behind, and installed the ubuntu 10.04 32Bit alternate.iso 
Same game, i deactivated the need for a password for logging into the desktop, and it froze up again.

..so i left ubuntu 10.04 and installed 9.04 again...;)  No just kidding, lets hunt this f*** bug down.

greetz Astrophysik

---

### Post by davidmohammed on 2010-07-21
... suggest use administrator - login screen to nominate which account you want to automatically login as.

---

### Post by AstroPhysik on 2010-07-21
> **davidmohammed said:**
> ... suggest use administrator - login screen to nominate which account you want to automatically login as.

Ah, you mean, the change as user did cause the problem, although i had to type the PW for the change?
But i'll try it as you mentoin..  

Hmm  i cannot log in anymore, there is the screen for: user   and others.
User freezes, and root or sudo is not known at the login terminal?

thanx AP.

---

### Post by davidmohammed on 2010-07-21
suggest - reinstall.  Next time, dont remove the password for the main administrator account.  Create a new user.  Use that user as the user account to automatically login as via the "login screen" in the administration menu area.

---

### Post by sisco311 on 2010-07-21
> **AstroPhysik said:**
> 
Hmm  i cannot log in anymore, there is the screen for: user   and others.
User freezes, and root or sudo is not known at the login terminal?

thanx AP.

Try to switch to a virtual console (Ctrl+Alt+F2), log in, and remove your user from the  nopasswdlogin group:
```
sudo gpasswd -d **username** nopasswdlogin
```
Switch back to GDM [noparse](Ctrl+Alt+F7 or Ctrl+Alt+F8)[/noparse] and try to log in.

Is your home directory encrypted?

---

### Post by AstroPhysik on 2010-07-22
Thanks Sisco311,
it worked, i can log in again.:popcorn:

@davidmohammed:
also thank you, 
But i'm not shure that this is the propper way.
Maybe i have something  understood wrong. At SUSE there is root and user, 2 accounts.
Here, we have one user account  with the sudo command. (Another user which knows sudo can use it?)
There is no main admin account? Or do i have to put a "main admin user" in a sudo group?


Anyway i can log in and explore Lucid again. Thank you!

But still open is:
**HOW can i deactivate password or skip the Login-Box**, without running in the troubles above?  I want switch on the pc and start directly into the desktop. (is this a new thread?)

greetz AP.

---

### Post by davidmohammed on 2010-07-22
understood - same advice - administrator - login screen

or via the terminal

gdmsetup

---

### Post by sisco311 on 2010-07-22
Hmmm, first, let's try to clear some things. :)

GDM allows any user from the **nopasswdlogin** group to log in without a password. This is a new feature, first introduced in Ubuntu 9.10. You still get a login screen, but when you click your user (or type in your username if the user list is disabled) you are automatically logged in without being prompted for a password. 

For those how are wondering, all the *magic* is done via a [pam]("http://en.wikipedia.org/wiki/Pluggable_Authentication_Modules") rule.

/etc/pam.d/gdm:
```
#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale
**auth    sufficient      pam_succeed_if.so user ingroup nopasswdlogin**
@include common-auth
auth    optional        pam_gnome_keyring.so
@include common-account
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so close
session required        pam_limits.so
@include common-session
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so open
session optional        pam_gnome_keyring.so auto_start
@include common-password

```

This is not the same feature as the automatic login mentioned by davidmohammed. You can configure GDM to automatically log in a user (immediately or after a short period of time). This method does not require any user interaction at the login screen. The computer will boot straight into your user's X session (GUI). You can configure this type of automatic login under System -> Administration -> Login Screen.

Regarding sudo/root. Take a look at the community documentation: [uhelp]community/RootSudo[/uhelp].

The root account is present in Ubuntu, but its password is locked. This means that you can not login in as root directly or use the su command to became root. This is not a problem, since sudo allows the users from the **admin** group to run commands as another user or root without knowing the root password. It prompts for the (admin) user's password.


And once again, is you home directory encrypted? Any type of auto login is incompatible with the encrypted home directory since the password is required at login time to decrypt the home directory and auto login does not allow you to enter a password.

---

### Post by AstroPhysik on 2010-07-22
It's done!

At the Control Center/ Login Screen, there is a field: which user should be loaded automatically.
but non was shown...  so i created an admin, but only the admin was shown in the automatic login field, and not the previous user. So i created user2, and whoala, all three were shown. i selected user1 for auto- login without pwd, deleted user2 from user & groups, and all is working fine.

i guess there is an error in reading the default user, in the selection-field, when only one user exists (after a fresh installation)  but with three users i could select th one i've wanted to. :p

so far so good,
greeetz AP.

---

### Post by AstroPhysik on 2010-07-22
Ah, hi sisco,
i just found out by myself,

well yes, the first dir was encrypted, the new user, i've created has no encryption, and boots direct into the X-Session.

thank you guys:popcorn:

AP

---

### Post by sisco311 on 2010-07-22
You're welcome!

I'm glad you figured it out. :)

---

### Post by AstroPhysik on 2010-07-24
yup, thanks,

afterwards it's clear: The login PW was necessary for the de-cryption of /home.  After attempting to boot directly into the desktop, the Login PW for de-cryption was missing, so 10.04 could not read /home and hung up.

Hmm.. a warning would have been nice at the Groub & Users Admin-Box: At the CheckBox: No PW is needed to login...

greetz AP.

---

