---
title: "completely remove grafana install, trying to start over"
date: 2020-10-05
forum: Installation &amp; Upgrades
---

### Post by shadowsaunter on 2020-10-05
I'm trying to install Grafana on Ubuntu 20.04 LTS, but when I try to get the GPG key with the command: 
```

wget --no-check-certificate -qO - https://packages.grafana.com/gpg.key | sudo apt-key add -

```

I'm getting:
 
```

gpg: no valid OpenPGP data found.

```

I was having issues with a corporate proxy with a previous install and tried to remove grafana, but I think I've only partially removed it because now I can't grab the GPG via wget or curl.

Could I get help completely removing my previous grafana install?

---

### Post by shadowsaunter on 2020-10-05
I guess I just needed 'sudo' in front of my wget command.

```


sudo wget --no-check-certificate -qO - [https://packages.grafana.com/gpg.key](https://packages.grafana.com/gpg.key) | sudo apt-key add -


```

This worked for me.  Sorry for starting a new thread for this, the 'No valid OpenPGP' message I was getting wasn't very helpful!

---

