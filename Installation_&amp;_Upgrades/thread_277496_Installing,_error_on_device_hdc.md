---
title: "Installing, error on device hdc"
date: 2006-10-14
forum: Installation &amp; Upgrades
---

### Post by daniel_a on 2006-10-14
I am installing Ubuntu 6.06 off of a cd I burned with an iso obtained from ubuntu's main site. The computer will boot and run the cd, I choose 'run/install ubuntu' on the main menu, it starts and then shows 'uncompressing linux... ok, booting to kernal' on the terminal, then it says:
 '[17179853.536000]buffer i/o error on device hdc, logical block 316930
[17179858.540000]hdc: drive not ready for command'. 
It keeps writing these two lines over and over but with different numbers. I have checked the md5sum on the cd and know that the cd isn't corrupted, any ideas? maybe a hardware issue?
p4 1.7 ghz, 512 mb, samsung cdrw/dvd sm-308b, 38 gb maxtor 6L040L2

---

### Post by Kateikyoushi on 2006-10-14
I would recommend to check the S.M.A.R.T. of that hard drive, I saw this on a drive with bad sectors.

You can do this with the free version of the program "Everest" in windows.

---

### Post by daniel_a on 2006-10-14
I installed everest and looked under storage then smart. The hard drive was selected at the top and the status on all the items was either 'value is normal' or 'always passing', so it doesn't look like the error is because of bad sectors.

---

### Post by Mark Stosberg on 2006-10-22
I ran into this today, too. For contrast, I tried booting a Damn Small Linux LiveCD, and that worked fine. I'm using a Dell L433c. I suspect something hardware related. 

I suggest reviewing [this thread]("http://ubuntuforums.org/showthread.php?t=254468"), which discusses the exact same issue and offers further solutions. 

  Mark

---

