---
title: "Error with recent Flash 7 upgrade"
date: 2006-09-20
forum: Installation &amp; Upgrades
---

### Post by aleska on 2006-09-20
Did anyone else get an error message when they installed the flash 7 upgrade?
I can't recall what the exact error message was.  Is there a log file I can reference to see what installed properly and what didn't?
Thanks!

---

### Post by tama on 2006-09-20
I've just upgraded flash (to v7.0.68 from the ubuntu repos) and I also get an error message:
```
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
dpkg: error when processing flashplugin-nonfree (--configure):
 the subprocess post-installation script returned the output error code 1
```
Any idea what it might be?
Thanks

---

### Post by aleska on 2006-09-20
Yup, that's the same error I received.

---

### Post by Japa on 2006-09-20
> **aleska said:**
> Yup, that's the same error I received.

I too had that same error! Now every time I use apt-get command in terminal it trys to install flash, but ofcurse without success.

Off topic: Yes, I'm new hi! :razz:

---

### Post by Robor on 2006-09-20
I got the same error.  I 'fixed' it by doing 'apt-get remove flashplugin-nonfree'  ;)

I figure I can always reinstall it later when they get it working properly.

Now if I could just get X to start after the latest kernel upgrade...  ](*,)

---

### Post by ctsdownloads on 2006-09-20
Well, I was able to remove it. However the installation of the plugin still presents the exact same error. When you did the remvovel, did you reboot or something? Obviously this is a bug in the install script, no? ](*,)

---

### Post by nbx909 on 2006-09-20
yep same problem anybody have a deb of the old one so i can remove the new one and install the old one?

---

### Post by hotani on 2006-09-20
Just chiming in with "same here". This is happening on two different ubuntu machines. 

Plus Flash is just generally sucking recently and has no sound at all. I tried the fix but was met by the exact same error listed above. Guess we're all waiting for the fix.

---

### Post by nbx909 on 2006-09-20
what fix? it's a partial fix, removing it will just get rid of it, the full fix would be reverting to an older package after removing it does anyone have this package?

---

### Post by nbx909 on 2006-09-20
Jack_Sparrow in the chat pointed me to this which works
[http://blog.mypapit.net/2006/08/install-mozilla-flash-plugin-in-ubuntu.html](http://blog.mypapit.net/2006/08/install-mozilla-flash-plugin-in-ubuntu.html)
just make sure you ```
sudo apt-get remove flashplugin-nonfree
``` first

---

### Post by Rob_H on 2006-09-20
Someone in another thread recommended this, which fixed it for me by downgrading:
```

sudo apt-get install flashplugin-nonfree/dapper

```

---

### Post by zaflaucich on 2006-09-20
I have solved doing what kubicle has suggested [here]("http://kubuntuforums.net/forums/index.php?topic=9172.msg36711#msg36711")

---

### Post by skymt on 2006-09-20
> **zaflaucich said:**
> I have solved doing what kubicle has suggested [here]("http://kubuntuforums.net/forums/index.php?topic=9172.msg36711#msg36711")

Worked for me too. Thanks!

---

### Post by Japa on 2006-09-20
> **zaflaucich said:**
> I have solved doing what kubicle has suggested [here]("http://kubuntuforums.net/forums/index.php?topic=9172.msg36711#msg36711")

It worked! Thanks to kubicle. :D

---

### Post by aleska on 2006-09-21
> **zaflaucich said:**
> I have solved doing what kubicle has suggested [here]("http://kubuntuforums.net/forums/index.php?topic=9172.msg36711#msg36711")

Yipee Ki-yay!  Works for me too!  Thanks to kublicle for the fix, and thanks to wet drippy cat for pointing me there.  You rock!

---

