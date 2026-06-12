---
title: "How do you DOWNGRADE from 12.10 t0 12.04 ?"
date: 2014-07-14
forum: Installation &amp; Upgrades
---

### Post by jhd3 on 2014-07-14
My 12.10 is no longer supported and I would like to go back to 12.04 . Is there a procedure to downgrade from 12.10 to 12.04
that will not wipe out my wireless network , my printer setup , and the few UBUNTU software installs , like VLC Media Player ,
that I've installed ? I don't remember ever updating from the auto-update list and I don't care if I lose them in the downgrade.
My worry is primarily with the drivers for my Apple wireless router and my HP wireless printer, the VLC Media Player , Thunderbird 
email , Firefox bookmarks, and files I have on my desktop display .

I would like to avoid the erase 12.10 and install 12.04 scenario because this would involve a lot re-setup work .
Any help will be greatly appreciated .

Thanks .

BTW ,, Be specific as you can in your instructions ,,,  I'm not exactly a computer guru . And I'm 75+ years to boot !

---

### Post by Bashing-om on 2014-07-14
jhd3; Hello, My Welcome to the forum.

I hate to be the bearer of bad news, but, here it is:
There is no way to downgrade a release. Your only options are to clean fresh install release 12.04 OR upgrade to release 14.04. On-line upgrade is not to be considered, in my opinion, as you will have to jump through several hoops: Back up your data ( This upgrade is risky at best ),Turn off all 3rd party software sources, disable your screensaver, revert the install to as close to default as possible, and-
The release upgrade path
12.10 is End_Of_Life and the software repository no longer exist -> sources will have to be redirected;
13.04  is End_Of_Life and the software repository no longer exist -> sources will have to be redirected;
13.10 current but support ends in a few days now
Finally you arrive at 14.04 after consuming a lot of time and bandwidth, maybe IF there were no problems in those intermediate steps.

If you choose to online up-grade:
  [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)
is the guide to assist you.

In my experience, will be much faster and cleaner just to fresh install a flavor of 'buntu and be done with it ( soon as all the aps and bugs are worked out) .. 14.04 has come a long way in driver support and has many enhancements. In my old box 14.04 ubuntu is solid as a rock.

Your time, your effort, your call

[INDENT][INDENT][INDENT]we are here to assist
[/INDENT][/INDENT][/INDENT]

---

### Post by coffeecat on 2014-07-14
Bashing-om is right - you can't downgrade, and I agree that you would be far better off installing 14.04 fresh rather than going through the risky 12.10 -> 13.04 -> 13.10 -> 14.04 upgrade path.

However, before you do that, check whether update manager is offering you a direct upgrade to 14.04. I believe that was a possibility.

If you do need a re-install, a few suggestions:

> **jhd3 said:**
> 
My worry is primarily with the drivers for my Apple wireless router and my HP wireless printer, the VLC Media Player , Thunderbird 
email , Firefox bookmarks, and files I have on my desktop display .

Apple wireless router - that shouldn't need any drivers in Ubuntu. Do you mean drivers for your computer wireless device?

HP wireless printer. There are some, but you'd be unlucky to find a HP printer that does not work out of the box with the latest Ubuntu. If you didn't have to install a driver for this in 12.10, you won't have to in 14.04.

VLC - just install it from the Software Centre in 14.04.

Thunderbird email. Copy the whole of the hidden .thunderbird folder together with contents in your home folder onto backup media. When you have installed 14.04, before you open Thunderbird, simply copy the backed up .thunderbird folder + contents into your home folder. You'll find all your emails and settings when you open thunderbird.

Firefox bookmarks - Bookmarks -> show all bookmarks -> Import and Backup -> Backup. Save the .json file in your backup media. When you have installed 14.04, Firefox ->  Bookmarks -> show all bookmarks -> Import and Backup -> Restore from your .json file.

---

### Post by sammiev on 2014-07-14
Running 14.04 on more than a few laptops now and all has been great. Worked on all right out of the box. 12.10 is EOL now so best to move on.

---

### Post by jhd3 on 2014-07-14
Ok!

---

