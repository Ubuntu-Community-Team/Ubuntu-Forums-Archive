---
title: "My root partition just keep filling up"
date: 2023-04-16
forum: Installation &amp; Upgrades
---

### Post by robertcull1 on 2023-04-16
In the past what I have done is to increase the root partition size by 10Gb. But eventually it just fills up.


I am not exactly sure why this is happening.

---

### Post by MAFoElffen on 2023-04-16
Please post the output of this, within CODE Tags:
```

sudo du -h --max-depth=1 / 2> /dev/null | sort -r

```
That will show the main directories off of root and where space is being used. Once we see that, then we can drill down on what seems abnormal, and see what is using up your space.

---

### Post by robertcull1 on 2023-04-16
```

8.9G	/usr
841M	/opt
5.8M	/lib32
509M	/boot
41G	/home
4.0K	/srv
4.0K	/lib64
4.0K	/cdrom
36K	/.sblvtmp
28K	/mnt
2.5G	/lib
23M	/etc
2.1M	/run
20G	/snap
203M	/root
195G	/
180K	/tmp
17G	/var
16K	/lost+found
13M	/sbin
13M	/bin
105G	/media
0	/sys
0	/proc
0	/dev



```

---

### Post by yancek on 2023-04-17
You can see in your output the largest directory is /media.  That is where external drives are usually mounted so we don't know exactly what that is, the same drive, a different drive (internal/external)??  The 2nd largest directory is /var which contains log files.  You can delete these files, oldest first as new ones are created while using the computer.  This (/var directory) is often the source of this problem.  You need to be root (use sudo) to delete files there.  To see the largest directories under /var, run the following command:

>  sudo du -h --max-depth=1 /var 2> /dev/null | sort -r

---

### Post by robertcull1 on 2023-04-17
I used these commands to delete a lot of files. Now I have 24G free.

```

cd /var/log/journal
sudo rm -r *
sudo apt purge snapd
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

```

Thanks!

---

### Post by ActionParsnip on 2023-04-17
What is the output of
```

df -Th

```

---

### Post by robertcull1 on 2023-04-17
```

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  7.7G     0  7.7G   0% /dev
tmpfs          tmpfs     1.6G  1.8M  1.6G   1% /run
/dev/sdb1      ext4       44G   24G   18G  57% /
tmpfs          tmpfs     7.7G   63M  7.6G   1% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     7.7G     0  7.7G   0% /sys/fs/cgroup
/dev/sdb3      ext4      103G   96G  1.7G  99% /media/robert/Extra
/dev/sdb2      ext4       84G   41G   39G  52% /home
tmpfs          tmpfs     1.6G  136K  1.6G   1% /run/user/1000

```

---

### Post by ActionParsnip on 2023-04-17
> **robertcull1 said:**
> ```

Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  7.7G     0  7.7G   0% /dev
tmpfs          tmpfs     1.6G  1.8M  1.6G   1% /run
/dev/sdb1      ext4       44G   24G   18G  57% /
tmpfs          tmpfs     7.7G   63M  7.6G   1% /dev/shm
tmpfs          tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs          tmpfs     7.7G     0  7.7G   0% /sys/fs/cgroup
/dev/sdb3      ext4      103G   96G  1.7G  99% /media/robert/Extra
/dev/sdb2      ext4       84G   41G   39G  52% /home
tmpfs          tmpfs     1.6G  136K  1.6G   1% /run/user/1000

```

Then your root file system isn't full. You have just under half free. Your external drive is nearly full. This isn't your root file system

---

### Post by TheFu on 2023-04-17
Manually deleting files in /var/log/journal isn't exactly safe.  They are a pseudo-DB.  The "correct" way to manage logs is through journald.conf and the journalctl command. Some examples for cleaning.

```
  journalctl --disk-usage   # See log file disk use
  sudo journalctl --vacuum-size=200M    # Drop log file size to 200M, if possible.
  sudo journalctl --vacuum-time=10d     # Drop logs, over 10 days old
```

But the "more correct" answer is to set the maximums in journald.conf to prevent stuff like this from happening.  The manpage for journald.conf explains all the settings in that file.

---

### Post by TheFu on 2023-04-17
> **MAFoElffen said:**
> 
```

sudo du -h --max-depth=1 / 2> /dev/null | sort -r

```


That command found about 16TB on my systems and took forever to run.  Then the results weren't sorted correctly.
If the error says the file system (or mount) that is full, we can limit the search to just that file system.

```
sudo du -xh --max-depth=1 {mount point} 2> /dev/null | sort -h
```
That will use "human" du output AND a human sort.  The largest directories will be at the bottom, so we don't need to scroll up 5 pages to see the largest directories.

For example, 
```
$ sudo du -xh --max-depth=1  /  2> /dev/null | sort -h
...
27M     /etc
1.4G    /lib
6.2G    /home
7.2G    /var
8.0G    /usr
23G     /

```
That doesn't always tell the full story.  **df** can show a summary of mounts.  With the correct options, all the junk is filtered out.
```
$ df -hT -x squashfs -x tmpfs -x devtmpfs
Filesystem                        Type  Size  Used Avail Use% Mounted on
/dev/mapper/hadar--vg-root        ext4   32G   23G  7.5G  76% /
/dev/sdb1                         ext2  719M  217M  466M  32% /boot
/dev/mapper/hadar--vg-lxd--lv     ext4   59G   14G   42G  25% /var/lib/lxd
/dev/mapper/hadar--vg-libvirt--lv ext4  173G  131G   33G  81% /var/lib/libvirt
/dev/mapper/vg--hadar-lv--backups ext4  459G   88G  371G  20% /Backups
istar:/TV                         nfs4  294G  121G  173G  42% /TV
```
That df only shows "real" storage, not fake stuff like bind-mounts, snaps, or pseudo-file systems which don't actually take any space that isn't accounted for in the "real" storage mounts.  The "mapper" lines are because I use LVM on that system.

Beware that BTRFS lies about the storage used.  That's the cost of the advanced features it provides.
On another system, 
```
$ sudo du -xh --max-depth=1  /  2>/dev/null | sort -h
1.0K    /cdrom
1.0K    /d
1.0K    /media
1.0K    /mnt
1.0K    /opt
47K     /tmp
58K     /home
23M     /etc
250M    /var
[B]6.9G    /usr
7.2G    /
[/B]
```
So, on that system, almost all the used storage is for the OS.  The df output makes less sense because it is a ZFS file system - that's also an advanced file system. Here's what that looks like (though only helpful to recognize it, not really for and data). I got tired of typing all those options, so an alias is used:
```
$ dft
Filesystem                                       Type  Size  Used Avail Use% Mounted on
rpool/ROOT/ubuntu_d0wbmk                         zfs    25G  6.8G   18G  28% /
rpool/USERDATA/jp_5njgy6                         zfs    28G  9.3G   18G  35% /home/jp
rpool/mydataset                                  zfs   2.0M  128K  1.9M   7% /media/mdata
rpool/ROOT/ubuntu_d0wbmk/var/games               zfs    18G  128K   18G   1% /var/games
rpool/ROOT/ubuntu_d0wbmk/var/lib                 zfs    18G   27M   18G   1% /var/lib
rpool/USERDATA/root_5njgy6                       zfs    18G  384K   18G   1% /root
rpool/ROOT/ubuntu_d0wbmk/usr/local               zfs    18G  256K   18G   1% /usr/local
rpool/ROOT/ubuntu_d0wbmk/var/mail                zfs    18G  128K   18G   1% /var/mail
rpool/ROOT/ubuntu_d0wbmk/srv                     zfs    18G  128K   18G   1% /srv
rpool/ROOT/ubuntu_d0wbmk/var/log                 zfs    19G  378M   18G   3% /var/log
rpool/ROOT/ubuntu_d0wbmk/var/snap                zfs    18G  128K   18G   1% /var/snap
rpool/ROOT/ubuntu_d0wbmk/var/lib/AccountsService zfs    18G  128K   18G   1% /var/lib/AccountsService
rpool/ROOT/ubuntu_d0wbmk/var/spool               zfs    18G  4.4M   18G   1% /var/spool
rpool/ROOT/ubuntu_d0wbmk/var/lib/apt             zfs    18G   88M   18G   1% /var/lib/apt
rpool/ROOT/ubuntu_d0wbmk/var/lib/NetworkManager  zfs    18G  256K   18G   1% /var/lib/NetworkManager
rpool/ROOT/ubuntu_d0wbmk/var/www                 zfs    18G  128K   18G   1% /var/www
rpool/ROOT/ubuntu_d0wbmk/var/lib/dpkg            zfs    18G   67M   18G   1% /var/lib/dpkg
bpool/BOOT/ubuntu_d0wbmk                         zfs   1.8G  401M  1.4G  23% /boot
/dev/vda2                                        vfat  512M   17M  496M   4% /boot/efi
romulus:/raid/media                              nfs4  1.8T  1.7T   53G  97% /R
romulus:/Data/r2                                 nfs4  1.3T  1.2T   19G  99% /S
istar:/TV                                        nfs4  294G  121G  173G  42% /TV
```

The last 3 in the list are NFS mounts, not local storage.  ZFS lies to the 'df' command too.  Advanced storage does that.
Sorry, I don't think I have any "normal" storage setups to show. ;) I'm using ZFS or LVM almost always here.

Always remember to use the -h on sort when you have 'human readable' output from other commands in the full pipe chain.  Otherwise, it will do an alphabetic sort and not know that "T" is larger than "G" is larger than "M" ...

Some handy aliases for storage:
```
alias dft='df -hT -x squashfs -x tmpfs -x devtmpfs'
alias du-big='du -xh --max-depth=1 '
```
Just remember the specific limitations/exclusions in any aliases.

---

### Post by robertcull1 on 2023-04-17
It's nice to get an explanation of how things work. 

Right now my system is up and running again. I will look into those man pages at a later time to make sure everything continues to work like it should.

Thanks so much for your help TheFu.

---

