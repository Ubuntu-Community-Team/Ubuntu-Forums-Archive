---
title: "preseed inject configuration"
date: 2020-10-26
forum: Installation &amp; Upgrades
---

### Post by johnnybee2 on 2020-10-26
Hi,

I'm trying to inject configuration in a specific file .conf with **ubiquity success_command **

In my preseed file i'm using ubiquity success_command.  (old d-i preseed/late_command is not compatible with ubiquity)

ubiquity ubiquity/success_command string \
in-target apt update -y; \
in-target apt upgrade -y; \
in-target wget -P /home  [https://apt.puppetlabs.com/puppet6-release-focal.deb;](https://apt.puppetlabs.com/puppet6-release-focal.deb;) \
in-target dpkg -i /home/puppet6-release-focal.deb; \
in-target apt update -y; \
in-target apt install -y puppet-agent; \
> WORKS

[B]in-target /bin/sh -c 'echo "[main]" | tee -a /target/etc/puppetlabs/puppet/puppet.conf'; \
in-target /bin/sh -c 'echo "certname = $HOSTNAME" | tee -a /target/etc/puppetlabs/puppet/puppet.conf'; \
in-target /bin/sh -c 'echo "server = server.example.com" | tee -a /target/etc/puppetlabs/puppet/puppet.conf';[/B]
> DOES NOT WORK

**in-target echo -e "[main]\ncertname = $HOSTNAME\nserver = ****[B]server.example.com**\nenvironment = production\nruninterval = 15m" >> /target/etc/puppetlabs/puppet/puppet.conf ;[/B]
> DOES NOT WORK

If i test manually in a simple terminal with command everything is working
Do you have the same behaviour ?

Ubuntu 20.04 LTS amd64 Live installer with Ubiquity

Thank you for help
Regards

---

### Post by johnnybee2 on 2020-10-28
Hi,

Finally, I'm using post-install script in chroot install env.

Ubiquity sucks, preseed with Ubuntu Ubiquity is too limited, it sucks too

---

