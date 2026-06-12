---
title: "Can't resolve partial upgrade warning"
date: 2014-06-28
forum: Installation &amp; Upgrades
---

### Post by qianian2 on 2014-06-28
I noticed Update Manager was popping up with a "Not all updates can be installed" warning. I found out medibuntu software sources were no longer supported, so I followed instructions to remove those. However, not only did the warning continue, there's now a second popup "Software index is broken." It says to use Synaptic or  and Synaptic opens with error "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. E: _cache->open() failed, please report"

I get: 
```
$ sudo dpkg --configure -a
dpkg: error: failed to open '/var/lib/dpkg/status' for writing status database: No space left on device
$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        19G   12G  5.6G  68% /
udev            1.5G  4.0K  1.5G   1% /dev
tmpfs           302M  872K  302M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.5G  688K  1.5G   1% /run/shm
/dev/sda5       202G  165G   27G  87% /home
$ sudo apt-get autoclean
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

```

I apologize I can't find the exact instructions I followed for removing medibuntu sources. Anything else I can try to diagnose the problem? 

Thank you in advance.

---

### Post by Vladlenin5000 on 2014-06-28
```
E: dpkg was interrupted, _you must manually run '**sudo dpkg --configure -a**' to correct the problem_.
```

Have you? If so what was the result, any new error messages?

---

### Post by bapoumba on 2014-06-28
```
dpkg: error: failed to open '/var/lib/dpkg/status' for writing status database: No space left on device
```

Please post the outputs to :
```
df  -h
df -i
```

---

### Post by qianian2 on 2014-06-30
Thanks for your help.

```
$ df  -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        19G   12G  5.6G  68% /
udev            1.5G  4.0K  1.5G   1% /dev
tmpfs           302M  892K  302M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.5G  716K  1.5G   1% /run/shm
/dev/sda5       202G  165G   27G  87% /home
```
```
$ df  -i
Filesystem       Inodes   IUsed    IFree IUse% Mounted on
/dev/sda1       1221600 1221233      367  100% /
udev             212985     539   212446    1% /dev
tmpfs            217390     464   216926    1% /run
none             217390       3   217387    1% /run/lock
none             217390      11   217379    1% /run/shm
/dev/sda5      13434880   38995 13395885    1% /home
```

---

### Post by deadflowr on 2014-07-01
This might help
[http://askubuntu.com/questions/231585/running-out-of-inodes](http://askubuntu.com/questions/231585/running-out-of-inodes)
I post this because while the size is only 68% used the inodes are 100% used.

---

### Post by bapoumba on 2014-07-01
Removing old kernels will help clear inodes.
```
sudo apt-get autoremove
sudo apt-get clean
```

---

### Post by qianian2 on 2014-07-04
I cleaned out the inodes using [http://askubuntu.com/questions/231585/running-out-of-inodes](http://askubuntu.com/questions/231585/running-out-of-inodes), but there's no change in Update Manager. As above, I still get:

$ sudo apt-get autoremove
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

---

### Post by deadflowr on 2014-07-04
What does df -i say now?
also
did you run the sudo dpkg --configure -a command?

---

### Post by qianian2 on 2014-07-05
```
$ df -i
Filesystem       Inodes   IUsed    IFree IUse% Mounted on
/dev/sda1       1221600 1221600        0  100% /
udev             212985     519   212466    1% /dev
tmpfs            217390     445   216945    1% /run
none             217390       3   217387    1% /run/lock
none             217390      14   217376    1% /run/shm
/dev/sda5      13434880   30106 13404774    1% /home 
```

I couldn't capture all the output the first time I ran dpkg. The tail was: 

```
space left on device
cp: cannot create regular file &#8216;/tmp/mkinitramfs_dwWssI//lib/ld-linux.so.2&#8217;: No space left on device
cp: cannot create regular file &#8216;/tmp/mkinitramfs_dwWssI//bin/date&#8217;: No space left on device
E: /usr/share/initramfs-tools/hooks/fixrtc failed with return 1.
update-initramfs: failed for /boot/initrd.img-3.2.0-64-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-64-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-64-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up cups (1.5.3-0ubuntu8.3) ...
Updating PPD files for cups ...
Setting up libqtgui4 (4:4.8.1-0ubuntu4.8) ...
Setting up libqt4-declarative (4:4.8.1-0ubuntu4.8) ...
dpkg: unrecoverable fatal error, aborting:
 unable to create `/var/lib/dpkg/updates/tmp.i': No space left on device 
```

When I run it again I get

```
$ sudo dpkg --configure -a
dpkg: error: failed to open '/var/lib/dpkg/status' for writing status database: No space left on device 
```

---

### Post by qianian2 on 2014-07-05
One more thing: I found that I couldn't run count_em on the root directory:

$ count_em
/home/user/bin/count_em: line 3: /tmp/count_em_11211: No space left on device
chmod: cannot access &#8216;/tmp/count_em_11211&#8217;: No such file or directory
find: `./root': Permission denied
xargs: /tmp/count_em_11211: No such file or directory

And when I try to create count_em in the root bin/ directory, I get:

cp: cannot create regular file &#8216;../../bin/count_em&#8217;: No space left on device

---

### Post by bapoumba on 2014-07-06
Here is a detailed procedure to remove kernels and kernel headers with dpkg : [http://ubuntuforums.org/showthread.php?t=2177876](http://ubuntuforums.org/showthread.php?t=2177876). please run **uname -a** first to know which kernel you are using. I'd keep this one, of course, and the previous working one.

---

### Post by qianian2 on 2014-07-08
Thanks, bapoumba, I thought I was putting in the wrong version or header numbers because I got "not found" errors but when I restarted today Update Manager is updating like normal! I'll update when the changes are applied.

---

