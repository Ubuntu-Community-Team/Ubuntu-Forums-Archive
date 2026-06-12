---
title: "Partitioning Crippled Encrypted Partition"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by lorenzgl on 2006-10-26
I hope this is the right forum for this problem:

I have installed edgy on a laptop with a 80 GB hard drive. Prior to installation the disk was devided into a 60 GB windows partition and a 20 GB partition that was encrypted with trucrypt.

When installing Edgy I used the manual partitioning option to cut out 20 GB from the windows partition to create a 512 MB swap and a linux partition. I did not change anything in the encrypted partition. 

It somehow had some problems and some error messages popped up during the later installation. I had to restart installation, but after that everything went fine.

Grub boot manager works and windows booted in the second atempt (in the first it forced chkdsk, did not find any errors, but later restarted before reaching the login screen).

However, now I cannot mount the truecrypt partition any more. Thats a bit of a let downer as all(!!!) my files, music, photos, ... is on there (and the last backup is half a year old).

Does anybody know what the partitioning could have done to the encrypted partition, and how, and why???

---

### Post by gn2 on 2006-10-26
> **lorenzgl said:**
> I hope this is the right forum for this problem:

I have installed edgy on a laptop with a 80 GB hard drive. Prior to installation the disk was devided into a 60 GB windows partition and a 20 GB partition that was encrypted with trucrypt.

When installing Edgy I used the manual partitioning option to cut out 20 GB from the windows partition to create a 512 MB swap and a linux partition. I did not change anything in the encrypted partition. 

It somehow had some problems and some error messages popped up during the later installation. I had to restart installation, but after that everything went fine.

Grub boot manager works and windows booted in the second atempt (in the first it forced chkdsk, did not find any errors, but later restarted before reaching the login screen).

However, now I cannot mount the truecrypt partition any more. Thats a bit of a let downer as all(!!!) my files, music, photos, ... is on there (and the last backup is half a year old).

Does anybody know what the partitioning could have done to the encrypted partition, and how, and why???

Do you have access to the encrypted partition from Windows?

If not, is it possible you installed Ubuntu to the wrong 20gb partition?

I like to keep partitions all different sizes, so that I can identify them by size alone.

---

### Post by lorenzgl on 2006-10-26
No, I can't access it from windows. And I am sure I installed it to the right partition. They are in fact of slightly different size.
But even if they weren't, the encrypted one had no file system assigned to it in the installation procedure. I'm sure ubuntu would have complained if I had tried to install it there?

---

### Post by gn2 on 2006-10-26
Ubuntu would probably have been able to wipe the encrypted partition away and create it's own file system during install. It can wipe away NTFS partitions nicely, for those wishing to fully convert.

If you're certain you installed to the correct partition then that can't be the problem.

I'm not familiar with the encryption software, but would it be possible to re-install it and see if that helps.?

Clutching at straws.....

---

### Post by orb9220 on 2006-10-26
Truecrypt for edgy is broken for now until someone recompiles it for edgy.

If truecrypt is critical then you will have to reinstall dapper then the deb for truecrypt 4.2a and see if it can see it.

That is why I create truecrypt file type of 4gb instead of partitions so I can move them around as individual files and backup to dvd. The 4gb limit  is for being able to also move to a fat32 partition which where they 
reside now.

I still havn't gotten truecrypt to run on edgy but someone should be posting the deb within the next month. Check out the truecrypt forums for     more help or info.

---

### Post by lorenzgl on 2006-10-26
I have to apologize. The partition is fine. The problem was that the keyfile got corrupted. No problem Ubuntu caused. :-~

I should have done the testing more carefully. But I got a bit freaked out when I thought I lost all my data.

Thanks to everyone who tried to help!

---

