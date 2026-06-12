---
title: "Encrypt root, home and swap"
date: 2006-11-21
forum: Installation &amp; Upgrades
---

### Post by RichJacot on 2006-11-21
Hello,

Since I couldn't get my encrypted /, swap and /home working on a fresh Edgy install, I resorted to another howto for Dapper and went with fresh Dapper install.

[https://help.ubuntu.com/community/EncryptedFilesystemLVMHowto]("https://help.ubuntu.com/community/EncryptedFilesystemLVMHowto")

This appears to be working fine, except for couple minor issues.  I say minor because everything appears to be working.

After following the above howto:

During boot I have to put the passphrase in twice.  I assume that this is because of the encrypted / and /home ?  I did use the same passphrase.  
Is there a way to have this only ask once (since they are the same passphrase)?  Once I login I get this pop-up:

[http://www.flickr.com/photos/39672899@N00/302942321/]("http://www.flickr.com/photos/39672899@N00/302942321/")
[IMG]http://www.flickr.com/photos/39672899@N00/302942321/[/IMG]

The root and /home appear to be crypted and are both mounted when I login (swap also). 

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/vgcrypt-lvroot
                       30G  4.1G   24G  15% /
varrun                1.5G   92K  1.5G   1% /var/run
varlock               1.5G  4.0K  1.5G   1% /var/lock
udev                  1.5G  156K  1.5G   1% /dev
devshm                1.5G     0  1.5G   0% /dev/shm
lrm                   1.5G   18M  1.5G   2% /lib/modules/2.6.15-27-686/volatile
/dev/mapper/vgcrypt-lvhome
                      104G   24G   75G  25% /home
/dev/sda5             184M   32M  143M  19% /boot
/dev/sdb1              70G   56G   14G  81% /data1
/dev/hda1             187G  141G   47G  76% /data2

```

I can just hit cancel, on the pop-up, and all is fine.  If I do enter the passphrase, it hangs for awhile and then fails.  I don't recall the message, but I can get it if someone thinks its important. 

My fstab looks like:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/vgcrypt-lvroot       /               ext3    defaults,errors=remount-ro 0       1
/dev/mapper/vgcrypt-lvhome /home    ext3    defaults    0       1
/dev/mapper/vgcrypt-lvswap none swap    sw              0       0
/dev/sda5       /boot           ext3    defaults        0       2
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto 0       0
/dev/sdb1       /data1          reiserfs    defaults        0       3
/dev/hda1       /data2          reiserfs    defaults        0       4

```

Swap:

```
cat /proc/swaps
Filename                                Type            Size    Used    Priority
/dev/mapper/vgcrypt-lvswap              partition       1048568 18424   -1

```

Disk layout:

```
sudo parted /dev/sda p
Disk geometry for /dev/sda: 0kB - 150GB
Disk label type: msdos
Number  Start   End     Size    Type      File system  Flags
1       32kB    3249MB  3249MB  primary
2       3249MB  150GB   147GB   extended
5       3249MB  3455MB  206MB   logical   ext3
6       3455MB  150GB   147GB   logical   ext3
Information: Don't forget to update /etc/fstab, if necessary.

```

Please let me know if I need to post any other files to help me with my issue.

Thank you!

---

### Post by RichJacot on 2006-11-22
Does anyone have any ideas?

Rich

---

### Post by RichJacot on 2006-11-27
Turns out I don't need to put the passphrase in twice during boot, but I am getting the pop-up once I login that I can just cancel.

Any ideas?

---

### Post by RichJacot on 2006-12-02
bump

---

### Post by RichJacot on 2006-12-06
bump one more time.

---

### Post by Stephen Howard on 2006-12-07
Can you *cat /etc/crypttab*?

What is sda6 meant to be dedicated to?

Odd how /dev/mapper doesn't appear to have a swap entry, but /proc/swaps claims it points to /dev/mapper.

My guess is that Gnome is going through your fstab at startup time and if it finds an entry that isn't already mounted it tries to mount it automatically - mount then prompts you for a password.  

I'm just theorising as I don't use gnome - but its a starting point.

---

### Post by Stephen Howard on 2006-12-07
Oh, and would you also show the output of *ls /dev/mapper*

---

### Post by RichJacot on 2006-12-07
As you requested:

```
/$ cat /etc/crypttab
# <target name> <source device>         <key file>      <options>

$ ls /dev/mapper
control     hda1     sda1  sda6  vgcrypt-lvhome  vgcrypt-lvswap
cryptdata1  pvcrypt  sda5  sdb1  vgcrypt-lvroot
/$

```


sda6 was the partition I initially used to install dapper on, then I created my crypt root and copied it over.  Basically its wasted space now.  I guess I could creat another 3GB partition for something else but I don't mind losing it to get the crypt filesystems working.

You'll notice cryptdata1.  That's what was: 

/dev/sdb1       /data1          reiserfs    defaults        0       3

I've converted it to crypt also, which I always need to mount by hand after I login.

Thank you!

---

### Post by Stephen Howard on 2006-12-08
Thanks - I'm heading out overnight, so probably be 12+ hrs before I can look at this.

That said, my suspicion is directed toward gnome-volume-manager (mainly because its happening after desktop login, and the prompt text matches the src code in g-v-m.  If you feel inclined, it might be worthwhile to see if there's a configuration file that controls g-v-m.

Also, perhaps try a brute force method to see where sda6 is referenced.  ie in a terminal go to /etc and then "grep -r sda6 *"   The results might give some clue.  Might be worthwhile to try the same search inside any gnome directories inside the users /home


talk to you later.

---

### Post by Stephen Howard on 2006-12-08
[I think this post is talking about the same problem and its solution]("https://launchpad.net/distros/ubuntu/+source/hal/+bug/57104").
In short, HAL is seeing it and trying to mount it.  I have not idea what the XML stuff in the solution is all about - I leave that to you to decipher.

Probably can't help you any more as I don't use gnome, but if you keep nosing around HAL I think you'll find the answer.

---

### Post by RichJacot on 2006-12-09
I've tried what the link you provided suggests.  I'll reboot later today to see if it helped and let you know.  Thank you!

---

### Post by RichJacot on 2006-12-10
The link you provided with that patch/fix worked!  Thank you!!

---

### Post by Stephen Howard on 2006-12-11
Cool.  Hopefully the upgrade will eventually make it into the repositories.

---

### Post by RichJacot on 2006-12-11
Thanks again Stephen!  I agree, I would hope this makes it into the repositories.


Does anyone know how I can get my additional encrypted /data1 partition to mount on boot (same key as / and /home)?  If I add it to my fstab it errors and boots to single user where I have to remove it from the fstab.

The way I do it now is after I boot I run this script to mount my /data1:

```
sudo cryptsetup luksOpen /dev/sdb1 cryptdata1
sudo mount /dev/mapper/cryptdata1 /data1

```

Thanks,
Rich

---

