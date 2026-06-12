---
title: "Partition Size for &quot;/&quot; - please help"
date: 2010-09-16
forum: Installation &amp; Upgrades
---

### Post by dmp2010 on 2010-09-16
I get a message that says,  "Not enough free disk space".

"The upgrade needs a total of 62.9M free space on disk '/'. Please free at least an additional 62.9M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'."

My partition sizes are:

/boot  256mb
/  3gb
/opt  4gb
/tmp  10gb
/usr/local  10gb
/var  80gb
swap 4gb
/home 80gb

The question i have is how big my "/" partition should be?


Thanks for help.

---

### Post by plucky on 2010-09-16
> **dmp2010 said:**
> I get a message that says,  "Not enough free disk space".

"The upgrade needs a total of 62.9M free space on disk '/'. Please free at least an additional 62.9M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'."

My partition sizes are:

/boot  256mb
/  3gb
/opt  4gb
/tmp  10gb
/usr/local  10gb
/var  80gb
swap 4gb
/home 80gb

The question i have is how big my "/" partition should be?


Thanks for help.

Why all the different partitions?


My system has a 10G / partition with the rest in /home and a separate /Storage partition on another disk.

This is my output to the **df-h** command ```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             9.9G  3.2G  6.2G  34% /
none                  245M  276K  245M   1% /dev
none                  249M  3.4M  246M   2% /dev/shm
none                  249M  320K  249M   1% /var/run
none                  249M     0  249M   0% /var/lock
none                  249M     0  249M   0% /lib/init/rw
/dev/sdb5              54G   32G   20G  62% /Storage
/dev/sda7              43G   18G   24G  44% /home

```


Good Luck

---

### Post by formaldehyde_spoon on 2010-09-16
> **plucky said:**
> Why all the different partitions?


My system has a 10G / partition with the rest in /home and a separate /Storage partition on another disk.



Snap!

---

### Post by psusi on 2010-09-16
Yea, why so many weird partitions?  There is no reason to have a /opt directory at all, let alone on its own partition.  /tmp is usually mounted as a ramdisk if anything.  Unless you are using an exotic filesystem for / that grub does not understand, there is no reason to have a /boot partition.  Unless you are running a massive web and/or mail server there is no reason to have /var on its own partition, let alone 80gb, and even then there isn't really any advantage.  And /usr/local?  Why?

---

### Post by pcal on 2010-09-16
> **dmp2010 said:**
> I get a message that says,  "Not enough free disk space".

"The upgrade needs a total of 62.9M free space on disk '/'. Please free at least an additional 62.9M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'."


What I think the other guys are suggesting, is that perhaps you should just start from scratch with your partition structure.

I'm no expert (I'm sure others could offer a more optimal solution), but what I have is about 5 gig for the swap partition, about 40% of remaining space into a /home partition, and whatever is left for the / partition.

The install will automatically allocate whatever other directories it needs within the / partition - so you don't need to specify them individually.

Pcal

---

### Post by dmp2010 on 2010-09-16
Thank you all for replying. I was following the partitioning guide offered at the following web site. I thought having separate partitions would make it easier to backup and restore. May be I am better of having only three partitions as plucky suggested.
 
[http://optics.csufresno.edu/~kriehn/fedora/fedora_files/f11/installation/partitions.html](http://optics.csufresno.edu/~kriehn/fedora/fedora_files/f11/installation/partitions.html)
 
Thanks.

---

### Post by snowpine on 2010-09-16
> **dmp2010 said:**
> Thank you all for replying. I was following the partitioning guide offered at the following web site. I thought having separate partitions would make it easier to backup and restore. May be I am better of having only three partitions as plucky suggested.
 
[http://optics.csufresno.edu/~kriehn/fedora/fedora_files/f11/installation/partitions.html](http://optics.csufresno.edu/~kriehn/fedora/fedora_files/f11/installation/partitions.html)
 
Thanks.

I see no mention of Ubuntu in that tutorial. :(

A better place to look is the Ubuntu documentation. The [System Requirements]("https://help.ubuntu.com/community/Installation/SystemRequirements") suggest a **minimum** of 5gb for / and 10gb for /home.

---

### Post by psusi on 2010-09-17
> **dmp2010 said:**
> Thank you all for replying. I was following the partitioning guide offered at the following web site. I thought having separate partitions would make it easier to backup and restore. May be I am better of having only three partitions as plucky suggested.
 
[http://optics.csufresno.edu/~kriehn/fedora/fedora_files/f11/installation/partitions.html](http://optics.csufresno.edu/~kriehn/fedora/fedora_files/f11/installation/partitions.html)
 
Thanks.

Wow that guy's nuts, don't listen to his advice ;)

Two or three partitions is more than enough.  Some people like to separate /home, but I generally find no benefit to this so don't bother.  About the only good reason I can think of to do so is so you can share your home directory between two different linux installs you are dual booting.

---

### Post by uRock on 2010-09-17
> **dmp2010 said:**
> The question i have is how big my "/" partition should be?
I use / (12GB) and /home, as I end up reinstalling every couple of months. It is nice not to have to restore all of my data from backups every time.

---

### Post by arubislander on 2010-09-17
> **dmp2010 said:**
> I get a message that says,  "Not enough free disk space".

"The upgrade needs a total of 62.9M free space on disk '/'. Please free at least an additional 62.9M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'."


/boot  256mb

...

The question i have is how big my "/" partition should be?

While there is merit in all the offered solutions, none has touched upon the original reason for your query here.

I am guessing that you were upgrading the kernel and there wasn't enough room in your /boot partition to extract the new one. A solution might be to remove any older kernel you're not using.

---

