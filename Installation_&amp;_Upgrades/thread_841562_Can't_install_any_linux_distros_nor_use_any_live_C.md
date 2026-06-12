---
title: "Can't install any linux distros nor use any live CDs"
date: 2008-06-26
forum: Installation &amp; Upgrades
---

### Post by Fzang on 2008-06-26
Yup, they simply won't load more than about 10% because of something called "ACPI" I believe...

If I turn ACPI off the wireless internet won't work, if I leave it on the whole distro won't boot

Is there some way to bypass it and boot WITH wireless?

The funny thing is, that linux actually used to work without having to mess with any settings

I've been able to install ubuntu gutsy without running into any problems (half of my hardware didn't work though... bad idea)

So what do I do? I want linux, but without internet it's useless

---

### Post by Midwest-Linux on 2008-06-26
The first thing we need to know what kind of machine you have laptop ,desktop? How old is it name and model number? Hard drive size, RAM, Speed, Pentium I II III IIII? Dual core? Then we can start to figure things out for you.

---

### Post by Fzang on 2008-06-26
Laptop
Model:........Acer Aspire 5050
Graphics:...ATI Radeon Xpress 1100, 256 MB
CPU:..........AMD Turion x64 mobile technology
Network:....Atheros Wireless, AR5006EG chipset
Touchpad:...Synaptics touchpad (had some trouble with this, so might as well list it)

[http://www.superwarehouse.com/Acer_Aspire_5050-4570_Notebook/LX.AXD0X.024/ps/1503717](http://www.superwarehouse.com/Acer_Aspire_5050-4570_Notebook/LX.AXD0X.024/ps/1503717)
^
For all specs, but these aren't the important ones

---

### Post by Midwest-Linux on 2008-06-26
Your laptop has Vista premium and 1 GB of RAM. Which is way more enough RAM to run a Live CD.

I found a thread that might be helpful to you.

[http://ubuntuforums.org/showthread.php?t=532567&page=2](http://ubuntuforums.org/showthread.php?t=532567&page=2)

 Possible problems. 

Check the CD that you are using to see if there are any errors.

Burn the CD at the lowest possible speed. Use high quality media.

 If you want to try a installation, shrink the Vista partition. Install Ubuntu on the freed partition. This might work better than trying to run a Live CD. If you decide on a installation, I would suggest using the alternate install CD. Again check the checksum figure and use the lowest burn speed when burning the ISO.

 Try Wubi and see if that makes it better. With Wubi, you can install Ubuntu and if you decide that you don't want ti. Then you can delete it with no partition issues or errors.

However, some say Wubi and Vista does not get along. I had this experience myself. So I went with the option of using the Vista shrink partition program to free space and installing Ubuntu using the alternate install CD on the freed space.

---

### Post by Fzang on 2008-06-26
I want to add something:

Computer runs windows XP because it's much faster than vista

I have a 70 GB free partition in case linux decides to get along with my computer


I know the problem is the ACPI... would it help by running the battery dry and perhaps take it out for 15-20 mins?


Another thing, they talk about up/downgrading the BIOS... would that be advised? Is it risky? How do I check current version of BIOS?

---

### Post by Fzang on 2008-06-26
Bump... I wantz leenoox!

---

### Post by Fzang on 2008-06-27
Bump

---

### Post by Fzang on 2008-06-28
Oh come on :(

No one?

---

### Post by Partyboi2 on 2008-06-28
You can check bios details from windows. See [[COLOR=Blue]here[/COLOR]]("http://pcsupport.about.com/od/tipstricks/ht/biosversysinfo.htm")
If you are going to flash the bios make sure that you are always connected to AC power during the whole process.

---

