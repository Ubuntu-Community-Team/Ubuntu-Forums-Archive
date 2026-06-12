---
title: "Can't install updates - &quot;not enough free space on boot/&quot;"
date: 2015-08-24
forum: Installation &amp; Upgrades
---

### Post by Michael_Byars on 2015-08-24
When I try to update using software updater I receive this error message:

"The upgrade needs a total of 86.2 M free space on disk '/boot'. Please free at least an additional 81.9 M of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'."

So I go into terminal and enter: 'sudo apt-get clean" 

Terminal doesn't return anything else back and moves down to a new blank command line "michael@michael-Aspire-4830TG:~"

I then reboot for good measure, run software updater again and it again returns the same not-enough-space error message. 

I checked with the Disk Usage Analyzer application and I'm only using 155/625 gigabytes on my harddrive. 

Is there another way to forcibly make extra space on /boot or have I done-goof'd in some way that is eating up space used by updater?

---

### Post by v3.xx on 2015-08-24
Try
```
sudo apt-get autoremove
```

---

### Post by Michael_Byars on 2015-08-24
I ran 'sudo apt-get autoremove', then ran updater and got a similar message:

The upgrade needs a total of 86.2 M free space on disk '/boot'. Please free at least an additional 70.6 M of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

---

### Post by v3.xx on 2015-08-24
Sounds like its too full for apt-get to work.  You will need to manually remove a few old kernels using "dpkg" or the "rm" command.

Then apt-get will work again.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=%2Fboot+full&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=%2Fboot+full&sa=Search&cof=FORID:9)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=manually+remove+old+kernels&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=manually+remove+old+kernels&sa=Search&cof=FORID:9)

Please first have a read. If you need further help, please post back and glad to help :)

---

