---
title: "How to get rid of - package &quot;1 not fully installed or removed&quot;"
date: 2012-12-10
forum: Installation &amp; Upgrades
---

### Post by masuch on 2012-12-10
Hi,

I have one package not fully installed because it just hung up within installation process.
I have been trying to remove it , purge it or reinstall it and it always hung.
I put it in hold status but every time when I tried to upgrade any packages it is going to try to install this not fully installed package and of course - hang. So I had/have to always kill this process and run dpkg --configure -a (package) manually ... etc. to install the rest of the packages.

Is there any way how to get rid of of not fully installed package which is not possible to install/reinstall/purge ?

thank you,
kind regards,
M.

P.S. I am interested of solution in terminal.

---

### Post by Frogs Hair on 2012-12-10
What package ?


I had a similar issue with a PPA package recently and I took forever to get into synaptic and finally be rid of it. This was the maintainers mistake. The command dpkg --configure -a would stall at every attempt and reinstalling the package left the apt cache open. It was a catch 22 nightmare! 

If it is the same package I will describe what I tried.

---

### Post by masuch on 2012-12-10
> **Frogs Hair said:**
> What package ?


I had a similar issue with a PPA package recently and I took forever to get into synaptic and finally be rid of it. This was the maintainers mistake. The command dpkg --configure -a would stall at every attempt and reinstalling the package left the apt cache open. It was a catch 22 nightmare! 

If it is the same package I will describe what I tried.

:-)
package rsyslog (I did not mention it intentionally - I wanted to try avoid the discussion about importance of this package :-)
I made "lock" in synaptic for that package and related packages but it does not have influence on it and neither on "apt-get ..." unfortunately. 
I have tried to 
"echo "rsyslog hold" | sudo dpkg --set-selections"
but no success on partly installed package. 
I did not try to 
"dpkg-divert --add --rename --divert file.ori file"
because it has influence only on one file - I need whole package.

dpkg --configure -a is always stall in that package but I killed it and it continues to install the rest of the packages.

So, I basically run out of ideas.

So , last week I have fun with upgrading:
-- always kill that post-install script process in the middle 
and run repeatedly:
dpkg --configure -a
kill process (apt-get or synaptic - depends on from where I am installing)
apt-get upgrade -f
and ...
(I have been thinking of to even write bash script for it - because they are always the same steps :-)

(I am doing it 'by the way' by the same way when I am upgrading ubuntu distribution :-( )

But you are lucky that synaptic worked for you. 
I did not have such luck :-(

So, I made my own compilation and installation (including all dependent libraries) - so software works, but I did not get rid of install it ... 'system' is trying to install that package again and again - even after apt-get clean. 
I do not know what else could I clean up :-?  ... ?

---

### Post by NightsShadeQueen on 2012-12-10
Where does it hang?

I got an issue recently where nothing would install - everything would hang on the exact same point of installation.

I eventually managed to find the exact bash command (ps aux --forest is awesome) that was failing to complete and got it to complete.

---

### Post by newbie-user on 2012-12-10
```
dpkg --purge [package name here]
```

---

### Post by Frogs Hair on 2012-12-10
I had a  different problem but for some strange reason I was able to get synaptic open after running the following command. I had tried every broken package command I could easily find.   ```
sudo rm -r /var/lib/apt/lists/*
```

---

### Post by NightsShadeQueen on 2012-12-10
Try
sudo dpkg --remove -force --force-remove-reinstreq package name
If you're really desperate, from this link: [http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/](http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/)

cd /var/lib/dpkg/info
sudo rm rsyslog.*

sudo dpkg --remove --force-remove-reinstreq rsyslog

---

### Post by masuch on 2012-12-11
Hi, thanks to all of you for help.

dpkg --purge rsyslog # works - did this command just delete /var/lib/dpkg/info/rsyslog.postinst script ?
rm -r /var/lib/apt/lists/* # did not try
rm /var/lib/dpkg/info/*.librelp # works
dpkg --remove -force --force-remove-reinstreq package name # did not try but I beleive it would work either. 

(so ,now I am using rsyslog 7.2.4 version. libee 0.4.1 , libstr 0.1.4 , librelp 1.0.1 with configuration:
./configure --enable-unlimited-select --enable-imdiag --enable-mysql --enable-pgsql --enable-relp --enable-libdbi --enable-extended-tests --enable-mysql-tests --enable-valgrind --enable-rtinst --enable-gnutls  --enable-mail --enable-snmp --enable-diagtools --enable-memcheck --enable-debug --enable-unlimited-select --enable-gssapi-krb5 --enable-omstdout --enable-smcustbindcdr
)

---

