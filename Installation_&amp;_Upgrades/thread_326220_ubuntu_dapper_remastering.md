---
title: "ubuntu dapper remastering"
date: 2006-12-27
forum: Installation &amp; Upgrades
---

### Post by gunoieru on 2006-12-27
hi there everybody,

I need help with a little problem and there may be some of you that have an answer for my problem.

i am trying to remaster a dapper server install cd (ubuntu 6.06). i was following the manual from [https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization)

using that tut, i have included within the cd a deb with a custom kernel image. everything seemed to work well. when i tried the installer, it worked well till the kernel installation part. it throws me a message that cannot find any kernel images available. of course i did not  deleted the debs containing the kernel image. actually i did not deleted anything.

in fact, as i discovered later, if i only recreate the repository with apt-ftparchive, no matter if i put other debs in or there are just the same debs, installer exits with this error.

sorry if i put this thread in the wrong place

---

### Post by az on 2006-12-27
Did you use the --stem=linux option when rebuilding the kernel with kernel-package?   That makes the kernel packages you make have a "linux-image" name instead of a "kernel-image" name.  That's all I can think of right now...

There is a project called reconstructor, which remasters the Ubuntu live cd.  Maybe you can try that?

---

### Post by gunoieru on 2006-12-27
i did not. but...

i gave a apt-ftparchive only to remake the repository lists with no changes at all over the existing debs in the pool (for testing) and, even so, the install fails with that error message. 
i mean, the only thing i did, was to regenerate the files: Packages and Packages.gz.

maybe there is actually some sort of special marking for a deb to be known as a kernel image. that may be an aberation though as i found nothing about it on the google.

i'll see about the reconstructor project, though i need to remaster the installl cd so i will be able to automatically deploy some software

thank you


later edit:
as usual it is user's fault. i just discovered that my Packages file is very different from the original (it has about one third in size....) I don't know why is that, i'll dig into it. if anyone can help... he/ her will be welcomed

thanks

---

