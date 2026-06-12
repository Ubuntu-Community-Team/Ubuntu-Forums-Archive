---
title: "SSH not working after upgrade 8.04"
date: 2008-06-14
forum: Installation &amp; Upgrades
---

### Post by pfwd.tech on 2008-06-14
Hi I have recent upgraded my Hardy version using the upgrade manager. I'm sure that I saw some open-ssh upgrades in the list.
The problem is after upgrading I can no long ssh into servers.
I'm getting the following errors:
```
/etc/ssh/ssh_config: line 52: Bad configuration option: PermitRootLogin
/etc/ssh/ssh_config: terminating, 1 bad configuration options
```I have tried changing the PermitRootLogin value from no to yes and the same error occurs.
Any one have any ideas?

---

### Post by pfwd.tech on 2008-06-14
I have now managed to access a server via ssh however i don't think my machine is as secure as it was.
I removed the permitRootLogin from the ssh_config file
Can someone tell me if by removing this my system is less secure?

---

### Post by wormser on 2008-06-14
You are more secure with eliminating root logins.  Did you just comment (#) out the line, completely remove it or give the option no?  Here is some good [documentation]("https://help.ubuntu.com/community/AdvancedOpenSSH") on it.

---

### Post by pfwd.tech on 2008-06-14
Hi,
I removed it from the ssh_config file.
I've put it back in now due to security.

Whilst searching for a solution on the net I've found some forum posts surgesting that the PermitRootLogin should not be set in the ssh_config file but in the sshd_config file instead.
is this correct?

I've checked my sshd_config and the setting PermitRootLogin is there and set to yes

---

### Post by wormser on 2008-06-14
Follow that guide in my other post.  It will make ssh more secure.

---

