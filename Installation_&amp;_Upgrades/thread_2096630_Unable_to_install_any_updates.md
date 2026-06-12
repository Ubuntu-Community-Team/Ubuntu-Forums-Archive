---
title: "Unable to install any updates"
date: 2012-12-20
forum: Installation &amp; Upgrades
---

### Post by bharathsv on 2012-12-20
Hello

I am using Ubuntu 11.10. Over the last couple of months I have not been able to install any updates. When I try to install updates, it fails giving the following error. 

The package openprinting-ppds-postscript-gestetner needs to be reinstalled, but I can't find an archive for it.

Can you please help me to resolve this?

Thanks in advance
Bharath

---

### Post by irv on 2012-12-20
Here is the life cycle of Ubuntu releases.
[ATTACH]228929[/ATTACH]
[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases]("http://en.wikipedia.org/wiki/List_of_Ubuntu_releases")

---

### Post by irv on 2012-12-20
Why don't you do an install of 12.04, It has a life span of 5 years?

---

### Post by grahammechanical on 2012-12-20
How did you install this software? did you install it through a PPA? If so remove the PPA from your Software Sources and then you should be able to update.

Perhaps you can un-install that software and re-install it.

[http://www.openprinting.org/driver/Postscript-Gestetner/]("http://www.openprinting.org/driver/Postscript-Gestetner/")

The printer may have a set up utility that will install this printer driver for you. You should also try going on the printer manufacturer's web site and seeing if you can get the printer driver from there. The information I have seen researching this is that some of these drivers are distributed under a non-free licence and for that reason will not be available through Ubuntu repositories. That might apply to your printer. Did you get a set up disk with the printer? Does it have this driver on it?

Regards.

---

### Post by bharathsv on 2012-12-20
Hi grahammechanical

Thanks for your comment. I dont know how this software got installed. I did not install it from PPA. May be this could have got installed while I was setting up a printer for me at my work place. Because of this I am not even able to go a partial upgrade and it asks me to uninstall this software. This might be a network printer and therefore I dont have any set up disk or things of that sort. I am not able to figure out how to delete this stuff. Is there a way that I upgrade my current ubuntu version to a stable ubuntu 12? If so, may be this problem will go off. I will be really grateful to you can help me to upgrade my ubuntu version to a stable 12.xx version.

Best regards
Bharath

---

### Post by bharathsv on 2012-12-20
Dear irv

thanks for your suggestion. I would like to know how to upgrade to 12.04. Actually I want to do that but the issue that I am facing is not allowing me to do an auto-upgrade. Is it easy to do an upgrade by downloading directly from the ubuntu page? Is 12.04 stable?

Best
Bharath

---

### Post by Pjotr123 on 2012-12-20
12.04 LTS is very stable indeed. Do a clean upgrade:
[https://sites.google.com/site/easylinuxtipsproject/reinstallation](https://sites.google.com/site/easylinuxtipsproject/reinstallation)

---

### Post by irv on 2012-12-21
May I suggest a nice clean install of 12.04. First make a backup of all the your personal file you want to keep. Don't worry about program file they will be reinstalled. If you backup your home folder make sure you get all the hidden files, because some of them contain configuration files. While in Nautlius go to view on the menu and select "show hidden files". Then select all and copy them to an external drive.
Then follow this step by step install of 12.04.
[http://www.krizna.com/ubuntu/ubuntu-12-04-installation-step-step-screenshots/]("http://www.krizna.com/ubuntu/ubuntu-12-04-installation-step-step-screenshots/")
You can download 12.04 from [http://releases.ubuntu.com/precise/]("http://releases.ubuntu.com/precise/")

---

### Post by bharathsv on 2012-12-21
Thanks everyone for your helpful comments. I am able to resolve the issue by using the link provided by grahammechanical and then upgraded to 12.04. 

Best
Bharath

---

