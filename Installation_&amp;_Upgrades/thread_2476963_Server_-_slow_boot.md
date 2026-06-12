---
title: "Server - slow boot"
date: 2022-07-12
forum: Installation &amp; Upgrades
---

### Post by Geoff_Lane on 2022-07-12
Needing to upgrade my main system I have been experimenting with Ubuntu Server.

No obvious issues except a painfully slow wait for [B]a start job is running for Network to be configured

[/B]This waits until around 2m 15s then continues.  On a previous practice installation after installing Mate desktop I altered the /etc/netplan/00-installer-config.yaml to show;

renderer
  NetworkManager

and it boots fine.

Any tips for speeding this Server boot process as at the moment I don't have a Desktop and not sure if I can use network manager without a Desktop.

Geoff

---

### Post by MAFoElffen on 2022-07-13
Mine did that, but on boot completion, all the network devices worked fine...

It was like it was waiting for the NIC devices to be up, but something wasn't there yet, in that section of the boot process.

The way I got around that was to edit my netplan .yaml file, by adding the line: 'optional: true' as the last line under all my NIC defines. The default, if not there is false. If now does a quick check, but if not up yet, goes on with the boot process. Boots much faster now.

Since everything works when it is booted, it's not a bother to me.

EDIT: When editing .yaml files, only use a text editor, ensure you only use spaces (no tabs) and respect the whitepace. Everything must line up correctly. One space more or less and it thinks it belongs to something else. Sort of like Pyhton... 

Then do 
```

sudo netplan try
sudo netplan generate
sudo netplan apply

```

---

### Post by TheFu on 2022-07-13
I remove network manager as the renderer in the YAML.
I'll have to try the 'optional' thing, but since it is on a per-device thing, looks like we have to list each unused ethernet device to add it.  

But since I reboot very seldom, boot time has not really be a concern to me. Anything under 60 sec is fine for a server.

```
$ systemd-analyze critical-chain 
The time after the unit is active or started is printed after the "@" character.
The time the unit takes to start is printed after the "+" character.

graphical.target @14.946s
&#9492;&#9472;multi-user.target @14.946s
  &#9492;&#9472;lxd-containers.service @6.074s +5.730s
    &#9492;&#9472;lxd.service @10.911s +32.149s
      &#9492;&#9472;network-online.target @10.908s
        &#9492;&#9472;network.target @10.899s
          &#9492;&#9472;networking.service @5.685s +5.213s
            &#9492;&#9472;apparmor.service @5.388s +262ms
              &#9492;&#9472;local-fs.target @5.356s
                &#9492;&#9472;run-user-1000.mount @22.287s
                  &#9492;&#9472;swap.target @1.863s
                    &#9492;&#9472;dev-hadar\x2dvg-swap_1.swap @1.739s +117ms
                      &#9492;&#9472;dev-hadar\x2dvg-swap_1.device @1.692s
```

---

### Post by Geoff_Lane on 2022-07-13
> **MAFoElffen said:**
> Mine did that, but on boot completion, all the network devices worked fine...

It was like it was waiting for the NIC devices to be up, but something wasn't there yet, in that section of the boot process.

The way I got around that was to edit my netplan .yaml file, by adding the line: 'optional: true' as the last line under all my NIC defines. The default, if not there is false. If now does a quick check, but if not up yet, goes on with the boot process. Boots much faster now.



Tried that, quick boot worked fine but no internet connection.

Tried restarting wpa_supplicant but advises me already running, not quite got the hang of manipulating wifi using the command line.

I'll install a desktop soon, just deciding which one.   That should sort it.

Geoff

---

### Post by TheFu on 2022-07-13
Wifi!   on a server!???

Say it isn't true!

---

### Post by Geoff_Lane on 2022-07-13
It's going to be a Desktop, I merely used the Server installation for two reasons, one to see how it went (learning curve) and secondly to maybe have more choice on setup.

My network server running numerous services for local and remote use is a Raspberry Pi with wired ethernet connection.

Geoff

---

