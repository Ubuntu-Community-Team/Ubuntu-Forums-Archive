---
title: "Unresolved dependency error when installing libapache2-mod-php7.4 on Ubuntu 22.04"
date: 2022-04-25
forum: Installation &amp; Upgrades
---

### Post by georgepapadop1974 on 2022-04-25
I recently installed Ubunto 18.04 LTS and then consecutively upgraded to 20.04 LTS -> 22.04 LTS. I then installed Apache2 and PHP 7.4, following this guide.
[https://www.linuxcapable.com/how-to-install-php-7-4-on-ubuntu-22-04-lts/](https://www.linuxcapable.com/how-to-install-php-7-4-on-ubuntu-22-04-lts/)

However, when installing libapache2-mod-php7.4, I always get this error:

```

sudo apt install libapache2-mod-php7.4
[sudo] password for localadmin: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libapache2-mod-php7.4 : Depends: php8.1-common (= 8.1.2-1ubuntu2) but 8.1.5-1+ubuntu22.04.1+deb.sury.org+1.1 is to be installed
E: Unable to correct problems, you have held broken packages.

```

I believe that I had fiddled with the installation so i tried this on second VM that I upgraded again to 22.04 using the same method. I got the same error.

I am quite at loss now and need to get PHP 7.4 working because we have a site that does not work properly with PHP 8.1 yet. Can you confirm whether you are facing similar issues?
The guide says otherwise but this is my experience.

Best regards,
George

---

