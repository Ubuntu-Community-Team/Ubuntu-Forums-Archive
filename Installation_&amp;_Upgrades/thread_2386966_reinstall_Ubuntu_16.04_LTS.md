---
title: "reinstall Ubuntu 16.04 LTS"
date: 2018-03-12
forum: Installation &amp; Upgrades
---

### Post by jerrylaz on 2018-03-12
I want have been running Ubuntu 16.04 LTS in 4 partitions.
Partition 1  Boot
Partition 2  System
Partition 3  Home
Partition 4  Swap

I have a boot-able DVD.

Question?
How can I reinstall the boot and system partition ****without**** disturbing my Home partition?

---

### Post by monkeybrain20122 on 2018-03-12
What do you need a boot partition for?

When you reinstall, just choose "something else" and use the original root partition as new root (/) and old /home also as /home but without formatting. I don't know what is the use of the /boot partition except being the place where old kernels piled up. I would just delete it and expand the / partition with gparted.

---

### Post by kerry_s on 2018-03-13
+1 to selecting something else

a separate /boot is fine to me. if your running a standard hdd making /boot ext2 can give you a little speed up.

---

### Post by jerrylaz on 2018-03-13
> **monkeybrain20122 said:**
> What do you need a boot partition for?

When you reinstall, just choose "something else" and use the original root partition as new root (/) and old /home also as /home but without formatting. I don't know what is the use of the /boot partition except being the place where old kernels piled up. I would just delete it and expand the / partition with gparted.

That is exactly why I did it that way.  /boot is ext2.

Thanks

So if I understand I just give part 3 /home and do not format it.  When done my data is there.  Am I right?

---

### Post by kerry_s on 2018-03-13
yes, that's right

if your not sure, make a copy/backup first

---

### Post by ajgreeny on 2018-03-13
Do remember, however, that if you choose to install the system using LVM or encryption you will have to have a separate /boot partition, which I believe will be made automatically whilst installing.

Otherwise I agree that using a separate /boot partition is nothing more than an extra and unneeded complication.

---

