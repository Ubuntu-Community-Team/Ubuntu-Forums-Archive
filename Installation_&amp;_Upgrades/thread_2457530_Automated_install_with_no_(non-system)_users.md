---
title: "Automated install with no (non-system) users"
date: 2021-02-04
forum: Installation &amp; Upgrades
---

### Post by newbuntu2020 on 2021-02-04
Is is possible to do an automated install of Ubuntu 20.04 that will create a system which has


[LIST]
[*]- No (non-system) users 
[*]- Login for root via SSH with key auth only 
[*]- A public key in root's ~/.ssh/authorized_keys 
[/LIST]

?

That  the documentation at  [https://ubuntu.com/server/docs/install/autoinstall-reference](https://ubuntu.com/server/docs/install/autoinstall-reference) says the  identity section doesn't have to be present if the user-data section is  present makes me think what I describe above might be possible. But I've  not been able to find any examples of how to do it, or work out what "cloud-init user-data" actually is, so  I've no idea what one might put in the user-data section.

---

### Post by TheFu on 2021-02-04
Yes. I don't know how and it isn't built-in. There are a few threads from other people in these forums about something similar.  Look for "kickstart" in the keyword search.  There may be a way using a PXE boot as well.  IDK.

However, the official ISOs all include the main user who is used during the installer as the sudo user and logins to the root account both local and remote are disabled. Non-OEM versions of Ubuntu use sudo.

Embrace the sudo.

DevOps tools all work fine with this sudo concept and have for over a decade, probably longer than that.

How much effort do you really want to spend creating a custom distro when you can easily setup an install, then clone it for industrial needs and use any of the DevOps tools to change the IP, ssh-keys, and hostname post-install in 15 seconds?

And whenever posting questions, it is always best to clearly state which version of Ubuntu you are targeting. Almost every release changes something about the installer.

Probably 99% of the people posting here are desktop users.  A few run servers, but not at scale where automated installs are mandatory.  May be better to search on cloudy deployment forums for more people in your boat and hope that most don't use cloudy VPS providers that handle that sort of setup already.

Cobbler is an install-streamer tool that people used to perform automatic installations.  I do recall a site in my metro area that used Cobbler and accidentally set the subnet to be reinstalled for a few hundred servers, instead of the 10 they meant.  It didn't turn out well when the unintended server owners found wiped servers with fresh installs.

---

### Post by grahammechanical on 2021-02-04
Canonical provides some information on server automated installs. I have no idea if this is any use.

[https://ubuntu.com/server/docs/install/autoinstall](https://ubuntu.com/server/docs/install/autoinstall)

Regards

---

