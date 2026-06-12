---
title: "Enter Password To Unlock Your Login Keyring"
date: 2010-04-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Uncle Spellbinder on 2010-04-11
Went from 2.6.32-19 to 2.6.32-20. Now I'm getting this popping up on screen any time I boot or restart.


[IMG]http://i42.tinypic.com/wtexz7.jpg[/IMG]

---

### Post by Owen.C93 on 2010-04-11
I think it alows you to connect to wireless. If I turn wireless of it doesn't show up. I've had this for a while though.

---

### Post by Uncle Spellbinder on 2010-04-11
Strange. I had this issue in Alpha 2. No problem in Beta 1. Started up again today. Hope this gets addressed as it's rather annoying.

---

### Post by VMC on 2010-04-11
> **Uncle Spellbinder said:**
> Went from 2.6.32-19 to 2.6.32-20. Now I'm getting this popping up on screen any time I boot or restart.


[IMG]http://i42.tinypic.com/wtexz7.jpg[/IMG]

Read this [**_blog_**]("http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/"), the answer is there if you want to use it.

---

### Post by Uncle Spellbinder on 2010-04-11
> **VMC said:**
> Read this [**_blog_**]("http://davestechsupport.com/blog/2009/01/16/how-to-remove-ubuntus-password-keyring/"), the answer is there if you want to use it.
Thanks for the link, but I don't think that's the route I want to take.

---

### Post by crlang13 on 2010-04-11
I scanned that blog entry, it's similar, but slightly different to the solution I've used in Karmic (which may not apply to Lucid).  open applications > accessories > passwords & encryption keys.  Right click on your default keyring and say change password.  Then, like the blog says, leave the new password field blank and agree with the warnings.

NOW, the nice thing about the password manager app is that you can create many keyrings.  For things like your network passwords where you don't want to be prompted, stick those in your unlocked default keyring.  If there are apps that you want protected, create a second keyring that is protected.  Hope that helps.

---

### Post by nanog on 2010-04-11
[SIZE="4"][COLOR="Blue"][PHP]sudo rm ~/.gnome2/keyrings/login.keyring[/PHP][/COLOR][/SIZE]

---

