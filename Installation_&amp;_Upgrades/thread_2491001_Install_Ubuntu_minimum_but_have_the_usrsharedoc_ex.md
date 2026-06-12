---
title: "Install Ubuntu minimum but have the /usr/share/doc examples"
date: 2023-09-22
forum: Installation &amp; Upgrades
---

### Post by gabecz on 2023-09-22
Hi
22.04.3
I'd like to keep my system at minimum but would like to have the examples downloaded when apt installing a package.
Is that possible?
Does it make THAT big of a difference installing a full vs a minimized system? We have a quite massive vmware environment, so basically no hardware/disk space restrictions but wouldn't want to have unnecessary packages/services/stuff to run on my ubuntu servers.
Thanks

---

### Post by ian-weisser on 2023-09-22
What examples do you have in mind? What packages provide those examples?

If examples are in a package you install, then you will get those examples.
If examples are in a package that you don't install, then you won't get those examples.

Apt won't selectively install files in most circumstances. It's the whole package or not.

---

### Post by gabecz on 2023-09-22
I have now installed a full ubuntu instead of a minimal.
ONE example is /usr/share/doc/netplan/examples but in particular I needed /usr/share/doc/openvpn/examples and openvpn radius examples. with minimal install these folders are empty. With full install the folders are populated with the apps example files.

---

### Post by gabecz on 2023-09-22
This is another that I found. His solution was to install a full install not minimized. I hope there's a middle road [https://ubuntuforums.org/showthread.php?t=2485956&p=14139232](https://ubuntuforums.org/showthread.php?t=2485956&p=14139232)

---

### Post by ian-weisser on 2023-09-22
Similar question to [https://askubuntu.com/questions/1486703/how-to-make-minimized-ubuntu-to-download-example-files](https://askubuntu.com/questions/1486703/how-to-make-minimized-ubuntu-to-download-example-files)

Is this some kind of class assignment?

[EDIT]: Apparently not, but as originally phrased it was certainly a possibility. The duplication in multiple venues under different names was suspicious. It's a fair question, as we get those folks here too and we are not a homework service.

---

### Post by jagsdesai on 2023-09-22
> **gabecz said:**
> Hi. I'm deleting this, because I don't like to be talked down for asking a question I haven't found an answer to googling it.

hi, you shouldn't feel that way. Anyway, I don't have an exact answer to your question but here are few ways to find examples you're looking for:

(1) Ubuntu manpages: [https://manpages.ubuntu.com/manpages/lunar/man5/netplan.5.html](https://manpages.ubuntu.com/manpages/lunar/man5/netplan.5.html)

(2) Netplan documentation on Ubuntu.com: [https://people.ubuntu.com/~slyon/netplan-docs/examples/](https://people.ubuntu.com/~slyon/netplan-docs/examples/)

(3) From this page: [https://ubuntu-mate.community/t/no-bash-doc-examples/17537](https://ubuntu-mate.community/t/no-bash-doc-examples/17537)

Sometimes you can just install the doc using apt: ```
sudo apt install bash-doc
``` This may not be true for all packages.

(4) Tutorials: [https://www.digitalocean.com/community/tutorials](https://www.digitalocean.com/community/tutorials)

These are just few sample links but there are many ways you can find examples/templates/tutorials for popular packages like netplan, iptables, nftables etc. Hope this helps. Thanks.

---

### Post by MAFoElffen on 2023-09-24
You forgot the output to this is support of your question and ian-weisser's answer
```

apt list openvpn --installed

```
On my test case, package openvpn shows as "installed,automatic". Which means it was not manually installed. It was a default installed package pulled in by dependencies of another package deemed as part of ubuntu-server-minimal. So since installed, it installed the docs and examples...

Since I've been on the Ubuntu Server Team since 2012, I feel that the part of what I contribute to Ubuntu is to the support of Ubuntu Server Edition, and testing of the pre-releases. I try my best to do that. Honestly, my focus and priorities lean towards supporting the User's of.

No emotions nor judgements. Just the facts.

---

### Post by gabecz on 2023-09-28
(without going down the road commenting on the first few posts which of i can't come out on the top and will ignore any further comments on it. it was not a class assignment)

the solution is to nano /etc/dpkg/dpkg.cfg.d/excludes and modify **exclude **to **include** below *# Drop all documentation* and apt install --reinstall the package i needed the example files for.
thanks for the suggestions, and hope it helps others too.

---

### Post by QIII on 2023-09-28
Original content of posts restored.

Thread closed.

---

