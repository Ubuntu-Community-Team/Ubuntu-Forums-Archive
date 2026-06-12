---
title: "Where to put grub ..."
date: 2012-04-29
forum: Installation &amp; Upgrades
---

### Post by Bucky Ball on 2012-04-29
Hi all,

I have Windows XP and 8.04 LTS (don't ask) dual-booting on sda. I want to install 12.04 LTS on sdb BUT I want the existing grub (8.04 LTS) to be running the show after install of 12.04 LTS.

So, I'm figuring I will need to install the 12.04 grub somewhere for it to boot. My questions:

Do I install the 12.04 grub onto the / partition on sdb (for instance sdb6=/)?
Will this allow me to boot with the original 8.04 grub, run 'sudo update-grub' in 8.04 and it will pick up the new 12.04 install and add it to the 8.04 grub menu?

Once I know that 12.04 is working okay I'm wanting to wipe 8.04 and have the 12.04 grub run things. 

I have three Ubuntu installs on my laptop plus Win7 and the original Ubuntu install grub is still in charge. I didn't notice how I did that and don't remember changing anything re grub when I installed the other Ubuntus. Didn't take any notice of where grub was going! Guess what I'm looking for is how to dual-boot Ubuntu with and installs on different hard drives with the first install's grub in charge at the end of it all. 

All advice welcome and tnx in advance ...

---

### Post by darkod on 2012-04-29
I would put grub2 from 12.04 on /dev/sdb (the MBR of sdb). If your grub1 from 8.04 is on /dev/sda, that wouldn't overwrite it. Grub2 is not designed to work on a partition.

Another option is not to install it at all. In 11.10 they removed the option not to install grub2 so you had to install it somewhere. I haven't checked with 12.04 whether you can avoid installing grub2 or you need to install it somewhere.

Note that your 8.04 is probably using grub1 and I am not sure it can detect other OSs with update-grub as grub2 can. Maybe you will need to make a manual entry in /boot/grub/menu.lst. There is no need to chainload grub1 to grub2. You can boot 12.04 from grub1 also.

---

