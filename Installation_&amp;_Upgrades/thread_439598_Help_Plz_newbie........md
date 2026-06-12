---
title: "Help Plz newbie......."
date: 2007-05-10
forum: Installation &amp; Upgrades
---

### Post by nabz on 2007-05-10
[FONT="Century Gothic"][/FONT] Hi i've just download Ubuntu using both Wubi and the live cd i tried using Wubi first as I dont know how to partion.... As I have a sony viao which is already partioned and dont wanna mess anything up could somebody please tell me how to install Ubuntu with out partioning.... Thanks for your help

---

### Post by starcraft.man on 2007-05-10
> **nabz said:**
> [FONT="Century Gothic"][/FONT] Hi i've just download Ubuntu using both Wubi and the live cd i tried using Wubi first as I dont know how to partion.... As I have a sony viao which is already partioned and dont wanna mess anything up could somebody please tell me how to install Ubuntu with out partioning.... Thanks for your help


Ummm, you can't install Ubuntu without partitioning, unless you install on thin air :p

Seriously though, partitioning isn't that hard and I recommend doing it manually in the cases that people want a dualboot. I've heard a few stories where the automatic partitioner made things a bit screwy...

Its not so difficult, can ya please tell me the size of your drive and the partitions ya have on it? 

The generic layout though that I give people is the following:

Root partition:
Mount to: /
Format: Ext3
Type: Primary
Size: 6-8 GB

Swap:
Mount to: doesn't mount
Format: swap-file
Type: logical
Size: 1-2 GB

Home (this is the directory your local files will be stored, like my documents)
Mount to: /home
Format: Ext3
Type: Logical
Size: X (its as much as you want, if you wish to store a lot of files make it bigger, if you don't want to store a lot of media and use Ubuntu just to try or for small files just stick with the root and swap partition and don't make a home partition.)

You don't have to be worried though, just opening the live partitioner/alternate partitioner doesn't actually write any changes to the disk, you have to push next to get it to write changes. [Here]("http://www.psychocats.net/ubuntu/index.php") is a good place to see step by step installation to get this set up.

Don't be afraid to take chances, life is too short to always play it safe :p

---

### Post by nabz on 2007-05-10
Thanks for the quick reply.....:) :) :)  I have a 100gb hard drive it's allready split in two the C-drive is 46gb with 12 gb free and the D-drive is 38gb with 22gb free... this was partion came with the laptop:confused: :confused:  i have 2gb ram and keep most my stuff on the Cdrive both drives are NTFS.... what would you recomend... sorry for my laziness

---

### Post by starcraft.man on 2007-05-10
> **nabz said:**
> Thanks for the quick reply.....:) :) :)  I have a 100gb hard drive it's allready split in two the C-drive is 46gb with 12 gb free and the D-drive is 38gb with 22gb free... this was partion came with the laptop:confused: :confused:  i have 2gb ram and keep most my stuff on the Cdrive both drives are NTFS.... what would you recomend... sorry for my laziness

Ah, I see... hmm, well that adds up to only around 80 GB but ok. First I would back up your data on your D drive, I assume you put your data there. If you only have 16 GB data I'd burn em to DVDs, as well as anything else on C you need. Its always good to be prepared and things can always go wrong. 

So, your going to boot into the live cd and get to the partitioner after answering the questions. I'm going to assume you want to continue to use your D drive for data (ubuntu supports NTFS drivers you can install later (they are called ntfs-3g, that comes after install). Then, select your D drive and right click, you should have option to resize it. Make it 8 GB less than it already is. Then your going to apply that and let the partitioner resize.

When its done your going to select the free space and make a 6 GB root partition like I listed above. Make sure its primary, and make sure its set to bootable, as well as all the other notes I made above. Then make a 2 GB partition for the swap-file.

Then write those changes to drive. And when you go next (I forget, I'm not sure this is perfect but I think you get the mount screen) you should see all your partitions and where they are mounted. Make sure root is mounted to /, your swap is to swap and your two partitions should be mounted to media/hda or sda#

That should be good. Hope that was helpful, and please read through [this]("http://www.psychocats.net/ubuntu/installing") to make sure ya know what to expect :) It will show ya exactly what each screen looks like and what to do :)

Good luck.

---

### Post by nabz on 2007-05-11
Thanks again.. sorry to keep asking question that are properly answered some where else but do you know why Sony partition the hard drive is there any important information there… can I access my files from windows in Ubuntu… and can I just partition my D-drive into two.. Oh yeah when I first bought the laptop I had to make some recovery disk..:) :) :)

---

