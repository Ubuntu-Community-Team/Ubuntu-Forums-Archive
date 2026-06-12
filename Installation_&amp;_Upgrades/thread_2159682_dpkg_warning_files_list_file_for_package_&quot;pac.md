---
title: "dpkg: warning: files list file for package &quot;pachage-name missing&quot;"
date: 2013-07-04
forum: Installation &amp; Upgrades
---

### Post by rodrigomartinho on 2013-07-04
Hello. I was having a problem with system upgrade that latter I found was caused by a full /boot partition. Before being aware that this was the problem (which is already solved), I tried some other solutions and I think I have messed something up that led to this other problem, where I get many dpkg warnings when [COLOR=#222222]I try to install or uninstall a package[/COLOR][COLOR=#222222]:
[/COLOR]
```
[COLOR=#222222][FONT=Ubuntu Mono]dpkg: warning: files list file for package "package-name" missing, assuming package has no files currently installed[/FONT][/COLOR]
```
[FONT=Ubuntu Mono]
This warning happens for a large number of packages (I would say about 800), but install (or uninstall) finishes. I don't know what are the consequences of these warnings.[/FONT][FONT=Ubuntu Mono]By what I read in other topics, it seems the .list files for these packages on /var/lib/dpkg/info are missing. I don't know if I deleted them by accident, but that could have happened when trying to solve the previous problem, since I have tried some things when the /boot problem led to dependencies problems.[/FONT][FONT=Ubuntu Mono]Could someone help with this issue? What would be the consequences of this problem? How should I proceed to solve it? I have already tried to re-install the packages, with no success. I'm sending an attachment with the list of packages with problem, which I got using the following code, got from another post about a similar problem:
[/FONT]
```
[FONT=Verdana]dpkg -l | grep ^ii | awk '{ print $2 }' > packages.txt[/FONT]
```

[FONT=Ubuntu Mono]Thanks in advance,
Rodrigo Martinho.[/FONT]

---

### Post by dino99 on 2013-07-04
how that ubuntu have been installed ? is it a server ? which release is it ?

---

### Post by rodrigomartinho on 2013-07-04
Ubuntu Server 12.04.2 LTS installed by myself about 3 years ago.

---

### Post by rodrigomartinho on 2013-07-04
I have another server which is pretty much similar to this I had the problem. I was making some upgrades on both, and on this second I didn't run into problems, so I'm pretty sure that I caused the problem when trying to solve a full /boot partition thinking I had apt problems. I just managed the second server after I solved the problem on first, so I didn't mess the second server up.

I compared folder /var/lib/dpkg/info on both servers and on second server I have much more files than in first server. So I'm pretty sure I deleted files on this folder on first server. Could a possible solution be copying files from second server to first?

---

### Post by rodrigomartinho on 2013-07-04
For instance, samba wasn't working, and I wasn't able to re-install it. I copied /var/lib/dpkg/info from second server to first, and after that I could re-install samba and it is working now, but when installing it still shows many dpkg warnings.

```
apt-get install --reinstall samba > problems.txt
```

I'm sending output file as an attachment.

---

### Post by rodrigomartinho on 2013-07-05
Anyone could help with this issue?

---

