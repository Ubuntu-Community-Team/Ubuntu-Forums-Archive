---
title: "How to allocate more space in /var directory"
date: 2019-06-23
forum: Installation &amp; Upgrades
---

### Post by hawk.eyee on 2019-06-23
For some times i'm getting a notification that " /var directory is out of space". at first i didn't give any attention, but for this reason " [COLOR=#000000]PCIe Bus Error: severity=Uncorrected (Non-Fatal), type=Transaction Layer, (Completer ID[/COLOR])" this problem was occurred. this problem is temporarily solved, but if this problem not happen again that's why i want to allocate more space to /var directory... someone please help me with this. also give any suggestion to avoid this kind of problems.
thanks in advance.

---

### Post by SeijiSensei on 2019-06-23
First, unless /var is mounted as a separate filesystem, there's no way to expand /var.  

The more important question is why is /var growing so large?  I'd bet you got some problems that are generating lots of entries in /var/log.  I'd start with /var/log/syslog and see if there are error messages being recorded.  If so, you need to fix that problem first.

---

### Post by hawk.eyee on 2019-06-23
how would i know that if there are any error messages in /var/log/syslog? actually I'm totally new in ubuntu, so if you guide me it would be very generous for you.

---

### Post by kpatz on 2019-06-23
Post the output of the commands:```
sudo du -d 1 /var
``````
sudo du /var/log
```and```
 df -hT -x squashfs -x tmpfs
```

Put the output of each inside [noparse]```
 and 
```[/noparse] tags when posting.

---

### Post by TheFu on 2019-06-23
> **hawk.eyee said:**
> how would i know that if there are any error messages in /var/log/syslog? actually I'm totally new in ubuntu, so if you guide me it would be very generous for you.

How would you know?  You would search for them either manually or setup an automatic tool that does it for you.  I use **logwatch** and get daily reports emailed to myself for each system. 

There are other ways to monitor the system for issues using monitoring tools and alarming tools. These are usually more trouble to setup than most end-users would be interested in.

For now, you can use
```
sudo egrep -i 'warn|error' /var/log/*g
```
That will use a regular expression to search case-insensitive for lines with warn or error in any filenames that end in 'g' in the log directory.  Most of the time, sudo isn't needed, but a few log files are only readable by root for security reasons. Need to look at those log files too.

With a little effort, you can have that egrep command run every morning at 8am and email locally the results. If you want to have the email sent somewhere else, that's more work and perhaps not a good idea, since it would contain sensitive information about the security of your system.  But some people do send their logs to their gmail accounts.  I wouldn't, but people do.

Or you could run the command and have it create a file with the output, waiting for you do read it daily.  Automating things is where Unix really is 1000x better than Windows.

---

### Post by hawk.eyee on 2019-06-23
> **kpatz said:**
> Post the output of the commands:```
sudo du -d 1 /var
``````
sudo du /var/log
```and```
 df -hT -x squashfs -x tmpfs
```

Put the output of each inside [noparse]```
 and 
```[/noparse] tags when posting.

Here is the outputs:

```


hawk-eyee@imam:~$ sudo du -d 1 /var
[sudo] password for hawk-eyee: 
3206660	/var/lib
4	/var/metrics
4	/var/mail
200	/var/snap
50368	/var/crash
2932	/var/backups
60	/var/tmp
56	/var/spool
523880	/var/log
4	/var/opt
16	/var/lost+found
136512	/var/cache
4	/var/local
3920704	/var
hawk-eyee@imam:~$ sudo du /var/log
4	/var/log/dist-upgrade
208	/var/log/apt
108	/var/log/lightdm
52	/var/log/cups
516276	/var/log/journal/65eefa17dd3a4232be4b166562b2ebde
516280	/var/log/journal
4	/var/log/speech-dispatcher
4	/var/log/gdm3
4	/var/log/samba/cores/nmbd
4	/var/log/samba/cores/smbd
12	/var/log/samba/cores
72	/var/log/samba
16	/var/log/unattended-upgrades
4	/var/log/hp/tmp
8	/var/log/hp
3696	/var/log/installer
523880	/var/log
hawk-eyee@imam:~$  df -hT -x squashfs -x tmpfs
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  1.9G     0  1.9G   0% /dev
/dev/sda4      ext4       92G  6.5G   81G   8% /
/dev/sda5      ext4      923M  112M  748M  14% /boot
/dev/sda8      ext4      5.5G   23M  5.2G   1% /tmp
/dev/sda2      vfat       47G  6.4M   47G   1% /boot/efi
/dev/sda3      ext4      109G   14G   90G  14% /home
/dev/sda7      ext4      4.6G  3.8G  528M  88% /var



```

---

### Post by ajgreeny on 2019-06-23
For some reason you chose to use a separate /var partition as shown by the output of ***df -hT -x squashfs -x tmpfs*** and of that /var/lib is using around 3G.  What was the reason for having a separate partition for var; did you choose to do so or was the system installed for you by someone else?

That /var partition in your system is 4,6G and presently 88% used.  Enlarging /var is not going to be a simple job as it will require another partition to be made smaller and at present we have no idea how they are arranged on the disk as they may not be in the order shown.

Do you run a server of some sort which uses /var/lib for its database, eg Plexmediaserver, which I run, and does need a lot of disk space; in my system /var/lib/plexmediaserver uses almost 2G on its own, and there is little I can do to reduce its size short of getting rid of some of the media it deals with.

I would start by running ```
sudo apt clean
``` to get rid of all the apt packages downloaded when installing packages or updating them; any that are needed can always be downloaded again. That may help but we may also need to consider removing more content of /var; let's see how you do after the clean up of packages and move on from there.

One more command to help us would be ```
sudo du -d 1 /var/lib | sort -h
``` which will show in useage size each sub directory of /var/lib and may show where the problem lies more clearly.

---

### Post by hawk.eyee on 2019-06-23
> **ajgreeny said:**
> For some reason you chose to use a separate /var partition as shown by the output of ***df -hT -x squashfs -x tmpfs*** and of that /var/lib is using around 3G.  What was the reason for having a separate partition for var; did you choose to do so or was the system installed for you by someone else?

That /var partition in your system is 4,6G and presently 88% used.  Enlarging /var is not going to be a simple job as it will require another partition to be made smaller and at present we have no idea how they are arranged on the disk as they may not be in the order shown.

Do you run a server of some sort which uses /var/lib for its database, eg Plexmediaserver, which I run, and does need a lot of disk space; in my system /var/lib/plexmediaserver uses almost 2G on its own, and there is little I can do to reduce its size short of getting rid of some of the media it deals with.

I would start by running ```
sudo apt clean
``` to get rid of all the apt packages downloaded when installing packages or updating them; any that are needed can always be downloaded again. That may help but we may also need to consider removing more content of /var; let's see how you do after the clean up of packages and move on from there.

One more command to help us would be ```
sudo du -d 1 /var/lib | sort -h
``` which will show in useage size each sub directory of /var/lib and may show where the problem lies more clearly.

Actually I was following an article during install Ubuntu, they suggested to create /var partition. and I don't run any server. By using this command from tty1 mode ```
 sudo apt clean 
``` I solved my this problem recently ```
 [COLOR=#000000][COLOR=#000000]PCIe Bus Error: severity=Uncorrected (Non-Fatal), type=Transaction Layer, (Completer ID[/COLOR][/COLOR][COLOR=#000000]) 
``` 

the result came from this [/COLOR] ```
sudo du -d 1 /var/lib | sort -h
``` are here:
```

hawk-eyee@root:~$ sudo du -d 1 /var/lib | sort -h[sudo] password for hawk-eyee: 
4	/var/lib/acpi-support
4	/var/lib/apport
4	/var/lib/avahi-autoipd
4	/var/lib/boltd
4	/var/lib/command-not-found
4	/var/lib/dbus
4	/var/lib/dhcp
4	/var/lib/fwupdate
4	/var/lib/git
4	/var/lib/hp
4	/var/lib/man-db
4	/var/lib/misc
4	/var/lib/os-prober
4	/var/lib/python
4	/var/lib/snmp
4	/var/lib/ubiquity
4	/var/lib/ubuntu-release-upgrader
4	/var/lib/udisks2
4	/var/lib/usb_modeswitch
8	/var/lib/bluetooth
8	/var/lib/geoclue
8	/var/lib/ispell
8	/var/lib/logrotate
8	/var/lib/plymouth
8	/var/lib/sudo
8	/var/lib/ubuntu-drivers-common
8	/var/lib/vim
8	/var/lib/whoopsie
8	/var/lib/xfonts
8	/var/lib/xkb
12	/var/lib/grub
12	/var/lib/initramfs-tools
12	/var/lib/lightdm-data
12	/var/lib/private
12	/var/lib/sgml-base
12	/var/lib/update-manager
16	/var/lib/libreoffice
16	/var/lib/locales
20	/var/lib/AccountsService
20	/var/lib/alsa
20	/var/lib/update-notifier
20	/var/lib/upower
24	/var/lib/dictionaries-common
24	/var/lib/emacsen-common
24	/var/lib/libxml-sax-perl
24	/var/lib/shim-signed
28	/var/lib/pam
36	/var/lib/ghostscript
52	/var/lib/NetworkManager
56	/var/lib/colord
64	/var/lib/polkit-1
140	/var/lib/ucf
168	/var/lib/lightdm
180	/var/lib/doc-base
204	/var/lib/fwupd
220	/var/lib/PackageKit
476	/var/lib/systemd
516	/var/lib/ureadahead
544	/var/lib/usbutils
828	/var/lib/gdm3
2232	/var/lib/samba
4176	/var/lib/aspell
7248	/var/lib/dkms
15200	/var/lib/mlocate
18412	/var/lib/app-info
82420	/var/lib/dpkg
260448	/var/lib/apt
2829468	/var/lib/snapd
3223564	/var/lib


 
``` 

Thank you for your kind response.

---

### Post by ajgreeny on 2019-06-23
It looks as if you have installed a lot of snap packages as the /var/lib/snapd folder is about 2.5G in size, a large chunk of your total /var partition.

What snaps have you installed and are they all necessary?  You can show all your current snaps with command ```
snap list
```
You may be able to use standard repository versions in place of some of your snap packages which should remove at least some of the content of that large /var/lib/snapd folder.

---

### Post by CatKiller on 2019-06-23
> **hawk.eyee said:**
> Actually I was following an article during install Ubuntu, they suggested to create /var partition. and I don't run any server.
This was bad advice, then. There is no benefit to having a separate /var partition unless you already know specifically why you need it and have specific requirements. Most server installs also won't require a separate /var.

The best thing to do would be to use a live image to reincorporate the stuff that you've got in that partition into a /var directory of your / partition, edit your fstab so that it doesn't try to mount your old /var partition, and then nuke the old /var partition. You can then extend your / partition into the space that is now unpartitioned.

As you've found, having separate partitions has the significant downside of needing to know how much space you'll need before you start.

---

### Post by ajgreeny on 2019-06-23
> **CatKiller said:**
> This was bad advice, then. There is no benefit to having a separate /var partition unless you already know specifically why you need it and have specific requirements. Most server installs also won't require a separate /var.

The best thing to do would be to use a live image to reincorporate the stuff that you've got in that partition into a /var directory of your / partition, edit your fstab so that it doesn't try to mount your old /var partition, and then nuke the old /var partition. You can then extend your / partition into the space that is now unpartitioned.

As you've found, having separate partitions has the significant downside of needing to know how much space you'll need before you start.
^^^^^ +1 ^^^^^
I would also be interested to see the website (assuming that's what it was) where you found the advice, so if possible please show us the link used;  I have seen many places online where they suggest the most ridiculously complicated partition setups, none of which I would ever recommend for a desktop machine.

There may be good reasons for having separate partitions for some of the folders usually contained in the root filesystem of a desktop machine, but that is a very different situation to yours, I assume.

---

### Post by kpatz on 2019-06-23
There's nothing intrinsically wrong with creating a separate /var partition, some sites do recommend doing so, especially if you're running applications like databases that put large amounts of data in /var.  Running out of space in / can cause more issues especially on servers; that said, there's usually no need on a desktop to have a separate /var partition.  I often create a separate /var on my systems.

What is wrong, in this case, is the *size *of /var.  If I create a separate /var, I give it a lot of space, more than / in any case.  Logs, snaps, apt cache, spool files, databases... /var usually ends up being the most space used on a Linux system other than /home.  Your root (/) partition has a lot of space.  I would boot from a live DVD or USB, mount the root and the var partitions, copy the files in the var partition over to the root partition (under <mountpoint>/var), remove the mount of /var from /etc/fstab, and then reboot back into your normal install.  The partition can then be recycled for swap, or an adjacent partition expanded into it.

---

### Post by TheFu on 2019-06-23
There are 2 ways to solved this.

There is a cheap trick that you can use to solve this.  It isn't elegant, but it will work.  You'll need to use alternate boot media to do it and you'll need to mount the /var/ partition somewhere and the /usr/ partition somewhere else.
Then move all of {tmp1-prefix}/var/lib/snapd to {tmp2-prefix}/usr/var/lib/snapd.  This will take some time.  I would use /mnt/var and /mnt/usr for those tmp prefixes.  Use sudo for the move.

Then in I would make a symbolic link from  {tmp2-prefix}/usr/var/lib/snapd  {tmp1-prefix}/var/lib/ so that when you boot up /var/lib/snapd points to the all the files correctly that happen to be in /usr/var/lib/snapd/.  Think of this as a workaround. Good while you consider other options.  It adds one level of indirection, but it works.  Stuff like this is commonly used in software development to have 2, 5, 20 versions of specific tools, but only change 1 link to make a specific 1 active.

The other option is to reduce the size of **the / partition to something reasonable, probably 25G**, which is still way too large.
```
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sda4      ext4       [COLOR="#FF0000"]92G[/COLOR]  6.5G   81G   8% /
/dev/sda5      ext4      923M  112M  748M  14% /boot
/dev/sda8      ext4      5.5G   23M  5.2G   1% /tmp
/dev/sda2      vfat       [COLOR="#FF0000"]47G [/COLOR] 6.4M   47G   1% /boot/efi
/dev/sda3      ext4      109G   14G   90G  14% /home
/dev/sda7      ext4      4.6G  3.8G  528M  88% /var
```
There is absolutely ZERO reason for /boot/eft to be 47G in size.  **It should be 512MB** - so reduce that by 46G.
/home is 5x larger than you need too, so if you want to reduce a bunch of these, you will likely have plenty of room to make a /var with all the room you can stand for all those snap packages.  It is also safe to remove the snapd package (remove all the snaps first), then you won't accidentally get stuck dealing with snaps anymore that you didn't specifically ask to have installed.  

If you want more control over storage, you could use LVM. Then resizing would be pretty easy using lvresize or lvextend or lvreduce.  LVM **is* more complex and flexible. Usually the people choosing to use it are professional admins.  I've posted my storage setup in these forums a few times the last few months. If you are interested, they are there.

I find what Canonical did by installing snaps without asking first to be rude.  Snaps make a huge difference in how programs run, how much RAM they use, how much storage they use and how we can interact with each program from other programs.  Anything that does all that needs to be a pro-active user/admin choice, especially for any LTS release.  Someone should create a script to swap all installed snaps with the normal packages and remove snapd.  I bet that would be very popular.  Snaps are not all bad, but there should be specific, high-risk, packages that are installed as snaps, not packages like a calculator.

IMHO.

---

### Post by kpatz on 2019-06-23
A quick way to free up some space on /var is to purge old systemd journals with the command **sudo journalctl --vacuum-time=1d**  (This deletes all but 1 day of journals... change this as needed if you want to keep more than day).

One more thing... post the output of the command **sudo gdisk -l /dev/sda** and that way we can determine the partition layout of your disk and what partitions, if any, can be enlarged after shrinking the / and /boot/efi partitions.

Your root partition is large enough that you could even move /home, /var, and /boot there, and then delete their partitions entirely.  And /tmp doesn't need its own partition either... I usually use a tmpfs for /tmp so it just sits in RAM.

Also, are any other OSes installed like Windows?

---

### Post by SeijiSensei on 2019-06-24
Given you have all that empty space in the root partition, I'd migrate /var there.  Something like this:

```

cd /
mkdir var2
cd /var
rsync -av . ../var2

```
/var2 will now be a duplicate of /var.

Now the last step is a bit tricky.  You'll need to reboot and enter recovery mode.  Choose the "root shell" option when offered.

```

mount -o remount,rw /
rm -rf var
mv var2 var

```

Finally, run "nano /etc/fstab" and find the line that mounts your current /var partition. Put a hash mark ("#") at the beginning of the line and save the file. Then reboot normally.

---

### Post by rsteinmetz70112 on 2019-06-26
Quick and dirty you could probbaly - sudo -s; mkdir /var2; cp -rp /var/* /var2;  edit fstab to comment the entry for /var; umount /var; mv /var to /var3; mv /var2 /var - then reboot. It will probably work, but if it doesn't you will still have your original /var

BTW I usually create a separate file /var  and relatively small / to prevent filling root in case something starts filling up /var with lots of logs or error messages. I had that happen a few times.

---

### Post by CatKiller on 2019-06-26
> **rsteinmetz70112 said:**
> BTW I usually create a separate file /var  and relatively small / to prevent filling root in case something starts filling up /var with lots of logs or error messages. I had that happen a few times.

I used to just mount /var/log as tmpfs. Easy enough to undo if you're actually interested in the contents of the logfiles past a reboot; they can simply go away the rest of the time.

---

### Post by hawk.eyee on 2019-06-27
thanks everyone for helping me with this one.

---

