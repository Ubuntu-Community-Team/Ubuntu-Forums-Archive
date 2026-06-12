---
title: "A piece of advice needed"
date: 2007-09-12
forum: Installation &amp; Upgrades
---

### Post by cursebg on 2007-09-12
Hi people,

I'm just installing Kubuntu 7.04 and I noticed that I could use the option for having different volumes for /  , /usr , /home , etc... And I'm wondering which is the best way for setting up the partitions, which file system, what size is best for them, etc...

I have two HDDs, 30 GB free on the first na 22 on the second and I wanna have a free partition for trying some other distros :)

Thanks

---

### Post by gautada on 2007-09-12
If you are just testing then create / for 10-15 GB and get to it.  For desktops this is what I generally do to cut down complexity.  For my servers I use the following layout.  But I also use LVM and a RAID system which is more than what you are asking.  

> 
 $ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             950M  437M  465M  49% /
udev                  754M  808K  753M   1% /dev
/dev/mapper/system-home
                       35G   21G   13G  63% /home
/dev/mapper/system-usr
                       20G  7.9G   11G  43% /usr
/dev/mapper/system-tmp
                      5.0G  378M  4.4G   8% /tmp
/dev/mapper/system-opt
                      9.9G  564M  8.8G   6% /opt
/dev/mapper/system-var
                       20G  3.5G   16G  19% /var
/dev/mapper/system-emulators
                       13G  6.6G  5.8G  54% /home/emulators
/dev/mapper/system-music
                      9.9G  5.6G  3.9G  60% /home/music
/dev/mapper/system-other
                      9.9G  8.0G  1.5G  85% /mnt/other
/dev/mapper/system-bak
                      8.9G  8.7G     0 100% /mnt/bak
/dev/mapper/system-movies
                       15G   14G  642M  96% /home/movies
/dev/mapper/system-iso
                      3.0G  2.9G     0 100% /home/iso
shm                   754M     0  754M   0% /dev/shm


Note: You don't need the /home/movies or /home/<whatever> it was just easier to post everything

---

### Post by cursebg on 2007-09-12
> **gautada said:**
> [QUOTE]If you are just testing then create / for 10-15 GB and get to it.
I'm switching to it for as long as possible... :)

And according to the quoted maybe I should do like this:

hda:
hda1 - ext3 - / - 4 GB
hda2 - reiserfs - /usr - 4 GB
hda3 - swap - none - 550 MB (my RAM is 256)
hda4 - ext3 - none - 7 GB (for testing)
hda5 - ext3 - none - 6,5 GB (storage?)

hdb:
hdb1 - ext3 - /home - 21,5 GB
hdb2 - swap - none - 500 MB


I'm totally not sure about size of partitions...

---

### Post by gautada on 2007-09-14
If you are looking for long term then I would highly suggest [LVM]("http://www.tldp.org/HOWTO/LVM-HOWTO/"). A more Ubuntu friendly [HOWTO]("http://www.debuntu.org/how-to-install-ubuntu-over-lvm-filesystem")

---

