---
title: "Trying to update, no space on /boot"
date: 2015-05-18
forum: Installation &amp; Upgrades
---

### Post by keymoo on 2015-05-18
Hi, how do I resolve this problem? I have 14.04 LTS and have a notification to install system updates. When I click to install them I get this message: 

[ATTACH=CONFIG]262045[/ATTACH]

From terminal:

```
~$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--vg-root  226G  7.6G  207G   4% /
none                         4.0K     0  4.0K   0% /sys/fs/cgroup
udev                         1.9G  4.0K  1.9G   1% /dev
tmpfs                        376M  1.2M  375M   1% /run
none                         5.0M     0  5.0M   0% /run/lock
none                         1.9G   38M  1.8G   3% /run/shm
none                         100M   64K  100M   1% /run/user
/dev/sda1                    236M  162M   62M  73% /boot



```

---

### Post by veddox on 2015-05-18
The usual problem in these cases is old kernel images filling up your  boot partition. If you go to /boot with your file browser, you will see a  lot of files with version numbers referring to the Linux kernel (in the  form *-3.x.y-generic). You should be able to delete a few old ones.  (This should not cause any system problems, because by default only the  newest kernel available is used. However, just in case, do make sure you  have a backup!)

For example, I have the following kernel images in my /boot directory:
```

daniel@ENIGMA:/boot$ ls vm*
vmlinuz-3.13.0-24-generic     vmlinuz-3.2.0-59-generic-pae
vmlinuz-3.13.0-27-generic     vmlinuz-3.2.0-60-generic-pae
vmlinuz-3.13.0-29-generic     vmlinuz-3.8.0-29-generic
vmlinuz-3.13.0-30-generic     vmlinuz-3.8.0-35-generic
vmlinuz-3.13.0-32-generic     vmlinuz-3.8.0-36-generic
vmlinuz-3.13.0-34-generic     vmlinuz-3.8.0-37-generic
vmlinuz-3.13.0-43-generic     vmlinuz-3.8.0-38-generic
vmlinuz-3.2.0-58-generic-pae

```

If I were in your situation, I would get rid of the 3.2 and the 3.8 series - save me about 5MB per image.

---

### Post by ian-weisser on 2015-05-18
> **veddox said:**
> If I were in your situation, I would get rid of the 3.2 and the 3.8 series - save me about 5MB per image.

'get rid of' means to use the package manager to uninstall the older kernel packages.
DO NOT manually delete kernel files. Always use the package manager.
Do not uninstall your currently running kernel, of course!

If you need further help, post the output of your 'dh' command.

---

### Post by mörgæs on 2015-05-18
```
sudo apt-get autoremove
``` should help.

---

