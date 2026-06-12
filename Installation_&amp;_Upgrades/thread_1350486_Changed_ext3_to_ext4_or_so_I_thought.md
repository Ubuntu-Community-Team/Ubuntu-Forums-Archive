---
title: "Changed ext3 to ext4 or so I thought"
date: 2009-12-09
forum: Installation &amp; Upgrades
---

### Post by Mark_in_Hollywood on 2009-12-09
I read that Karmic (v. 9.10) would use ext4. I had Jaunty, v. 9.04. I downloaded a fresh GParted LiveCD, checked for the partitions, saw 3, one for the OS, a separate /home and a swap. I changed the OS and /home to ext4. Clicked apply and waited. Shortly, GParted showed the work as done and reported no errors.

Taking my new Karmic Desktop CD, (even ran the MD5 checksums), and ran the install. Nothing showed up as a problem. Not until I cold booted the next day. Something was broken. At first I thought this was a Compiz problem. Then an NVidia driver problem.

I had asked about this in several [posts]("http://ubuntuforums.org/showthread.php?t=1348711") since I made the installation. I said this:

After the desktop comes up, the top panel "cuts off" the desktop. If I run Chrome or Firefox, the panel gets in the way. The app windows cannot be move around. 

Then I started thinking it was a Gnome Desktop fault. I reinstalled that. No luck. 

Finally, I decided to check the ext4. I loaded GParted-LiveCd and in fact, it reports ext3. 

Is there a fix for this? Or is it time to drop the hard drive from the 2nd story where I work, to see if that will make the 3 become a 4?

---

### Post by doas777 on 2009-12-09
do these instructions come close to what you were attempting? perhaps they cover a step that you missed.
[http://maketecheasier.com/how-to-upgrade-from-ext3-to-ext4-without-formatting-the-hard-disk/2009/04/21](http://maketecheasier.com/how-to-upgrade-from-ext3-to-ext4-without-formatting-the-hard-disk/2009/04/21)

---

### Post by phillw on 2009-12-09
There are methods to convert ex3 to ext4 covered in the ext4 wiki, however - On the subject of ext4, I'm more concerned about this entry & have not had an answer to my question on it.

> **  For people who are running Ubuntu **

 Ubuntu 9.04 and later include ext4 as a manual partitioning option at installation time, including support for ext4 as the root filesystem. 
For people who are running Ubuntu, it is *highly* recommended that you download a set of modified util-linux packages and install them. Packages for Ubuntu Hardy are available [here]("ftp://ftp.kernel.org/pub/linux/kernel/people/tytso/ubuntu-fixed-util-linux").   These packages revert a [change made by Ubuntu]("http://changelogs.ubuntu.com/changelogs/pool/main/u/util-linux/util-linux_2.12r-19ubuntu1/changelog") to use the volid library instead of the blkid library. The volid library has a number of shortcomings, including that they don't work on freshly created filesystems or swap devices until after you reboot (since it is tied to udev probing) and the volid library doesn't understand ext4dev filesystems. The blkid library is much better, and Debian uses the blkid library for util-linux. Unfortunately, Ubuntu chose to make this decision for some unknown reason. For other versions of Ubuntu, the patch that was applied can be found [here]("ftp://ftp.kernel.org/pub/linux/kernel/people/tytso/ubuntu-fixed-util-linux/util-linux-patch"). 
 So, which flavour of ext4 should I use - the one every one else uses - or the one Ubuntu use ?

I'm not doing the convert twice - Once is quite scary enough !!

The Source of that ? -->  [http://ext4.wiki.kernel.org/index.php/Ext4_Howto](http://ext4.wiki.kernel.org/index.php/Ext4_Howto)

Phill.

---

### Post by Mark_in_Hollywood on 2009-12-09
For 

doas777

As I said, in this post, before I did a clean install of Karmic, I used a GParted LiveCD. While in the LiveCD session, I set the filesystem (OS & separate /home) to EXT4. I clicked "Apply". I waited. The GParted said it was "finished". That accomplished, I exited the LiveCD session. I took the "Desktop Install" disk I post about in this thread, loaded it, ran the install. The Karmic Koala OS was installed and the installation closed, reporting NO errors.

For

phillw

My understanding is that ext4 was not an "install time" option for Jaunty Jackalope (v. 9.04).  Rumors of trouble were rampant. I waited for 9.10. Canonical didn't make ext4 on the "Desktop CD" until Karmic.

As I said at the top of this thread, I used GParted LiveCD to convert ext3 to ext4.

Since this is not a post about "manually" changing from ext3 to ext4 as doas777 describes, via his link, I ask you both to help me with the problem in another manner, if you have knowledge of this type of problem I'm having.

---

### Post by phillw on 2009-12-09
Manually converting, or not - If you have the latest GParted and it says you are ext3, then, it seems it did not, in fact change over to ext4.

What does

```
df -T
```

Report ?

Phill.

---

### Post by Mark_in_Hollywood on 2009-12-09
Just enough to drive me NUTS!

mark@Lexington-19-karmic:~$ df -T
Filesystem    Type   1K-blocks      Used Available Use% Mounted on
/dev/sda1     ext4    11535344   4091624   6857752  38% /
udev         tmpfs      513184       320    512864   1% /dev
none         tmpfs      513184       500    512684   1% /dev/shm
none         tmpfs      513184       196    512988   1% /var/run
none         tmpfs      513184         0    513184   0% /var/lock
none         tmpfs      513184         0    513184   0% /lib/init/rw
/dev/sda5     ext4   288370908  33073944 240648500  13% /home

---

### Post by phillw on 2009-12-09
> **Mark_in_Hollywood said:**
> Just enough to drive me NUTS!

mark@Lexington-19-karmic:~$ df -T
Filesystem    Type   1K-blocks      Used Available Use% Mounted on
/dev/sda1     ext4    11535344   4091624   6857752  38% /
udev         tmpfs      513184       320    512864   1% /dev
none         tmpfs      513184       500    512684   1% /dev/shm
none         tmpfs      513184       196    512988   1% /var/run
none         tmpfs      513184         0    513184   0% /var/lock
none         tmpfs      513184         0    513184   0% /lib/init/rw
/dev/sda5     ext4   288370908  33073944 240648500  13% /home


Being an olde fashioned soul - I tend to trust the Command Line more than fancy GUI's ;-)

I'd say that is ext4 :-)

Phill.

---

### Post by phillw on 2009-12-09
Oh, and one short-coming in the current release of ext4, that they are working on ...

If someone buys you 1,048,577 one Terra-Byte drives ... It won't see the last one !!

The guyz reckon that 1 ExaByte will be enough for now, but - they're working on it ;)

Phill.

---

