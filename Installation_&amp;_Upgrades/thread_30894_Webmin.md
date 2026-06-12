---
title: "Webmin"
date: 2005-04-30
forum: Installation &amp; Upgrades
---

### Post by fractalvibes on 2005-04-30
I downloaded and installed the webmin package today, but when I go to [https://localhost:10000](https://localhost:10000) and try to login, it does not like the username/password I use when doing sudo su...

And when I do su root, it does not like the pw there either.....but if I have alread done the sudo su and logged in, it lets me su root just fine.  So evidently I never set a root password during Ubuntu install???  Rather confused....I wrote down the machine name, username, and password when I installed Ubuntu, but perhaps they do not apply to the root?  Or did Ubuntu by default not let me define a root username/password?

Help!

fv

---

### Post by d0nk on 2005-04-30
sudo allows you to execute root commands with your user password.  su needs a root password.  If you want to set a root password (there isnt one by default in ubuntu), just do sudo passwd and enter a password for root.

I know some people here will say not to, but its up to you.  Personally, i do it since i was used to using root, and not typing sudo for every command that needs root.

---

### Post by SFN on 2005-04-30
Do

```
/usr/share/webmin/changepass.pl /etc/webmin root newpassword
```

Replace "newpassword" with what you want the root password to be.

---

### Post by fractalvibes on 2005-04-30
Ah - ok - so I wasn't stupid about knowing the root password!

Thanks!!!!

Also thanks for the correct path to changepass.pl!  The webmin.com FAQ lists it
as /usr/local/webmin-1.200/changepass.pl /etc/webmin admin foo
which is perhaps outdated.

Can get into webmin just fine now.

I truly appreciate the assistance, and hope someday to be knowledgable enough to provide such good help to other new users!

(I can help with sql!)

fv

---

