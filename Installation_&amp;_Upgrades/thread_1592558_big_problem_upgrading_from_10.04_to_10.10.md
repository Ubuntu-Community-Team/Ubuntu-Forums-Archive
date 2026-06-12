---
title: "big problem upgrading from 10.04 to 10.10"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by cwhitney24 on 2010-10-10
i upgraded from 10.04 to 10.10 from the update part of ubuntu.  after it  downloaded the necessary files and installed them it had to restart.   after restarting Ubuntu will not open up.  my computer will turn on the  the boot screen where i can choose from vista or ubuntu.  i choose  ubuntu and it comes up the no wubildr message then the next screen says  error: no suitable mode found.   Someone please help!  i dont know what  to do!

---

### Post by JackAcid on 2010-10-10
I have the same result after trying to upgrade via the update manager on my 64bit gateway NV79. Original installation of Ubuntu 10.04 was via wubi. what went wrong?

Please help! I now have only Windows7 as the only OS available. Guess it's a good thing I backed up all of my data!

---

### Post by cwhitney24 on 2010-10-10
> **JackAcid said:**
> I have the same result after trying to upgrade via the update manager on my 64bit gateway NV79. Original installation of Ubuntu 10.04 was via wubi. what went wrong?

Please help! I now have only Windows7 as the only OS available. Guess it's a good thing I backed up all of my data!


yeah dummy me i didnt back up anything.  i am hoping to hear an answer to fix this tonight.  if i dont get an answer back then i guess tomorrow ill have to just reinstall the whole thing.

---

### Post by Cathhsmom on 2010-10-10
> **cwhitney24 said:**
> yeah dummy me i didnt back up anything.  i am hoping to hear an answer to fix this tonight.  if i dont get an answer back then i guess tomorrow ill have to just reinstall the whole thing.
  

Are you able to see your Window files in Ubuntu?  If so, you can back it up now before reloading Windows, followed by Ubuntu.

---

### Post by cwhitney24 on 2010-10-10
> **Cathhsmom said:**
> Are you able to see your Window files in Ubuntu?  If so, you can back it up now before reloading Windows, followed by Ubuntu.

i cant get into ubuntu period.  after i went through the upgrade stuff it said it needed to restart.  once it did it wont let me load up ubuntu at all.

---

### Post by lm1980 on 2010-10-10
I like many have upgrade from 10.04 to 10.10.
my method was to burn the Alternate 10.10 upgrade.iso to cd and upgrade that way.

[http://cdimage.ubuntu.com/daily/current/maverick-alternate-i386.iso](http://cdimage.ubuntu.com/daily/current/maverick-alternate-i386.iso)

This worked for me with no issues.

My only issue over the upgrade is that bootup seems slower than 10.04 but I wont thread-jack on this issue, even though I was unable to reply to the correct thread.

Try my method.

---

### Post by biniou14 on 2010-10-10
My upgrade also failed (netbook edition)
When booting on 2.6.35-22-generic kernel, I've got two instances of an error missing reporting missing modules.dep file for this kernel. But boot process continues, ask me for the key storage password, and... nothing
When booting on 2.6.32-25-generic kernel, no error but same result

---

### Post by JackAcid on 2010-10-10
take a look here [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide) at the section "Can I back up the installation files?
If  you still have the C:\ubuntu\disks\root.disk file maybe your data is not gone after all. In reading the wubi guide I do not see that upgrade is supported for 10.04-> 10.10, and maybe that is the problem?

I may end up having to  reload as well , but it looks like there is a way to save the data.
Hope this helps!

---

### Post by bcbc on 2010-10-11
The 10.10 release notes state that wubi upgrades will fail.

The good news is that the upgrade is successful and your data is still there, just you can't boot it.

To get around it you can follow this note [http://ubuntuforums.org/showpost.php?p=9932369&postcount=5](http://ubuntuforums.org/showpost.php?p=9932369&postcount=5)

---

### Post by JackAcid on 2010-10-11
THANK YOU!
You have saved my linux install!
Excellent instructions  bcbc. I did not see the release note warning about wubi installs or I would not have tried it.

I used my 10.04 64bit live cd and was able to mount the hard drive from Nautilus, mount the virtual disk and then edit the grub.cgf file.

Ubuntu rocks! You are awesome!

And next time I will read the release notes more thoroughly (as well as backing up data).

---

### Post by vroberts on 2010-10-11
I upgraded from 10.04 to 10.10 on an MSI Wind (using the desktop version for both) and when I choose the 2.6.35-22 kernel I get a modprobe error that it can't find files in lib/kernel, and then procceds to boot, perhaps with an older kernel. 

If I choose the next older kernel at the Grub boot screen, all is OK. 

Vic Roberts

---

