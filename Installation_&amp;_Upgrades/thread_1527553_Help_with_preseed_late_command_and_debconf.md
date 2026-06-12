---
title: "Help with preseed late_command and debconf"
date: 2010-07-09
forum: Installation &amp; Upgrades
---

### Post by sonic6567 on 2010-07-09
Hello,

I am working on customizing my install via preseed etc.

I am using 9.10  (was going to use 10.04 but 10.04 locks up all the time so back to 9.10)

My problem right now is with a debconf script.

I followed the docs at: [https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization)

I set this up in my preseed:

d-i	preseed/late_command string cp /cdrom/finisher/finisher_g.sh /target/root/; chroot /target chmod +x /root/finisher_g.sh; chroot /target bash /root/finisher_g.sh


and copied exactly the script from:
[https://help.ubuntu.com/community/InstallCDCustomization/AccessDebconfFromYourScript](https://help.ubuntu.com/community/InstallCDCustomization/AccessDebconfFromYourScript)
to use as finisher_g.sh

(as a test before this, I wrote my own finisher_g.sh with just shell commands and it worked fine)

With the debconf script in place it just fails.

I am running in a virtual machine so I don't know how to send an alt-f1 to see if there are any more specific errors.

Can anyone help me with debconf integration in a preseed?

Thanks

Ben

---

