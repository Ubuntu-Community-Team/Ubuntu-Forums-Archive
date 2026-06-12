---
title: "Dual Boot with 8.04 &amp; 10.04?"
date: 2010-06-11
forum: Installation &amp; Upgrades
---

### Post by colintivy on 2010-06-11
Hi!

I use a single laptop with 8.04 running and am considering installing 10.04 in a dual boot system. I am very loath to lose Hardy until I have Lynx fully up and running. From what I have seen there are pitfalls ahead which may be difficult to sort without a means to get back onto the net. I know that I can try the new OS without installing it, I have the 10.04 CD from Linux Format which has some additional apps which are useful but Whether this allows a comprehensive run-through I rather doubt. I know that speed of use from the CD will be slow.

There seem to be issues with USB, Grub2, ext4 and finding hardware for starters,all of which are needed. Reading posts from other posts makes for sombre thoughts. Do I hear of 10.04.1 soon with some bug fixes??

I would have the option of doing a clean install on a 80GB USB HD in an external enclosure. Do I presume correctly that this would have to be formatted to ext4? are there any problems with dual booting with the two HDs apart from tweaking the BIOS?

I intend to put my existing /home onto a separate partition before mucking about. What is the drill to allow the newer OS to use it after installation? Note that all the data in it will be on ext 3. There seems to be a possible conflict when Lynx gets going if all its files will be on Ext4 or will there be some legacy support? 

All the info that I have seen do not cover 2 x linuxes in one or two HDs. Hence my plea for help.

Thanks in advance.

colintivy :confused:

---

### Post by oldfred on 2010-06-11
Dual boot info:
Dual boot 2 drives
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)


I have three drives with XP, 9.04, 9.10  & 10.04. I had upgraded in place from about 6.06 to 9.04 and then decided to do a clean install. I moved /home to a 100GB partition (new drive so lots of room), but then moved all my data to /data. My /home is now 1GB still in the 100GB (needs shrinking). I would not assume you can go back to 8.04 with /home once settings start getting updated. I kept my 9.04 incase their were settings I missed, but only had to boot it once or twice to find something.

You can export all your programs and it will install the newer versions. I did that but had not housecleaned before and it reinstalled some things I really did not want or need (like python 2.5).

sudo cp /etc/apt/sources.list ~/sources.list.backup
Otherwise if you have added any PPAs or other sources, this tip won't work.
generate new sources file

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

---

### Post by colintivy on 2010-06-12
Thanks oldfred!

Impressed by erudition as well as hardware. Now feels very inferior. Will give some time to looking into your refs. They look like the ones that I want. Will come back if trouble erupts!!

:D :D

---

### Post by colintivy on 2010-07-20
@ oldfred,

I am a bit mystified, After a bit of trouble with grub2 over-writing grub on my laptop HD which has now been resolved, I have 9.10 safely installed on a USB 80GB HD (because the 10.04 Live DVD insists that I have it installed by going straight to the Log-In panel instead of the Live CD option, so I tried 9.10 which installed perfectly!). The laptop BIOS only allows booting from one HD which is the internal one with 8.04 on it. It seems that grub and grub2 are incompatible, also Ext3 and Ext4 are incompatible. Both of which look like being difficult. Is there a work-round possible?

:confused:

---

### Post by oldfred on 2010-07-20
Both Karmic & Lucid also use old grub as an alternative boot loader for upgrades. But Ubuntu updated grub legacy with 9.04 to read ext4 partitions so older version of grub legacy will not work with ext4 partitions.

The easiest solution is just to let grub2 control booting. You will be able to boot either system but will have grub2 in the BIOS. The disadvantage is if the rest of grub2 is in the external then you would not be able to boot without the external. You could create a separate grub2 partition on the internal just for booting.

Is system so old that the BIOS does not allow USB booting? The standard recommendation is to install grub2 to external with the newer Ubuntu and boot from the external and not change the internal.

Grub2
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition_]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition_")

To see where everything is at:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by colintivy on 2010-08-10
@oldfred.

Just got back to problem. Interested in BIOS with USB booting facility. Sadly BIOS is pre 2000 and presumably does not have it (although machines have USB but not USB2). How does one go about updating the BIOS since it is in CMOS??

:confused:

---

### Post by oldfred on 2010-08-10
If the system is that old you probably cannot get a BIOS update that will include USB booting. You have to go to the vendor and see if they have any updates for your model PC. BIOS are unique to each system.

There are some work arounds that can use either a CD or Floppy to boot and then load a system from USB but if it is the older version of USB it will be very slow. Even USB2 is somewhat slow compared to SATA or PATA internal drives.

---

### Post by colintivy on 2010-08-11
Thanks, I have posted in Dell support to see. Dell website does not list the Optiplex110 so seemingly I cannot ask them but will persevere.

  :D

---

