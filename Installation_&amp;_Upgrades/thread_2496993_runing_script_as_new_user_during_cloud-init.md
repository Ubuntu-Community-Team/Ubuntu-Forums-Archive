---
title: "runing script as new user during cloud-init"
date: 2024-04-19
forum: Installation &amp; Upgrades
---

### Post by harryzwh on 2024-04-19
I am new to use cloud-init to automate the installation of Ubuntu22.04. I am now able to install the OS by using the cloud-config below
```

#cloud-config
autoinstall:
  version: 1
  apt:
    primary:
    - arches: [default]
      uri: http://freenas.boot.pxe:9081/repository/apt-proxy/
  user-data:
    timezone: Asia/Shanghai
    disable_root: true
  identity:
    hostname: ubuntu
    password: $6$FhcddHFVZ7ABA4Gi$r9wyPRFCtp1fL28aj6C9G4GIePSfqqUDVJAq7.qAtookMeYJCY6NH7TF19NZHk.x0ign7Y7Xgh3JEGcXVfozH1
    username: oai 
  keyboard: {layout: us, variant: ''}
  locale: en_US.UTF-8
  ssh:
    install-server: true
  packages:
    - htop
    - iftop
    - curl
    - git
    - gnupg-agent
  storage:
    layout:
      name: direct
  late-commands: 
    - curtin in-target --target=/target -- wget -O /usr/local/bin/post_script.sh http://freenas.boot.pxe:8080/PXE/Preseed/post_script.sh
    - curtin in-target --target=/target -- chmod +x /usr/local/bin/post_script.sh
    - curtin in-target --target=/target -- /bin/bash /usr/local/bin/post_script.sh

```

During the installing, a new user named "oai" is created and post configuration script "post_script.sh" is downloaded to the target and executed. However, when executing the post_script, it cannot see the newly created user "oai". A simple script below will throw an exception says user "oai" is not exist.
```

#!/bin/bash

mkdir -p /home/oai
chown oai:oai /home/oai

```

It seems that the user "oai" is not yet created when running late-commands. It is the right place the put the post configuration script in late-command? Is there any other way to set the owner of a file/path to the newly created user rather than root during the cloud-init process.

Thanks.

---

### Post by ActionParsnip on 2024-04-19
Can you set the UID in the code, then set it using the UID? Does that work?

---

### Post by MAFoElffen on 2024-04-20
Cloud-init is executed as root. Yiu can set user permissions and user or group ownership's as root. It there s problem with that  concept in itself?

I tend to put more value on group memberships, for things that need to be shared beyond a single user. May be just me, but there is a big difference between a personal computer, and server(s) with clients infrastructure... And what sense to implement it's support.

---

### Post by harryzwh on 2024-04-20
> **ActionParsnip said:**
> Can you set the UID in the code, then set it using the UID? Does that work?

chown using uid/gid works. Thank you!

---

