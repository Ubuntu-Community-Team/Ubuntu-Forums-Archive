---
title: "Installing krb5"
date: 2005-05-05
forum: Installation &amp; Upgrades
---

### Post by joshpjones99 on 2005-05-05
Sorry if this is a ignorant question but I am a Windows network admin who is also a Linux N00B.  We are a 100% MS house and I am trying to find a Linux distro to start using on my desktops to help keep costs and viruses down.  

I am working on getting the ability to log in to my ubuntu with my 2003AD credentials.  Every 'how to' and article on the subject says to use Kerberos5 (which I fully agree with)  It would appear I need krb5-user ??? but when I try to apt-get it or the GUI software install in ubuntu (forget its name but its a really nice interface)  I get a no package found are you looking for krb5-doc.

I am sure I am just doing something wrong but I have run every search I can think of here and through google (web) and google (groups) and they all say that

apt-get install krb5-user

should install the software.

Any help is greatly thanked.


Thanks in advance.

Joshua Jones.

---

### Post by Xian on 2005-05-05
[QUOTE=joshpjones99]Every 'how to' and article on the subject says to use Kerberos5 (which I fully agree with)  It would appear I need krb5-user ??? but when I try to apt-get it or the GUI software install in ubuntu (forget its name but its a really nice interface)  I get a no package found are you looking for krb5-doc.[/QUOTE]
You just need to add the universe repos to pull packages from since that is where krb5-user resides. Your /etc/apt/sources.list should contain the lines listed below. Note the 'universe' tag on the end. Just append that to your own config.

```
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted universe
```

---

