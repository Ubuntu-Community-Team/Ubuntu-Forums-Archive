---
title: "unattended-upgrades doesn't upgrade some packages from allowed origin"
date: 2024-04-28
forum: Installation &amp; Upgrades
---

### Post by ygoe on 2024-04-28
Hello,

I have installed PHP from an external PPA and .NET from Microsoft's repository. Both of them should be upgraded automatically, so I added them to the existing unattended-upgrades configuration. It worked for the PHP packages as with all other security upgrades like libc or the kernel, but .NET will still be ignored. Why?

Here's my changes to the file /etc/apt/apt.conf.d/50unattended-upgrades:

Unattended-Upgrade::Allowed-Origins {
    // (existing lines)
    "LP-PPA-ondrej-php:focal";
    "microsoft-ubuntu-focal-prod:focal";
};
// (more lines)

Running Ubuntu 20.04.

---

### Post by ian-weisser on 2024-04-28
The most common reason is that Allowed-Origin is inaccurate. It must be an exact match.

Did you check your unattended upgrades log?

---

### Post by ygoe on 2024-05-02
I believe the name is correct. I found it from some other command I can't remember now. So I have log files, but what would I look out for? The source name is in there but nothing gets upgraded automatically. Packages would only be upgraded when I call apt manually.

---

### Post by ygoe on 2024-05-02
This was the command: 

apt-cache policy

It prints this, among others:

 500 [http://ppa.launchpad.net/ondrej/php/ubuntu](http://ppa.launchpad.net/ondrej/php/ubuntu) focal/main i386 Packages
     release v=20.04,**o=LP-PPA-ondrej-php,a=focal**,n=focal,l=***** The main PPA for supported PHP versions with many PECL extensions *****,c=main,b=i386
     origin ppa.launchpad.net
 500 [http://ppa.launchpad.net/ondrej/php/ubuntu](http://ppa.launchpad.net/ondrej/php/ubuntu) focal/main amd64 Packages
     release v=20.04,**o=LP-PPA-ondrej-php,a=focal**,n=focal,l=***** The main PPA for supported PHP versions with many PECL extensions *****,c=main,b=amd64
     origin ppa.launchpad.net
 500 [https://packages.microsoft.com/ubuntu/20.04/prod](https://packages.microsoft.com/ubuntu/20.04/prod) focal/main all Packages
     release **o=microsoft-ubuntu-focal-prod focal,a=focal**,n=focal,l=microsoft-ubuntu-focal-prod focal,c=main,b=all
     origin packages.microsoft.com
 500 [https://packages.microsoft.com/ubuntu/20.04/prod](https://packages.microsoft.com/ubuntu/20.04/prod) focal/main amd64 Packages
     release **o=microsoft-ubuntu-focal-prod focal,a=focal**,n=focal,l=microsoft-ubuntu-focal-prod focal,c=main,b=amd64
     origin packages.microsoft.com

The Microsoft source has a space and "focal" in its name which is unexpected. I tried both, as shown and truncated.

---

### Post by ian-weisser on 2024-05-02
Please show us a complete apt policy <packagename> output for a package that doesn't upgrade.

You wrote that you notice this only when you run an apt upgrade, so we understand that a useful response may be a while until it happens again.

---

