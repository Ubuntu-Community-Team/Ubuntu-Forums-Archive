---
title: "looking fo which package has iptables-save, etc"
date: 2022-11-17
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2022-11-17
this is in Focal Fossa 20.04 LTS.

i am looking for which package has *iptables-save*, etc.  packages iptables-save and iptables-tools do not exist.  i do have package iptables installed but it does not have iptables-save.   looking at various apt data files all i can see names for are some non-English man page packages.  sure, i do want the man pages, but the program binaries are essential.  all these data files for package i don't have installed should include everything.

---

### Post by &amp;KyT$0P# on 2022-11-18
Looks like those are symlinks managed through [FONT=Courier New]update-alternatives[/FONT] .  Try
```
dpkg-query -S "$(realpath "$(which iptables-save)")"
```

---

### Post by ubfan1 on 2022-11-18
The sylinks eventually get to /usr/sbin/iptables-nft-save , which should have been in the iptables package.

---

### Post by Skaperen on 2022-11-19
[FONT=courier new]**which iptables-save**[/FONT] will give no answer as *iptables-save* is not (yet) installed.

package *iptables* is installed.  yes, it is missing *iptables-save*.

---

### Post by &amp;KyT$0P# on 2022-11-20
I would try
```
sudo apt-get --reinstall install iptables
```
or maybe
```
sudo dpkg-reconfigure iptables
```

Looks like the default binary to use for iptables-save on 20.04 is [FONT=Courier New]/usr/sbin/iptables-legacy-save[/FONT] , do you have that?

---

### Post by Skaperen on 2022-11-20
its a symlink to **[FONT=courier new]xtables-legacy-multi[/FONT]** which exists.  iptables-save is the traditional name.  that name should be included, somehow (such as a symlink).  i guess i will do that manually elsewhere.
```

lt1a/forums/1 /home/forums 8> ls -dl /usr/sbin/{ip,x}tables*
lrwxrwxrwx 1 root root     26 May 25 00:59 /usr/sbin/iptables -> /etc/alternatives/iptables
-rwxr-xr-x 1 root root   7057 Feb 28  2020 /usr/sbin/iptables-apply
lrwxrwxrwx 1 root root     20 May 25 00:59 /usr/sbin/iptables-legacy -> xtables-legacy-multi
lrwxrwxrwx 1 root root     20 May 25 00:59 /usr/sbin/iptables-legacy-restore -> xtables-legacy-multi
lrwxrwxrwx 1 root root     20 May 25 00:59 /usr/sbin/iptables-legacy-save -> xtables-legacy-multi
lrwxrwxrwx 1 root root     17 May 25 00:59 /usr/sbin/iptables-nft -> xtables-nft-multi
lrwxrwxrwx 1 root root     17 May 25 00:59 /usr/sbin/iptables-nft-restore -> xtables-nft-multi
lrwxrwxrwx 1 root root     17 May 25 00:59 /usr/sbin/iptables-nft-save -> xtables-nft-multi
lrwxrwxrwx 1 root root     34 May 25 00:59 /usr/sbin/iptables-restore -> /etc/alternatives/iptables-restore
lrwxrwxrwx 1 root root     17 May 25 00:59 /usr/sbin/iptables-restore-translate -> xtables-nft-multi
lrwxrwxrwx 1 root root     31 May 25 00:59 /usr/sbin/iptables-save -> /etc/alternatives/iptables-save
lrwxrwxrwx 1 root root     17 May 25 00:59 /usr/sbin/iptables-translate -> xtables-nft-multi
-rwxr-xr-x 1 root root  99296 Feb 28  2020 /usr/sbin/xtables-legacy-multi
lrwxrwxrwx 1 root root     17 May 25 00:59 /usr/sbin/xtables-monitor -> xtables-nft-multi
-rwxr-xr-x 1 root root 220488 Feb 28  2020 /usr/sbin/xtables-nft-multi
lt1a/forums/1 /home/forums 9> 

```
what is **[FONT=courier new]xtables[/FONT]**?

well...  there it is:  /usr/**s**bin/iptables-save

---

### Post by ubfan1 on 2022-11-22
locate works for things not in your path, unlike which.

---

