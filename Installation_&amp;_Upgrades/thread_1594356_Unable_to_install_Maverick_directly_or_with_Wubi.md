---
title: "Unable to install Maverick directly or with Wubi"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by Brian88 on 2010-10-12
I have a Compaq Evo N1020v notebook computer which I wanted to install Ubuntu Maverick on it.

I tried to install using both the live-CD and the alternate installer, but those methods drop me to the grub rescue prompt and messed up my XP's MBR.

Installing using Wubi gave me no luck, too. At first boot after installing, it says that it 'cannot read file' and 'you need to load kernel first'.

Is there any solution to install Maverick on my system?

Thank you very much.

-- EDIT: It is now solved. Somehow my system was incompatible with GRUB2, so I installed an ancient version of Ubuntu (8.04 I think), then upgrading it step by step to Maverick (8.04-9.04-9.10-10.04-10.10). Yes, it took time, but the reason I really need Maverick is because the driver for my WiFi card has built in on Maverick (and I don't have to use the buggy, processor-consuming Ndiswrapper).

---

