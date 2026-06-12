---
title: "Ubuntu bionic kernel does not support cgroup cpu real-time runtime"
date: 2018-07-18
forum: Installation &amp; Upgrades
---

### Post by smbptnk on 2018-07-18
[LEFT][FONT=arial][COLOR=#24292e]Hi

[/COLOR][COLOR=#24292e]How can we enable cpu-rt-runtime on Ubuntu bionic .

Info: reading kernel config from /boot/config-4.15.0-23-generic ...[/COLOR][/FONT][/LEFT]

[LIST]
[*][FONT=arial]CONFIG_RT_GROUP_SCHED: missing
error message got -
docker create -t -i --hostname racnode1 \[/FONT]
[/LIST]
[INDENT][FONT=arial]      --volume /boot:/boot:ro \
      --volume /dev/shm --tmpfs /dev/shm:rw,exec,size=4G \
      --volume /opt/containers/rac_host_file:/etc/hosts  \
      --dns-search=example.com \
      --privileged=false --volume racstorage:/oradata \
      --cap-add=SYS_ADMIN --cap-add=SYS_NICE \
      --cap-add=SYS_RESOURCE --cap-add=NET_ADMIN \
      -e NODE_VIP=172.15.1.160  -e VIP_HOSTNAME=racnode1-vip  \
      -e PRIV_IP=192.168.17.150  -e PRIV_HOSTNAME=racnode1-priv \
      -e PUBLIC_IP=172.15.1.150 -e PUBLIC_HOSTNAME=racnode1  \
      -e SCAN_NAME=racnode-scan -e SCAN_IP=172.15.1.70  \
      -e OP_TYPE=INSTALL -e DOMAIN=example.com \
      -e ASM_DISCOVERY_DIR=/oradata -e ORACLE_PWD="Oracle_12c" \
      -e ASM_DEVICE_LIST=/oradata/asm_disk01.img,/oradata/asm_disk02.img,/oradata/asm_disk03.img,/oradata/asm_disk04.img,/oradata/asm_disk05.img  \
      -e CMAN_HOSTNAME=racnode-cman1 -e CMAN_IP=172.15.1.15 \
      -e OS_PASSWORD=Oracle_12c \
      --restart=always --tmpfs=/run -v /sys/fs/cgroup:/sys/fs/cgroup:ro \
      --cpu-rt-runtime=95000 --ulimit rtprio=99  \
      --name racnode1 oracle/database-rac:12.2.0.1

[/FONT][LEFT][FONT=arial][COLOR=#24292e]Error response from daemon: Your kernel does not support cgroup cpu real-time runtime[/COLOR][COLOR=#24292e]
[/COLOR][COLOR=#24292e]Distribution:

Distributor ID: Ubuntu
Description:    Ubuntu 18.04 LTS
Release:        18.04
Codename:       bionic[/COLOR][COLOR=#24292e]
[/COLOR][COLOR=#24292e]Thanks in adv.[/COLOR][/FONT][/LEFT]
[/INDENT]

---

### Post by ubfan1 on 2018-07-18
You need a real-time kernel, not the one distributed with bionic. See [https://wiki.archlinux.org/index.php/Realtime_kernel](https://wiki.archlinux.org/index.php/Realtime_kernel)

---

