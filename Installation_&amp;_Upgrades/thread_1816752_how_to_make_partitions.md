---
title: "how to make partitions"
date: 2011-08-02
forum: Installation &amp; Upgrades
---

### Post by Kind_Man on 2011-08-02
Hello everyone
I'm new to the linux just few days ago, tried my slef to install Ubuntu on my laptop then I have help of friend to install Opensuse for me in my laptop I face problems with Opensuse and couldn't solve it so my friend install the Ubuntu in the free partition which was 120Gb, and the rest of the 320Gb was dedecated to the OpenSuse, I see no use of having OS with problems in my laptop so I wonder how can I install Ubuntu once again in my laptop and give it the entire 320Gb at least to be usable in storage data
my laptop is dell xps it seem work fine with ubuntu
Model M1330
RAM is 4 Gb I think of upgrade it to 8 if it work with it
HHD is 320Gb 7200rpm
I'll be thankful to show me how I can use the maximum HHD size for Ubuntu 
I'll use Ubuntu 10.04 LTS  64bit
thanks in advance

---

### Post by Beacon11 on 2011-08-02
The installer will take care of this for you. Check out [http://techie-buzz.com/foss/ubuntu-10-04-lts-installation-guide.html](http://techie-buzz.com/foss/ubuntu-10-04-lts-installation-guide.html) . On the Prepare Disk Space step, simply select "Erase and use the entire disk" and complete the installation.

---

### Post by grahammechanical on 2011-08-02
Hi Welcome to the forums. May I make a suggestion?  Study this

[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

If you are willing to re-install Ubuntu then do some experimentation. Choose the Do Something Else option and reduce the 120GB partiton to about 20-25GB and give it a mount point of /, a format of ext4 and to be formatted. Then enlarge the 320GB partiton to take up the unused space and give it the mount point of /home, a format of ext4 and to be formatted (you will loose any data, so back up). You can set the same swap partition to mount point /swap.

What this will do is install Ubuntu in the 25GB partition and set the rest of the disk (the /home partition) to be the home folder where all the data and settings are stored.

The advantage of doing this is that if you need to re-install Ubuntu in the future you will not loose your data or settings. You just tell the installer to put Ubuntu in the / partition and you do not tell it to format the /home partition and everything will be safe.

Regards.

---

### Post by Kind_Man on 2011-08-03
thanks a lot for passing by and help me out

---

### Post by Beacon11 on 2011-08-03
No problem :) . If your issue is solved, could you please mark the thread as such?

---

### Post by Kind_Man on 2011-08-03
> **Kind_Man said:**
> thanks a lot for passing by and help me out
that's brilliant dear [grahammechanical ]("http://ubuntuforums.org/member.php?u=1087323")
that's what i'm looking for make partition in way that I can have the big size of the HHD as storage place and safe in case of reinstall or damage in OS 
[]("http://ubuntuforums.org/member.php?u=1087323")

---

### Post by Beacon11 on 2011-08-03
> **Kind_Man said:**
> that's brilliant dear [grahammechanical ]("http://ubuntuforums.org/member.php?u=1087323")
that's what i'm looking for make partition in way that I can have the big size of the HHD as storage place and safe in case of reinstall or damage in OS 
[]("http://ubuntuforums.org/member.php?u=1087323")

Just make sure you leave enough space on the root partition for updates and extra software (especially if you play games). It sucks to run out of room.

---

### Post by Kind_Man on 2011-08-03
surely your option is great option, but I like the idea of [grahammechanical  ]("http://ubuntuforums.org/member.php?u=1087323")[URL="http://ubuntuforums.org/member.php?u=1087323"]_I might go with the other option I know it might be tricky and hard but I'll go for it_
[/URL]

---

### Post by Beacon11 on 2011-08-03
> **Kind_Man said:**
> surely your option is great option, but I like the idea of [grahammechanical  ]("http://ubuntuforums.org/member.php?u=1087323")[URL="http://ubuntuforums.org/member.php?u=1087323"]_I might go with the other option I know it might be tricky and hard but I'll go for it_
[/URL]

Haha, I'm not pouting-- grahammechanical's method is definitely the way to go! I just wanted to make sure you were aware.

---

### Post by Kind_Man on 2011-08-03
> **Beacon11 said:**
> Haha, I'm not pouting-- grahammechanical's method is definitely the way to go! I just wanted to make sure you were aware.
thanks Man, I do really appreciate your care and great help to be honest you taught me by writing me I wasn't aware of what you said and your open my mind on new thing, my mind still work with the windows OS way, thanks again

---

