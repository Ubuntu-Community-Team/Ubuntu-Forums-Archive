---
title: "[SOLVED] never land between upgrade and new install"
date: 2008-06-15
forum: Installation &amp; Upgrades
---

### Post by rickyble on 2008-06-15
I was upgrading from 6.06 to feisty and now my system boots but xserver fails.  If I run apt-get -f install I have all these dependency missing.  If I check my version it still shows 6.06.2 LTS.  I am at a loss.  I started to just do a re-install but the live cds will not let me now.  I get the endless loop for not being able to find the block.  I seem to remember when I did the first install I had a problem with the system and I thought I used the ide=nodma at boot but it doesnt seem to work.  Im now stuck in the neverland between upgrade and nothing.  No new install no upgrade.  
Any help would be greatly appreciated.  
thanks

edit to add:

I did the apt-get -f install and redirected to a text file and it looks like I have a python version dependencies problem. There is a list that reads about 27 long for libs etc.

---

### Post by prshah on 2008-06-15
> **rickyble said:**
> Im now stuck in the neverland between upgrade and nothing.  No new install no upgrade.  



Take a look at my (solved) thread [http://ubuntuforums.org/showthread.php?t=780531](http://ubuntuforums.org/showthread.php?t=780531) on recovering a failed hardy upgrade. Maybe the same thing may work for a 6.06 upgrade.

You will need the "alternate" CD or a working internet connection.

Hope this helps.

---

### Post by rickyble on 2008-06-15
Finally got it back up using this
[http://ubuntuforums.org/showthread.php?t=186672](http://ubuntuforums.org/showthread.php?t=186672)
Looks like I have still have some updates that need to take place but it looks like from here it can be done thru the manager.

---

### Post by Dale61 on 2008-06-15
> **rickyble said:**
> I was upgrading from 6.06 to feisty and now my system boots but xserver fails.  If I run apt-get -f install I have all these dependency missing.  If I check my version it still shows 6.06.2 LTS.  I am at a loss.  I started to just do a re-install but the live cds will not let me now.  I get the endless loop for not being able to find the block.  I seem to remember when I did the first install I had a problem with the system and I thought I used the ide=nodma at boot but it doesnt seem to work.  Im now stuck in the neverland between upgrade and nothing.  No new install no upgrade.  
Any help would be greatly appreciated.  
thanks

edit to add:

I did the apt-get -f install and redirected to a text file and it looks like I have a python version dependencies problem. There is a list that reads about 27 long for libs etc.

Did you upgrade to Edgy first?  I'm of the understanding that you cannot go directly to Feisty from Dapper without upgrading to Edgy first.

However, you can now go from 6.06 LTS to 8.04 LTS without the steps in between.

---

