---
title: "Prompting for passphrase for virtual disk"
date: 2019-03-01
forum: Installation &amp; Upgrades
---

### Post by Nigel_Pain on 2019-03-01
I've just upgraded a virtual machine (VMWare) from 14.04 LTS to 16.04 LTS. Since then there's a pause in the boot process which seems to be prompting for a passphrase. Hitting Enter causes the process to continue but after that, certain operations (I think using /tmp) also produce a broadcast message:

```
Password entry required for 'Please enter passphrase for disk Virtual_disk (cryptswap1)!' (PID 3877).
Please enter password with the systemd-tty-ask-password-agent tool!
```

I've done a bit of searching around and it appears to be something to do with the swap being encrypted? There's an entry in /etc/crypttab:

```
cryptswap1 /dev/sda7 /dev/urandom swap,cipher=aes-cbc-essiv:sha256
```

There wasn't anything like this before the upgrade, and a different machine doesn't seem to have this after the same upgrade. Any ideas how to sort it?

---

