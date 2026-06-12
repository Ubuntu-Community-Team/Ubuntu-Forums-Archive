---
title: "grub configured static ip/gw causes &quot;gateway4 has been deprecated&quot; error in netplan"
date: 2022-05-18
forum: Installation &amp; Upgrades
---

### Post by gorantornqvist on 2022-05-18
Hi,
Trying to create a ubuntu-22.04 host with packer and for the build/template VM we set a static IP in grub using variables from packer:

"ip=\"{{ user `vm_ip` }}::{{ user `vm_gateway` }}:{{ user `vm_netmask` }}::::{{ user `vm_dns` }}\" "

And in the last step in the build process we clear /etc/netplan/* which will make VMs cloned from the template to use dhcp.
This worked fine with 20.4 but with 22.04 this causes the error:
[COLOR=#242424][FONT=-apple-system]** (generate:1614): WARNING **: 10:54:43.330: `gateway4` has been deprecated, use default routes instead.[/FONT][/COLOR]
[COLOR=#242424][FONT=-apple-system]See the 'Default routes' section of the documentation for more details.[/FONT][/COLOR]

And netplan will then revert to use the old config from /run/netplan which is the static ip!

Not sure what part generates the "[COLOR=#242424][FONT=-apple-system]gateway4[/FONT][/COLOR]" part of the netplan config, cloud-init, netplan, something else ...

Any suggestions how to make my install generate this netplan conf instead?
```

routes:
      - to: default
        via: 192.168.1.1

```

Thanks ...

EDIT:
These are post steps that doesnt seem to work anymore.
rm /etc/cloud/cloud.cfg.d/*.cfg
cloud-init clean -s -l

Also tried adding these steps but it doesnt help:
rm -f /etc/netplan/*
rm -f /run/netplan/*

[COLOR=#D4D4D4][FONT=Consolas]

[/FONT][/COLOR]

---

### Post by gorantornqvist on 2022-05-19
Found the reason, for some reason the autoinstall and ip settings etc that I set in grub with packer boot command:

        "ip=\"{{ user `vm_ip` }}::{{ user `vm_gateway` }}:{{ user `vm_netmask` }}::::{{ user `vm_dns` }}\" ",
        "autoinstall ds=\"nocloud-net;seedfrom=http://{{.HTTPIP}}:{{.HTTPPort}}/\"<enter><wait>",

These persisted in grub after installation for some weird reason
Quick fix was to do:

sed -i 's/GRUB_CMDLINE_LINUX_DEFAULT\=.*/GRUB_CMDLINE_LINUX_DEFAULT\=\"\"/' {/etc/default/grub,/etc/default/grub.ucf-dist}

---

