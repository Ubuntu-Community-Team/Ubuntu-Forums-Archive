---
title: "Encryption"
date: 2007-11-16
forum: Installation &amp; Upgrades
---

### Post by derbert on 2007-11-16
I love Ubuntu and Linux, its the only OS on my laptop, and after installing 7.04 and having it upgrade to 7.10 I'm having no problems, but reading later I saw there is a different install where you can encrypt your hard drive. is this a good idea, does it work ok, I installed off an alternate cd is there a way to encrypt it now or do i have to do a fresh install?

---

### Post by tgcUbuntu on 2007-11-16
I have used dm-crypt & LUKS to encrypt a partition. Once I had it set up it was easy to use and seemed reliable. 
Here's a HowTo to set things up:
[http://ubuntuforums.org/showthread.php?t=404346&highlight=luks+aes](http://ubuntuforums.org/showthread.php?t=404346&highlight=luks+aes)

Once I got it all set up I created a script to mount & unmount the encrypted partition. I created a script named mountcrypt:

#!/bin/bash

case "$1" in
        mount)
                sudo cryptsetup luksOpen /dev/hda10 mydata
                sudo mount /dev/mapper/mydata /media/mydata
                ;;
        unmount)
                sudo umount /media/mydata && sudo cryptsetup luksClose mydata 
                ;;
        *)
                echo "Usage: mountcrypt [mount|umount]"
                ;;
esac

exit 0


To mount  it:        mountcrypt mount
and to unmount: mountcrypt unmount

After mounting the partition you just access data on it as usual.

I have this on a 7.04 installation and haven't tried it on my Gutsy installation yet.

---

### Post by petteriIII on 2007-11-17
I have completed a method to transfer all the user-data and partially the functioning of PC when the whole disc is encrypted - it is not in English so I don't enclose it.I don't think that cloning of encrypted volumes is security risk - the encryption-keys do function as before, and the security-keys needed by BIOS could be transfered also. 
But these procedures require so much work that I believe that before people begin to use encryption the copying (=cloning) must operate. Does anybody know if cloning-methods are arriving ?

---

### Post by dangermouse28 on 2007-11-19
As I have a laptop, I wanted the whole thing encrypted.

BIG MISTAKE

To sum it up, after using the alternate CD and encryption to install Gutsy, it needed a load of updates immediately, very slow to boot (>3mins), wouldn't shut down and had loads of freezing / networking issues.

After struggling with it for a week, in desperation I re-installed using the Live CD. No encryption with this one, but everything worked a treat - no freezing or network problems, it boots in 60 secs and shuts down when it's told.

There are big differences in the Alternate and Live installations  - the Alternate behaves like a bad Beta version. Not good.

---

### Post by Seisen on 2007-11-19
You can always make a small partition and make it encrypted instead of using the whole hard drive.

---

