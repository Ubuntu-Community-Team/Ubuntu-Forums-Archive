---
title: "Having Trouble with the Install....New To Linux"
date: 2008-03-09
forum: Installation &amp; Upgrades
---

### Post by Josiah87 on 2008-03-09
Hello All, I have the Ubuntu 7.10 CD I ordered from Ubuntu,

I have the AMD64+ Bit

I had a freind help me install Ubuntu the first time, and now he is not available to help me this time.

I am trying to clean my hard drive of my last install...I insert the CD and select 

Start/Install Linux...or whatever that says...its the first option. I do that and it looks like it's inatlling with the yelllow bar going left and right, then it boots to a window that is asking for a username and password...I try everything and I just can't get passed it, after 30secs it boots to the desktop for 2secs and goes back to the login screen...and repeates...

any suggestions?

did I do a clean install how do I know if I did?

---

### Post by Pumalite on 2008-03-09
It looks like a bad burn. Do md5sum on your iso, burn a new CD at 4x or less. Use CD-R

---

### Post by Josiah87 on 2008-03-10
well the only problem with that is, I ordered the CD From Ubuntu. And Ihave tried 2 different CD's.

is there a way for me to know if I have wiped the hard drive clean? I can't figure it out in LInux.

---

### Post by Pumalite on 2008-03-10
sudo fdisk -lu
Or try Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot frrom it.

---

