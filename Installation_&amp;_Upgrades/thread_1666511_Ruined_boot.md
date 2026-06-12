---
title: "Ruined boot"
date: 2011-01-13
forum: Installation &amp; Upgrades
---

### Post by Icel on 2011-01-13
I installed ubuntu netbook editiopn of my dell inspirion 15r laptop alongside windows 7 home premium.

Everything went fine. After restart I loaded windows to check that its all okay there. Before loading it had a disk check preform on the drive, and I let it run.

Windows loaded fine, I restarted. Then I get a "No modules found. Press any key to restart". And nothing.

Can't get windows, can't get Linux, can't get boot from the installation CD even to run Live CD- I press f12 for booting options, select CD drive, but still get the "No modules found. Press any key to restart" message.

What do I do now?

=====

Edit:


Okay, so you know who "nothing good happens after 2 am"?
Yes, also my ability to work computers sucks at night.
All I did now was change the boot sequence to CD >> HDD, instead of using the "select boot" options on the loading screen. And now it works!

Know I need to re-enable GRUB and then find out which Win7 Dell program has written to my MBR the last time...

=====

Now the LiveCD doesn't work again... Arr!!!
I got to the "Try Ubuntu" screen and it got stuck (Clock icon for 20 minutes with no CD or HDD action), so I rebooted the machine. But now it won't Boot from the CD again...

---

