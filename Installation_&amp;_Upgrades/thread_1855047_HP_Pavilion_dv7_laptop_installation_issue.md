---
title: "HP Pavilion dv7 laptop installation issue"
date: 2011-10-05
forum: Installation &amp; Upgrades
---

### Post by plaknas on 2011-10-05
Hi,

I tried installing both the Ubuntu and Kubuntu 10.04 distros and I face the same problem. Everything goes fine and when I have to restart, my BIOS shuts down saying that there was overheating.

I installed with a dual boot alongside windows but I chose not to install the boot loader (I don't like GRUB for some reason) and it installs fine till the restarting part. It gives me a 90D message. Now I am sure this is not a problem with Ubuntu/Kubuntu but any help will be appreciated.

Oh, and if I put my laptop on a cooling pad and run the wubi installer, I get to use it but even with that, I can't shut down properly as it overheats while shutting down. Any suggestions regarding this heating problem will be helpful. I know its my computer problem and I am trying out every possible source for solutions.

---

### Post by Bucky Ball on 2011-10-05
When you boot from the LiveCD you get to the options screen. Hit F6 and you can get some boot options.

When you run 'Try Ubuntu' from the LiveCD do you have this overheating problem? Does it run fine? You should see an icon on the desktop there to install Ubuntu. Try that and see how you go. Some machines have a problem related to load-cycle-count which can be fixed but try that first.

---

### Post by plaknas on 2011-10-05
I am trying that now. I just tried reinstalling with the lappy on a fat book. It did shut off again but no heating issue but it wouldn't show up in the boot menu and when windows loaded, I had to do check disk. That was probably because I didn't install boot loader? Anyway gonna try installing from the live cd, which seems to be working fine.

---

### Post by plaknas on 2011-10-05
I got it working. I was hoping to use the Windows Boot Loader but  I guess I will have to go with GRUB. I mean, are there any problems running Windows 7 on GRUB? If not, I am all good :) A fat textbook under the laptop always helps :P

---

### Post by Bucky Ball on 2011-10-07
Hey, good news. No, no problem running Win with Grub. Makes no diff.

You might want to check out the load-cycle-count issue as I mentioned earlier. Million and one ideas here:

[http://www.google.com.au/#pq=laptop+overheating&hl=en&sugexp=eppshb&cp=25&gs_id=1z&xhr=t&q=laptop+overheating+ubuntu&pf=p&sclient=psy-ab&biw=1366&bih=596&source=hp&pbx=1&oq=laptop+overheating+ubuntu&aq=0&aqi=g2g-v2&aql=f&gs_sm=&gs_upl=&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=ce65c273d1288c46](http://www.google.com.au/#pq=laptop+overheating&hl=en&sugexp=eppshb&cp=25&gs_id=1z&xhr=t&q=laptop+overheating+ubuntu&pf=p&sclient=psy-ab&biw=1366&bih=596&source=hp&pbx=1&oq=laptop+overheating+ubuntu&aq=0&aqi=g2g-v2&aql=f&gs_sm=&gs_upl=&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=ce65c273d1288c46)

Start diggin'. You shouldn't need to put your machine on a text book, phone book, or anything else. Sounds like your drive is overspinning and heating the machine and that is a known prob with some models (HPs I know as I used to have one). They should purr, not steam. Do a bit of digging about smartmontools.

Good luck and enjoy. ;)

---

