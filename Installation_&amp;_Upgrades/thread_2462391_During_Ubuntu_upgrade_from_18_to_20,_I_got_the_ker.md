---
title: "During Ubuntu upgrade from 18 to 20, I got the kernel related error: “could not get m"
date: 2021-05-19
forum: Installation &amp; Upgrades
---

### Post by ziegel1 on 2021-05-19
[COLOR=#242729][FONT=-apple-system]I'm running a Plesk server on AWS latest infrastructure (May, 2021) which I have upgraded from Ubuntu 18 to 20.[/FONT][/COLOR]
[COLOR=#242729][FONT=-apple-system]During this upgrade process I got the below error message:[/FONT][/COLOR]
could not get modinfo from 'crc32' as there was no such file or directory

[COLOR=#242729][FONT=-apple-system][IMG]https://i.stack.imgur.com/Yyqc4.png[/IMG]

[/FONT][/COLOR]
[COLOR=#242729][FONT=-apple-system]I do have at the moment crc32 module installed:[/FONT][/COLOR]
# lsmod | grep crc
libcrc32c              16384  4 nf_conntrack,nf_nat,btrfs,raid456

# dpkg -l | grep linux-modules | grep "ii  "
ii  linux-modules-5.4.0-1047-aws           5.4.0-1047.49                                    amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-5.4.0-1048-aws           5.4.0-1048.50                                    amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-5.4.0-73-generic         5.4.0-73.82                                      amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.4.0-73-generic   5.4.0-73.82                                      amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
[COLOR=#242729][FONT=-apple-system]May I ask:[/FONT][/COLOR]

[LIST=1]
[*][FONT=inherit]What was it that went wrong?[/FONT]

[*][FONT=inherit]How can I diagnose the issue? and,[/FONT]

[*][FONT=inherit]What should be done to fix it?[/FONT]
[/LIST]

---

### Post by Xian on 2021-05-19
Run the command below and view the output. 

The error message will most likely disappear after completing the upgrade.

$ sudo update-initramfs -u

---

### Post by guiverc on 2021-05-20
Also asked at [https://askubuntu.com/questions/1339395/during-ubuntu-upgrade-from-18-to-20-i-got-the-kernel-related-error-could-not](https://askubuntu.com/questions/1339395/during-ubuntu-upgrade-from-18-to-20-i-got-the-kernel-related-error-could-not)


Ubuntu Core 18 is a different product to Ubuntu 20.04 LTS.

Ubuntu uses the *yy format *for *snap* only releases, with *yy.mm* for the more popular *deb* based releases.   Please provide correct details.

---

### Post by ActionParsnip on 2021-05-20
In future, if the output you can see is text based, just copy and paste the text. Screenshots of text isn't needed.......think about it

---

