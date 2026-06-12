---
title: "Ubuntu Server LTS 22.04.1: Boot loop after applying updates"
date: 2022-09-13
forum: Installation &amp; Upgrades
---

### Post by doalwa2 on 2022-09-13
Hello everybody, 

we're running an Ubuntu LTS 22.04.1 VM under HyperV 2016. We use the server for a deployment of the Vaultwarden docker container.

Today, after upgrading the server with the usual

```

sudo apt update && sudo apt update -y

```

followed by a reboot, the VM boots to the Grub2 boot screen and then just reboots.

The only way to get out of this boot loop is manually selecting the grub entry 

"Ubuntu, with Linux 5.15.0-46-generic"

The automatically selected entry

"Ubuntu, with Linux 5.15.0-47-generic"

just results in a reboot.

According to /var/log/apt/history.log, the following packages were upgraded during the last apt upgrade:

```

Start-Date: 2022-09-13  14:49:04
Commandline: apt upgrade
Requested-By: admin (1000)
Upgrade: dmidecode:amd64 (3.3-3, 3.3-3ubuntu0.1), docker-ce-cli:amd64 (5:20.10.17~3-0~ubuntu-jammy, 5:20.10.18~3-0~ubuntu-jammy), docker-ce:amd64 (5:20.10.17~3-0~ubuntu-jammy, 5:20.10.18~3-0~ubuntu-jammy), docker-ce-rootless-extras:amd64 (5:20.10.17~3-0~ubuntu-jammy, 5:20.10.18~3-0~ubuntu-jammy), linux-firmware:amd64 (20220329.git681281e4-0ubuntu3.4, 20220329.git681281e4-0ubuntu3.5), zlib1g:amd64 (1:1.2.11.dfsg-2ubuntu9, 1:1.2.11.dfsg-2ubuntu9.1), intel-microcode:amd64 (3.20220510.0ubuntu0.22.04.1, 3.20220809.0ubuntu0.22.04.1)
End-Date: 2022-09-13  14:51:35

```


Is there a known issue with the 5.15.0-47 kernel? Any idea were I could check what exactly is causing the boot loop with this particular kernel?

Thanks in advance,

Dominik

---

