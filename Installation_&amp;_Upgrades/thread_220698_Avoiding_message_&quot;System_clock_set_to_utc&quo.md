---
title: "Avoiding message &quot;System clock set to utc?&quot; during automated installation"
date: 2006-07-21
forum: Installation &amp; Upgrades
---

### Post by scarpaz on 2006-07-21
Hi people,

I'm preparing a zero-intervention preseed file for ubuntu dapper.
Although the documentation is not much, i have been able to collect and prepare a decent preseed file, by collecting the current installation information with, as usually suggested:

```

debconf-get-selections --installer > /root/preseed-ken1.cfg
debconf-get-selections >> /root/preseed-ken.cfg

```

The only problem is that for some reason, the above commands do not fetch the answer to question "Set system clock to UTC?", so this dialog box keeps nagging me in the middle of the installation process.

I thought it was enough to add the following line:
```

base-config	tzconfig/gmt boolean true

```
but I was wrong.

Finally, I unzipped the initrd provided with the ubuntu installation and went through the installation script. So, the actual line to add is as follows:

```

d-i	clock-setup/utc	   boolean true

```

It is not reported or documented elsewhere AFAIK, therefore I thought it might be useful to others.

Ciao everyone.

---

### Post by SkyNet2029 on 2006-07-22
Interesting post.
Now maybe I can make my 'set it and forget it' install cd. 
Thanks.! 
Ohhh. because there is no base-config prior to calling the d-i clock-setup/utc during initial setup. (?)

---

