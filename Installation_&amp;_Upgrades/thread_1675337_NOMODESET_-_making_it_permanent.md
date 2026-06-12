---
title: "NOMODESET - making it permanent"
date: 2011-01-25
forum: Installation &amp; Upgrades
---

### Post by smudgy on 2011-01-25
Is there any way of making nomodeset permanent one has to reinstall? :?:


I know at least 1 distro has an etc/sysconfing/kernel file you can edit to make the value NO_KMS_IN_INITRD=yes

then mkinitrd makes nomodeset permanent

Otherwise its a real bind to have to keep burrowing into the grub2 menu each time to make sure it loads..  :>(

---

### Post by drs305 on 2011-01-25
> **smudgy said:**
> Otherwise its a real bind to have to keep burrowing into the grub2 menu each time to make sure it loads..  :>(

Have you added **nomodeset** to the kernel options in /etc/default/grub ?
> 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **nomodeset**"


It's still a 'per session' setting but you only have to set it once and then run update-grub to make it take effect on each boot.

---

### Post by smudgy on 2011-01-25
> **drs305 said:**
> Have you added **nomodeset** to the kernel options in /etc/default/grub ?


It's still a 'per session' setting but you only have to set it once and then run update-grub to make it take effect on each boot.

Thanks drs it worked a treat (educational also). Added parameters for nomodeset xdriver=radeon etc

Now all I have to figure out is how to use traditional ifup instead of Network Manager... Until then I can't use suspend/hibernate without rebooting Ubuntu ...  I know from openSUSE that using traditional ifup works and all I have to do there is ifdown then ifup with a couple of launchers and then my internet is back. But in Ubuntu its not obvious how to do the same thing (suse have a yast tool with the same name as network tools but with functionality to effect change to traditional ifup and dismantle Network Managers grip on the network.


Any ideas welcome   ;)

(Then if I get there the icing on the cake would be to know how to add  similar hooks to the suspend and resume scripts to execute sudo  /sbin/ifdown eth0 and the reverse for resume).
.

---

### Post by wildmanne39 on 2013-04-01
Thread closed. Please do not post in old threads.

---

