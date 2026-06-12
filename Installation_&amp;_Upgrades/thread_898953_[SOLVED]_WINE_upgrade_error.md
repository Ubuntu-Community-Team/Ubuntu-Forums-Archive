---
title: "[SOLVED] WINE upgrade error"
date: 2008-08-23
forum: Installation &amp; Upgrades
---

### Post by prshah on 2008-08-23
Hello,

I've recently (since yesterday) been getting errors from update manager, with only 1 update, that of WINE.

The exact error message is> 
E: /var/cache/apt/archives/wine_1.1.3~winehq0~ubuntu~8.04-0ubuntu1_i386.deb: files list file for package `devede' is missing final newline


I've deleted the relevant deb file from /var/cache/apt/archive/ and had update-manager redownload the file (twice), but it comes back to the same error message.

I've apt-get updated twice (which completes without any errors), both with and without the wine repository, but in either case I get the same message (after running update manager). For reference:```
Sun Aug 24 06:01:05 treo650:$ cat /etc/apt/sources.list | grep -i wine
deb http://wine.budgetdedicated.com/apt hardy main

```

I do have "devede" installed on the machine, but I can't see any relevance between the two.

I cannot find anything related on the forums, and so I assume that there's something wrong with my machine.

Any suggestions?

---

### Post by Partyboi2 on 2008-08-23
There are a few possible solutions mentioned [[COLOR=Blue]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=12737")

---

### Post by prshah on 2008-08-23
> **Partyboi2 said:**
> There are a few possible solutions mentioned [[COLOR=Blue]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=12737")

Yes that did the trick, thanks; essentially, I just had to move the package information for devede (the affected package) out of the /var/lib/dpkg/info ```
sudo mv devede* /home/user/
```

---

