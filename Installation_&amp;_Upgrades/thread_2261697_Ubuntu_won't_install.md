---
title: "Ubuntu won't install"
date: 2015-01-20
forum: Installation &amp; Upgrades
---

### Post by alex318 on 2015-01-20
I just build my first computer and it works.  I haven't installed an OS yet and I was going to use Ubuntu.  I put the disk into the optical drive and then select install.  Then it says Ubuntu that has a few circles under it that change from orange to white.  Then when it is done it restarts the computer and goes back to the very first installation screen asking me if I want to install it or not.  I have clicked install more than once and after 30 or so minutes it then just brings me back to the very first installation page.  Why is this?  Do I need to burn it again on a new disk?  How do I fix this problem?  I'm using the msi A78M-E45 motherboard if that helps.

---

### Post by mörgæs on 2015-01-20
Hi,welcome to the fora.
When you reboot do you remember to remove the DVD?

---

### Post by alex318 on 2015-01-20
So I took out the DVD and rebooted it and all it says is "Reboot and select proper Boot device or Insert Boot Media in selected Boot device and press a key."

It said this before I installed Ubuntu too.

---

### Post by ajgreeny on 2015-01-20
Do you never see anything more than the word **ubuntu** plus the animated dots when you are installing?
It should offer you a lot more choice than that to allow you to select the disk or partitions to use, and to set up a user, etc etc.

I suspect that no OS has been installed so far, maybe because the DVD is not a good burn, or the .iso file you used was corrupt; did you check the md5sum [UbuntuHashes - MD5sum]("https://help.ubuntu.com/community/UbuntuHashes") ?

So try using the live desktop first by choosing "Try Ubuntu without installing" and then you can install from that by double clicking on the **Install** icon on the desktop.

---

### Post by alex318 on 2015-01-20
There is no OS installed on this PC yet and I tried "try Ubuntu without installing", but it did the same thing.  I think my only option is to burn another disk.

---

### Post by ajgreeny on 2015-01-20
Yes, that does seem likely.

---

### Post by mörgæs on 2015-01-21
Please take a look in BIOS and post the boot priority list.

---

### Post by Morten_Fjellheim on 2015-01-21
Like the other post says, go back to your bios and put your hardisk as first device to boot from.

---

### Post by ajgreeny on 2015-01-21
> **Morten_Fjellheim said:**
> Like the other post says, go back to your bios and put your hardisk as first device to boot from.
I suppose you my be correct, but normally if the DVD drive is first priority but is empty, the hard disk, usually second priority will boot automatically; I have never had to set my machines the way you are suggesting.

---

