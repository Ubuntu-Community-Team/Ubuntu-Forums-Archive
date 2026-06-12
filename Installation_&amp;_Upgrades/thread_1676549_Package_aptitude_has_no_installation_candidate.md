---
title: "Package aptitude has no installation candidate"
date: 2011-01-27
forum: Installation &amp; Upgrades
---

### Post by bobnw on 2011-01-27
I am trying to install Webmin on a VPS server.  I am using and identical version of Ubuntu on my laptop.  Both systems use Ubuntu 10.04 on AMD64,  but I am using SSH only for the VPS system, and Gnome on the laptop.   When I tried to install Webmin using the Webmin web site instructions I hit a dead end of "Package libnet-ssleay-perl has no installation candidate.
  
I had already installed Webmin on the laptop using a method from another post on the Ubuntu forems.  It used the following command to install the dependices: 

   # aptitude -y install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime
   libio-pty-perl  libmd5-perl apt-show-versions libapt-pkg-per

When I enter this command on the VPS system I got "aptitude command not found ",  and when I try
 # apt-get install aptitude I get 

                # Package aptitude has no installation candidate

 I tried  # apt-get udate,  and then # apt-get upgrade and then #apt-get install aptitude,  as suggested in another post,  but this did not help.

I copied /etc/apt/source.list from the laptop to the VPS,  but still get the same error,  no installation candidate for aptitude.

There must be a way to set up Webmin on the VPS because it works the exact same system on the laptop.

Thanks in advance for any suggestions.

---

