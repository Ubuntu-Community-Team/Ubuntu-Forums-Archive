---
title: "Reinstalling on a multi-user system."
date: 2010-08-12
forum: Installation &amp; Upgrades
---

### Post by uRock on 2010-08-12
To give a scenario, I have an account for myself, my wife, and my daughter;
1. uRock
2. DragonLady
3. LilFireball

On install I have no problem adding myself back to the system, but when try to add the other users who already have a home folder but no logon, I get an error saying the other accounts are already in use, but they still have no way to log on. 

How do I get them back online?

Thanks,
uRock

---

### Post by Sanjeevtrip on 2010-08-12
how you are adding the users?

mv the existing homefolders, then add the users see if works.
you can mv the homefolders back and chown them.

---

### Post by uRock on 2010-08-12
> **Sanjeevtrip said:**
> how you are adding the users?

mv the existing homefolders, then add the users see if works.
you can mv the homefolders back and chown them.
I am using System> Administration> Users & Groups

I will give you suggestion a try.

Thanks,
uRock

---

### Post by mick222 on 2010-08-13
I've got the same problem reinstalled after breaking my system ,but my previous home folder has only read permissions i tried adding it but still cant alter the files . how can i change the permissions filesystem is mounted at / with seperate /home partition.
  Hope I'm not hijacking the thread.

---

### Post by uRock on 2010-08-13
> **mick222 said:**
> I've got the same problem reinstalled after breaking my system ,but my previous home folder has only read permissions i tried adding it but still cant alter the files . how can i change the permissions filesystem is mounted at / with seperate /home partition.
  Hope I'm not hijacking the thread.
Not hijacking at all. Running ```
sudo chown -R username ~/home/username
``` should make the folder yours. You may want to run man chown first and look at the syntax they show.

---

### Post by mick222 on 2010-08-13
thx for the reply will try it.

---

