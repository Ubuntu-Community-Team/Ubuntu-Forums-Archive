---
title: "Cant install Ubuntu"
date: 2010-03-10
forum: Installation &amp; Upgrades
---

### Post by koyigo on 2010-03-10
Hi friends! I try installing Ubuntu 9.10 in my computer On reaching the prepare disk section it shows me that there is no operating system installed yet i have XP installed. it is also not showing the partitions in my computer yet i have 4 partitions. Please  help because i cant do without ubuntu in my machine.

---

### Post by Fafler on 2010-03-10
Does it find the harddrive at all? You should tell us a bit more about the computer youre trying to install Ubuntu on, manufacturer and model name of motherboard and what not.

---

### Post by koyigo on 2010-03-10
am so happy av found the solution: (though i cant remember the whole of if) nway  I downloaded the TestDisk application, run it and saw 3 partitions which were not supposed to be in my drives, there is one partition; besides Linux swap and linux extended, by the name (ext'd LAB/D/cant rem it very well) just noted it. came back to terminal run partprobe, and delete the above noted partition(ext'd LAB...) save the changes and try to continue installing your ubuntu. the partition table is alive and kicking.




am proud to be a UMUNTU

---

