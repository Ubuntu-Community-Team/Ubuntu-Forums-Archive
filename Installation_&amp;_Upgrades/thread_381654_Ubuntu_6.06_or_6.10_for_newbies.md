---
title: "Ubuntu 6.06 or 6.10 for newbies ???"
date: 2007-03-11
forum: Installation &amp; Upgrades
---

### Post by manic34 on 2007-03-11
Hi All,

Could someone please offer me some advice. I am new to Ubuntu and have only recently replaced my working copy of Windows XP with Ubuntu 6.10 and whilst I really like the look and feel of Ubuntu, I am having serious problems. I have been unable to get the 'Add/Remove' tab to work, everytime I try to update or add new packages the connection times out without downloading anything.

Would I be better off with version 6.06 ... does it have less bugs and issues ??

Or, being that I dont have a technical background, would I be better off just sticking to Windows ?  I really hope that someone can help me as Ubuntu looks and feels like a great os.

Any feedback would be greatly appreciated.

Thanks,
Anthony :)

---

### Post by Kateikyoushi on 2007-03-11
The network might be the same with 6.06 as well, all your problems are related to DNS because Add/remove relies on apt-get which does not work for you.

Many people who use ubuntu have or had no tehnical background either, it is different from windows you have to learn some new things but still worth it.

---

### Post by manic34 on 2007-03-11
PLEASE PLEASE PLEASE !!

Can anyone offer me some suggestions how I might fix this problem.  I really dont want to go back to Windows but have no idea how to fix Ubuntu.

---

### Post by DeusEx on 2007-03-11
do you see anything unusual in /var/log/syslog?

in terminal:
```
cat /var/log/syslog
```

---

### Post by manic34 on 2007-03-11
Hi,

None of this means a thing to me but if you can see whats going on please tell me

Thanks> Reading package lists... Done
Building dependency tree
Reading state information... Done
Initializing package states... Done
Building tag database... Done
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg
Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release.gpg
Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Translation-en_US
Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/restricted Translation-en_US
Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/multiverse Translation-en_US
Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Translation-en_US
Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/universe Translation-en_US
Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release.gpg
Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/main Translation-en_US
Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/universe Translation-en_US
Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates/multiverse Translation-en_US
Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out


---

### Post by PilotJLR on 2007-03-11
The issue here is DNS. Could you please post the results of the following:
```

ifconfig -a

```

and also

```

cat /etc/resolv.conf

```

---

