---
title: "Howto debootstrap a dapper system."
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by eldaria on 2006-10-30
Does anyone have an Easy and quick way to setup a remote system with debootstrap?

I have a server wich I'm not in front of, it has edgy installed on it but due to some bugs, I want to reinstall it with dapper.

After reading abit I figured out that by running the command:
```

debootstrap --include=openssh-server dapper /mnt/newinstall/

```

I was able to create all the directories, and install ssh server...

But I guess I need a kernel also so I added dappers sources to my sources.list and ran apt-get update && apt-get install linux-image-2.6.15-27-amd64-server

I have copied the interfaces config from my existing setup to make sure I get the same static IP and not DHCP.

What else should I do before i Modify grub to use the new installation, and reboot the system, I would prefere not to loose contact with the server, since I have very far to get to it.
like I guess I need to add my username and also set a password and set up sudo for it, but how? :-)

Any help higly apreciated.

Regards.
Brian

---

