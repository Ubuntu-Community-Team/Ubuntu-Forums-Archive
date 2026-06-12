---
title: "Install Zend Server from local installation file"
date: 2011-07-16
forum: Installation &amp; Upgrades
---

### Post by cazzy on 2011-07-16
Hi,
 
I am running *Windows XP Pro* and the latest edition of *Virtualbox*. I [COLOR=darkgreen]installed Ubuntu 11.04 Desktop Edition[/COLOR][COLOR=darkgreen] on a virtual drive in Virtualbox[/COLOR]. I connect to the internet via a mobile phone at expensive rates, so I [COLOR=red]do not[/COLOR] want to [COLOR=red]retrieve and install Zend Server from the repository[/COLOR] via my Ubuntu Desktop Edition. I would prefer to [COLOR=darkgreen]install Zend Server directly from the file that I have on my hard drive.[/COLOR]

**[COLOR=sienna]My Question:[/COLOR]**
[COLOR=sienna]What are the series of commands that I must type into the terminal window within the Ubuntu 11.04 **Desktop Edition** (on the virtual drive) to install the latest "Zend Server Community Edition" considering that the .tar.gz file is located in a sub folder titled "zend" at the root of my C: drive on windows XP?[/COLOR] 
 
[COLOR=sienna]Example:[/COLOR] [COLOR=darkgreen]C:\mydownloads\zend\ZendServer-CE-php-5.3.5-5.1.0-linux-glibc23-i386.tar.gz[/COLOR]

I would be most appreciative for your advice.
 
Kind Regards,
Cazzy

---

### Post by cazzy on 2011-07-18
[COLOR=sienna]Can anybody advise [/COLOR][COLOR=sienna]me of[/COLOR] [COLOR=#a0522d]the series of commands that I must type into the terminal window within the Ubuntu 11.04 **Desktop Edition** (on the virtual drive) to install the latest "Zend Server Community Edition" considering that the .tar.gz file is located in a sub folder titled "zend" at the root of my C: drive on windows XP?[/COLOR] 

[COLOR=sienna]Example:[/COLOR] [COLOR=darkgreen]C:\mydownloads\zend\ZendServer-CE-php-5.3.5-5.1.0-linux-glibc23-i386.tar.gz[/COLOR]

---

### Post by dino99 on 2011-07-18
look at /var/cache/apt/archives/ to see if the package(s) is there, otherwise grab it from a cdrom, or connect from an other place with better connection

---

