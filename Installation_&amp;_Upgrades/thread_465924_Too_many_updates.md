---
title: "Too many updates"
date: 2007-06-06
forum: Installation &amp; Upgrades
---

### Post by akshayas1986 on 2007-06-06
Hello people,

I have been using Ubuntu for over 2 years now and and I have just fallen in love with it. The support and the communitites make it the most usable linux distro. So first of all, thank you to all the people who have contributed so much to Ubuntu..

I have an issue with Ubuntu. I keep formatting the disk once in a while and everytime I format my disk, I re-install Ubuntu, After re-installation I have to updates the OS and the updates are of the size of 200 to 300 MB. And from what I can see, many of these updates are not necessary..

So can someone tell me what to do about it??

Thanks and regards
Akshaya Srivatsa

---

### Post by Mongoose on 2007-06-06
Yes, stop needlessly reformatting your disk.   =)

---

### Post by ajgreeny on 2007-06-06
Next time before you reformat, if you really have to, copy all the deb files from /var/cache/apt/archives to a CD, and then before you update the new install, copy the CD back to the same place, where the files came from.  You will not then need to download any updates as the system will think they are already downloaded and synaptic or apt-get will just install required packages.  There is a way to do this using the terminal, but I can't remember how at the moment, and this gui method does work without problems.

---

### Post by zvacet on 2007-06-07
Use APTonCD.If you are runing Feisty it is in your synaptic.if you run some other version you can download it from

[http://aptoncd.sourceforge.net/]("http://aptoncd.sourceforge.net/")

---

### Post by akshayas1986 on 2007-06-07
Hi

Sorry for asking so many questions but I am not able to install APTonCD. It says

Error: Dependency is not satisfiable: python-support

Whats should I do now??

---

### Post by steeleyuk on 2007-06-07
sudo apt-get install python-support

---

### Post by mikewhatever on 2007-06-07
You can also go yo System>Administration>Software Sources and specify which of the updates to download. Leave only Important Security Updates to get fewer.

---

### Post by akshayas1986 on 2007-06-11
Hey people,
Thanks a lot for the info. But I came across another way of doing it..Create a backup of /var/cache and /var/lib. restore them after you reinstall your OS. Apt will look at it as new downloaded updates and will install them.

Akshaya Srivatsa:)

---

### Post by srirambond007 on 2007-06-13
Actually what you have to do is as told just copy the files from the /var/cache/apt/archives to some other folder or a cd and after formatting and installing just goto synaptic package manager under system->administration and click on File menu and say ADD downloaded packages ....now select the folder in which u have backed up all the .deb files
and repositories
and click open ...the files cant be selected , clicking on the files is disabled.....so dont worry that u cant select the files just go ahead click on open 
and their u go .......
click on apply on synaptic application manager and it will show a window just like u will see when u select any other .deb package for download......
Simple Right

---

