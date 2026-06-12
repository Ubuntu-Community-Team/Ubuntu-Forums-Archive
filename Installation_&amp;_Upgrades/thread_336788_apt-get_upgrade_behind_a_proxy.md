---
title: "apt-get upgrade behind a proxy"
date: 2007-01-12
forum: Installation &amp; Upgrades
---

### Post by afternine on 2007-01-12
Hi!

I'm having troubles with upgrading of the packages on my Eggy, I'm behind a proxy, so I have set int /etc/apt/apt.conf:
root@alex-kubuntu:/etc/apt# cat apt.conf
Acquire::http::Proxy "http://hitko.hit.si:8080/";
root@alex-kubuntu:/etc/apt#         

I can do apt-get update and it reads successfully all the package headers:
root@alex-kubuntu:/etc/apt# apt-get update
Get:1 [http://main.archive.ubuntu.com](http://main.archive.ubuntu.com) edgy Release.gpg [191B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg [191B]
Ign [http://main.archive.ubuntu.com](http://main.archive.ubuntu.com) edgy/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US
Get:3 [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com) edgy-updates Release.gpg [191B]
Ign [http://main.archive.ubuntu.com](http://main.archive.ubuntu.com) edgy/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Translation-en_US
Ign [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com) edgy-updates/main Translation-en_US
Ign [http://main.archive.ubuntu.com](http://main.archive.ubuntu.com) edgy/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Translation-en_US
Ign [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com) edgy-updates/restricted Translation-en_US
Get:4 [http://main.archive.ubuntu.com](http://main.archive.ubuntu.com) edgy-updates Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release
Get:5 [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com) edgy-backports Release.gpg [191B]
Hit [http://main.archive.ubuntu.com](http://main.archive.ubuntu.com) edgy Release
Ign [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com) edgy-backports/main Translation-en_US
Hit [http://main.archive.ubuntu.com](http://main.archive.ubuntu.com) edgy-updates Release
Ign [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com) edgy-backports/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
Hit [http://main.archive.ubuntu.com](http://main.archive.ubuntu.com) edgy/main Packages
Ign [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com) edgy-backports/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/restricted Packages
Ign [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com) edgy-backports/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/universe Packages
Hit [http://main.archive.ubuntu.com](http://main.archive.ubuntu.com) edgy/restricted Packages
Hit [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com) edgy-updates Release
Hit [http://main.archive.ubuntu.com](http://main.archive.ubuntu.com) edgy/main Sources
Hit [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com) edgy-backports Release
Hit [http://main.archive.ubuntu.com](http://main.archive.ubuntu.com) edgy/restricted Sources
Hit [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com) edgy-updates/main Packages
Hit [http://main.archive.ubuntu.com](http://main.archive.ubuntu.com) edgy/universe Packages
Hit [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com) edgy-updates/restricted Packages
Hit [http://main.archive.ubuntu.com](http://main.archive.ubuntu.com) edgy-updates/main Sources
Hit [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com) edgy-backports/main Packages
Hit [http://main.archive.ubuntu.com](http://main.archive.ubuntu.com) edgy-updates/restricted Sources
Hit [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com) edgy-backports/restricted Packages
Hit [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com) edgy-backports/universe Packages
Hit [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com) edgy-backports/multiverse Packages
Fetched 955B in 2s (400B/s)
Reading package lists... Done



However, when I do a apt-get upgrade I get:

root@alex-kubuntu:/etc/apt# apt-get -u upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  avahi-daemon dbus gnupg info katapult kate kcontrol kdebase-bin kdebase-data
  kdebase-kio-plugins kdepasswd kdeprint kdesktop kdm kfind khelpcenter kicker
  klipper kmenuedit konqueror konqueror-nsplugins konsole kopete ksmserver
  ksplash ksysguard ksysguardd kwin language-pack-en language-pack-kde-en
  libavahi-client3 libavahi-common-data libavahi-common3
  libavahi-compat-libdnssd1 libavahi-core4 libavahi-qt3-1 libdbus-1-3
  libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libimlib2 libkonq4
  libmagick++9c2a libmagick9 libpng12-0 libpq4 libruby1.8 libxine1
  linux-headers-2.6.17-10 linux-headers-2.6.17-10-generic
  linux-image-2.6.17-10-generic linux-libc-dev
  linux-restricted-modules-2.6.17-10-generic linux-restricted-modules-common
  openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-impress
  openoffice.org-java-common openoffice.org-kde openoffice.org-math
  openoffice.org-style-crystal openoffice.org-style-default
  openoffice.org-writer python-uno ruby1.8 screen tar ttf-opensymbol w3m
  wlassistant x11-common xbase-clients xorg xserver-xorg xserver-xorg-core
  xserver-xorg-input-all xserver-xorg-video-all xutils
82 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 130MB/170MB of archives.
After unpacking 4235kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com) edgy-updates/main x11-common 1:7.1.1ubuntu6.2 [291kB]
Err [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com) edgy-updates/main x11-common 1:7.1.1ubuntu6.2
  Error reading from server - read (104 Connection reset by peer)
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main tar 1.15.91-2ubuntu0.3 [346kB]
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main tar 1.15.91-2ubuntu0.3
  Error reading from server - read (104 Connection reset by peer)
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libpng12-0 1.2.8rel-5.1ubuntu0.1 [114kB]
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main libpng12-0 1.2.8rel-5.1ubuntu0.1
  Error reading from server - read (104 Connection reset by peer)
Get:4 [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com) edgy-updates/main language-pack-en 1:6.10+20061130 [357kB]
Err [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com) edgy-updates/main language-pack-en 1:6.10+20061130
  Error reading from server - read (104 Connection reset by peer)
Get:5 [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com) edgy-updates/main language-pack-kde-en 1:6.10+20061130 [336kB]
Err [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com) edgy-updates/main language-pack-kde-en 1:6.10+20061130
  Error reading from server - read (104 Connection reset by peer)
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main screen 4.0.2-4.1ubuntu5.6.10 [584kB]
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main screen 4.0.2-4.1ubuntu5.6.10
  Error reading from server - read (104 Connection reset by peer)
..  trimmed.. ..
Failed to fetch [http://si.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-math_2.0.4-0ubuntu4_i386.deb](http://si.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-math_2.0.4-0ubuntu4_i386.deb)  Error reading from server - read (104 Connection reset by peer)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
root@alex-kubuntu:/etc/apt# 


I can sucessfully browse to [http://si.archive.ubuntu.com](http://si.archive.ubuntu.com), the page opens fine.
I have also manually set the proxy in the networking section of the system settings.

What else can I do to get the upgrades??

Bye

---

### Post by bapoumba on 2007-01-12
hello,
at work i also am behind a proxy, and i get apt or aptitude to work. I cannot use the automatic proxy, though (the one i am using for browsing for ex), so i use the previous squid proxy, that the admins kept running.
What kind of proxy is yours ? (ISA proxy can be difficult to handle)

One more thing : in my apt.conf, I have {}, I am not sure this is mandatory (well, I have not checked the syntax):
```
ACQUIRE { 
http::proxy "http://proxy.blabla.fr:3128"
};

```

---

### Post by afternine on 2007-01-12
Hi!

I believe it is (this is from the top of my head) a squid 2.4 or something like that). I guess our network admin has some kind of traffic shaping in place and that cuts me out of internet for the upgrades. How did you manage to get past the squid?

Bye

---

### Post by bapoumba on 2007-01-13
Hello,

I could not do the upgrades with the "automatic" proxy (not sure about the English translation for it, they use HAVP to filter out many things) which is a .pac http proxy. I contacted the network admins, all debian gurus ;)
They just recommended me to use the former squid proxy, on the 3128 port, that they kept alive for some reason. And it worked.

BTW, they do not allow IM (jabber or IRC for ex), bittorent (well, this is a 10-100 Go connection, could be quite convenient to dl ISO files). I can understand why, this is a university network, I cannot imagine what the network would look like if the 25 000+ students were on msn or other kind of networks all day long. So when I want to dl big ISO files, I just ask them, they do it for me in less than 5 mins and that's it.
So I would say, just ask your network admins, they may not be aware that you use Ubuntu, and that some rules are preventing you from doing upgrades.

Do you need an authentication ? You can check this link for apt.conf :
[http://www.die.net/doc/linux/man/man5/apt.conf.5.html]("http://www.die.net/doc/linux/man/man5/apt.conf.5.html")

Apt relies on this file only, to access internet.
Cheers !

---

### Post by afternine on 2007-01-13
Thanx for the tips, I guess I'll have to go to our network admin to see if he can "let me through" the proxy.

Have a nice day!

---

### Post by jonnybecker on 2007-01-28
Hi,

I'm also having troubles with upgrading of the packages at a friend (at home it works great). How can I tell if we are behind a proxy?

Is it possible, that the ports apt uses have to be 'opend' on his router?
Which ports does apt use?

Thanks
Jonny

---

### Post by bapoumba on 2007-01-28
> **jonnybecker said:**
> How can I tell if we are behind a proxy?

Do you have to change anything to your browser settings or to your environment to have access to internet ?

---

### Post by jonnybecker on 2007-01-28
Hi,

thanks for the quick reply.

> Do you have to change anything to your browser settings or to your environment to have access to internet ?No

Cheers
Jonny

---

### Post by bapoumba on 2007-01-28
Then I would guess, if access to internet via a browser is fine, that it has to do with the router.

---

### Post by jonnybecker on 2007-01-28
Any hints? Ports that have to opened?

Cheers
Jonny

---

### Post by bapoumba on 2007-01-28
Please do a search on this forum with the router type. Give it in here also, so that we can check it out ;)

---

### Post by jonnybecker on 2007-01-28
it's a d-link g664. Couldn't find it in the forums. i'll search a little more and tell you my result.

Thanks for your help.

---

