---
title: "What are &quot;backports&quot; ??"
date: 2005-05-31
forum: Installation &amp; Upgrades
---

### Post by pappo on 2005-05-31
I have the instructions on how to add the backports repositories to my sources.list, but I really don't know what "backports" are ?

Are they just more applications that are in the un-stable category ?

Thanks

Pappo

---

### Post by grim42 on 2005-05-31
From Wikipedia...

> Backporting is the action of taking a certain software modification (patch) and applying it to an older version of the software than it was initially created for. Example:

Software v2.0 has a security vulnerability that is fixed by changing the text 'is_insecure' to 'is_secure'. The same security hole exists in Software v1.0 but there the text is called 'is_notsecure'. By taking the modification that fixes Software v2.0 and changing it so that it applies to Software v1.0 one has effectively backported the fix.


From backports.ubuntuforums.org...

> About Ubuntu Backports
Ubuntu Linux is a great distribution, but falls short in the desktop realm to Gentoo and Fedora Core. Why? Once a stable version is released, no new software updates are accepted. I subscribe to the view that a distribution can be both stable and up-to-date, so I've taken it into my own hands to recompile newer packages from Hoary and Debian Sid for Warty.

Ubuntu backports include newer software that is not in the official frozen release for which only bug-fixes and security updates are released. Ie. No newer versions are added for the particular release.

---

### Post by pappo on 2005-06-01
grim42

Thanks for the answer.

pappo

---

### Post by az on 2005-06-01
Perhaps to further clarify the situation, one needs to understand the nature of open source software.

Instead of there being one version of the operating system (for example, there is only one Windows XP, in some sense) there are many versions of all the different pieces.

The wonderful part of open source software is that you have the choice of using whatever software works for you.  There are usually many ways of doing the same task.

With this advantage comes the dissadvantage of increased complexity.  You cannot have a very powerful and flexible operating system and have it be simle for everyday use.  The more an operating system is simplified, the less power and flexibility you get.

That is why linux is generally available in the form of distributions.  People who make these distributuns work out the problems of interconnecting the various packages before making the operating system available.  If you stick to the distributions' packages, you avoid problems.

So, if you wans something other than the prebuilt packages that your distribution makes available, you have to compile it for yourself, or find someone who compiled a compatible version for you.  You lose the simplicity.

---

