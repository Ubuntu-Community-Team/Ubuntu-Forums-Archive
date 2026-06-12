---
title: "Ubuntu 12.04 LTS and Samba4 full release"
date: 2012-12-13
forum: Installation &amp; Upgrades
---

### Post by karolo on 2012-12-13
Hi,

Wondering does anyone know if Ubuntu 12.04 LTS server will get the full release version of Samba4 server in the repository now that the Samba team have released it?

I see that it currently has Samba4 alpha18 which is a bit buggy and missing a lot of elements.

Thanks in advance

---

### Post by ikt on 2012-12-15
Also interested in this.

---

### Post by Merrattic on 2012-12-15
If you really want it:

[http://wiki.samba.org/index.php/Samba4/HOWTO](http://wiki.samba.org/index.php/Samba4/HOWTO)

---

### Post by ikt on 2012-12-15
> **Merrattic said:**
> If you really want it:

[http://wiki.samba.org/index.php/Samba4/HOWTO](http://wiki.samba.org/index.php/Samba4/HOWTO)

I really want it, but I really really don't want to compile :p

Waiting for it to be packaged and included in Ubuntu.

---

### Post by tkman26 on 2012-12-19
Unless I have done something wrong, even when you compile the latest code the version still ends up being 
root@30://usr/local/samba/sbin# samba -V
Version 4.0.0alpha18
I suspect the alpha18 is the latest.

---

### Post by ikt on 2012-12-20
> **tkman26 said:**
> Unless I have done something wrong, even when you compile the latest code the version still ends up being 
root@30://usr/local/samba/sbin# samba -V
Version 4.0.0alpha18
I suspect the alpha18 is the latest.

I don't think so.

[http://wiki.samba.org/index.php/Samba4#Previous_Releases](http://wiki.samba.org/index.php/Samba4#Previous_Releases)

They celebrated 4.0 the other day

[http://www.samba.org/samba/history/samba-4.0.0.html](http://www.samba.org/samba/history/samba-4.0.0.html)

"This is is the first stable release of Samba 4.0."

I assume a stable release isn't an alpha.

---

### Post by friedmar on 2012-12-21
I to would like to have samba native included in 12.04 not the very old alpha18.

As I workaround I use  

deb [http://ppa.launchpad.net/kernevil/samba4/ubuntu](http://ppa.launchpad.net/kernevil/samba4/ubuntu) precise main
deb-src [http://ppa.launchpad.net/kernevil/samba4/ubuntu](http://ppa.launchpad.net/kernevil/samba4/ubuntu) precise main

Works great but there is a problem with winbind/getent etc.

---

### Post by Garyx on 2013-01-02
I´m also waiting on the official repo's to catch up. Anyone know when they will have the stable 4.0 up and ready.

---

### Post by joeprice on 2013-01-06
I am also interested when I will be able to get Samba 4 full release in a package. Will it be made available in 12.04 LTS? or will I need to use 12.10?

Thanks for any replies

---

### Post by friedmar on 2013-01-07
Hi UBUNTU Officials,

could you please answer our Question? LTS means for me also to update alpha or beta packages if they went RTM. Samb4 is important! I do not want to install 13.04 to get it!

---

### Post by friedmar on 2013-01-07
> **joeprice said:**
> I am also interested when I will be able to get Samba 4 full release in a package. Will it be made available in 12.04 LTS? or will I need to use 12.10?

Thanks for any replies
My guess is 13.04!

---

### Post by Garyx on 2013-01-10
Anyone checked the reps for 13.04 yet if they have samba 4 final?

---

### Post by Cheesemill on 2013-01-10
You can check for yourself, but it appears so.

[http://packages.ubuntu.com/search?keywords=samba4&searchon=names&exact=1&suite=all&section=all](http://packages.ubuntu.com/search?keywords=samba4&searchon=names&exact=1&suite=all&section=all)

---

### Post by gavfranc on 2013-01-16
Well I have asked that question via Ubuntu paid support service. 
Disappointingly their response was not good. 

Read below a transcript...

Dear Gavin Francis,

Your case # ********: Authentification has been updated.

Comment added:
Samba4 (stable) is not currently planned to be made available for the 12.04 LTS and I don't expect that to change.  I cannot assist with Samab4 as it is not supported by Canonical.  It is important for me to point out that most Samba4 setups still used OpenLDAP and Kerberos.

We do have a local partner that could help evaluate your options and set up your systems.
Fleten.net.   Kjetil Fleten, CEO.   [email]kjetil@fleten.net[/email]
Fleten is both an Ubuntu partner and a Zentyal partner.   Zentyal is an Ubuntu based (and supported through them) system that creates an easy to use small business server (with roaming profiles, authentication, etc).  

Please let me know how you choose to proceed.

Please click on the link below to view this case on the online web portal:
[url]https://login.ubuntu.com/+saml/init/salesforce/***************

Should you have any questions, additional comments or information, or attachments related to this case, we ask you to please add them via the link above.

Thank you,

Canonical Support & Services

.............................

Well thats just great, not only have we been waiting for this for 10 years but now they are not going to release it on lts very short sited. 
To add insult to injury, their suggested partner is in Denmark and I live in Norway. Doh!

---

### Post by joeprice on 2013-01-28
Gavfranc,

Thanks for posting that information, at least we now know what our options are. I will have a look at Zentyal.

Joe Price

---

### Post by erikf on 2013-02-06
> **gavfranc said:**
> Well I have asked that question via Ubuntu paid support service. 
Disappointingly their response was not good. 

Read below a transcript...

Dear Gavin Francis,

Your case # ********: Authentification has been updated.

Comment added:
Samba4 (stable) is not currently planned to be made available for the 12.04 LTS and I don't expect that to change.  I cannot assist with Samab4 as it is not supported by Canonical.  It is important for me to point out that most Samba4 setups still used OpenLDAP and Kerberos.

We do have a local partner that could help evaluate your options and set up your systems.
Fleten.net.   Kjetil Fleten, CEO.   [email]kjetil@fleten.net[/email]
Fleten is both an Ubuntu partner and a Zentyal partner.   Zentyal is an Ubuntu based (and supported through them) system that creates an easy to use small business server (with roaming profiles, authentication, etc).  

Please let me know how you choose to proceed.

Please click on the link below to view this case on the online web portal:
[url]https://login.ubuntu.com/+saml/init/salesforce/***************

Should you have any questions, additional comments or information, or attachments related to this case, we ask you to please add them via the link above.

Thank you,

Canonical Support & Services

.............................

Well thats just great, not only have we been waiting for this for 10 years but now they are not going to release it on lts very short sited. 
To add insult to injury, their suggested partner is in Denmark and I live in Norway. Doh!

This is the worst response ever. Don't they realize that the Samba4 final package might be the most important package for Ubuntu Server that has come out in a long time!

Still running Samba4 Alpha18 but desperately want to upgrade to final!

---

### Post by jolae on 2013-02-26
[https://launchpad.net/~wagungs/+archive/samba4](https://launchpad.net/~wagungs/+archive/samba4)

Have you tried this unofficial repository?

---

### Post by friedmar on 2013-04-22
It looks like Ubuntu is ignoring Samba4! Actual is samba4 4.0.5. 13.04 is as of today still on 4.0.0 from december 2012!!!

---

### Post by Roswebnet on 2013-04-23
Yep. I get bad feels about it. With samba4.0.5 Ubuntu should looks like a "normal" windows server (2003). But as far as i know there are still many complications about samba4. I have one :)

---

### Post by CMDRSweeper on 2013-04-28
I feel the same way, no proper Samba 4 Repos for autoupdating.
So I guess for now I am stuck compiling my own Samba 4 which can be a pain in the long run :(

---

### Post by Roswebnet on 2013-05-16
With this tutorial:
[http://iabsis.com/EN/article/35-2/Samba4-installation](http://iabsis.com/EN/article/35-2/Samba4-installation)
Samba 4.0.1 development version is now available on Ubuntu 12.04.2.

---

