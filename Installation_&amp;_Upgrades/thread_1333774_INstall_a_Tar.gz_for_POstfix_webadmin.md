---
title: "INstall a Tar.gz for POstfix webadmin"
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by sylvesterbeck on 2009-11-21
POstfix Webadmin

Hi all 

New to Ubunti and need some help , need simple explanations!

I have Ubuntu server9.10 installed , also installed postfix on the server with Mysql all of that is okay , I know am trying to install the Postfix webmail admin tool from 

[http://postfixadmin.sourceforge.net/](http://postfixadmin.sourceforge.net/)

I use the commadn wget http:// ????? etc etc 

the file dowmnloads I can see it but when I rub 

Tar xvfy "filename.tar.gz" 

it says it is not a valid tar file

I triee renaming it as per some other threads but stil no luck 

anybosy know of a sudo command to install postfix webadmin tool or how I can work around this

Please try to be detailed in the explanation as I am not a pro at linix at all.

Thank you

---

### Post by TheDude21 on 2009-11-21
It looks like your tar arguments are wrong. Try using "xvzf" instead of "xvfy"

---

