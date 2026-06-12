---
title: "How to migrate a 11.10 system into a newly installed 12.04?"
date: 2012-05-10
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2012-05-10
Over the years I have upgraded and got so less and less space. 

I bought a 3T Sata hard disk and just finished the installation of 12.04
To make sure that nothing goes wrong, I unplugged the old IDE hard disks.

Now, I would like to migrate most of the things from the IDE hard disks.

1. Firefox
2. Thunderbird
3. my web sites, located at the old drive /var/www and /var/www-ssl

all others can wait.

How to do, and what to take care of?

I guess Firefox and Thunderbird I need just to find the link of the description, I am sure hundreds have done that already.

More problem I see with the web sites, which are mysql supported. Is there a way to copy just the mysql data files over? 

Thanks for your help!

bye

Ronald

---

### Post by kurt18947 on 2012-05-10
Do you know about Firefox' sync?  It works pretty well for me.  I don't sync passwords though, I don't have THAT much confidence in sync security.  If you have quite a few saved passwords, you could use something like Password Exporter in the add-ons.

For Thunderbird, you should be able to copy your current .thunderbird profile in your home folder to a portable device then copy it to the new install.  Do make sure the I.D. (some alphanumeric gibberish)  in profile.ini is the same as the name of the folder.  My success in doing this is mixed so if someone else has a better explanation I hope they'll chip in.

For web sites, I have no clue, sorry.

---

### Post by zombifier25 on 2012-05-10
For Firefox, copy the .mozilla folder in your old home folder to the new one. For Thunderbird, .thunderbird. Remember to delete the existing folders before copying.

---

