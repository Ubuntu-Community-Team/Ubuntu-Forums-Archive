---
title: "Using XP's Boot Manager"
date: 2008-10-29
forum: Installation &amp; Upgrades
---

### Post by RMOP on 2008-10-29
I'd like to use XP's BM on one of my systems, but have two questions. I found a link telling how to do it using SUSE, but cant quite figure out the name of the Ubuntu file corresponding to bootsek.lin referenced in the SUSE instructions.

1) What Ubuntu file should I place on the "C:" drive in order for XP's BM to be able to boot Ubuntu?

[http://en.opensuse.org/SDB:Booting_Linux_with_the_Windows_NT/2000/XP_Boot_Manager](http://en.opensuse.org/SDB:Booting_Linux_with_the_Windows_NT/2000/XP_Boot_Manager)

2) Is GRUB essential for booting Ubuntu? It seems silly to have one BM point to another, but perhaps that's the best XP's BM can manage<g>. I have GRUB on another system which replaced the XP BM and both XP and Ubuntu boot fine from GRUB.

Yes, I have REASONS for wanting to do it this way, but they're entirely mundane and uninteresting...

Many thanks.

---

### Post by caljohnsmith on 2008-10-29
That method in the tutorial should work just fine, assuming that Ubuntu and XP are on the same HDD. Just make sure you install Grub to the boot sector of your Ubuntu partition, and then the dd command will copy that boot sector to the "bootsek.lin" file in that tutorial. Then place the bootsek.lin in your C:\ root directory, modify your boot.ini as they instruct, and you should be good to go. And you can call the "bootsek.lin" anything you want, as long as you use the same name in the boot.ini file. Good luck and let me know how it goes.

---

### Post by Partyboi2 on 2008-10-29
deleted

---

