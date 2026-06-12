---
title: "Big problems with Ubuntu 18.04"
date: 2018-08-14
forum: Installation &amp; Upgrades
---

### Post by claudeski on 2018-08-14
I usually hesitate to upgrade but I did.
My computer runs like it has 1MB of ram. Firefox takes up to 3 minutes to come up.
Oo takes 1 to 2 minutes. And sometimes freezes.
Thunderbird 30 second to one minute. Sometimes I cannot reply to emails.
Screen constantly freezes from 30 seconds to who knows how long. I have had to turn off the computer a dozen times.
This isn't working at all.
Intel 2.90 Ghzx2
5.7Gib ram
64 bit

---

### Post by kansasnoob on 2018-08-14
What graphics chip do you have?

---

### Post by claudeski on 2018-08-15
> **kansasnoob said:**
> What graphics chip do you have?


My computer says Intel Sandy Bridge Desktop, GNOME 3.28.2

My book says LGA 1155 package
MSI 7680 motherboard

---

### Post by claudeski on 2018-09-04
> **claudeski said:**
> I usually hesitate to upgrade but I did.
My computer runs like it has 1MB of ram. Firefox takes up to 3 minutes to come up.
Oo takes 1 to 2 minutes. And sometimes freezes.
Thunderbird 30 second to one minute. Sometimes I cannot reply to emails.
Screen constantly freezes from 30 seconds to who knows how long. I have had to turn off the computer a dozen times.
This isn't working at all.
Intel 2.90 Ghzx2
5.7Gib ram
64 bit

Am I the only one on the planet having trouble with this? My computer was working fine before I upgraded. And my home network disappeared too!
18.04 is the only boot option I have.

---

### Post by djchandler on 2018-09-05
[SIZE=3]Wild Suggestion:

Turn your old partition into /home mount point. Resize as necessary to make room for / (filesystem) mount point and swap area. 20-35 gigabytes will give you room depending on how many applications are installed. Reinstall 16.04 or 14.04. The box I'm working on wouldn't boot 16.04.05 or 18.04.01 distribution DVDs or thumb drive ISOs due to kernel panic, including lubuntu 18.04 386 (32-bit) distro DVD. You need to know how to use gnome-disk-utility while re-installing. Choose "Do something else" at bottom of Installer dialog suggesting reformatting target hard drive and losing all your data. As SUDO, you can remove all those old folders in the root directory on the /home partition except /home. Personal files should be intact. Make sure you use the same password and user name on the new installation to access your old files, or you'll have change their ownership as SUDO. If encrypted and you forgot the old password, say goodbye to them.

No, you're not the only one having problems. I am having similar issues on an HP with an Intel Core 2 Duo E4600, 2 GB DDR2-800 ram I am fixing for a friend. (Yes, I'm one of THOSE guys!) I'm going back to 14.04 and stopping with upgrade to 16.04. Good until 2021. Bionic upgrade borked that first series of installation and upgrades, and starting over is easier than fixing an unknown problem. I suspect many are getting kernel panics and don't know it because of Plymouth (the purple screen with "Ubuntu" and orange and white moving dots).

It seems that the older your machine, the harder time you're having. I also have a box running 18.04.01 with i7-5775R with 8 GB--upgrade ran fine. But I cannot edit in Gimp at all. That's my killer app. Now add to that., I have an old Tosh laptop with AMD dual core (QL-65, 4 GB ram)) that's running 18.04.01 (AMD-64) with 4.15.x kernrel just fine (use LXDE AND Gnome 3.28 now for desktop, want Budgie) and has been running like that since 10.04. The Toshiba came with Vista originally, same as the HP I'm working on. Who knows?
:confused:[/SIZE]

---

### Post by claudeski on 2018-09-13
djchandler. I am not an expert and I can't say that I understand what you told me to do. I have 3 HDs and I don't know which one has my /home. I try not to put it on the same HD where the OS is. Anyway I put in a video card to replace the onboard video. After a few reboots everything was great! Then a notice of updates. Being the fool that I am, I installed them. Now I am back to my original Problem. Looks like there is a Microsoft programmer trying to sabotage the program. I can't get my work done with this crap! I need help now!
Thanks,
Claude

---

### Post by claudeski on 2018-09-15
Interesting note: I was in GIMP doing a resizing batch on 5 photos. For something that takes 30 seconds it took 5 minutes. After that there was a report problem notice with GIMP and Ubuntu 18......
Then instantly everything is working great! Lesson learned Say NO on updates and don't upgrade the OS for 2 or 3 years.
Done

---

