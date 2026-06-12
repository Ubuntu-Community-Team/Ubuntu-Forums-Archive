---
title: "Problem reverting to PHP 5.2 on Lucid"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by rsanchez1 on 2010-05-11
After upgrading to Lucid, I found that I still had a need for php 5.2, instead of the 5.3 that is installed during the Lucid upgrade. I tried the method found here:

[http://ubuntuforums.org/showthread.php?t=1447401&highlight=reverting+php5.2+lucid](http://ubuntuforums.org/showthread.php?t=1447401&highlight=reverting+php5.2+lucid)

I added in /etc/apt/preferences.d/php all the packages that I use for php, including libapache2-mod-php5, installed, and ran a2enmod php5 before restarting apache. However, my browser still tells me if I want to download php files on my server. I cleared the browser cache, a2enmod'ed again, restarted apache2 again, and still the same.

I'd appreciate some advice on how to get php scripts running again on apache.

EDIT: I should note I can get SOME php files parsed by apache, but some are not parsed. All files reside in some subdirectory of /var/www/.

---

### Post by VcDeveloper on 2010-09-02
What install program do you use to see the changes?    I ran the Synaptic Package Manager and didn't see any changes.  And what did they mean listing all the php packages you want installed?  May I see how your files look?  I would appreciate it!  Thanks!

---

### Post by VcDeveloper on 2010-09-03
I just rent back to 9.10 and locked php5.2.10 then upgrade to 10.04...

---

