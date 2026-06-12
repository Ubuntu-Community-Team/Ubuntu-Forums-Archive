---
title: "Can't Boot Vista after Ubuntu 8.04 install"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by matthiasj on 2008-04-26
Hey i'm having some serious problems.  I installed Ubuntu on my laptop that has vista installed and was hoping for a dual boot setup but now i can only boot ubuntu and no vista.  Bottom line, i need to remove this ubuntu or get my vista to boot, i have a lot of important files needed for school on vista and i cant loose these files.  

thank you so much!

---

### Post by matthiasj on 2008-04-26
bump

---

### Post by the8thstar on 2008-04-26
Hello there,

run the following command in the terminal

> sudo fdisk -l

and paste the results in your next answer. First I want to make sure you haven't erased Vista before we try anything else. We'll go more in depth afterwards.

---

### Post by matthiasj on 2008-04-26
> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9e86f523

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18662   149902483+  83  Linux
/dev/sda2           18663       19457     6385837+   5  Extended
/dev/sda5           18663       19457     6385806   82  Linux swap / Solaris


here it is

---

### Post by matthiasj on 2008-04-26
> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9e86f523

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18662   149902483+  83  Linux
/dev/sda2           18663       19457     6385837+   5  Extended
/dev/sda5           18663       19457     6385806   82  Linux swap / Solaris


here it is

---

### Post by tomsa on 2008-04-26
I'm sorry to hear that you're having problems.  I had a bit of trouble getting my laptop to dual boot vista and gutsy as well.  Hopefully this will help-  I haven't ried any of this with Hardy yet.

If you have a Vista disk, reboot from the disk as though you were going to do a fresh install.  When the disk loads, you'll be given two options- load vista, or fix vista.  You will want to fix vista.

When you are able to boot into vista again, dowload easyBCD:

[http://neosmart.net/dl.php?id=1]("http://neosmart.net/dl.php?id=1")

Install it into vista.  EasyBCD will allow you to load both ubuntu and vista using the vista bootloader.  Vista does not like GRUB. at all.

Then, follow the directions here:

[http://neosmart.net/wiki/display/EBCD/Ubuntu]("http://neosmart.net/wiki/display/EBCD/Ubuntu")

That should get you going.  let me know if this works, please- it did for me, but with gutsy.  I'd love to know if it works just as well with hardy.  good luck!

---

### Post by the8thstar on 2008-04-26
> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9e86f523

Device Boot Start End Blocks Id System
/dev/sda1 * 1 18662 149902483+ 83 Linux
/dev/sda2 18663 19457 6385837+ 5 Extended
/dev/sda5 18663 19457 6385806 82 Linux swap / Solaris 

I don't want to alarm you, but all I see there is Linux. No Vista. I'm afraid you've wiped out your Vista partition altogether during the setup process. This is why you can't dual-boot, since there is no more Vista on your computer. Sorry. :(

From here, what you can do is look for methods for recovering the deleted files on the forums. This may help you recover some/all of your Vista files.

---

### Post by matthiasj on 2008-04-26
i have 2 HP recovery discs i made when i got my laptop but it wont let me log into vista through them, only restore it.  

is there any way to access the files through ubuntu?

---

### Post by the8thstar on 2008-04-26
Like I said, your Vista partition is gone, which means also that YOUR FILES ARE GONE. Using the liveCD or the HP recovery disks is useless. 

Now the only way to retrieve your deleted files is to use specific software to recover the lost data. Check this: 
[http://ubuntuforums.org/showpost.php?p=4764158&postcount=14]("http://ubuntuforums.org/showpost.php?p=4764158&postcount=14") 
[http://ubuntuforums.org/showpost.php?p=4713206&postcount=2]("http://ubuntuforums.org/showpost.php?p=4713206&postcount=2")
[http://ubuntuforums.org/showpost.php?p=4740112&postcount=10]("http://ubuntuforums.org/showpost.php?p=4740112&postcount=10")


and tell me if it works for you.

---

### Post by matthiasj on 2008-04-26
i downloaded testdisc for linux and i cant get it to execute

---

### Post by the8thstar on 2008-04-26
What do you mean? Can you paste what the terminal returns in your next post?

---

### Post by matthiasj on 2008-04-26
i got it to install through the terminal by reading other posts but now i can't find or use the app. what command would run the application and restore my files?

---

### Post by the8thstar on 2008-04-26
do this:

> photorec /dev/sda

---

### Post by matthiasj on 2008-04-26
> matthiasj@matthiasj-laptop:~$ photorec /dev/sda 
PhotoRec 6.8, Data Recovery Utility, August 2007
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)

Unable to open file or device /dev/sda

Usage: photorec [/log] [/debug] [/d recup_dir] [file or device]

/log          : create a photorec.log file
/debug        : add debug information

PhotoRec searches various file formats (JPEG, Office...), it stores them
in recup_dir directory.

If you have problems with PhotoRec or bug reports, please contact me.


:(

---

### Post by the8thstar on 2008-04-26
Okay, try this:

> sudo photorec /d sda


If it doesn't work, try: 

> sudo photorec /d sda1

---

