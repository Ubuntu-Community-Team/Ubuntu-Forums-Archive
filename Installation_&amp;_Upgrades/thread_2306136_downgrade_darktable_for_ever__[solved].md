---
title: "downgrade darktable for ever  [solved]"
date: 2015-12-12
forum: Installation &amp; Upgrades
---

### Post by hughes-bigo on 2015-12-12
hello,

My system (Ubuntu 14.04LTS) had upgated  the new darktable version the 2.0~rc3+136~g48 i386   version. 
This version does not work on 32bits as the warning says  it.
I would love to use it but I cannot change my computer for a  64bits for now.

So, how to downgrade and stay with version 1.6.9 in Ubuntu 14.04LTS or reinstall the 1.6.9 version and stay with it forever

Thanks.

---

### Post by deadflowr on 2015-12-12
How did you install it in the first place?

Ubuntu only goes to 1.4-2.
I see there are two ppa's for darktable (releases and unstable)
releases seems to still be at 1.6-9
[https://launchpad.net/~pmjdebruijn/+archive/ubuntu/darktable-release](https://launchpad.net/~pmjdebruijn/+archive/ubuntu/darktable-release)

and unstable seems to be at 20-rc3-yada-yada
[https://launchpad.net/~pmjdebruijn/+archive/ubuntu/darktable-unstable](https://launchpad.net/~pmjdebruijn/+archive/ubuntu/darktable-unstable)

Did you install it through these, or some other way?

---

### Post by hughes-bigo on 2015-12-14
Hello deadflowr

Yes I've installed DT through **[https://launchpad.net/~pmjdebruijn/+...ktable-release]("https://launchpad.net/%7Epmjdebruijn/+archive/ubuntu/darktable-release") **the stable release and then an** apt-get install darktable**
so if the version 1.6-9 are still in the depot how must I write the command like 
[B]apt-get install darktable 1.6-9
[/B]would it be correct ?sorry for that silly question

---

### Post by Vladlenin5000 on 2015-12-14
No, apt-get always get the newest version available. And, again, if you have version 2.0 then you must have added the 'unstable' PPA instead or along with the 'release' one.
It should downgrade if you purge the unstable PPA:
```
sudo apt-get purge ppa:pmjdebruijn/darktable-unstable
```

---

### Post by hughes-bigo on 2015-12-14
Ok did in case of```
sudo apt-get purge ppa:pmjdebruijn/darktable-unstable
```
but the regular version today seems indeed to be 2.0 (the 2.0~rc3+189). I downloaded it again to check.

So now for me the problem is to known the command to get the 1.6.9 version and on what depot?
Darktable don't have a forum to ask for but a mailing list, which I tried to send message but the only answer I get is : 
```
Is being held until the list moderator can review it for approval.

The reason it is being held:

    Post by non-member to a members-only list
```
well because I not use to mailing list and I'm not a native English speaker, I'm a bit confuse to get help.
Thanks for your time and help.

---

### Post by deadflowr on 2015-12-14
Please run
```
apt-cache policy darktable
```
and post the COMPLETE output

---

### Post by hughes-bigo on 2015-12-14
if there no mistakes, this is :
```
ngux@ngux:~$ apt-cache policy darktable
darktable:
  Installed: 1:2.0~rc3+189~g41e56d9-0pmjdebruijn1~trusty
  Candidate: 1:2.0~rc3+189~g41e56d9-0pmjdebruijn1~trusty
  Version table:
 *** 1:2.0~rc3+189~g41e56d9-0pmjdebruijn1~trusty 0
        500 http://ppa.launchpad.net/pmjdebruijn/darktable-unstable/ubuntu/ trusty/main i386 Packages
        100 /var/lib/dpkg/status
     1:1.6.9-0pmjdebruijn1~trusty 0
        500 http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu/ trusty/main i386 Packages
     1.4-2 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/universe i386 Packages
ngux@ngux:~$

```

---

### Post by hughes-bigo on 2015-12-14
Seems your right, this is a unstable release

---

### Post by deadflowr on 2015-12-14
I think you should install a special package called ppa-purge.
```
sudo apt-get install ppa-purge
```
then run
```
sudo ppa-purge ppa:pmjdebruijn/darktable-unstable
```
Unfortunately, the default behavior is to downgrade all the affected packages to the official Ubuntu repo versions.
(As you can see the Ubuntu repo version is 1.4-2)
However, since you also have the stable (release) ppa, it might only downgrade to that.

---

### Post by hughes-bigo on 2015-12-14
It's worked pretty good with pp-purge but now Darktable don't launch because :
```
darktable
[init] database version of `library.db' is too new for this build of darktable. aborting
ERROR : cannot open database

```
I've uninstalled and purged and reinstalled, but nothings changed
any idea where to find and erase this library.db if it is not compulsory for the OS ? or downgade it ?

---

### Post by deadflowr on 2015-12-14
Look at this:
[http://www.darktable.org/2015/07/released-darktable-1-6-8/](http://www.darktable.org/2015/07/released-darktable-1-6-8/)

particularly this comment:
> houz
on October 20, 2015 at 16:52 said:


That means that you used a development build with that library at least once. darktable updated it and that is not reversible. If you didn&#8217;t use any new features in the processing of your images (which 1.6.8 wouldn&#8217;t know) it should be safe to remove ~/.config/darktable/library.db and just reimport your raw files. All the processing is kept in the associated XMP files. You would however lose your custom module presets.

Hope that helps

Edit: to add, I have removed the duplicate posting.
In future reference, if you post and it causes a duplicate(again), you can simply click on the report post button at the bottom of the post and the staff will help remove it.

---

### Post by hughes-bigo on 2015-12-14
Cool! i've just erase ***~/.config/darktable/library.db*** and Darktable opened again, with the version 1.6.9. 
Perfect!
So the downgrade is done, now how to be sure to never upgrade again ? 
does it work if i erase the depot from sources.list 
```
deb http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu trusty main

```

---

### Post by hughes-bigo on 2015-12-16
> **hughes-bigo said:**
> Cool! i've just erase ***~/.config/darktable/library.db*** and Darktable opened again, with the version 1.6.9. 
Perfect!
So the downgrade is done, now how to be sure to never upgrade again ? 
does it work if i erase the depot from sources.list 
```
deb http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu trusty main

```


Eventually, the best answer I've found to block further upgrade of darktable:
```
sudo apt-mark hold darktable
```
to check
```
dpkg --get-selections
```
to unhold
```
sudo apt-mark unhold darktable
```

---

### Post by Luc_vervecken on 2016-01-05
Hello guys!

I have exactly the same problem as hughes - bigo but for me it does not work.
Probably because I've done the update after December 24th.
> 
luc@luc-Macmini ~ $ apt-cache policy darktable
darktable:
  Geïnstalleerd: 1:2.0.0-0pmjdebruijn1~trusty
  Kandidaat:     1:2.0.0-0pmjdebruijn1~trusty
  Versietabel:
 *** 1:2.0.0-0pmjdebruijn1~trusty 0
        500 [http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu/](http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu/) trusty/main i386 Packages
        100 /var/lib/dpkg/status
     1.4-2 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/universe i386 Packages
luc@luc-Macmini ~ $ 

So I miss the 1.6.9 version

I tried to install through this link , but it is too difficult for me.
[https://github.com/darktable-org/darktable/releases/tag/release-1.6.9](https://github.com/darktable-org/darktable/releases/tag/release-1.6.9)


Does anyone know another solution?

thanks in advance

---

