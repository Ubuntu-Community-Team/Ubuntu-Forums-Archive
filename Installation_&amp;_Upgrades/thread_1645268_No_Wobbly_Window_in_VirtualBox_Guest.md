---
title: "No Wobbly Window in VirtualBox Guest"
date: 2010-12-14
forum: Installation &amp; Upgrades
---

### Post by mathgeek2000 on 2010-12-14
I'm having trouble with my Ubuntu VM's --
   -- I'm running a Win 7 Home Premium Host, (8GB RAM, 1TB HDD, NVidia GeForce Video)
   -- Oracle VirtualBox (Current version)

-- When I set up Linux VM's w/ 3D Acceleration, and 128MB Video Ram, 
  -- I can't enable the 'Extra' Video Effects, to get Compiz working.
  -- Even when VBox Guest Additions is installed.

VBox Guest Additions does let me use Full Screen, & Seamless mode, correctly though.
But if I try to set 'Extra' Video Effects, it can't find the correct driver.
   ```
ps -A | grep compiz
```
Does not show compiz running.

FYI: Nor can I get Unity on 11.04 Alpha 1, under the VM.

Any all help appreciated.

---

### Post by dino99 on 2010-12-14
do you know that 128 MB is quite nothing ?

---

### Post by mathgeek2000 on 2010-12-14
> **dino99 said:**
> do you know that 128 MB is quite nothing ?

perhaps today -- But it is the maximum amount I can set the VM Machine to recognize:
  -- FYI: The settings are: 2GB RAM, -- similar to my laptop,
                128 MB Video Ram w/ 3D on. -> The Maximum, as I said.

---

