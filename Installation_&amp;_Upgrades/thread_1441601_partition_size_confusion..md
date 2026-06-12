---
title: "partition size confusion."
date: 2010-03-28
forum: Installation &amp; Upgrades
---

### Post by wizarddrummer on 2010-03-28
Hi,
I've read several posts and searched on the internet and I have been presented with a wide variety of conflicting information, so I am a little confused on sizes and where things are placed.

Suppose I have these partitions: (sizes are not important at this moment)
/boot
/
/swap
/home

Suppose I install 200 various educational, office, internet, and game applications. In which partition will the applications reside?


Does it make sense to create these partitions? ( I saw these on a web page)
/usr
/usr/local
/opt
/tmp

---

### Post by Arand on 2010-03-29
/boot
will host kernel images and other items required to boot the system, ~200MB is normally more than sufficient (2 kernel versions takes ~30MB)

/swap
See: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
general guideline ~1.5*amount of RAM

/
Root filesystem, everything you install normally will go here, ~20-30GB should do fine depending on the size of the software you plan on installing (normally you can get away with ~10GB on a system with a "normal" amount of applications installed). 

/home
User config and user saved data (if not stored elsewhere)
No really good guidelines can be given, all depending on if you plan on keeping your music/movie/downloads archive on here or not.

/usr
/usr/local
/opt
/tmp
Would make sense if you have specific preferences which you know of.
If not, they probably don't.

Often, an easy solution is to simply use one big / and /swap, thus one does not need to worry about individual allocation, which might turn out wrong after the fact.


- Arand

---

### Post by oldfred on 2010-03-29
Applications go into root.

Explaination of file structure
[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

Unless you have a very old system where the BIOS only lets you boot in the beginning of the drive you do not need /boot. Only server installs may want to break out the other parts of the root system into separate partitions to give better control over server applications that may use large amount of different parts of root. Normal desktop installs are fine with just root & swap. If you are planning clean installs every 6 months with new Ubuntu releases then a separate /home makes sense. I like a separate /data for all my data. That makes my root about 5GB with lots of programs and my home is only 1GB with all data in the data partition including some of the hidden folders normally in /home like firefox and thunderbird profiles.

Unless you have a server where you know exactly how you are using the system the extra partitions end up wasting space as you may not estimate sizes correctly. I had just root and swap with some data in a shared partition for dual booting windows for three years. Then I had a better idea of how large to make partitions and organize my system for my use.

---

### Post by wizarddrummer on 2010-03-29
> **oldfred said:**
> Applications go into root.

Explaination of file structure
[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

Unless you have a very old system where the BIOS only lets you boot in the beginning of the drive you do not need /boot. Only server installs may want to break out the other parts of the root system into separate partitions to give better control over server applications that may use large amount of different parts of root. Normal desktop installs are fine with just root & swap. If you are planning clean installs every 6 months with new Ubuntu releases then a separate /home makes sense. I like a separate /data for all my data. That makes my root about 5GB with lots of programs and my home is only 1GB with all data in the data partition including some of the hidden folders normally in /home like firefox and thunderbird profiles.

Unless you have a server where you know exactly how you are using the system the extra partitions end up wasting space as you may not estimate sizes correctly. I had just root and swap with some data in a shared partition for dual booting windows for three years. Then I had a better idea of how large to make partitions and organize my system for my use.

Thanks everyone for your replies but something still does not make any sense to me at all.

IF the applications I install (for example:[]("http://linuxappfinder.com/package/stellarium") Stellarium, []("http://linuxappfinder.com/package/rekall") Rekall,many others) are NOT installed in /home, but INSTEAD are installed in / then, from what I understand, every time I do a major upgrade I have to reinstall all of the applications.

That's crazy or else I am not getting this concept it at all.

---

### Post by oldfred on 2010-03-29
The majority of standard apps are included in the standard install and will be the more recent versions.

You can export a list of all applications and easily import them again. When I did it on my latest install I did get some older apps that had newer versions as the new standard.

sudo cp /etc/apt/sources.list ~/sources.list.backup
Otherwise if you have added any PPAs or other sources, this tip won't work.
generate new sources file

[http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
from lovinglinux
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

and using synaptic
[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)

---

### Post by garvinrick4 on 2010-03-29
Install from disk is 690 meg or so and if you update && upgrade and add all the app's you can think of you will not get over 5 gig if you wanted to. Only you know how much of a Home you need. If you have 2 gig or more of Ram you should not need a swap unless you use Ram entensive apps, like desktop publishing for instance. 
 When you dist-upgrade everything will be upgraded do not worry about that you apps will be fine. If you want to dist-upgrade into a Alpha or Beta stage of a version to bug test you will get some quarks but that you know going into Alpha of Beta stages.

---

### Post by garvinrick4 on 2010-03-29
> **oldfred said:**
> The majority of standard apps are included in the standard install and will be the more recent versions.

You can export a list of all applications and easily import them again. When I did it on my latest install I did get some older apps that had newer versions as the new standard.

sudo cp /etc/apt/sources.list ~/sources.list.backup
Otherwise if you have added any PPAs or other sources, this tip won't work.
generate new sources file

[http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
from lovinglinux
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

and using synaptic
[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)

Like the first couple of links.

---

### Post by wizarddrummer on 2010-03-29
> **oldfred said:**
> The majority of standard apps are included in the standard install and will be the more recent versions.

You can export a list of all applications and easily import them again. When I did it on my latest install I did get some older apps that had newer versions as the new standard.

sudo cp /etc/apt/sources.list ~/sources.list.backup
Otherwise if you have added any PPAs or other sources, this tip won't work.
generate new sources file

[http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
from lovinglinux
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

and using synaptic
[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)

Thanks for your reply, but this still does not answer my question.

Specifically this is what I want to understand.

When I partition this disk (a 250GB Maxtor) I do not want to fuss with anything other than new OS files when I upgrade. To put it another way, I installed over 100 applications that WERE NOT part Ubuntu Standard Install during my last install. I had some hardware problems and had to zero out my hard drive. So I am starting over again.

When I do an upgrade, at some point after the install, I certainly don't want to waste the huge amount of time selecting and reinstalling all of the apps I intend to download again and again after each upgrade.

Once I install a program I do not want to install it again (unless of course I choose to)

What I want to do is create a partition where all applications will get stored when installed. Sort of like Program Files in Windows. This way when I do an upgrade the only thing I have to do is reboot and move forward.

I'm an old, really old, Unix hack. 

In those days I knew where things were located and how to partition effectively. 
I just don't know that much about the new and improved Linux; so much has changed.

I don't have any problems figuring out partition sizes if I have some basic info. 


Here's my current plan.
/ (root) 200 MB
/swap 1 GB (3x memory)
[COLOR=Red]/??? for apps 50 GB[/COLOR]
/home 248 GB
and possibly a /tmp 

Can someone please tell me what I need to replace the ??? with so that when I use normal program installation methods the programs will get stored in that location?
Thanks,

---

### Post by wizarddrummer on 2010-03-29
> **garvinrick4 said:**
> Install from disk is 690 meg or so and if you update && upgrade and add all the app's you can think of you will not get over 5 gig if you wanted to. Only you know how much of a Home you need. If you have 2 gig or more of Ram you should not need a swap unless you use Ram entensive apps, like desktop publishing for instance. 
 When you dist-upgrade everything will be upgraded do not worry about that you apps will be fine. If you want to dist-upgrade into a Alpha or Beta stage of a version to bug test you will get some quarks but that you know going into Alpha of Beta stages.

Unless Linux apps are incredibly small, I can't see that 5GB would even scratch the surface. My fltsim in windows was more than 7GB. My windows System had 2 500GB disks and both were more than 80% full. 30% was apps.

Yikes yet more confusion.
I see apps might be fine on an upgrade but what about these LTS?? versions? Don't these versions completely overwrite the root area and if that is where the games are put and its formatted then how does it preserve the games.

I know that this is not difficult for someone that is familiar with it, but for some reason, I am going around in circles.

Sill looking for the ??? name of the partition that holds the programs so I can get on with my progress.

As a preference I don't want my apps in the / (root) directory.

Does anyone know this?

---

