---
title: "Ubuntu- [Errno 5]"
date: 2008-04-11
forum: Installation &amp; Upgrades
---

### Post by ketzerei on 2008-04-11
[IMG]http://i193.photobucket.com/albums/z289/ketzerei/Screenshot-2-2.png[/IMG]

[IMG]http://i193.photobucket.com/albums/z289/ketzerei/Screenshot-3-2.png[/IMG]

[IMG]http://i193.photobucket.com/albums/z289/ketzerei/Screenshot-2-2.png[/IMG]

[IMG]http://i193.photobucket.com/albums/z289/ketzerei/Screenshot-6-1.png[/IMG]

[IMG]http://i193.photobucket.com/albums/z289/ketzerei/Screenshot-8.png[/IMG]

[IMG]http://i193.photobucket.com/albums/z289/ketzerei/Screenshot-9.png[/IMG]

[IMG]http://i193.photobucket.com/albums/z289/ketzerei/Screenshot-10.png[/IMG]

[IMG]http://i193.photobucket.com/albums/z289/ketzerei/Screenshot-11.png[/IMG]

Suggestions?

I've posted this before somewhere else, because 7.10 (32 & 64 AND the alternate cd's) did the SAME THING! Kubuntu wont even install now. I get the same error after error. The cd check passes, the md5 was and is fine, I burned using k3b at 16x.... I dont know whats wrong.

---

### Post by Pumalite on 2008-04-11
You have to burn at 4x or less to CD-R and check CD integrity after burn and before install. Did you clean the lens? Maybe you need a new drive.

---

### Post by ketzerei on 2008-04-11
I'm absolute in the fact that there is nothing wrong with my cdrom drive. I know it has nothing at all to do with it.

---

### Post by Herman on 2008-04-11
:) Hey, the same thing happened to me last weekend, here's my story about it, [Hardy Heron Beta / Gutsy Gibbon Graphical Installation C]("http://www.herman.linuxmaniac.net/p22.html"). :)

This happened to me once a year or two back but the failure occurred right in the middle of partitioning that time. I was installing a newer Ubuntu in my wife's computer. It borked the partition table but luckily we had everything (files) backed up so she didn't mind, I just had to re-install her other two operating systems for her too.
A partition table disaster can easily be fixed these days with TestDisk if you know how to use it, but it's better to make sure we run an md5sum integrity test on our downloaded .iso files before we burn them to disk, then use the 'Check CD for  defects' option in the installation disk before starting to install.

Like Pumalite says, it's best to burn your CD at a nice leisurely pace.
> I'm absolute in the fact that there is nothing wrong with my cdrom drive. I know it has nothing at all to do with it.
Maybe it's just your CD then.
In my case it turned out to be just the CD this time too, but the time before that it really was the CD/DVD drive lense.

:) Regards, Herman

---

