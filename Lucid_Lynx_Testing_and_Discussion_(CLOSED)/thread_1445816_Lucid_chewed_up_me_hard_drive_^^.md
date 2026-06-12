---
title: "Lucid chewed up me hard drive ^^"
date: 2010-04-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Naiki Muliaina on 2010-04-03
Im not finished yet, but i got told in the Ubuntu SL group that its happened to other people with no solution yet found, so just putting up my current findings. Heres how it went and what i have found. 

I have 4 hard drives in my PC, that one i tried an upgrade on was a 1TB Sata (hence why i am reluctant to bin it ^^). This hard drive is my sda and i normally boot of it.

I tried an upgrade from a full working Karmic install. About 20 minutes into the installing software bit my PC seemed to hang for a couple of minutes then restarted. It wouldnt boot though, it got to checking my hard hard drive but wouldnt load grub.

I chucked in a Karmic CD and booted into the live environment. I tried to intall as normal, but it hung at the '5% formatting hard drive' part. I gave it a couple of goes and the same each time.

I booted up into Jaunty and had the same so flicked open GParted. 908gb of the 1TB drive show as unknown. The swap file is however still there along with some empty space. I tried formatting the hard drive with Gparted and it hung when it tried.

Not sure why i did this, but i installed Karmic onto my 3rd drive, a little 360 gig sata. Install went fine. My bios says im still booting from my sda 1TB drive, and its able to boot up perfectly fine into Grub, and i can boot into sdb, sdc and sdd.

I tried the Gparted disk on its own, again it hung when it tried formatting the drive.

I wonderd if it was a gparted thing. I was sure Suse used something else, so i grabbed a copy of 11.1 Suse of a magazine, did an install onto sda. It seemed to work, format and all. Awesome win! I was able to boot into Suse and use it, with a big sigh of relief i reached for the Karmic cd to get Ubuntu back on sda.

It hung at 5% formatting....

I checked gparted and it had gone back to being 908gb unknown with swap showing and some empty space. I also tried Fedora 12, same, it hangs when formatting the drive.

Tonight im going to use boot and nuke (last time i used that it took 2-3 days to clear a 360gig drive....) So i guess wish me luck, if anyone has any suggestions before tonight please god tell me ^^ If not ill tell you how it goes in a few days ^^

Ooo and just to add, i did a clean install of lucid onto the 360gig drive this morning, works ok and no hard drive problems :)

---

### Post by VMC on 2010-04-03
This probably has nothing to do with it, but what is your make and model # of you 1TB hard drive, and is it one of the newer 4096 byte sectors? 

the new "green" models have that 4096 sector issues. There is a work around though.

---

### Post by Naiki Muliaina on 2010-04-03
Ooos interestin! TY!

I believe its a Samsung EcoGreen 1TB. Well.... I know its a 1TB... 




Ahah! Found receipt for it!

1 x 1Tb Samsung EcoGreen F2 SATA-2 Hard Drive HD103SI @ 52.82GBP from Aria.co.uk

Gots any links to the literature on the bugs fer these things? :)

---

### Post by VMC on 2010-04-03
> **Naiki Muliaina said:**
> Ooos interestin! TY!

I believe its a Samsung EcoGreen 1TB. Well.... I know its a 1TB... 




Ahah! Found receipt for it!

1 x 1Tb Samsung EcoGreen F2 SATA-2 Hard Drive HD103SI @ 52.82GBP from Aria.co.uk

Gots any links to the literature on the bugs fer these things? :)

Interesting, it shows "Bytes per Sector - 512".

I was referring to [this]("http://ubuntuforums.org/showthread.php?t=1407098&highlight=4096") topic on 4096 bytes per sector.

---

### Post by techunit on 2010-04-03
A lot of people have trouble with upgrading there systems over the internet. I always try to stick with a LTS release for a year and then do clean installs for upgrades. The infrastructure used for the update procedure can be iffy. I don't recommend it. Um there is some circuitry on the HD that could have been fried when the system rebooted unexpectedly but reboots during the installation are normal. What may have happened is that by stopping the process you corrupted the drive. 1tb harddisks are also kind of iffy because they have different standards than smaller  brands. If you must replace the Drive I recommend a Barracuda Harddrive.

---

