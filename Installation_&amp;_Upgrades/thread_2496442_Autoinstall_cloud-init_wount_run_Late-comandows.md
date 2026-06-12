---
title: "Autoinstall cloud-init wount run Late-comandows"
date: 2024-03-28
forum: Installation &amp; Upgrades
---

### Post by eura on 2024-03-28
Using Ubuntu Server 22.04, I am attempting to create an  auto-installation setup for a physical client. I want to enable root  login and execute late commands. Additionally, I want the hostname to be  set as "new-client-macadress" without colons. Despite trying various  syntaxes, the commands do not seem to take effect. I have experimented  with different configurations, but none have yielded the desired  results.

Here is my cloud-init conf
[QUOTE][
#cloud-config
   autoinstall:
   version: 1
     user-data:
     hostname: new-client
     timezone: Europe/Stockholm
     chpasswd:
     expire: false
     list:
     - root:$6$exDY1mhS4KUYCE/2$zmn9ToZwTKLhCw.b4/b.ZRTIZM30JZ4QrOQ2aOXJ8yk96xpcCof0kxKwuX1kqLG/ygbJ1f8wxED22bTL4F46P0
   keyboard:
     layout: se
    toggle: null
    variant: ''
   
   late-commands:
     - sed -i "s?new-client?new-client-$(cat /target/sys/class/net/enp*/address | sed 's/\://g')?g" /target/etc/hostname /etc/hosts"
     - echo "PermitRootLogin yes" | tee -a /target/etc/ssh/sshd_config"
     - systemctl restart ssh
/QUOTE]
Very grateful for any feedback

---

### Post by dgrosvenor on 2024-05-07
Not sure if you figured this out or not, but this is what I do for the `late_commands` section:

```

late_commands:
  zz_01_verify_curtin_userdata_ubuntu_ppc : ['curtin', 'in-target', '--', 'sh', '-c', "echo 'curtin_userdata_ubuntu_ppc' >> /var/log/verify"]

```

I name them with `zz_<step#>_<info>` just for my own purposes, but I think you can name them whatever you want. So you should do (with the correct quote escaping):

```

late_commands:
  zz_01_sed : ['curtin', 'in-target', '--', 'sh', '-c', "sed ..."]
  zz_02_echo : ['curtin', 'in-target', '--', 'sh', '-c', "echo ..."]
  zz_03_restart : ['curtin', 'in-target', '--', 'sh', '-c', "systemctl ... "]

```

Edit:
Here is the docs on curtain and how to use the <stage>_commands option:
[https://curtin.readthedocs.io/en/latest/topics/config.html#stages](https://curtin.readthedocs.io/en/latest/topics/config.html#stages)


> **eura said:**
> Using Ubuntu Server 22.04, I am attempting to create an  auto-installation setup for a physical client. I want to enable root  login and execute late commands. Additionally, I want the hostname to be  set as "new-client-macadress" without colons. Despite trying various  syntaxes, the commands do not seem to take effect. I have experimented  with different configurations, but none have yielded the desired  results.

Here is my cloud-init conf
[QUOTE][
#cloud-config
   autoinstall:
   version: 1
     user-data:
     hostname: new-client
     timezone: Europe/Stockholm
     chpasswd:
     expire: false
     list:
     - root:$6$exDY1mhS4KUYCE/2$zmn9ToZwTKLhCw.b4/b.ZRTIZM30JZ4QrOQ2aOXJ8yk96xpcCof0kxKwuX1kqLG/ygbJ1f8wxED22bTL4F46P0
   keyboard:
     layout: se
    toggle: null
    variant: ''
   
   late-commands:
     - sed -i "s?new-client?new-client-$(cat /target/sys/class/net/enp*/address | sed 's/\://g')?g" /target/etc/hostname /etc/hosts"
     - echo "PermitRootLogin yes" | tee -a /target/etc/ssh/sshd_config"
     - systemctl restart ssh
/QUOTE]
Very grateful for any feedback

---

