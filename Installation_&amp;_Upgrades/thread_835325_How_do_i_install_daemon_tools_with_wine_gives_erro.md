---
title: "How do i install daemon tools with wine? gives error: &quot;Platform not supported&quot;"
date: 2008-06-20
forum: Installation &amp; Upgrades
---

### Post by dinbrca on 2008-06-20
When i try to install daemon tools on linux with wine it tells me error:
"Platform not supported"
Thx For The Helpers

---

### Post by Qrikko on 2008-06-20
hmm.. why would you want Deamon tools in wine?

I might be wrong here, but as far as I know you could just mount the media and use it from wine as well.. you could even set it up in yoru fstab to automatically mount it on boot..

check man mount for full info

but if it's a iso you want to mount I think you can just do a:
$> mount isofile.iso /path/to/folder_to_mount_on

then you can do:
$> cd /path/to/folder_to_mount_on
$> wine my_exe_on_the_cd.exe

Hope I understood and hence could help :)

Check some info on using fstab if you want a more "permanent" solution :) it is very easy to use :)

Ah, and by the way you could even set this mounted volume up in your winecfg to use it as a volume.. so it is a bit like deamontools + :P

---

### Post by dinbrca on 2008-06-20
do you have any website for linux begginers?

---

### Post by Qrikko on 2008-06-20
Hmm.. good question I will check around a little if I can find something interesting :)

I have been using Linux for many years, I started out from Sun Solaris, (Unix) and went on to a couple of distros.. Slackware, Gentoo, redhat and some more I think :P

So I am not all familiar with resent good material.. but I will search and post back in a minute :)

---

### Post by Qrikko on 2008-06-20
[http://www.ubuntu.com/support](http://www.ubuntu.com/support) is a nice site (but of cause a bit far away from what you ask for ;))

[http://www.linux.org/lessons/beginner/toc.html](http://www.linux.org/lessons/beginner/toc.html) (this seem to be a nice resource.. pretty strength forward and more importantly it is a bit biased toward debian (Ubuntu is based from debian). I think this could be a nice reference to start out, and also this place where we are right now ^^ the ubuntu community is way awesome!

if it is not to your liking or I can do something to help I check the forums regularly (read too often :P) and also put this thread in my watched once :)

---

### Post by MASTER_455 on 2011-10-15
hi, im new to ubuntu and i was wondering if some one could create a file/script that would fix my installation of daemon tools , i have installed it. but as i'm a complete noob  i dont undersand any of the solutions to this problem.

i would be gratefull if some one could help me with this problen.

---

### Post by oldos2er on 2011-10-15
Closed, necromancy. Please start a new thread.

---

