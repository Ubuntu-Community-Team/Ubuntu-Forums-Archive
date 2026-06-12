---
title: "Creating a new user"
date: 2010-04-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ukblacknight on 2010-04-07
I wanted to create an account for my girlfriend on my Lucid install for when I'm away.  However, once I've created the account, I get an "Authorisation Error" when trying to log in, and then the account becomes disabled.

Using example data, this is what I did:

Entered name "Joe Blogs", which gave me a default short name of "joeb", which I changed using the dropdown list as "joe".

I then manually entered the password, "hunter2" and then the confirmation password "hunter2".  The user is then created, and I close the Users & Groups window.

The user "Joe Blogs" then appears in the shut-down applet on the panel under "Switch from tom" (me).

Even if I restart, I'm unable to log into the account, it says authorisation error, and then when I go into my own account and administer the new account, it says that it's disabled, and gives me the option to re-enable it.

Also, if I go to switch user using the previously mentioned shutdown-applet, I can no longer get back to my own account!  As the authorisation fails on the new account, there is no option to get back, and therefore must reboot in order to get back to my account.

Anyone else had similar experiences? Or know of a way to create a new user?

---

### Post by ubername on 2010-04-07
I have the same problem. I think I saw something saying it was a bug in passwd, but I can't remember where I saw that.

Haven't been able to solve it, but interestingly I have installed squid since then. The install process obviously creates a user called 'squid', as this now shows up in the user list at logon. I  will wait for user management to get sorted before I raise a bug for this (if it still is a problem).

---

