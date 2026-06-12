---
title: "Update problem"
date: 2011-11-26
forum: Installation &amp; Upgrades
---

### Post by zenzy on 2011-11-26
I'm running the ubuntu version prior to 9.04, and when I try to update it says
"Failed to extract

Extracting the upgrade failed. There may be a problem with the network or with the server. "

What do I do??? Note: I'm not good with commands or the terminal so make it simple for me.

---

### Post by zenzy on 2011-11-27
Omg answer me!!!!!!!!!!!!!!!!

---

### Post by Old_Grey_Wolf on 2011-11-27
Nothing older than 10.04 is supported.

---

### Post by zenzy on 2011-11-27
Yeah, but how do I upgrade from one of those versions...........

---

### Post by searchfgold6789 on 2011-11-27
OK, by "prior to 9.04" do you mean 8.10?
 - search

---

### Post by zenzy on 2011-11-27
^^^^ Yes 8.10

---

### Post by searchfgold6789 on 2011-11-27
You can't upgrade [easily] from that version (though you can upgrade from 8.04); try this: [https://help.ubuntu.com/community/LucidUpgrades#Upgrading_Using_the_Alternate_CD.2BAC8-DVD](https://help.ubuntu.com/community/LucidUpgrades#Upgrading_Using_the_Alternate_CD.2BAC8-DVD)

---

### Post by zenzy on 2011-11-27
I have to do it completely software I can't use cd's or the such.........

---

### Post by searchfgold6789 on 2011-11-27
Then just follow these steps from your current Ubuntu installation:> [COLOR=White]

[LIST=1]
[*][/color]
[*]
[LIST]
[*]If the ISO file is on the computer to be upgraded, you could avoid wasting a CD by [mounting the ISO as a drive]("https://help.ubuntu.com/community/ManageDiscImages#MountISOFiles") with a command like: 
sudo mount -o loop ~/Desktop/ubuntu-10.04-alternate-i386.iso /media/cdrom0
[/LIST]
 
[*]A dialog will be displayed offering you the opportunity to upgrade using that CD.
[*]Follow the on-screen instructions.
[/LIST]
If the upgrade dialog is not displayed for any reason, you may also run the following command using Alt+F2: 
gksu "sh /cdrom/cdromupgrade"

---

### Post by zenzy on 2011-11-27
It says it's already mounted as the loop........

---

### Post by searchfgold6789 on 2011-11-27
Try unmounting it first.
If not, then do ```
gksudo "sh /cdrom/cdromupgrade"
```

---

### Post by Old_Grey_Wolf on 2011-11-28
To Upgrade from **[COLOR="Red"]8.10[/COLOR]** the OP will need to download alternate iso images for 9.04 and 9.10 from [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/)

Then do the CDROM upgrade procedure described previously using the mounted iso file. 

Once at 9.10 they may be able to upgrade to 10.04.03 using the normal upgrade procedure; however, I've never tried to do that. I always upgrade before the release I have installed becomes unsupported. There is a 10.04.2 in [http://old-releases.ubuntu.com/](http://old-releases.ubuntu.com/) if it doesn't work.

All I can say to the OP is ... Good Luck. It may be time to find a fix for the CD drive in order to do a fresh install of a supported release; such as, 10.04.03 after backing up /home to a USB drive.

---

