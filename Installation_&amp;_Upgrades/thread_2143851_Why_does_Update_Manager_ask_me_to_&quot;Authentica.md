---
title: "Why does Update Manager ask me to &quot;Authenticate&quot; ?"
date: 2013-05-10
forum: Installation &amp; Upgrades
---

### Post by Stef700 on 2013-05-10
Usually I just click on "Install Updates" when Update Manager runs - but today it is asking me to "Authenticate" so it wants the root password.
(The box actually says: "To install or remove software, you need to authenticate. An application is attempting to perform an action that requires privileges. Authentication is required to perform this action"

Is this normal? i.e does Update Manager sometimes requre the root passward and other times not?

Thanks, Stef
(Ubuntu 12.04 64bit)

---

### Post by darkod on 2013-05-10
Yes, it will ask you to authenticate often during updates because it needs to change system files. If your user has sudo rights you simply enter your own password.

That is quite normal from update manager.

---

### Post by kostkon on 2013-05-10
It usually asks you for your password when it is about to install new packages (sometimes updated versions of packages have new dependencies and need to pull some additional packages from the repositories).

---

### Post by Stef700 on 2013-05-10
Great thanks :)

---

