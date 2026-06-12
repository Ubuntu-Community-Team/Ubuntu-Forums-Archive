---
title: "df and mount question"
date: 2005-08-22
forum: Installation &amp; Upgrades
---

### Post by rb123 on 2005-08-22
I have Ubuntu installed on a root partition, except for home and swap which are on their own partitions. I also have several other distros installed similarly. Recently, I screwed something up, and spent a while trying to understand some odd behaviour until I realized the following:

On boot, root is specified in /boot/grub/menu.lst. If a different root partition is listed in /etc/fstab, even a non-existent partition, there are no error messages (that I can find), and df and mount report the bogus partition as being mounted.

Is there some other way to query what is mounted on root? Am I doing something fundamentally wrong?

thanks,

rod

---

### Post by skoal on 2005-08-22
Well, what more than likely happened is that your Ubuntu kernel was mounted on one of those other distro partitions.  Then, that other distro fstab mounted what it normally would (as if you were using that distro's kernel) but were using the Ubuntu kernel.  No real harm there...

Both grub and mount (using fstab) will generate errors if a partition does not exist.  If it does exist, it could care less where you mount it as long as there's actually a partition there and that filesystem matches the fstab entry for it.  Mount will generate errors in those specific cases, normally to the console.

You can check the /var/log path in the files "syslog", "kern.log" and "messages" for some mount entries.  Outside of that, mount just looks at what is actually mounted in the /etc/mtab file.  You can see what is actually mounted and where:
> skoal@morpheus://~ $ df -Th
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda3 reiserfs    1.9G  1.4G  493M  75% /
tmpfs        tmpfs    380M     0  380M   0% /dev/shm
/dev/sda1 reiserfs     63M   38M   26M  60% /boot
/dev/sda4 reiserfs    6.6G  2.8G  3.8G  42% /data
/dev       unknown    1.9G  1.4G  493M  75% /.dev
none         tmpfs    5.0M  2.8M  2.3M  55% /dev

skoal@morpheus://~ $ cat /proc/partitions 
major minor  #blocks  name

   8     0    8965347 sda
   8     1      64228 sda1
   8     2     128520 sda2
   8     3    1951897 sda3
   8     4    6819592 sda4
which shows me what partition I'm using in the far left column (/dev/...) and where I'm mounting it in the far right (/<path>...).  You just need to remember what each partition is used for.  In my case (although not shown here above), when having multiple distros (or whatever) and multiple partitions, the size of the partition and the filesystem it uses will generally give it away and tell me.  sda6,reiserfs,4GB = / (Ubuntu) or sda9,ext3,3GB = / (Red Hat), etc.

What exactly happened in your case?  I find it hard to believe that grub used a /home parition as it's "root" and you were able to run the init scripts.  If it used an Ubuntu kernel and ran another distro (partition) init scripts, it may or may not have generated errors during that process.  If so, check those /var/log paths on those partitions.

\\//_

---

### Post by rb123 on 2005-08-22
Thanks for the reply. i was not exactly clear when i described my situation, but you are correct in that a valid root partition was accidentally mounted in place of the one I intended. And, when I referred to the mount command, I didn't make it clear that I was referring to its use to display currently mounted devices, rather than using it to mount a device. In that case, of course, it would generate an error message.

What perplexed me, and this time I'll try to be more complete, was this:

Somehow, I screwed up grub/menu.lst so that the incorrect partition was listed as root: the Ubuntu root that I intended to mount was at /dev/sdb5, and that is what I listed in my /etc/fstab file. I have my Ubuntu install mirrored (manually) on dev/sda5, with the same partition size, and that is what was mounted, as is clear from the log files.

However, the reason for my post is this: with /dev/sda5 mounted on root, df -Th and mount (with no args) both state that /dev/sdb5 is mounted on root, apparently because that is what /etc/fstab says.

I referred to non-existent partitions in an attempt to make clear how confusing this could be to a newbie like me. In order to see what I was misunderstanding, I intentionally put a non-existent partition in /etc/fstab for root, rebooted, did not see any error messages, and noted that both df -Th and mount state that the non-existent partition is mounted at root.

At the moment, my root is on /dev/sdb5, per menu.lst, but I put /dev/sdb14 as root in my fstab file to see what would happen.  I do not have a /dev/sdb14, as you will see below, but look at what df and mount think:

$ df -Th
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sdb14    ext3    7.4G  2.1G  4.9G  31% /                                         <======== sdb14 
tmpfs        tmpfs    443M     0  443M   0% /dev/shm
/dev/sdb12  reiserfs    5.6G  722M  4.9G  13% /home
none         tmpfs    5.0M  2.9M  2.2M  58% /dev



$ mount
/dev/sdb14 on / type ext3 (rw,errors=remount-ro)                                 <======== sdb14
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
/dev/sdb12 on /home type reiserfs (rw)
none on /dev type tmpfs (rw,size=5M,mode=0755)
usbfs on /proc/bus/usb type usbfs (rw)


and now cat /proc/partitions:

~$ cat /proc/partitions
major minor  #blocks  name

8     0  195360984 sda
8     1   19543041 sda1
8     2   48837600 sda2
8     3   90831510 sda3
8     4          1 sda4
8     5    7823623 sda5
8     6     987966 sda6
8     7    2939863 sda7
8     8    1959898 sda8
8     9    2939863 sda9
8    10    2939863 sda10
8    11    3911796 sda11
8    12    5863693 sda12
8    13    6779398 sda13
8    16  199148544 sdb
8    17   19543041 sdb1
8    18   48837600 sdb2
8    19   90831510 sdb3
8    20          1 sdb4
8    21    7823623 sdb5
8    22     987966 sdb6
8    23    2939863 sdb7
8    24    1959898 sdb8
8    25    2939863 sdb9
8    26    2939863 sdb10
8    27    3911796 sdb11
8    28    5863693 sdb12
8    29   10562706 sdb13     <==== sdb14 does not exist


Note that I do not have a /dev/sdb14, but df and mount think I do, simply because of an error I made in my /etc/fstab file. 

So, the question remains: is there a way to ask the system what is actually mounted on root? 

While this is clearly a case of garbage in (my fstab file), garbage out (df and mount using the only info they have, apparently), I'm beginning to wonder if specifying the root partition in two unrelated places, menu.lst and fstab, should be  reconsidered, since menu.lst is actually used, while fstab is used for reporting purposes. I'm thinking that it might make sense for people like me who constantly tinker with everything to intentionally put bogus values in fstab as a reminder that df and mount have no idea what is actually mounted on root.


rod

---

### Post by skoal on 2005-08-23
Ah, I gotcha.  I understand now.  Well, once grub is finished and passed to the kernel, at that point your filesystem _is_ mounted @ /dev/sdb5, not /dev/sd14 as reported by the GNU tool 'df' (and reflected in /etc/fstab, see below for explanation why).

The incorrect partition reporting of /dev/sdb14 (instead of the _actual_ /dev/sdb5 it's using) could be several things:

1. First, a little background info.  The seperate 'menu.lst' and '/etc/fstab' entries are intentionally seperate and uniquely different.  The first gets your root filesystem mounted, and the latter just mounts everything else, as described above for very specific reasons.  1) Imagine if grub used /etc/fstab entry to determine where to mount the root partition instead of using 'menu.lst'.  You wouldn't even be able to boot.  Grub would error out, so that's in small part reason for their seperation and qualifiable uniqueness.  2) fstab isn't just for "reporting" purposes.  In fact, in your specific case, mount is pretty "smart" (or "dumb") in that it went ahead and mounted all the other partitions despite one erroneous error, the root partition.  

2. Try and make an erroneous error in your /etc/fstab file for another partition _other_ than root which will be mounted.  It should generate an error report and consequently not mount it.  More importantly, try erroneously changing the "menu.lst" to root=/dev/sdb14 instead and see what happens.  You won't be able to boot.  Guaranteed!

* 3. What you are witnessing is how the /proc interface, /etc/mtab, GNU 'df' util, init scripts, and the kernel work together (or interact).  Check your /etc/mtab file for any possible discrepancies (as stated in my original post).  If none are shown there, then quite possibly, the 'df' GNU tool is using either '_PATH_MNTTAB' or '_PATH_MOUNTED' from glibc #defines.  The first is "/etc/fstab" and the latter "/etc/mtab".  So, more than likely, 'df' is using the first and just returning what it _sees_, not actually what was mounted specifically for / at boot.  You would need to dig deeper into the source for 'df' to see what it actually uses.  Even if it did use _PATH_MOUNTED, it's quite possible that /etc/mtab has already undergone a face change (from the init process, see 4. below)...

4. so, outside of all that voodoo magic required in mounting partitions at boot or later, /etc/mtab would be your best bet at actually seeing what's mounted, and where.  Check the '/etc/init.d' init scripts and you'll see how man times /etc/mtab gets tossed about and changed (at any given time during the init process).  NOTE: at some point during the init process, the kernel stops telling mtab what's mounted.  Other user space tools like mount take over and _may_ change it.  So, you may or may not be able to actually see what's really mounted for /, for your very _specific_ case.  

I hope that helps explain some things related to your own particular discovery process.  Where else to look for such accurate partition information is beyond me, but that's how I've always understood it.  The reason such an error may not show up in any log files has to do with when the / partition is actually writable, and consequently, when mount can actually notify the log daemons to record that discrepancy...

\\//_

---

### Post by Jenda on 2005-08-27
I have some trouble with mount too. It freezes the machine (mouse&keyboard not responsive) when I try to mount a non-existent partition (accidentally) or a FAT32 partition.
Anything I can do for it not to do that?

---

### Post by Jenda on 2005-08-27
Takeback: Not FAT32, forget that part, it's just with the non-existent partitions. Anyway, I downloaded Gparted and I'll prolly stick with that.

---

