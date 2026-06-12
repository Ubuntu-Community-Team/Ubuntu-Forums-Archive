---
title: "What happened to gnome keyring?"
date: 2010-04-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by x-shaney-x on 2010-04-27
Something I have always hated about new gnome installs is the default keyring password box coming up all the time.
It's something I suffered with when I installed beta 2 but after doing a fresh install with the RC I have not had a single gnome keyring password prompt for ANYTHING.  Not even Evolution or wireless.

The only thing I have done differently this install is NOT to enable auto login because I know that cuts out some of the problems but I should have had at least one prompt from each app that uses it?

---

### Post by jpeddicord on 2010-04-27
> The only thing I have done differently this install is NOT to enable auto login because I know that cuts out some of the problems but I should have had at least one prompt from each app that uses it?That's exactly why. The keyring needs a passphrase to decrypt its content. When you have autologin turned on, it doesn't have any way to decrypt itself. When you sign in with a password, GDM sends it to the keyring daemon.

---

### Post by x-shaney-x on 2010-04-27
Ahh, yes.  I checked seahorse and all the stuff (email accounts, empathy accounts etc) are now listed under login instead of under default as I am used to.

I should have done this all along.

---

