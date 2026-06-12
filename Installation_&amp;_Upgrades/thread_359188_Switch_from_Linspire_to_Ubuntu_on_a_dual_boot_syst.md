---
title: "Switch from Linspire to Ubuntu on a dual boot system"
date: 2007-02-11
forum: Installation &amp; Upgrades
---

### Post by RobJN on 2007-02-11
Hi

I have read a few posts on dual booting Windows Xp and Ubuntu 6.10 but am still a bit confused and was hoping for some guidance.  (I am very new to linux)

My current setup is a dual boot system between Windows XP and Linspire.  However, i havent got on with linspire and would like to try out ubuntu.  I am a bit confused how to do this as i am unsure whether it will work after removing Linspire and what it put in the boot menu.

Ok, at the moment my single hard drive is partitioned as follows:

/dev/sda1            Fat32         4.31GiB      --- This was left on by computer manufacturer
/dev/sda2            NTFS         25GiB         --- This has Windows XP on it
/dev/sda3            extended   82.47GiB

     Under this extended partition I have:

     /dev/sda5         NTFS      67GiB          ---  I use this for my files under windows 
     /dev/sda6         reiserfs  15GiB          ---  Has Linspire on it

Now what confuses me is that i seem to have linspire on a extended partition, but from what i read Ubuntu has to be on a primary partition.  Is this right?  How should i go about removing Linspire and installing Ubuntu?  How should the drive be partitioned?

AND most importantly, now that i already have a boot menu from my Linspire installation, will the Ubuntu installation sort this out properly so that i can boot into ubuntu and windows?

Sorry to be a nuisance
Thanks in advance

(if you have any questions that you need to ask me first, i wont be able to reply until later tomorrow as i have a busy day)

Thanks again

---

### Post by RobJN on 2007-02-12
Well I've had more time to search for information to help out, and have found this:
[URL="http://help.linspire.com/cgi-bin/linspire.cfg/php/enduser/std_adp.php?p_faqid=65&p_created=1019517095&p_sid=lg6A*2ui&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9NTImcF9wcm9kX2x2bDE9JnBfcHJvZF9sdmwyPSZwX2NhdF9sdmwxPSZwX2NhdF9sdmwyPSZwX3BhZ2U9MSZwX3NlYXJjaF90ZXh0PXJlbW92ZSBsaW5zcGlyZQ**&p_li="]
Click here for Page on Linspire website[/URL]

So using that info i guess that i can now return my system to just windows xp and the spare partition, then simply install ubuntu as by dual boot instructions.

Probably wont get the chance to actually try it until late this week/ the weekend, but will post again if i am successful (or even fail!)

---

### Post by confused57 on 2007-02-12
> **RobJN said:**
> Well I've had more time to search for information to help out, and have found this:
[URL="http://help.linspire.com/cgi-bin/linspire.cfg/php/enduser/std_adp.php?p_faqid=65&p_created=1019517095&p_sid=lg6A*2ui&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9NTImcF9wcm9kX2x2bDE9JnBfcHJvZF9sdmwyPSZwX2NhdF9sdmwxPSZwX2NhdF9sdmwyPSZwX3BhZ2U9MSZwX3NlYXJjaF90ZXh0PXJlbW92ZSBsaW5zcGlyZQ**&p_li="]
Click here for Page on Linspire website[/URL]

So using that info i guess that i can now return my system to just windows xp and the spare partition, then simply install ubuntu as by dual boot instructions.

Probably wont get the chance to actually try it until late this week/ the weekend, but will post again if i am successful (or even fail!)

You should be able to install Ubuntu onto your current Linspire partition, Ubuntu will then overwrite the mbr with grub, which should enable you to boot Windows or Ubuntu.

If you have less than 1 Gb of memory, you may need to set up a swap partition.

Here's an excellent guide for installing with the Desktop cd:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

or alternate cd:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

