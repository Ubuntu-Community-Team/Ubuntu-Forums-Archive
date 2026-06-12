---
title: "Dual boot problems. Partitioning etc."
date: 2005-12-02
forum: Installation &amp; Upgrades
---

### Post by knobcottage on 2005-12-02
Hi! goes a bit like this.  I decided to try linux about a year ago and am slowly migrating.  I wanted to use debian but it seemed to hard.  I have two 40gig HD and currently have SUSE on one and Windows on the other.  I' going off SUSE since v 10 as nothing extra ships and it's a pain to find and instal it.  To the issue, SUSE has default installed and taken the whole of hdb.[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)
:confused:  It does not need 40gig.  I can't find a way to shrink SUSE to a smaller ammount as if I try to partition in SUSE it says hdb is busy and won't.  If I try to use LIVE UBUNTU it says the same.  Windows does not even see hdb.  I would like to keep SUSE and GRUB.  Any simple ideas.  Thanks!

---

### Post by lleb on 2005-12-02
[QUOTE=knobcottage]Hi! goes a bit like this.  I decided to try linux about a year ago and am slowly migrating.  I wanted to use debian but it seemed to hard.  I have two 40gig HD and currently have SUSE on one and Windows on the other.  I' going off SUSE since v 10 as nothing extra ships and it's a pain to find and instal it.  To the issue, SUSE has default installed and taken the whole of hdb.[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)
:confused:  It does not need 40gig.  I can't find a way to shrink SUSE to a smaller ammount as if I try to partition in SUSE it says hdb is busy and won't.  If I try to use LIVE UBUNTU it says the same.  Windows does not even see hdb.  I would like to keep SUSE and GRUB.  Any simple ideas.  Thanks![/QUOTE]

IIRC the newer vs of partition magic can see and manipulate Linux partitions.  so you can do that via windows, or you can reinstall SuSe and at that time resize the partitions to your desiered amounts.

---

### Post by knobcottage on 2005-12-02
Wow! how's that for a swift answer.  Thanks.  I'll give one of those a go. However,  I do not have partition magic and the last upgrade from Suse 9.3 to 10 took 4 hrs+ !!  (I have got a slow CD rom)  Is there a quicker/another option? (No disrespect intended for the superb advice so far)

---

### Post by lleb on 2005-12-03
[QUOTE=knobcottage]Wow! how's that for a swift answer.  Thanks.  I'll give one of those a go. However,  I do not have partition magic and the last upgrade from Suse 9.3 to 10 took 4 hrs+ !!  (I have got a slow CD rom)  Is there a quicker/another option? (No disrespect intended for the superb advice so far)[/QUOTE]

there is, but i am not skilled enough to detail it for you.  i know Knoppix has the ability to do something like that, but i do not know how.

---

### Post by amohanty on 2005-12-03
Boot off of an Ubuntu live cd 
use parted to manipulate the partitions.
[http://www.gnu.org/software/parted/manual/html_mono/parted.html#SEC25](http://www.gnu.org/software/parted/manual/html_mono/parted.html#SEC25)

HTH
AM

---

### Post by towsonu2003 on 2005-12-03
[QUOTE=amohanty]Boot off of an Ubuntu live cd 
use parted to manipulate the partitions.
[http://www.gnu.org/software/parted/manual/html_mono/parted.html#SEC25](http://www.gnu.org/software/parted/manual/html_mono/parted.html#SEC25)

HTH
AM[/QUOTE]

and back up your data!! :)

if it says 'partition busy' or something again, look under /media (in live cd) to see what's mounted. if you see one of the partitions in ther, just unmount it (sudo umount /media/whatever).

also, note somewhere what current /boot/grub/menu.list says for your suse, just in case, bf. the ubuntu install.

---

### Post by knobcottage on 2005-12-03
This help is excellent, but I'm still not there....yet.  I tried all this with live ubuntu, but according to the media "directory" the linux hard drive drive, the one with the hungry SuSe on it, it is not mounted, or was it that I couldn't unmount it... one of the two.  Anyway I can't make it say it's not busy.

---

### Post by lleb on 2005-12-03
[QUOTE=knobcottage]This help is excellent, but I'm still not there....yet.  I tried all this with live ubuntu, but according to the media "directory" the linux hard drive drive, the one with the hungry SuSe on it, it is not mounted, or was it that I couldn't unmount it... one of the two.  Anyway I can't make it say it's not busy.[/QUOTE]


then something is running off of that partition.

an other option (if you have 1G or more of ram) is to try the toram boot option as that will load EVERYTHING into your RAM and not touch any drives on the system, then you should be able to umount /dev/hdx

---

### Post by knobcottage on 2005-12-03
Help like this does not even come at a price.  Thanks.  I'm going to try again over the next few days, and return with a solution or the same problem.. Thnaks for the help...and by the way I've only just got 1 gig(hz) of processor, let alone ram!!  but keep the help coming.  I'll sort it out yet!

---

### Post by knobcottage on 2005-12-03
So I got ubuntu LIVE running and messed around a little not really knowing much about linux.  I found that the hdb was NOT mounted BUT in the dev folder (what's that?) where there appeared to be many hda b and c's I clicked on the  hdb and noticed that the permissions were all greyed out.  "You cannot change the permissions here as you are not the owner".  Is this a safety feature to prevent amateurs like myself buggering up the hard drive by mistake? It seem the  live repartition won't work....unless someone clever knows how to get round this...anyone????.  It's fun here and I'll get ubuntu installed somehow, I just don't want the four hour SuSe re-install specially if I can't find a way to get it to NOT eat the whole drive!!  Perhaps the install version in expert mode would do the trick.....if only I was an expert!

---

### Post by Cuppa-Chino on 2005-12-03
[QUOTE=amohanty]Boot off of an Ubuntu live cd 
use parted to manipulate the partitions.
[http://www.gnu.org/software/parted/manual/html_mono/parted.html#SEC25](http://www.gnu.org/software/parted/manual/html_mono/parted.html#SEC25)

HTH
AM[/QUOTE]

Although I am using (trying to) Ubuntu I actually use the Knoppix Live CD for the parted actions. It is very straight forward to do so - similar to the above PLUS you will find 101 explanations on the internet about it.

see also this thread[parition manager]("http://ubuntuforums.org/showpost.php?p=507531")

---

### Post by bwog on 2005-12-03
When you are booting from the live CD suse cant be running. Did you change the boot order to boot from CDROM?

This is the advantage of running gparted (the partitioning program) from the live CD: nothing is mounted when you are running the booted live CD.

"Windows does not even see hdb." I find that reassuring though :)

---

### Post by amohanty on 2005-12-03
One more thing - to see what processes are running off of the drive you can use the following command:

```
/usr/sbin/lsof
```

The manual is here:
[http://www.physiol.ox.ac.uk/Computing/Online_Documentation/lsof-quickstart.txt](http://www.physiol.ox.ac.uk/Computing/Online_Documentation/lsof-quickstart.txt)

Look at #4.

HTH
AM

---

