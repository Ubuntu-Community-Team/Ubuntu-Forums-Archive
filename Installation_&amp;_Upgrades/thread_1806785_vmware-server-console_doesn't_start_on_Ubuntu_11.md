---
title: "vmware-server-console doesn't start on Ubuntu 11"
date: 2011-07-18
forum: Installation &amp; Upgrades
---

### Post by agad on 2011-07-18
After upgrading Ubuntu to version 11, vmware-server-console stopped working - only gray window opens. After killing the process error message appears:
/usr/lib/vmware-server-console/bin/vmware-server-console: symbol lookup error: /usr/lib/i386-linux-gnu/libgio-2.0.so.0: undefined symbol: g_cclosure_marshal_VOID__VARIANT

Is there the way to make the program working?
Thanks in advance for any help.

---

### Post by ponzonio on 2011-07-28
Hello!

I have exactly the same problem with versions of vmware-server-console previous to 1.0.10. 

However, with version 1.0.10 the console starts and respond normaly until i try to connect to a server or check for updates. It seems that something is wrong with the network :(

If i discover something more, i will post.

Good luck!

---

### Post by agad on 2011-07-29
I installed VMware Server Console 1.0.10 build-203137 but the bef\havior is the same: gray window opens and after a closing the window by the cross I get the message:
/usr/lib/vmware-server-console/bin/vmware-server-console: symbol lookup error: /usr/lib/i386-linux-gnu/libgio-2.0.so.0: undefined symbol: g_cclosure_marshal_VOID__VARIANT

---

### Post by ponzonio on 2011-08-15
Hello again!

Well, this is a very strange problem. As you can see in the bug report below, the behavior of the vmware console depends on the appearance theme that is selected:

[https://bugs.launchpad.net/ubuntu/+bug/660458](https://bugs.launchpad.net/ubuntu/+bug/660458)

---

### Post by agad on 2011-08-26
Thank you. After changing the appearance wmware-server-console works fine.

---

