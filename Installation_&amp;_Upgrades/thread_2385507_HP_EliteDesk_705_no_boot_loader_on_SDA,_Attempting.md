---
title: "HP EliteDesk 705 no boot loader on SDA, Attempting to Boot from Hard Drive"
date: 2018-02-21
forum: Installation &amp; Upgrades
---

### Post by thatsmyboy on 2018-02-21
Used the [boot-repair tool]("https://help.ubuntu.com/community/Boot-Repair") and I'm still experiencing problems with boot. The computer is stuck on "Attempting Boot from Hard Drive". It is an encrypted hard disk installed in EFI mode. As mentioned in the subject, I have an HP EliteDesk 705. Can someone help me get this back up and running?


The relevant pastebin is below
[http://paste.ubuntu.com/p/H3pzXTtrVX/]("http://paste.ubuntu.com/p/H3pzXTtrVX/")

---

### Post by thatsmyboy on 2018-02-22
Looks like I got it back! I first searched for "No boot loader is installed in the MBR of /dev/sda" and found [this link]("https://askubuntu.com/questions/683155/black-screen-on-startup#683168"), which identified an "Error code 32" as the culprit. Then I followed *some* of the instructions on that page, namely > Boot the Ubuntu LiveDVD
Select the option Try Ubuntu

Then mount the encrypted disk, (I did it by double clicking the icon and entering my password)
Then re-run boot-repair ```
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair
```

My [final pastebin is here]("http://paste.ubuntu.com/p/pr3HC4vj5d/").

When I first rebooted, it took me to a terminal with (initramfs), but I just rebooted and tried another line under the grub menu. I'll get together and figure that out when I have time.

---

