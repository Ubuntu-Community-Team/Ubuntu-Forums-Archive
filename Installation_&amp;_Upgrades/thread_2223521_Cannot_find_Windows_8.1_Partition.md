---
title: "Cannot find Windows 8.1 Partition"
date: 2014-05-11
forum: Installation &amp; Upgrades
---

### Post by Yusuf_Yildiz on 2014-05-11
My computer originally had windows 8.1 on it (that's what it came with). I tried to install Ubuntu on it but during install it told me that it could not find any operating systems so I had to manually create a partition. Looking back on this I don't think this was a good idea at all. Now when I go into BIOS all I see are two Ubuntu OS and no Windows OS. Is there any way that I can access my windows partition? When I tried boot-repair I got this error: [http://paste2.org/6YCFasjP](http://paste2.org/6YCFasjP)

I would REALLLLYYY appreciate some help from you guys, thanks!

---

### Post by miegiel on 2014-05-11
It looks like you deleted the windows and restore partitions from your disk. Sorry for the bad news.

What you can do it boot from the ubuntu dvd and **try ubuntu**, instead of installing it. That will boot you machine to ubuntu running from the dvd. With *gparted* you can view the partitions on your disk and maybe salvage something. Gparted also has some partition/disk checking options, I would try those too and if you can run a SMART self test (not sure if you can do that running ubuntu from the dvd).

There are also other live-CD's you can download that might help you recover something and your hard disk manufacturer should have a bootable live-CD to test your disk.

edit: Welcome to ubuntu forms

---

### Post by Yusuf_Yildiz on 2014-05-11
Thanks for the welcome.

Oh jeez, does this mean that I will have to re install windows? I'm about to try to and salvage what may be left of my computer. Do you know how I can set my computer back to the factory settings from BIOS? I used to be able to see the partitions that allowed me to do this but now the only ones that are there are the ubuntu ones. I enjoy learning how to deal with these kinds of problems but damn this is a hassle! Thanks for any help!

---

### Post by oldfred on 2014-05-11
When you did the install to entire drive it erased the recovery partition also. Did you make a DVD set from the recovery partition? Or a full image of your Windows install.

If you have files you did not backup that are critical, you may be able to get some back with lots of effort with testdisk, photorec or paid Windows tools. But then stop using system as you are overwriting it as you go. Only use live installer.

You may be able to get a recovery set from your vendor for a nominal charge. Some offer that others do not.
One user posted that they still sold the same model from the store he bought his system from and tech their made a recovery DVD set. Good customer service, but not sure how many would do that.

---

