---
title: "What is the point of automatic login in Lucid?"
date: 2010-04-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Sennaista on 2010-04-16
In Karmic I had my computer on automatic login and that was it, I only had to put my password in only when I was doing admin work. In Lucid though, if I use automatic login I will be presented with another dialogue just after login which asks me for my password because the keyring hasn't been unlocked. I can either dismiss it or attempt entering my password, which, if entered wrongly, will send me back to the login screen! 

I really don't understand the logic behind this. If I'm using automatic login then it's for a reason; speed and I'm happy to sacrifice some security to get it. Another thing is, why should the keyring get unlocked at login? I have no passwords in there that needs unlocking at login, like wireless password and such.

If someone can be bothered to explain the logic, I shall be eternally grateful. :)

---

### Post by aviramof on 2010-04-16
i too don't understand the problems with automatic login in lucid if i set keyring as unsafe 
meaning with no password it works but not always for instance empathy sometimes don't recognize my accounts
until i restart because of problems connecting to keyring password engine or something in seashore.  

and not to mention this bug i reported not long ago:
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/540775](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/540775)

---

### Post by Killigrew on 2010-04-16
Hi

perhaps it get fixed till release, if not, open /etc/pam.d/gdm-autologin and change it to this:
```

#%PAM-1.0
auth    requisite       pam_nologin.so
auth    required        pam_env.so readenv=1
auth    required        pam_env.so readenv=1 envfile=/etc/default/locale
auth    required        pam_permit.so
**auth    optional        pam_gnome_keyring.so**
@include common-account
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so close
session required        pam_limits.so
**session optional        pam_gnome_keyring.so auto_start**
@include common-session
session [success=ok ignore=ignore module_unknown=ignore default=bad] pam_selinux.so open
@include common-password

```greetings

---

### Post by Owen.C93 on 2010-04-16
I doesn't unlock your computer, but gives it access to password for wireless and other things. You can disable it like me in "startup applications".

---

### Post by QwUo173Hy on 2010-04-16
I get a wireless connection straight away. THEN I'm asked for the password to unlock the keyring. I just dismiss it - what do I need it for!?

---

### Post by lean on 2010-04-17
Can you post the details of the dialog? The keyring dialog should show which app that are trying to open the keyring.

---

### Post by uRock on 2010-04-17
> **Sennaista said:**
> In Karmic I had my computer on automatic login and that was it, I only had to put my password in only when I was doing admin work. In Lucid though, if I use automatic login I will be presented with another dialogue just after login which asks me for my password because the keyring hasn't been unlocked. I can either dismiss it or attempt entering my password, which, if entered wrongly, will send me back to the login screen! 

I really don't understand the logic behind this. If I'm using automatic login then it's for a reason; speed and I'm happy to sacrifice some security to get it. Another thing is, why should the keyring get unlocked at login? I have no passwords in there that needs unlocking at login, like wireless password and such.

If someone can be bothered to explain the logic, I shall be eternally grateful. :)

If you have keyring unlocking your Network Manager, then fixing will be easy.

---

### Post by uRock on 2010-04-17
> **jarlath said:**
> I get a wireless connection straight away. THEN I'm asked for the password to unlock the keyring. I just dismiss it - what do I need it for!?

You must have set it for something at some time.Once you find out what it is for, then we could get it to stop popping up.

---

### Post by rogerdean on 2010-04-17
I've got it too. Very annoying. Could it be UbuntuOne?

---

### Post by cariboo on 2010-04-17
If you go to Applications->Accessories->Passwords & Encryption Keys, you will see that the password is set to login, by default, just change it to a null password, and you won't have to type your keyring password again.

Please search this sub-forum, as this seems to be about the third time this question has been asked.

---

### Post by rogerdean on 2010-04-17
thanks cariboo, i've set the password as blank for now. of course this isn't ideal because then all my login details are stored in unencrypted text somewhere.

presumably this isn't the intended behaviour for 10.4, but i've looked at the other threads and can't find a reference to this as something that is going to be fixed. does anyone know?

cheers
Roger

---

### Post by mcduck on 2010-04-17
> **rogerdean said:**
> thanks cariboo, i've set the password as blank for now. of course this isn't ideal because then all my login details are stored in unencrypted text somewhere.

presumably this isn't the intended behaviour for 10.4, but i've looked at the other threads and can't find a reference to this as something that is going to be fixed. does anyone know?

cheers
Roger

If you don't use a login password then it makes absolutely no difference if the Password Manager stores your passwords encrypted or not.

So yes, this is the intended behavior in 9.10, just like it has been in all previous Ubuntu versions.

And I doubt that it wold be fixed, I can't really even see any way how it could be fixed, what is the point of encrypting something if you don't then require a password to decrypt it? (If you use a login password, and it's set to same as the keyring password, the keyring will be unlocked automatically as you have already confirmed that you are you and not somebody else when you input your password in the login screen)

---

### Post by rogerdean on 2010-04-17
Thanks for the reply. Did you mean to say 9.10 or 10.4? We're talking about 10.4 here...

I guess the question is, 'if i select auto login, should the default behaviour be that i'm asked for a password immediately after boot?' I don't remember this as normal on previous versions.

I'm not sure I understand your first point - why is it ok for my passwords to be in a plain text file? Even if autologin automatically unlocks my keyring on boot I still don't want those passwords able to be copied, do I?

Cheers
Roger

---

### Post by QwUo173Hy on 2010-04-17
> **uRock said:**
> You must have set it for something at some time.Once you find out what it is for, then we could get it to stop popping up.
Thanks uRock. But the only entry in Password & Encryption Keys is for 'Login'.

---

### Post by QwUo173Hy on 2010-04-17
I see that 'Login' actually expands to cover Ubuntu One, CouchDB, imap, jabber, irc and several others.

The only change since Karmic seems to be that wireless starts up independent of that. So I wasn't getting it for no reason. Thanks for your help.

---

### Post by mcduck on 2010-04-17
> **rogerdean said:**
> Thanks for the reply. Did you mean to say 9.10 or 10.4? We're talking about 10.4 here...

I guess the question is, 'if i select auto login, should the default behaviour be that i'm asked for a password immediately after boot?' I don't remember this as normal on previous versions.

I'm not sure I understand your first point - why is it ok for my passwords to be in a plain text file? Even if autologin automatically unlocks my keyring on boot I still don't want those passwords able to be copied, do I?

Cheers
Roger

sorry, I of course meant to say 10.04... :D

And yes, this has been the behavior in all Ubuntu versions.

The point about encrypting your passwords or not if you use automatic login is that if you don't require a login password to access your user account, then anybody can just log in as you and access your passwords. So it makes no difference if the passwords aren't encrypted. If you can access your user account and passwords without any authentication, then everybody else is able to do the same.

---

### Post by chris.olsen on 2010-04-17
I am running into the same issue, except for I am unable to enter anything into the password prompt, which then essentially locks up my system.

---

