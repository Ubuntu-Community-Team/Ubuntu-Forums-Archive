---
title: "Upgrading Hoary Hedgehog to Oneiric Ocelot"
date: 2011-12-05
forum: Installation &amp; Upgrades
---

### Post by kio_http on 2011-12-05
Hi, I have a Kubuntu Hoary system on an old computer (very surprising and long story to explain). Will upgrading it to each release cycle in between work smoothly. There is a lot of stuff on this computer and upgrading from Hoary is a major change also as its Kubuntu there is a huge difference in KDE 3 and 4.

---

### Post by 2F4U on 2011-12-05
It may work, but I would really doubt it. Anyways, whether you do a fresh install or attempt an upgrade, you would have to make a backup of your data. There are uncountable posts about people loosing their data during an upgrade and if you value your data, make a backup before you do anything.

---

### Post by Lars Noodén on 2011-12-05
I would be inclined to recommend a clean installation, especially if you have a separate [font=Courier New]/home[/font] directory.  As usual, back everything up first.

---

### Post by snowpine on 2011-12-05
Upgrading Ubuntu is very well-documented. I recommend you read the following page carefully and write back if you have any specific questions:

[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

Personally I would do a fresh install of the new release, side-by-side with the old in a "dual boot" configuration. Then I could gradually move files/documents/settings over to the new environment, with dual-boot to the old install as a "safety net."

---

### Post by kio_http on 2011-12-05
> **2F4U said:**
> It may work, but I would really doubt it. Anyways, whether you do a fresh install or attempt an upgrade, you would have to make a backup of your data. There are uncountable posts about people loosing their data during an upgrade and if you value your data, make a backup before you do anything.

I think I'll back up and try the upgrade.

---

### Post by mörgæs on 2011-12-05
Apart from the risk: Have you thought of how long it takes compared to a fresh install?

---

### Post by Old_Grey_Wolf on 2011-12-05
I have my doubts that it would be successful.

If you upgrade from Hoary Hedgehog to Oneiric Ocelot you will not get all of the changes. For example, it will not upgrade you to the ext4 file system nor will it upgrade you to Grub 2. 

Also, upgrading using the old-releases repositories is not a simple process.

You will spend I lot of time downloading updated packages from the repositories, and installing the updates. It would be a lot faster to make a backup of you /home, just in case you run into problems. Then, you could install the new release, or dual boot with Hoary Hedgehog and the new release; then, copy over what you want to keep to the new release from the /home of Hoary Hedgehog. Downloading the newer release from one of the torrent mirrors, that can be found on the Ubuntu website, would make it even faster.

---

### Post by Old_Grey_Wolf on 2011-12-05
> **snowpine said:**
> 
personally i would do a fresh install of the new release, side-by-side with the old in a "dual boot" configuration. Then i could gradually move files/documents/settings over to the new environment, with dual-boot to the old install as a "safety net."

+1

---

### Post by kio_http on 2011-12-06
I've got time and I can to other things while it upgrades.

I currently upgraded to Karmic 9.10. The switch fro KDE 3 to 4 is over! Except for a few hiccups everything worked out.

---

