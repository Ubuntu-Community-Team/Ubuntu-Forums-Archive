---
title: "&quot;Enter Password for Default Keyring to Unlock&quot;"
date: 2008-10-28
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by kestal on 2008-10-28
**Why?**

I mean, why does this happen? How can I avoid it? I do not want to type in ANY passwords going into Ubuntu (but I wish to avoid going through root). So is there any way to have an automatic login AND automatic unlock?

I prefer using Network Manager over WICD but with WICD.. this problem never occurred. I know, it isn't a 'problem' but it is problematic for me as I wish to turn on my laptop and go straight into Ubuntu 8.10 without having to type in a password. (even if it IS just to access the internet).
[B]
It...[/B]
- is set to connect automatically
- is set as a system setting.


**I tried to**

@ include common-pamkeyring

but it did nothing.

I tried a few other things, but then realized that it was with libpam-keyring and it is no longer used in Intrepid, but a libpam-gnome-keyring.

How do I solve this? My user password and unlock password are the same, if that helps.

**Note:**
- I realize, this is for security. But currently I am more so hoping for convenience.

---

### Post by psyke83 on 2008-10-28
On a default installation, the keyring will unlock without any prompt.

There are a few possible reason why you're experiencing this issue:
[LIST=1]
[*]You configured automatic login via GDM. In this case you need to manually unlock the key;
[*]You performed a partial upgrade and/or some configuration files didn't update properly, so the libpam integration isn't working as intended;
[*]Your default keyring password is different from your user's password. They need to be identical in order for the keyring to automatically unlock. You can change it via Seahorse.
[/LIST]

---

### Post by kestal on 2008-10-28
> **psyke83 said:**
> [*]You configured automatic login via GDM. In this case you need to manually unlock the key;

There is the problem. 

**[[COLOR="DeepSkyBlue"]X[/COLOR]]** **I have an automatic login**. I want to keep my automatic login. 
**[[COLOR="DeepSkyBlue"]X[/COLOR]]** **I do not want to type in ANY passwords.** Aside from hindered security, this is reasonable request.
**[[COLOR="DeepSkyBlue"]X[/COLOR]]** **I want to keep Network Manager** (over WICD, which doesn't have this problem)

So what........ because I set an automatic login **[COLOR="Red"]([/COLOR][COLOR="Gray"]the idea is to have less passwords to type in[/COLOR][COLOR="Red"])[/COLOR]**, Gnome-keyring plagues me with .... *drumrolls* .... another password to fill in? Isn't that a bit redundant?

any way around this?

---

### Post by kestal on 2008-10-28
Anyone?

---

### Post by yellerKat on 2008-10-28
Have you created an auto connection in NM?

---

### Post by kestal on 2008-10-28
Yes, I right clicked nm-applet, went to Edit Connections -> Wireless -> MyConnection, then ticked Connect Automatically.

When I cold boot, the message appears.

---

### Post by forger on 2008-10-28
Have you ever changed your user account password (from System > Administration > Users and Groups)?

Seems like you have this bug:
[https://bugs.edge.launchpad.net/ubuntu/+source/shadow/+bug/162710](https://bugs.edge.launchpad.net/ubuntu/+source/shadow/+bug/162710)

---

### Post by kestal on 2008-10-28
This is an out of the box install. The passwords are the same and untouched from the first time I entered them.

But if thats the case, any way to restore that to default so I can test it out?

---

### Post by psyke83 on 2008-10-28
> **kestal said:**
> There is the problem. 

**[[COLOR="DeepSkyBlue"]X[/COLOR]]** **I have an automatic login**. I want to keep my automatic login. 
**[[COLOR="DeepSkyBlue"]X[/COLOR]]** **I do not want to type in ANY passwords.** Aside from hindered security, this is reasonable request.
**[[COLOR="DeepSkyBlue"]X[/COLOR]]** **I want to keep Network Manager** (over WICD, which doesn't have this problem)

So what........ because I set an automatic login **[COLOR="Red"]([/COLOR][COLOR="Gray"]the idea is to have less passwords to type in[/COLOR][COLOR="Red"])[/COLOR]**, Gnome-keyring plagues me with .... *drumrolls* .... another password to fill in? Isn't that a bit redundant?

any way around this?

Using Seahorse, change the unlock password for the default keyring to an empty password. NetworkManager will now automatically connect without prompting. 

Of course, your keyring will be unsecured - but that's not such a big deal if you have automatic login configured, is it?

---

### Post by forger on 2008-10-28
In that case, seems likely that it's this bug:
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/137247](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/137247)
"libpam-keyring broken on autologins"

I'm not sure how to provide a fix or workaround for this, sorry, but as a hint I think you can resolve this if you find a proper way (or order?) to load pam modules for keyring in /etc/pam.d/gdm-autologin ?

perhaps something similar to /etc/pam.d/gdm ?
> @include common-auth
auth    optional        pam_gnome_keyring.so
@include common-account
session required        pam_limits.so
@include common-session
session optional        pam_gnome_keyring.so auto_start
@include common-password


edit: psyke83's solution seems much easier :)

---

### Post by kestal on 2008-10-28
> **psyke83 said:**
> Using Seahorse, change the unlock password for the default keyring to an empty password. NetworkManager will now automatically connect without prompting. 

Of course, your keyring will be unsecured - but that's not such a big deal if you have automatic login configured, is it?

hmm. in Seahorse, there is only one password being stores, and that is my router password. my Router password is different than my login password and my unlock password.

There is nothing under personal/trusted/other keys.  The one under password, when I check properties and ask to 'Show Password' its the router password. When I clear it, I have to then enter THAT password every time, ontop of Unlock..

What am I missing? :|

Also, when I go through preferences and see the password keyrings, and change the login/default to blank (unsafe), it says access denied. Can't do it through Sudo as it takes the roots passwords (haven't touched root yet, dont want to).

---

### Post by psyke83 on 2008-10-28
> **kestal said:**
> hmm. in Seahorse, there is only one password being stores, and that is my router password. my Router password is different than my login password and my unlock password.

There is nothing under personal/trusted/other keys.  The one under password, when I check properties and ask to 'Show Password' its the router password. When I clear it, I have to then enter THAT password every time, ontop of Unlock..

What am I missing? :|

Also, when I go through preferences and see the password keyrings, and change the login/default to blank (unsafe), it says access denied. Can't do it through Sudo as it takes the roots passwords (haven't touched root yet, dont want to).

You probably received the "access denied" error because you didn't enter the correct "old" password (which is likely to be your current user password).

If you can't figure it out, just delete the entire "default" keyring, then re-create it with a blank password.

I have a system configured to automatically login via GDM, and NM connects to the wireless network automatically (once I removed the password from the default keyring).

---

### Post by kestal on 2008-10-28
worked! thanks!

---

