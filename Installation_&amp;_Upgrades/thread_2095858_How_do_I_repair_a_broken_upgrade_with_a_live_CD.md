---
title: "How do I repair a broken upgrade with a live CD?"
date: 2012-12-18
forum: Installation &amp; Upgrades
---

### Post by ambdeep on 2012-12-18
I just upgraded my Ubuntu from 12.04 to 12.10 and I seem to have broken my OS in the process. I ran```
sudo dpkg-reconfigure -phigh -a
``` but it doesnt seem to correct the problem. I have searched all over the internet to find out how to reinstall ubuntu with the live cd but I havent been ablt to find out any solution. Please Help!!

---

### Post by mastablasta on 2012-12-18
just install it and do not reformat the drive while doing it. it should overwrite the borked upgrade with a fresh install.

---

### Post by darkod on 2012-12-18
It depends whether you have important data that you don't want to lose, or not. And where that data is.

If there is no important data, you can simply boot the cd and start the install, then either use the manual partitioning to reuse the existing partitions, or one of the auto methods (it might offer an option to replace the current installation, so you can use that option too, but be advised that it deletes the data inside if I remember correctly).

If there is little important data, you can first boot the cd in live mode and copy it to usb stick or usb hdd. After that do the clean install as above.

If there is a lot of data to copy and a lot of settings you don't want to lose, you can try repairing it first. That command you posted is not the best one for repairing broken upgrades.
And where did you run it from? Can you boot your ubuntu right now or not?

---

