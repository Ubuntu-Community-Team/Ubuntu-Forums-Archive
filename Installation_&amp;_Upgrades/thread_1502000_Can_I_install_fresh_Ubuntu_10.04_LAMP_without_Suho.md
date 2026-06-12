---
title: "Can I install fresh Ubuntu 10.04 LAMP without Suhosin?"
date: 2010-06-05
forum: Installation &amp; Upgrades
---

### Post by 5circles on 2010-06-05
I'm going crazy with the problem I posted on yesterday about Wordpress not working properly on my Ubuntu systems on the LAN. [http://ubuntuforums.org/showthread.php?t=1501043](http://ubuntuforums.org/showthread.php?t=1501043) 

After comparing results from phpinfo() with those from my public server, making a few adjustments and still seeing the same results, the biggest thing still to be tested is the Suhosin version of PHP.  My public server doesn't have the Suhosin version installed.  I can't figure out how to change the PHP to one without Suhosin, but I've seen some mentions of it not being installed by default on a fresh version of 10.04.

Is this true, and if so how can I build a LAMP server without Suhosin?

Suhosin may not be the problem, but I'd like to eliminate it before going further.

Thanks
Mike

---

### Post by wojox on 2010-06-05
It's not the Suhsion patch. Did you read the [WordPress troubleshooting]("http://codex.wordpress.org/Tools_Upgrade_SubPanel#Troubleshooting") ?

---

### Post by 5circles on 2010-06-05
> **wojox said:**
> It's not the Suhsion patch. Did you read the [WordPress troubleshooting]("http://codex.wordpress.org/Tools_Upgrade_SubPanel#Troubleshooting") ?

Yes, I've read this.  

1.  I'm properly connected to the Internet (whatever that means).  I can get the same file via wget.

2.  There is no .maintenance file.

3.  I've checked file ownership and permissions.   I copied all of the files from the public server to the private with wget, logged in as www-data (the user running apache). I've checked all the permissions, and also added an explicit upload_tmp_dir to php.ini (even though that wasn't on the public server).

So, if it isn't Suhosin, what is it?

Thanks
Mike

---

### Post by wojox on 2010-06-05
Don't remember is there a suhosin extension in php.ini you could comment out?

---

### Post by 5circles on 2010-06-05
> **wojox said:**
> Don't remember is there a suhosin extension in php.ini you could comment out?

The Suhosin documentation mentions that you can make adjustments in php.ini, but it doesn't seem possible to just switch it off.  

I've just installed 10.04 on a separate partition, but it seems that the PHP packages all have Suhosin included.

---

### Post by 5circles on 2010-06-14
I wasn't able to configure suhosin out, but it wasn't the problem.

---

