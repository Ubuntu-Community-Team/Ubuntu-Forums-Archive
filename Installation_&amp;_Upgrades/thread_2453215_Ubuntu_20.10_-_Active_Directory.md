---
title: "Ubuntu 20.10 - Active Directory"
date: 2020-11-05
forum: Installation &amp; Upgrades
---

### Post by torfig2 on 2020-11-05
Hello all,

I just installed Ubuntu 20.10 on a test machine at work.
I was interested in trying out link to Active Directory in the setup but couldn't.
It asks for domain admin but I do not have an admin account on that particular domain, but I have an account that is allowed to join computers to it.
Decided to try to use that, but since it has a "." (like super.user) in it I could not use that account.
Isn't that a bit strange?
I have never had any issues joining a machine to the domain using that user account before.
Followed some instruction last spring when I joined a Ubuntu 20.04 to the exact same domain using [these instructions]("https://computingforgeeks.com/join-ubuntu-debian-to-active-directory-ad-domain/") I believe.

I was really excited when I read about this new feature in 20.10 but it seems like I cannot use it using that user at the moment.

Does anybody in here know why it asks for domain admin and why I cannot have a . in my username?

Thanks,
Torfi

---

### Post by aromo2 on 2020-11-05
So, what is the output of:
```
$ sudo realm join -U super.user [example.com]("http://example.com")
```

---

### Post by torfig2 on 2020-11-06
It joined the computer to the domain.
I can see it appear in Active Directory.
However, I am not able to logon as a domain user.
I tried username, username@domain, e-mail address and I also created an enterprise login under users.
Then I could see the user at the login window but I always get a wrong password error.

---

