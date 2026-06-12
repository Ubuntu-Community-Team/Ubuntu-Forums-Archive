---
title: "Installing with a SATA drive bringing up I/O errors"
date: 2006-11-15
forum: Installation &amp; Upgrades
---

### Post by vivi the mage on 2006-11-15
Hey all! 

I am not sure why I get this problem, but this is my first ubuntu install. I have xp pro sp2 on the hard drive. I have the drive partitioned into two spots 35 gb for windows (in use NTFS format) and the empty partition for ubuntu (about 2 gb)...

I load the CD from boot and press Enter and it gives me a screen where its loading I guess...takes about 2 minutes and I get a 

[171799719.940000] BUFFER I/O ERROR ON DEVICE HDA, LOGICAL BLOCK 85639
[171799726.940000] BUFFER I/O ERROR ON DEVICE HDA, LOGICAL BLOCK 85640

and it keeps doing this, scrolling down the screen, any ideas?

btw, I do have a SATA hard drive, my guess is this is the issue.

let me throw this on too : Its my work PC ( I am the IT guy here, so dont worry about it not being my PC ). It is a Dell Optiplex GX280.

---

### Post by wpshooter on 2006-11-15
Did you check the integrity of your Ubuntu Cd by running the verification test found on the initial Ubuntu boot screen menu ?

---

### Post by vivi the mage on 2006-11-15
> **wpshooter said:**
> Did you check the integrity of your Ubuntu Cd by running the verification test found on the initial Ubuntu boot screen menu ?

Yes and It ends up giving me these errors again! Do you think its the CD Rom drive?

I am installing version 6.10

---

### Post by nova- on 2006-11-15
make a new cd/dvd of ubuntu, and try again

or you could even make a new cd of some random 600mb file, burn it, then confirm that the hash of the file on cd is correct.
you can use fsum (google it) to make/check hashes.

generate a md5 hash from filename:
fsum -md5 c:\filename >c:\hash.txt

burn filename to cd.

verify the hash of the file on cd:
fsum -c -md5 f:\filename >c:\hash.txt

---

### Post by ebirkenes on 2006-11-15
I have exactly the same problem. 

I'm trying to boot the 6.10 cd on a laptop (An AOpen 1556 barebook). I have a IDE drive, but I get the same error as above. 
I checked the md5sum on the iso and burned it 2 times with nero on a brand new cd burner. Both cd's give the same error.

I don't think there is something wrong with the cd or cd drive.

Anyone have a clue?

---

### Post by ebirkenes on 2006-11-15
BTW, I just noticed that Vivi's error is on HDA so the SATA drive is probably not the problem. 
HDA is (probably) the CDROM, the SATA drive would be SDA. 
My error is on HDC wich is my CDROM.

So it seems to me it's a problem with the cdrom driver or something like that.



rgds

---

### Post by vivi the mage on 2006-11-16
looks like it was my CD drive...

the old CD drive burned it okay, but it was not working, so I replaced the drive and it booted, loaded, ran fine and I got it installed 100%!

but now I get something even weirder!

[http://www.ubuntuforums.org/showthread.php?p=1766821#post1766821](http://www.ubuntuforums.org/showthread.php?p=1766821#post1766821)

---

