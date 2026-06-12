---
title: "Can't install slapd - Broken package"
date: 2010-10-06
forum: Installation &amp; Upgrades
---

### Post by luvshines on 2010-10-06
Can't install slapd (OpenLDAP) server on my laptop running Ubuntu 10.04 (lucid)
Gives broken package error

```
sudo apt-get install slapd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  slapd: Depends: libldap-2.4-2 (= 2.4.21-0ubuntu5.2) but 2.4.21-0ubuntu5.3 is to be installed
E: Broken packages
```

ldap-utils and libldap are already there
```
dpkg -l | egrep "libldap|ldap-utils"
ii  ldap-utils                            2.4.21-0ubuntu5.3                               OpenLDAP utilities
ii  libldap-2.4-2                         2.4.21-0ubuntu5.3                               OpenLDAP libraries
```

Can't figure out how to resolve this. Also tried updating the repo
**Even --fix-broken won't work. Ubuntu software center and Synaptic also complain**

HELP PLZ!!!

---

### Post by luvshines on 2010-10-06
Still stumped, hence bumped

Ne Ubuntu dpkg Guru out there ??

---

### Post by luvshines on 2010-10-07
New Day, New Bump !! :P

Still not solved. Any suggestions ??

---

### Post by sikander3786 on 2010-10-07
Simply did you try aptitude?

```
sudo aptitude install slapd
```

---

### Post by luvshines on 2010-10-07
This is what aptitude says:

```
sudo aptitude install slapd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages are BROKEN:
  slapd 
The following NEW packages will be installed:
  libdb4.7{a} 
The following packages will be REMOVED:
  auth-client-config{u} ca-certificates-java{u} ktorrent-data{u} libaccess-bridge-java{u} libaccess-bridge-java-jni{u} libao2{u} libepub0{u} libflac++6{u} libglademm-2.4-1c2a{u} 
  libibus-qt1{u} libkonq5-templates{u} liblastfm0{u} libmsn0.3{u} libqca2-plugin-ossl{u} libqtscript4-core{u} libqtscript4-network{u} libqtscript4-sql{u} libqtscript4-xml{u} 
  libsubtitleeditor0{u} libtag-extras1{u} libxml++2.6-2{u} libzip1{u} mplayer-skins{u} pinentry-gtk2{u} python-qt4-dbus{u} 
0 packages upgraded, 2 newly installed, 25 to remove and 1 not upgraded.
Need to get 2,192kB of archives. After unpacking 16.1MB will be freed.
The following packages have unmet dependencies:
  slapd: Depends: libldap-2.4-2 (= 2.4.21-0ubuntu5) but 2.4.21-0ubuntu5.3 is installed.
The following actions will resolve these dependencies:

Downgrade the following packages:
ldap-utils [2.4.21-0ubuntu5.3 (now) -> 2.4.21-0ubuntu5 (lucid)]
libldap-2.4-2 [2.4.21-0ubuntu5.3 (now) -> 2.4.21-0ubuntu5 (lucid)]

Score is 52

Accept this solution? [Y/n/q/?] q
```

Is it that the slapd that is being installed is some previous version and not latest ??
**Can't figure out why it says broken**

---

### Post by luvshines on 2010-10-07
Found this bug reporting some similar issues:
[https://bugs.launchpad.net/ubuntu/+source/openldap2.3/+bug/321689](https://bugs.launchpad.net/ubuntu/+source/openldap2.3/+bug/321689)

It says removing libldap and then reinstalling it solved it.

When I try to remove libldap it reports that it will uninstall 360 other packages.
How can I downgrade it safely without disturbing other packages

---

### Post by luvshines on 2010-10-07
Whoopieee...!! :guitar:

Was finally able to resolve it. Did a lot of jugglery with the software source list - removed/added some, checked/unchecked some and then it worked like a charm

I'll try to see if I can point to the exact source which resolved it.

[B]It's sad that my queries are not being answered in this forum :(
I have to resolve all of them on my own

But I'll continue to post and resolve other ppl's issues[/B] :KS

---

### Post by sikander3786 on 2010-10-07
You should have accepted the solution from aptitude and you should have been ok. Sometimes there are missing dependencies and aptitude works better with the resolution.

> It's sad that my queries are not being answered in this forum
I have to resolve all of them on my own

I posted in the morning and then waited for quite some time, at least 1 hour, you were online at that time but didn't post back the output of my suggestion. Now I have got some time and you have already solved it. What can we do more than that? :-)

---

### Post by luvshines on 2010-10-07
> **sikander3786 said:**
> You should have accepted the solution from aptitude and you should have been ok. Sometimes there are missing dependencies and aptitude works better with the resolution.



I posted in the morning and then waited for quite some time, at least 1 hour, you were online at that time but didn't post back the output of my suggestion. Now I have got some time and you have already solved it. What can we do more than that? :-)

I would have have humbly accepted aptitude's solution if it had ever said that slapd will be installed.
What is said was:
[B]The following packages are BROKEN:
  slapd 
The following NEW packages will be installed:
  libdb4.7{a}[/B]

It never said slapd will be installed, only libdb was being installed, loads of others removed and 2 of them downgraded
Since that is what I didn't like, I didn't say 'yes' to aptitude and **[COLOR="Red"]will still hold on to the belief that 'my queries are not being answered'[/COLOR]**
Let's see, I am sure there will be many more to come from my side. Maybe some of us here can prove me wrong

---

