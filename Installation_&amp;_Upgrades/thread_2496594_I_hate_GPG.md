---
title: "I hate GPG"
date: 2024-04-05
forum: Installation &amp; Upgrades
---

### Post by georgy-trubetkoy-ru74 on 2024-04-05
Recenly I knew that apt add-key was deprecated and in new Ubuntu version it will be replaced by GPG.
I started to study GPG and I realized what developers are user-unfriendly monkeys. The GPG is too complex, and here are not simple guides for it.
But I just want to install key for apt unofficial repository, no more. Why this is was made so complex? For what? For security? You don't need to know from where I took my packages.
I'm just a user, not IT-security specialist. And due of situations like this almost 90% users using only official repositories (and also they don't know about capability to install unofficial repo), and I can see the nginx 1.14 and 1.18, postgresql 14 everywhere.
Thanks a lot.
The main idea of Linux about what? This is about if I learn somethin 10-years ago, I can use it now. Or maybe this is because the developers too young and they're not have 10-year experience?
And, of course, I could learn GPG instead of write this messege, of course.

---

### Post by MAFoElffen on 2024-04-05
If you trust that repo, then why try to install a GPG key for it, when you could just add trusted=yes to the sources.list.d entry? If you do that, no key is needed right?

---

### Post by Holger_Gehrke on 2024-04-07
'apt-key' being deprecated doesn't mean you have to learn and use gpg. It means that instead of having one keyring-file (/etc/apt/trusted.gpg) which you administer using apt-key you should use the directory /etc/apt/trusted.gpg.d/ and simply drop the key files (either binary .gpg files or ascii-armored .asc files) with a descriptive name into that directory. For PPAs on launchpad 'apt-add-repository --ppa ...' does this automatically. For other repositories you will have to do this manually. So the management of keys turns from a job for a special program that understands the format of a special file into a simple file management task. You only need to use gpg if you want to do something advanced and unusual - like for example create a key of your own for setting up your own repository.

Holger

---

### Post by ActionParsnip on 2024-04-08
Is there a question here or just a rant?

---

