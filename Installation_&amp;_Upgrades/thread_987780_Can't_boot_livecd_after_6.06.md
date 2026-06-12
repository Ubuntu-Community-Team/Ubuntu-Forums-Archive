---
title: "Can't boot livecd after 6.06"
date: 2008-11-19
forum: Installation &amp; Upgrades
---

### Post by The_Dark_Lord on 2008-11-19
I have previously been using these disks and the OS fine on an older windows computer but i have another 2 year old computer that will not boot from your official live CD disks properly. These disk work fine in my older computer.
In my new computer it boots up the disks to the main screen "start, install, CD check" etc but when i select start Ubuntu with out changes it goes to the blinking command prompt screen with the blinking line in the top left right before the Ubuntu logo screen with the with the start up progress and just sits there doing nothing.
i have tried the official CD's (all working on my other computer) 8.04, 7.10, 7.04
and 6.10, 7.04 dvd's from my local Disksmith shop with out success.
I have tried copying them to a dvdrw but still no luck. Would a dvdr be better?
BUT i can boot both the official 6.06 32bit and 64bit cds (can't try earlier ones as i don't have any)
Haven't tried installing yet as that not my intention yet but won't to get livecd working
BIOS settings are all correct

Any help appreciated

Windows Xp sp2
LG HL-DT-ST DVDRam GSA-H10N dvd burner
St380811AS SATA2 Harddrive (looks like a Seagate)
512DDR2 ram
INtel Pentium D 3.40GHZ dual Core CPU
Integrated Graphics in a ATX PM8PM motherboard
RealTeK network card
and looks like 2 generic Card Reader and Dial-up Modem

---

### Post by The_Dark_Lord on 2008-11-19
.....

---

### Post by The_Dark_Lord on 2008-11-25
can anyone help me?

---

### Post by The_Dark_Lord on 2008-12-18
No Help?

---

### Post by The_Dark_Lord on 2008-12-18
...

---

### Post by overdrank on 2008-12-18
Hi and it may have something to do with the S3 graphics. Have you tried any of the options under the F4 key. 
You may also try and use the F6 key and edit the kernel line to remove the quiet splash to see any errors. 
Sorry for the 4 week wait but I did not see this post as when you bump the thread it does not show on the unanswered post. :)

---

### Post by The_Dark_Lord on 2008-12-18
Its Ok
F4 Key, if i remember that has the safe graphics option yer i tried it with no success but ill try it again and ill try to also remove quite splash in a few minutes

---

### Post by The_Dark_Lord on 2008-12-18
I just removed "quite splash --" from the end of the kernel line in normal mode and it booted straight into the live cd, i didn't get any errors in the desktop of the few minutes I tried it. I tried it with 8.10 and 8.04 and both worked and both i had problems with.
So it seems i just need to remove quite splash -- in future to get it going

---

### Post by Partyboi2 on 2008-12-18
Good to see you got it working. If you decide to install ubuntu after playing around with it and find that you run into the same problem after the installation is complete, you will need to remove the splash screen using a slightly different method then you used with the ubuntu live cd. You will need to follow [[COLOR=Blue]this[/COLOR]]("https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation"), which will be temp. Then you will need to make the changes permanent by following [[COLOR=Blue]this [/COLOR]]("https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Permanently%20On%20An%20Existing%20Installation")

---

### Post by The_Dark_Lord on 2008-12-20
Thanks for the help and links.
I already run ubuntu on this box so i all ready no i like it :P
Do you have any idea why that is causing a problem on my other system?

---

