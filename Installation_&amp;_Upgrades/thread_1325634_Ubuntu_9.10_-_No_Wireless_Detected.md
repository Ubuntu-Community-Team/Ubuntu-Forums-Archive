---
title: "Ubuntu 9.10 - No Wireless Detected"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by Dreamer8001 on 2009-11-13
[FONT=Times New Roman][SIZE=3]Hello Everyone,[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]I just download Ubuntu 9.10 and did a fresh install on my hp dv6-1030us. After the installation is completed Ubuntu doesn’t automatically recognize or detect my wireless card. I didn’t seem to have this problem when installing version 9.04. [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [COLOR=white].[/COLOR][/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Does anyone know to fix this problem? Or is it best for me to reinstall and use Ubuntu 9.04 instead.[/SIZE][/FONT]

---

### Post by earthpigg on 2009-11-13
my advice, honestly? unless there is a 'must-have' feature for you in 9.10, stick with what works. 9.04 is a solid release and will be supported for another year.

---

### Post by earthpigg on 2009-11-13
i just came across a nice post on this subject written by someone else [in another thread]("http://ubuntuforums.org/showpost.php?p=8310721&postcount=6"):

> As of now Hardy is very stable. It was not so stable for the first 6 months or so but neither was any other distro. Upgrading every 6 months on each new release is a good way to have a permenently unstable system. Upgrading 6 months after each release is a good way to have a permanently stable system.

I still use hardy as my main os and will do so until six months or so after the next LTS release when I will upgrade to that. I also have jaunty and karmic and suse and mandriva and debian which I use for testing and for learning all the new stuff.

---

### Post by GWallraff on 2009-11-18
Hey, do not know if you've fixed this yet but for future reference, you can do this:

[Wallraff] # sudo apt-get update
[Wallraff] # sudo apt-get install bcmwl-kernel-source

Then, just reboot. Ubuntu then you should find the NIC :D

---

### Post by Ubulindy on 2009-11-19
9.10 detected my wireless, it showed in the restricted drivers window, however I wasnt able to enable it. It even showed in the network manager, and now it doesnt show in either. Ive tried everything to no avail. I give up til they fix this, and I guess I'll be wired for now. A few bugs here and there, but overall Ive got to say everything works great, and 9.10 is quite fast. Had to tweak some settings here and there, but oh well. Also, I still had to install flash, right after the fresh install in order for videos to play. I dont know why that isnt default, out of the box.

UPDATE: I got my wireless working by simply uninstalling everything I had installed pertaining to Broadcom in synaptic. The fwcutter, b43 driver, ect. Then I rebooted, went to system>admin>hardware drivers ( again )... did the search, and it found the driver for b43 automatically. I was then finally able to enable it. Worked like a charm, been using wireless ever since! Woo hooo!  \o/

---

### Post by stanwang on 2009-12-04
> **GWallraff said:**
> Hey, do not know if you've fixed this yet but for future reference, you can do this:

[Wallraff] # sudo apt-get update
[Wallraff] # sudo apt-get install bcmwl-kernel-source

Then, just reboot. Ubuntu then you should find the NIC :D

==== :popcorn: Excellent post GWallraff keep the good work ====

---

### Post by Darkz_Soul on 2009-12-07
I have a kinda similar problem when install ubuntu 9.10 from the live disk it sees my wireles but after the instal it cannot... I have a broadcom 4328 that works since it was working before i was forced to reinstall ubuntu... To clarify i don't see the broadcom drivers in the restricted drivers... so if there is a way to update the driver list to add my restricted hardware let me know soon... Thanks in advance

---

### Post by Ubulindy on 2009-12-07
> **Darkz_Soul said:**
> I have a kinda similar problem when install ubuntu 9.10 from the live disk it sees my wireles but after the instal it cannot... I have a broadcom 4328 that works since it was working before i was forced to reinstall ubuntu... To clarify i don't see the broadcom drivers in the restricted drivers... so if there is a way to update the driver list to add my restricted hardware let me know soon... Thanks in advance
  Go into synaptic, in the search type in b43, broadcom,and fwcutter... see if it is installed. If not, install it, then go into menu>admin>hardware drivers...... it will search, and then alls you do is enable it. If all that is already installed, uninstall them, then re-boot. Then go straight to hardware drivers, and let it search again. It should work. Good luck

---

