---
title: "mate 24.04 installer bug"
date: 2024-07-10
forum: Installation &amp; Upgrades
---

### Post by zanetto on 2024-07-10
ubuntu mate 24.04 installer can't create partitions

---

### Post by Rubi1200 on 2024-07-10
Your post contains barely any information. We have no idea what you tried, how many partitions you want to create, how large the HD or SSD is etc. etc.

Personally, I always recommend using GParted on the live USB to first create all the relevant partitions and then when starting the installer choose the Manual Partitioning option.

Then just mark the relevant partitions for what you need, root home etc.

Please provide some more information so we can offer the best advice.

---

### Post by zanetto on 2024-07-10
When I launch ubuntu mate 24.04 installer and set partitions scheme, the installer crashes

---

### Post by Rubi1200 on 2024-07-10
Please post any crash logs or error reports.

Before installing, post the output of this command:
```
sudo fdisk -l
```

Would also be good to know some system specs. like how much RAM and graphics card.

---

### Post by guiverc on 2024-07-10
> **zanetto said:**
> When I launch ubuntu mate 24.04 installer and set partitions scheme, the installer crashes

Did you verify ISO after download and before write?  If there was even a single bit incorrect during this process; you're just wasting your time trying to use it, so I consider this cheap insurance.  I've written about it on this [answer on another site]("https://askubuntu.com/questions/993407/is-verifying-isos-downloaded-from-the-official-website-worthwhile").

In your case I'd also ensure the ISO write was perfect, as this is where I've experienced the most problems.

Next, given your ISO will attempt background validation during your boot, did you verify it completed? as it is something I'd do in your case; especially as you're experiencing something you don't expect.   I've written about it [here ]("https://askubuntu.com/questions/1311183/do-i-need-to-check-the-integrity-of-a-ubuntu-install/1311209#1311209")as if doesn't show a valid ISO media check completed; you should be not attempting to use the installer at all, as it could be corrupted & cannot be trusted.

The installer has some logs available if you look, though if the *crash* means the window closed, you'll need to use a terminal, or file-browser to go and seek those out. Myself, I'd start at the basics, which is media validation first; as if that didn't verify successfully then you cannot trust anything after that as you cannot tell what is accurate or corrupted results due to problems in the prior step(s).

Inability to create partitions can be for many reasons, including your partition table is full (*you don't specify any specifics; but a legacy/MBR partition table only allows four primary partitions so cannot create a fifth, if you have another OS installed that is hibernated (windows fastboot is a hibernated system) parts of your disk will be in an unclean state so the system may not want to touch those etc*), to an unclean file-system or partition table problems.

---

