---
title: "Installation as administrator"
date: 2015-03-21
forum: Installation &amp; Upgrades
---

### Post by Rex Bouwense on 2015-03-21
My soon to be daughter-in-law has a laptop with Ubuntu 14.04 installed.  The problem is that it was installed with her as Administrator account and to log-in automatically.  I told her that was not a good thing because anyone who had access to the computer would then have administrator priviledges.  Even though I changed the automatic log-in to require a password, it still logs her in automatically.  Short of re-installation is there a way to correct this situation to requiring her to log-in?  I thought of creating a new account for her and deleting the admin account, but wasn't sure of the other things that might be caused by that.  Could she then be given sudo priviledges?  I have no idea how the installation was done.

---

### Post by Lars Noodén on 2015-03-21
> **Rex Bouwense said:**
>   Could she then be given sudo priviledges?  

Full, unfiltered sudo rights actually is "admin" level access.  So if you want her to run an unprivileged account, then create a second account and give that one full privileges by being member of the groups : adm cdrom sudo dip plugdev lpadmin sambashare

Then once you have tested the new account to make sure it can install and remove software and so on you can remove privileges from her account by taking her out of the groups : sudo, admin and adm -- if she is in those groups.  

Sudo, however, is quite flexible and you can provide an in-between level of access if you know of specific programs you would like her to be able to run.

---

### Post by Rex Bouwense on 2015-03-21
Thank you for the response.  Currently there is only one account on her machine.  I do not know how it was installed but it is not a standard account.  It is an administrative account.  To compound matters there is the matter of automatic log-in which I have tried to chage unsuccessfully.  I suppose if I could get rid of the automatic log-in it would solve her dilemma.  On my installs I have always given the user a standard account with sudo privileges.  I just had never seen this before and was unsure how to proceed.

---

### Post by grahammechanical on 2015-03-21
As you say, this is an unusual set up. Normally, a single user would be classed as administrator but would work as a standard user and use their password to authenticate any task that required administrator privileges. In this normal situation having automatic login would not be a risk to security.

I am wondering if someone has enabled the root password. This will show how to disable the root password again. I have no idea if it will solve this.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Regards.

---

### Post by bardo2 on 2015-03-22
OMG, you are correct: This is an unusual and security-wise bad setup. Although your question looks like a marginal one (remove autologon), there is more to be said:

Linux in general is quite good at making a difference among necessary privileges when used in normal circumstances. The installation with only an admin user messed this up. Plenty of configuration files (normally in the scope of the unpriviledged user) have now been modified by the admin and may resist any attempt to be modified from a normal user account. If it was just that, it may be possible to fix this, but the unfortunate effects are scattered all over the place and the time to fix those exceeds the time of a new install to get adjusted to the users needs. Because of that, i would blame the installation screens (they dont warn or otherwise recommend a better setup). A new user usually doesnt know how to make decisions which tend to turn out bad only very much later.

So please reconsider your options:
- reinstall now, possibly losing relevant parts of her configuration
- reinstall when the next system change invites it (like, say when Ubuntu Vivid goes public), thus motivating "the newest best Ubuntu to be used...)
Also a better setup needs different behavioral habits to be incorporated (like using sudo at times when it wasn't required before)

Habits dont come by themselves, there needs to be some sort of training + understanding... Use that time NOW, or she might feel lost in the BETTER setup.
Care about backups? So at least you'll have a place to look up?

If disk space allows it, i would immediately install to a different partition, to have a fallback option ready in case of a (felt) emergency, but use conviction to lead her into using the newer setup whenever possible.

Good luck and dont bother with the details of autologin (which usually resides in Preferences -> Users -> (your user). Those problems *could* be side effects.

---

### Post by deadflowr on 2015-03-22
>  On my installs I have always given the user a standard account with sudo privileges
On Ubuntu--That is and always has been an Administrator account.
A Standard account has no, nor will ever have any, sudo rights.
(Of course an exception is if the sudoers file is manipulated to allow a standard user access to otherwise admin-controlled functions)

Autologin does what it says.
It logs a user in without the need to input the user password.
You can change the password till the cows come home, but until you turn off autologin, it'll keep logging in with asking for a password.
But setting it with autologin does not automatically log the user in with open-root-privileges.
The user still needs to use a password when doing any admin-related action.

This has been my experience, routinely.
This is on Ubuntu, how other desktop environments work would probably be different.

---

