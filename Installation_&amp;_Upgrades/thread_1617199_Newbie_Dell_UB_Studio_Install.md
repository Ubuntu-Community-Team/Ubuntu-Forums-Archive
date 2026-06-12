---
title: "Newbie Dell UB Studio Install"
date: 2010-11-09
forum: Installation &amp; Upgrades
---

### Post by bonnetteanthony on 2010-11-09
Audio pro, pretty excited about UB Studio possibilities, attempting install 10.10 on xtra pc(Dell Studio 1737 w/Win7), but having some problems. 
 
CD/DVD drive not working well, so I opted to try usb install w/Unetbootin
I was able to boot from usb drive and proceed through the following menu steps:
 
Language
Country
Keyboard
Keyboard Origin
Keyboard Layout
Config Network w/Dhcp
*Network Authentication Failed*
Config Network Manually
Enter IP
Enter Netmask
Enter Name Server
Host Name
Domain Name
Choose Mirror (Selected us.)
*Download Release Files* (100%)
*Bad Archive Mirror*
 
My primitive mind leads me to believe that I have a network problem, but my connection is fine in win7. Again, I am totally ignorant, and would really appreciate any suggestions.

---

### Post by mörgæs on 2010-11-09
Hi, welcome to the forum.

For diagnosing network problems (remember to have wired access): If you try a live boot without installing, can you surf the web?

For installing: If the network connection works, have you tried selecting different mirrors?

---

### Post by bonnetteanthony on 2010-11-09
Thanks. Ill give it a go with wired access.

---

### Post by bonnetteanthony on 2010-11-10
Okay. Wired up and breezed through the install menu. 
However during "Select and Install Software" I got "Install step failed" on Grub legacy 2. 
Skipped that step, went to "Install LILO", also failed. 
Finished install. 
ReBoot. 
"Loading Linux...................................................BIOS Data check success. Gave up waiting for root device. Alert /dev/sdc5 does not exist dropping to a shell. 

I was so close. Any more suggestions?

---

