---
title: "Cloning new Ubuntu Server Boot LUN still boots to old LUN?"
date: 2019-03-18
forum: Installation &amp; Upgrades
---

### Post by n1nj4888 on 2019-03-18
Hi There,

I have installed Ubuntu Server 18.04 LTS to an iSCSI Target/LUN on a Synology NAS... All works well so far and I can boot (using iPXE) to the Ubuntu Server 18.04 LTS LUN (lets call it IQN_OLD)...

However, if I clone the iSCSI Target / LUN to a new IQN (let's call it IQN_NEW) on the Synology and add an iPXE menu item to boot the new IQN_NEW, I still end up getting connected to the IQN_OLD...

I suspect this is because /etc/initiatorname.iscsi is set to IQN_OLD - Do I Just have to update this single file to IQN_NEW or are there additional steps to follow after cloning an ISCSI LUN to get Ubuntu Server to boot off the new ISCSI LUN?

[EDIT] - I know that the IPXE config is correct since the IQN_NEW LUN is booted (showing as "connected" in the Synology GUI) and shows the Ubunt Grub menu... It's only when I select "Ubuntu" to boot Ubuntu that the Synology GUI shows that the connection switches from IQN_NEW to IQN_OLD and the old LUN is booted...

Thanks!

---

