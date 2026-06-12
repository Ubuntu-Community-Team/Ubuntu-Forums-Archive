---
title: "Upgrading from 8.10 to 9.04 to 9.10"
date: 2010-01-03
forum: Installation &amp; Upgrades
---

### Post by umechanism on 2010-01-03
My goal is to upgrade from 8.10 to 9.10 but, according to my package manager, I have to upgrade to 9.04 first.  Okay..fine, I can do that but when I try to do that, Synaptic begins to download an "upgrade tool".  Once downloaded, nothing happens.  I wait and wait but nothing ever launches and 9.04 never begins to download.

What should I do?  I want to get to 9.10.

Thanks!

---

### Post by raymondh on 2010-01-03
> **umechanism said:**
> My goal is to upgrade from 8.10 to 9.10 but, according to my package manager, I have to upgrade to 9.04 first.  Okay..fine, I can do that but when I try to do that, Synaptic begins to download an "upgrade tool".  Once downloaded, nothing happens.  I wait and wait but nothing ever launches and 9.04 never begins to download.

What should I do?  I want to get to 9.10.

Thanks!

Not even a prompt for your password after the upgrade tool download?

Some things to check/try:

1.  Make sure you are fully updated in intrepid 
2.  Try selecting a different server

Any reason why a fresh, clean install of 9.10 is not possible?  nevertheless, always have a back-up of your files.

Regards,

---

### Post by umechanism on 2010-01-03
I think a clean install might be too much trouble seeing I've got all of these custom settings and programs that I've installed and I really don't want to go through all of that headache again.  Most of my programs are not in the repos and they took me a month of Sundays to get working.  

I tried your suggestions but still no luck.  Anything else I could try?

---

### Post by jonest1 on 2010-01-03
I did the upgrade from 8.10 to 9.10 just as you are attempting, but did not run into any of the problems you are experiencing.  I had a bit of tweaking afterward, though.

I found these alternative methods which may work.

```
sudo apt-get install update-manager-core
sudo do-release-upgrade
```

and here is a 2nd method
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

### Post by umechanism on 2010-01-04
Jonest1,

I started the upgrade process using your suggestions before I left for work this morning.  I'm happy to say that everything is proceeding...except for one little problem.  Just a moment ago, the installation paused and I was shown a message that 94 obsolete packages were about to be removed.  I was given the option to continue (Y) or "details" (d)...so I selected "d" to see the packages to be removed.  Now, I want to continue to installation process but there is no option to "continue".  How do I get this going again?

---

### Post by k64 on 2010-01-04
I would have to respectfully agree with ```
$ sudo apt-get dist-upgrade
```

---

### Post by umechanism on 2010-01-04
But how do I get the installation to restart?

---

### Post by ptn107 on 2010-01-04
Try hitting 'y'?

---

