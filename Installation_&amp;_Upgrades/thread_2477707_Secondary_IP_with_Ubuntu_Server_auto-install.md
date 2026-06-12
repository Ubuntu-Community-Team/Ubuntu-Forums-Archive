---
title: "Secondary IP with Ubuntu Server auto-install"
date: 2022-08-04
forum: Installation &amp; Upgrades
---

### Post by pclvv1 on 2022-08-04
I'm seeing two IP addresses on my hosts after running the cloud-init auto-installer.

This is on both VMs/bare metal, using the 20.04.4 and 22.04 install media. No user-data key is present in the autoinstall config. I've tried omitting the network section altogether as well as including:

```
[COLOR=#d8dee9][FONT=Consolas][COLOR=#616e88]network:[/COLOR]

[COLOR=#616e88]    ethernets:[/COLOR]

[COLOR=#616e88]      eth1:[/COLOR]

[COLOR=#616e88]        dhcp4: true[/COLOR][/FONT][/COLOR]

```

That part of the config seems apply normally, but it looks like the configuration in /etc/netplan/50-cloud-init.yaml is being applied in addition to it (output of cat /etc/netplan/*.yaml attached). Deleting it, flushing IPs and re-applying netplan seems to confirm that as just one IP is created then. However, if I reboot the system, 50-cloud-init.yaml is regenerated, despite a file with *network: {config: disabled}* being present in /etc/cloud/cloud.cfg.d/.

Has anyone encounted similar? If possible I'd like to handle this all during install and avoid hacking about with services afterwards.

---

