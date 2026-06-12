---
title: "Ubuntu upgrade from 16.04 LTS to 17.10 leaves a huge of amounts of files"
date: 2017-10-30
forum: Installation &amp; Upgrades
---

### Post by munichmachine59 on 2017-10-30
Hello 

I have upgraded from 16.04 to 17.10, and the following set is a huge amounts of files :

/dev/mapper/ubuntu--vg-root      287G   16G   257G    6% /

Is there a way to minimize that. 16GB is way to much. I have deleted every old kernel and their DEV / devel files. I've cleaned APT and other temp files. I have used the program Stacer to see if there was some other files to delete. I have deleted all Unity files. So there is more to do I think.

---

### Post by deadflowr on 2017-10-30
How are your partitions actually laid out?
look at
```
df -h
sudo parted -l
sudo fdisk -l
```

---

### Post by munichmachine59 on 2017-10-30
```
df -h :

udev                             2,9G     0   2,9G    0% /dev
tmpfs                            588M   18M   571M    3% /run
/dev/mapper/ubuntu--vg-root      287G   16G   257G    6% /
tmpfs                            2,9G   25M   2,9G    1% /dev/shm
tmpfs                            5,0M  4,0K   5,0M    1% /run/lock
tmpfs                            2,9G     0   2,9G    0% /sys/fs/cgroup
/dev/sdb2                        237M   73M   152M   33% /boot
/dev/sdb1                        511M  4,6M   507M    1% /boot/efi
tmpfs                            588M   20K   588M    1% /run/user/126
tmpfs                            588M  6,1M   582M    2% /run/user/1000
```

There is so many tmpfs. But there's root with 16GB of data. That must be wrong.

---

### Post by deadflowr on 2017-10-30
Looks normal to me.
You only have a single lvm partition --thingy.
So all your personal files are also inside that one.
what does something like
```
du -sh ~
```
show?
that should list disk usage of your home folder
(The last line will show total; or total of what the system is able to read, any files or folder erroneously saved in your home folder as root or other user than you might not be readable and will show as Permission denied in the output, for what it's worth)

---

### Post by mörgæs on 2017-10-30
Please edit your post and add CODE tags around the output. Makes it more pleasant and less error-prone to read.

---

