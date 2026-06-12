---
title: "No hard drives in installation"
date: 2010-02-23
forum: Installation &amp; Upgrades
---

### Post by General5580 on 2010-02-23
I was able to mount, browse and manage the hard drive in Ubuntu, but when I went to install, it would not detect the hard drive (it's a Seagate SATA drive).

I opened up gparted and there's my hard drive. So I've deleted it and had an unpartitioned space, opened up the install and no hard drive.

It only detected my two other IDE hard drives, I removed them and it still doesn't detect my SATA drive..

I couldn't find any information on it and the "No hard drives found" search gave me nothing that I was looking for.

Same result on Kubuntu.

---

### Post by darkod on 2010-02-23
This usually happens if the drive was used in raid and has raid settings remains on it. Or from another source.

Boot the live desktop again, in Gparted check the drive name, for example /dev/sda and close Gparted.

Then in terminal run, using your drive name instead of /dev/sda if it was different:

sudo dmraid -E -r /dev/sda
sudo apt-get remove dmraid

Click the Install icon on the live desktop and the installer should see it now.

Note: If the drive is actually used in raid, those commands may break the array. (but you said you wiped it so I guess it's not)

---

### Post by General5580 on 2010-02-23
> **darkod said:**
> This usually happens if the drive was used in raid and has raid settings remains on it. Or from another source.


As soon as I saw that.... Wow...

You're right, I had the drive in a RAID on my other computer, switched computers without deleting the raid, sure enough what you said fixed it..

I was thinking deleting a partition should have removed the raid settings, guess not..

But, thank you! I guess if I searched more I would have found that...

Marked my thread as solved.

---

### Post by darkod on 2010-02-23
> **General5580 said:**
> As soon as I saw that.... Wow...

You're right, I had the drive in a RAID on my other computer, switched computers without deleting the raid, sure enough what you said fixed it..

I was thinking deleting a partition should have removed the raid settings, guess not..

But, thank you! I guess if I searched more I would have found that...

Marked my thread as solved.

Strange enough even formatting doesn't remove it I think. I guess the info stays in the first sector that formatting doesn't touch. Glad you got it going.

---

### Post by Mathboy on 2010-04-20
Thank you so much! I had the same problem, and it was driving me crazy. I must have had that drive in a Linux box with software RAID over a year ago. 

The dmraid commands fixed it for me too. :D

(Note: even creating a clean partition table in fdisk wasn't enough to clear this!)

---

