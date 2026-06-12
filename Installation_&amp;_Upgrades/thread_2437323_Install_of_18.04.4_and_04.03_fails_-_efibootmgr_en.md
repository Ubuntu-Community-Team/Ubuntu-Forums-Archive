---
title: "Install of 18.04.4 and 04.03 fails - efibootmgr: entry xxF does not exist."
date: 2020-02-21
forum: Installation &amp; Upgrades
---

### Post by joeost on 2020-02-21
Im having an odd issue. Im trying to install 18.04.4-server or 18.04.3 on a Dell Inspiron 5680, but it fails. Version 17.10 sems to work, and other distors (Debian 9) work as well. Its failing with the following errors. I tested in both UEFI and BIOS mode



**New UEFI boot order: 100F,0000,000A,000B,000C,000D,000E,0008,0009**

**Invalid BootOrder order entry value100F   	**
**                                                       ^**
**efibootmgr: entry 100F does not exist.**

---

### Post by CelticWarrior on 2020-02-21
Exactly when that error message appears?

---

### Post by joeost on 2020-02-21
Here is a copy of the syslog. Search for "[COLOR=#000000]Invalid BootOrder order entry[/COLOR]"

[https://paste.ubuntu.com/p/43h73SBVWf/](https://paste.ubuntu.com/p/43h73SBVWf/)

I get the error message when during the ubuntu install. I complete setup wizards, language, disk/partition (i select guided complete disk). It starts the install, and then at some point it fails. I select view log, and i see the the following as the last entry

Feb 21 18:38:00 ubuntu-server curtin_log.1941[2190]: Setting currently booted 1010 as the first UEFI loader.
Feb 21 18:38:00 ubuntu-server curtin_log.1941[2190]: New UEFI boot order: 1010,0000,0009,0008,000A,000B,000C,000D,000E
Feb 21 18:38:00 ubuntu-server curtin_log.1941[2190]: Running command ['mount', '--bind', '/dev', '/target/dev'] with allowed return codes [0] (capture=False)
Feb 21 18:38:00 ubuntu-server curtin_log.1941[2190]: Running command ['mount', '--bind', '/proc', '/target/proc'] with allowed return codes [0] (capture=False)
Feb 21 18:38:00 ubuntu-server curtin_log.1941[2190]: Running command ['mount', '--bind', '/sys', '/target/sys'] with allowed return codes [0] (capture=False)
Feb 21 18:38:00 ubuntu-server curtin_log.1941[2190]: Running command ['unshare', '--fork', '--pid', '--', 'chroot', '/target', 'efibootmgr', '-o', '1010,0000,0009,0008,000A,000B,000C,000D,000E'] with allowed return codes [0] (capture=False)
Feb 21 18:38:00 ubuntu-server curtin_log.1941[2190]: Invalid BootOrder order entry value1010
Feb 21 18:38:00 ubuntu-server curtin_log.1941[2190]:                                      ^
Feb 21 18:38:00 ubuntu-server curtin_log.1941[2190]: efibootmgr: entry 1010 does not exist
Feb 21 18:38:00 ubuntu-server curtin_log.1941[2190]: Running command ['udevadm', 'settle'] with allowed return codes [0] (capture=False)
Feb 21 18:38:00 ubuntu-server curtin_log.1941[2190]: TIMED subp(['udevadm', 'settle']): 0.008
Feb 21 18:38:00 ubuntu-server curtin_log.1941[2190]: Running command ['umount', '/target/sys'] with allowed return codes [0] (capture=False)
Feb 21 18:38:00 ubuntu-server curtin_log.1941[2190]: Running command ['umount', '/target/proc'] with allowed return codes [0] (capture=False)
Feb 21 18:38:00 ubuntu-server curtin_log.1941[2190]: Running command ['umount', '/target/dev'] with allowed return codes [0] (capture=False)
Feb 21 18:38:00 ubuntu-server curtin_event.1941[4041]: finish: cmd-install/stage-curthooks/builtin/cmd-curthooks: FAIL: curtin command curthooks
Feb 21 18:38:00 ubuntu-server curtin_log.1941[2190]: finish: cmd-install/stage-curthooks/builtin/cmd-curthooks: FAIL: curtin command curthooks
Feb 21 18:38:00 ubuntu-server curtin_log.1941[2190]: Traceback (most recent call last):
Feb 21 18:38:00 ubuntu-server curtin_log.1941[2190]:   File "/snap/subiquity/1093/lib/python3.6/site-packages/curtin/commands/main.py", line 202, in main
Feb 21 18:38:00 ubuntu-server curtin_log.1941[2190]:     ret = args.func(args)
Feb 21 18:38:00 ubuntu-server curtin_log.1941[2190]:   File "/snap/subiquity/1093/lib/python3.6/site-packages/curtin/commands/curthooks.py", line 1471, in curthooks
Feb 21 18:38:00 ubuntu-server curtin_log.1941[2190]:     builtin_curthooks(cfg, target, state)
Feb 21 18:38:00 ubuntu-server curtin_log.1941[2190]:   File "/snap/subiquity/1093/lib/python3.6/site-packages/curtin/commands/curthooks.py", line 1437, in builtin_curthooks
Feb 21 18:38:00 ubuntu-server curtin_log.1941[2190]:     setup_grub(cfg, target, osfamily=osfamily)
Feb 21 18:38:00 ubuntu-server curtin_log.1941[2190]:   File "/snap/subiquity/1093/lib/python3.6/site-packages/curtin/commands/curthooks.py", line 535, in setup_grub
Feb 21 18:38:00 ubuntu-server curtin_log.1941[2190]:     uefi_reorder_loaders(grubcfg, target)
Feb 21 18:38:00 ubuntu-server curtin_log.1941[2190]:   File "/snap/subiquity/1093/lib/python3.6/site-packages/curtin/commands/curthooks.py", line 393, in uefi_reorder_loaders
Feb 21 18:38:00 ubuntu-server curtin_log.1941[2190]:     in_chroot.subp(['efibootmgr', '-o', new_boot_order])
Feb 21 18:38:00 ubuntu-server curtin_log.1941[2190]:   File "/snap/subiquity/1093/lib/python3.6/site-packages/curtin/util.py", line 689, in subp
Feb 21 18:38:00 ubuntu-server curtin_log.1941[2190]:     return subp(*args, **kwargs)
Feb 21 18:38:00 ubuntu-server curtin_log.1941[2190]:   File "/snap/subiquity/1093/lib/python3.6/site-packages/curtin/util.py", line 275, in subp
Feb 21 18:38:00 ubuntu-server curtin_log.1941[2190]:     return _subp(*args, **kwargs)
Feb 21 18:38:00 ubuntu-server curtin_log.1941[2190]:   File "/snap/subiquity/1093/lib/python3.6/site-packages/curtin/util.py", line 141, in _subp
Feb 21 18:38:00 ubuntu-server curtin_log.1941[2190]:     cmd=args)
Feb 21 18:38:00 ubuntu-server curtin_log.1941[2190]: curtin.util.ProcessExecutionError: Unexpected error while running command.
Feb 21 18:38:00 ubuntu-server curtin_log.1941[2190]: Command: ['unshare', '--fork', '--pid', '--', 'chroot', '/target', 'efibootmgr', '-o', '1010,0000,0009,0008,000A,000B,000C,000D,000E']
Feb 21 18:38:00 ubuntu-server curtin_log.1941[2190]: Exit code: 8
Feb 21 18:38:00 ubuntu-server curtin_log.1941[2190]: Reason: -
Feb 21 18:38:00 ubuntu-server curtin_log.1941[2190]: Stdout: ''
Feb 21 18:38:00 ubuntu-server curtin_log.1941[2190]: Stderr: ''

---

### Post by joeost on 2020-02-21
I used the server instead of the live-server ISO, and install was successful

Worked - [http://old-releases.ubuntu.com/releases/18.04.3/ubuntu-18.04.3-server-arm64.iso](http://old-releases.ubuntu.com/releases/18.04.3/ubuntu-18.04.3-server-arm64.iso)
Failed - [http://old-releases.ubuntu.com/releases/18.04.3/ubuntu-18.04.3-live-server-amd64.iso](http://old-releases.ubuntu.com/releases/18.04.3/ubuntu-18.04.3-live-server-amd64.iso)
Failed - [http://mirror.eu-lo.kamatera.com/ubuntu-releases/18.04.4/ubuntu-18.04.4-live-server-amd64.iso](http://mirror.eu-lo.kamatera.com/ubuntu-releases/18.04.4/ubuntu-18.04.4-live-server-amd64.iso)

---

