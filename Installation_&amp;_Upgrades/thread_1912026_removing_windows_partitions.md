---
title: "removing windows partitions"
date: 2012-01-19
forum: Installation &amp; Upgrades
---

### Post by azurehi on 2012-01-19
My question is more Theoretical at this point:

I have an HP laptop running windows7.  Were I to use gparted to remove all partitions, including the HP recovery partiton, and the reformat to One partition to, say, Ext.4, would I be able then to install Ubuntu or another linux distribution?

I am not sure I want to do this but wonder whether the laptop would be usable for linux.  I know I could not re-install w7 without having the complete installation disc, not just the recovery discs.

I use Ubuntu exclusively on my desktop, but the computer was locally built with the full xp installation discs and no recovery partition like on the laptop.

Thanks for any comments.

---

### Post by Bucky Ball on 2012-01-19
Kill 'em with Gparted. You can create partitions (you are going to need more than one) during the Ubuntu install so don't bother about creating them beforehand.

/
/home
/swap

... is pretty basic. / = root where OS goes, 15-20Gb;  /home = where your personal data goes, as big as you like; /swap = swap, 2Gb plenty.

You have the option of creating recovery disks in Win7 for HP recovery. I would do this before you do anything. Do it twice to be safe.

---

### Post by raja.genupula on 2012-01-20
> **Bucky Ball said:**
> Kill 'em with Gparted. You can create partitions (you are going to need more than one) during the Ubuntu install so don't bother about creating them beforehand.

/
/home
/swap

... is pretty basic. / = root where OS goes, 15-20Gb;  /home = where your personal data goes, as big as you like; /swap = swap, 2Gb plenty.

You have the option of creating recovery disks in Win7 for HP recovery. I would do this before you do anything. Do it twice to be safe.
+1 
yeah! i like this way of doing installation . Even though some serious problem raised no problem to our personal information . Because of /home is a separate partition .Its safe. :)

---

### Post by azurehi on 2012-01-20
> **Bucky Ball said:**
> Kill 'em with Gparted. You can create partitions (you are going to need more than one) during the Ubuntu install so don't bother about creating them beforehand.

/
/home
/swap

... is pretty basic. / = root where OS goes, 15-20Gb;  /home = where your personal data goes, as big as you like; /swap = swap, 2Gb plenty.

You have the option of creating recovery disks in Win7 for HP recovery. I would do this before you do anything. Do it twice to be safe.

Thanks for your info.  So, you are saying that even though my laptop was produced by HP, complete removal of the windows partitions will Not result in the laptop being unusable Because the HDD was setup for windows and HP rescue?

---

### Post by nipunshakya on 2012-01-20
@azurehi: there is no problem for you to install ubuntu inside your machine after getting out windows 7 partitions. Just make sure that you create recovery disks for your current windows OS system(its important.) Rest, you can create your partitions as people above suggested.
Just make sure of how u partition your ubuntu filesystems and make sure to mount them properly as /, /home and swap area too....

I would suggest you read this once before proceeding:
[http://news.softpedia.com/news/Installing-Ubuntu-11-10-227809.shtml](http://news.softpedia.com/news/Installing-Ubuntu-11-10-227809.shtml)

Goodluck
Regards,WinuxUser

---

### Post by azurehi on 2012-01-20
> **WinuxUser said:**
> @azurehi: there is no problem for you to install ubuntu inside your machine after getting out windows 7 partitions. Just make sure that you create recovery disks for your current windows OS system(its important.) Rest, you can create your partitions as people above suggested.
Just make sure of how u partition your ubuntu filesystems and make sure to mount them properly as /, /home and swap area too....

I would suggest you read this once before proceeding:
[http://news.softpedia.com/news/Installing-Ubuntu-11-10-227809.shtml](http://news.softpedia.com/news/Installing-Ubuntu-11-10-227809.shtml)

Goodluck
Regards,WinuxUser

Thank you and others who responded...the information is most helpful.

---

### Post by azurehi on 2012-01-20
thank you all

---

