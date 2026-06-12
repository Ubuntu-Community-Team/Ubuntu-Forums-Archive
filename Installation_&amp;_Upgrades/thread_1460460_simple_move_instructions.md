---
title: "simple move instructions"
date: 2010-04-22
forum: Installation &amp; Upgrades
---

### Post by sean13128 on 2010-04-22
I have been searching around for simple instructions on moving my old install of Ubuntu to my new Sdd with no luck. All I could find was some craziness about DD to the new drive and re aligning partitions.

I had a 500Gb HDD with a 40g Ubuntu partition that is now an external Hdd. I have installed a 40g SSD and installed Ubuntu 10.04 x64

The old hdd had the same install 10.04 x64 on it and had all updates and all the software that I use. 

My question is how do I keep from re downloading all the software and system updates? Can I just copy them over again. Re downloading them would be un wise on my now extremely slow connection.

Thanks 
Ubuntu tard

---

### Post by dominiquec on 2010-04-22
There are some helpful tips here: [http://ubuntuforums.org/showthread.php?t=1047072](http://ubuntuforums.org/showthread.php?t=1047072)

I think the safest way is to make a backup list of all your installed packages and restore to a new system.

---

### Post by sean13128 on 2010-04-22
I actually have the backup list but If I'm right I would be re downloading all of the items in that list. 

I I'm looking for some way to copy all the previously downloaded packages to the new machine. So that when I do the restore It just snags up the packages instead of re downloading.

---

### Post by grege on 2010-04-22
You need some sort of disk cloning software.

Not the answer to your problem

In /var/cache/apt/ you will find all of the deb files your old system downloaded - copy the whole folder across and then do a dist-upgrade and then install all of your other programs one by one - at least they will not have to be re-downloaded as they will already be there. I have never actually tried this so there may well be some enormous gotcha. Just a thought - try at own risk

---

### Post by sean13128 on 2010-04-22
> **grege said:**
> 
In /var/cache/apt/ you will find all of the deb files your old system downloaded - copy the whole folder across and then do a dist-upgrade and then install all of your other programs one by one - at least they will not have to be re-downloaded as they will already be there. I have never actually tried this so there may well be some enormous gotcha. Just a thought - try at own risk

Bingo. Love you

You just saved me about 3 days of downloading at 4k a sec

---

