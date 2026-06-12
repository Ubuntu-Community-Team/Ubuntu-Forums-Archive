---
title: "Ubuntu-OpenVPN problem related to yourfreedom"
date: 2011-04-07
forum: Installation &amp; Upgrades
---

### Post by xic816 on 2011-04-07
I'm installing yourfreedom as the instruction tells me to. Now I'm  trying to get it to regognize openVPN but cant manage the last steps: If  you are not a member of a suitable group, make sure you join one. A  good choice would be adm or dialout. Let's assume you are a member of  the dialout group (to become one, open /etc/group as root and add your  name to it, then log out and back in). We need to install the openvpn  binary in a way that all members of the group dialout can run it as  root, but ordinary users can't:

# chgrp dialout openvpn
# chmod u+s,g+rx,o-rx openvpn

Your permissions should now look like this:

# ls -al openvpn

-rwsr-x--- 1 root dialout 371152 Dec 22 19:43 openvpn

Now in order to ensure that the Your Freedom client actually finds the  OpenVPN binary, click on Configure, go to the Proxy panel and configure  the full path of the binary there (in this example, /usr/sbin/openvpn).

That's all you should have to do, OpenVPN mode should now work for you.  But don't forget to tick the OpenVPN box in the Ports panel of the Your  Freedom client!

Tried: groups and got "mss90 adm dialout cdrom plugdev lpadmin admin sambashare"

Does this mean i need to change group if so, how?

And when I tried chgrp dialout openvpn this appeared: chgrp: changing group of `openvpn': Operation not permitted

What to do? Help needed

[http://www.your-freedom.net/index.php?id=173](http://www.your-freedom.net/index.php?id=173)

---

### Post by xic816 on 2011-04-08
> **xic816 said:**
> I'm installing yourfreedom as the instruction tells me to. Now I'm  trying to get it to regognize openVPN but cant manage the last steps: If  you are not a member of a suitable group, make sure you join one. A  good choice would be adm or dialout. Let's assume you are a member of  the dialout group (to become one, open /etc/group as root and add your  name to it, then log out and back in). We need to install the openvpn  binary in a way that all members of the group dialout can run it as  root, but ordinary users can't:

# chgrp dialout openvpn
# chmod u+s,g+rx,o-rx openvpn

Your permissions should now look like this:

# ls -al openvpn

-rwsr-x--- 1 root dialout 371152 Dec 22 19:43 openvpn

Now in order to ensure that the Your Freedom client actually finds the  OpenVPN binary, click on Configure, go to the Proxy panel and configure  the full path of the binary there (in this example, /usr/sbin/openvpn).

That's all you should have to do, OpenVPN mode should now work for you.  But don't forget to tick the OpenVPN box in the Ports panel of the Your  Freedom client!

Tried: groups and got "mss90 adm dialout cdrom plugdev lpadmin admin sambashare"

Does this mean i need to change group if so, how?

And when I tried chgrp dialout openvpn this appeared: chgrp: changing group of `openvpn': Operation not permitted

What to do? Help needed

[http://www.your-freedom.net/index.php?id=173](http://www.your-freedom.net/index.php?id=173)


Managed to solve this myself.

---

