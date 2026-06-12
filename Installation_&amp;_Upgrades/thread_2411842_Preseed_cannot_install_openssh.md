---
title: "Preseed: cannot install openssh"
date: 2019-02-04
forum: Installation &amp; Upgrades
---

### Post by dclabaut on 2019-02-04
Hello everyone,
I am preparing an installation ISO based on Ubuntu Desktop 18.04 and preseed to ease my Ubuntu installations.
I need a basic install with an Ansible user account and openssh-server configured, so that I can access the machine from Ansible and run more complex tasks.

However, I cannot find a way to install openssh-server. My apt configuration is as follows:
```
# Apt
d-i apt-setup/restricted boolean true
d-i apt-setup/universe boolean true
d-i apt-setup/backports boolean true
d-i apt-setup/use_mirror boolean true
d-i apt-setup/services-select multiselect security, updates
d-i apt-setup/security_host string security.ubuntu.com
d-i apt-setup/security_path string /ubuntu
```

I have tried installing with pkgsel:
```
d-i pkgsel/include string openssh-server
```

but the package is not installed after reboot (apt install openssh-server does install a NEW package)

I also tried with late_command:
```
d-i preseed/late_command string \
        apt install -y openssh-server openssh-sftp-server; \
        systemctl start sshd
```

but I get the same result.

I do not see any logs:
```
root@newbie:~# grep -Ri ssh /var/log/installer
root@newbie:~# 
```

PS: While searching for similar issues, I have found people looking for a way to do a fully unattended install. There is a good documented example here, that works on 18.04: [https://askubuntu.com/questions/806820/how-do-i-create-a-completely-unattended-install-of-ubuntu-desktop-16-04-1-lts](https://askubuntu.com/questions/806820/how-do-i-create-a-completely-unattended-install-of-ubuntu-desktop-16-04-1-lts)

---

### Post by dclabaut on 2019-02-04
Ok, so after many things tried, here is an explanation:
In the short yet useful UbiquityAutomation documentation ([https://wiki.ubuntu.com/UbiquityAutomation](https://wiki.ubuntu.com/UbiquityAutomation)), it is specified that Ubiquity ignores commands such as tasksel, pkgsel and late_command.
It is recommended to use ubiquity/success_command instead.

However, that's not enough.
In this Linux Mint forum post from 2017 ([https://forums.linuxmint.com/viewtopic.php?t=236838](https://forums.linuxmint.com/viewtopic.php?t=236838)), it is specified that Ubiquity shuts down the network interface before running the success_command, so it needs to be re-enabled manually.
I modernized the answer from the Mint forum, and I now have this solution:
```
ubiquity ubiquity/success_command \
    string ip link set up dev enp0s3; \
           dhclient enp0s3; \
           apt-get update -y; \
           in-target apt-get install -y openssh-server;
```

This is working, I can now ssh to localhost, and should be able to ssh from outside too!

---

