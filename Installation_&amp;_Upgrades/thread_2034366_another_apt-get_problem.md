---
title: "another apt-get problem"
date: 2012-07-28
forum: Installation &amp; Upgrades
---

### Post by Jorel on 2012-07-28
Hi guys,

im having a problem with "apt-get"... due that im having a lot of errors while installing my CUPS saying "package has no installation candidate",, even when im just updating and upgrading my system all i can see is an error,, i tried "apt-get autoclean" but it doesn't help..

im here at Qatar, so all i can see is:

W: Failed to fetch [http://qa.archive.ubuntu.com](http://qa.archive.ubuntu.com)....................................

i tried adding:
deb [http://ubuntu.mirrors.isu.net.sa/ubuntu/](http://ubuntu.mirrors.isu.net.sa/ubuntu/) precise main  deb-src [http://ubuntu.mirrors.isu.net.sa/ubuntu/](http://ubuntu.mirrors.isu.net.sa/ubuntu/) precise main 

(its from [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors) )but still no good, 

thanks in adnvance...

---

### Post by 2F4U on 2012-07-28
Have you tried to use another mirror, maybe from a different country? It may just be a temporary problem with the mirror.

---

### Post by Jorel on 2012-07-28
hi 2F4U,

is it ok to put additional mirrors or i can just remove the old ones?

---

### Post by raja.genupula on 2012-07-28
> **2F4U said:**
> Have you tried to use another mirror, maybe from a different country? It may just be a temporary problem with the mirror.

+1 choose best server option , that will give you the best server from your location .

---

### Post by vipulkumar7 on 2012-07-28
i have same problem I did fix it, though, by deleting /var/lock/dpkg/status and then touching a new one (sudo touch /var/lock/dpkg/status) :)

---

### Post by Jorel on 2012-07-28
Hi raja.genupula,

i tried adding 4 diff country but still no good,,

Hi vipulkumar7,

im still newbie with handling servers hehehe can you tell me how to delete /var/lock/dpkg/status?


thanks guys...

---

### Post by raja.genupula on 2012-07-28
you can do it like this 
```
sudo rm /var/lock/dpkg/status
```

---

### Post by Jorel on 2012-07-29
ah yes, just as i thought,,,

i thought im doing it wrong, but the thing is "there is no var/lock/dpkg/status to remove", i know this is not normal... right?

i checked my /var/ and all it got is a /lock/, and it has a "/run/lock" within it... and i dont know what does it means,, the output of my /var/lock is:

lrwxrwxrwx 1 root root 9 Jul 10 12:26 /var/lock -> /run/lock


thanks..

---

### Post by finito on 2012-07-29
Ohh this happened to me in Kuwait it was freaking frustrating, I let it happen for 3 days then I figured it was my ISP.

I called them up only to be told what/who/when/huh figures when you have monkeys for support staff.

I then called corporate support and asked them who was handling the conical/Ubuntu servers then I got the response and they fixed it for me. 

I just tried to ping it and I also went to [http://qa.archive.ubuntu.com/ubuntu/](http://qa.archive.ubuntu.com/ubuntu/) seems like it\s alive and kicking maybe try again?

Peace.

---

### Post by Jorel on 2012-07-29
Hi finito,

yes, previously the [http://qa.archive.ubuntu.com/ubuntu/](http://qa.archive.ubuntu.com/ubuntu/) is working and that is my default mirror,, and i tried also updating on a ubuntu client and its also working but still its not working on my headless server when i apt-get and its now a week since i noticed it, i just thought its normal,i just realize that its not :( ,, 

in addition, is it really normal for the "back-ports" and "security" not commented out?


thanks..

---

### Post by Jorel on 2012-08-01
hi guys,

im really frustrated about my apt-get problem,, so what i did is i downloaded from another machine a ".deb" file and i placed it in a shared folder,, but the things is i don't know where will i copy it for it to be installed... i mean i know where to find the file that i downloaded, but i dont know where to move it,, i used a folder from my samba files...

please help guys..

---

### Post by Jorel on 2012-08-01
i saw where to place it,, but install is not working, what i did is:

apt-get install --no-download <package name>

result is:

E: Unable to locate package splix_2.0.0+svn300-1.1ubuntu2_all.deb
E: Couldn't find any package by regex 'splix_2.0.0+svn300-1.1ubuntu2_all.deb'

even the dpkg -i shows:

Selecting previously unselected package splix.
(Reading database ... 31627 files and directories currently installed.)
Unpacking splix (from .../splix_2.0.0+svn300-1.1ubuntu2_all.deb) ...
dpkg: dependency problems prevent configuration of splix:
 splix depends on printer-driver-splix; however:
  Package printer-driver-splix is not installed.
dpkg: error processing splix (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 splix

because im installing another ppd for my printer,, but i cant see how to make it work...

help guys..

---

### Post by Jorel on 2012-09-01
Hi guys,,

Im on a longest vacation ever,,, and i think i know my problem now,, i think i blew my resolv.conf and most probably i can fix that when i got back to the office....

Thanks

---

### Post by Jorel on 2012-09-10
Hi guys,

now i confirmed it that the problem that i encountered is that my resolv.conf lost its nameserver and search,, im just wondering, is this a known bug on a server? due that im not touching resolv.conf coz i dont know that to put on it... but suddenly its been erased... anyway, its fixed now, if theres someone who can tell me if its a bug or not then thank you for that and also if its not yet known then hope someone can raise it up to the dev team so it will be fixed somehow...

thanks guys.

---

