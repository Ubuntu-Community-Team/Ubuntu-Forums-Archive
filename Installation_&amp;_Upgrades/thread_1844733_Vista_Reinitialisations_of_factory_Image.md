---
title: "Vista Reinitialisations of factory Image"
date: 2011-09-15
forum: Installation &amp; Upgrades
---

### Post by tallpaull7723 on 2011-09-15
Hi All Novice/ Newbee here!

I have a Dell Studio 1535 with a duel boot of Windows Vista and Ubuntu 10.04,
I want to reinstall the dell factory Image so I can start again in the Vista side of thing. I have save what I want to keep on BOTH OS.
I have had a look around and read many posts on here and on windows forums, and they all seam to say the same thing of "press f8" or "press f11" or "press ctrl + f11" during the boot up sequence and you will be able to enter the advance boot menu to be able to select the  Repair Your Computer option to then be able select the Dell Factory Image Restore. 
Yet my laptop one doesn't have the "f8" option and non of the others above bring up the advance options. can some one tell me how to get to the menu please?


Also i have gone in to the "window recovery partition" and gone through and found and program icon which give me the  option to "reinstall the dell factory image" and when I select the the tick to confirm that this process will wipe everything and install the factory image. and I click next it start the process and then stops and come up with and "error" with no explanation what the error is and then freezes! 

Any help offers much needed!!! thanks:mad:

---

### Post by haqking on 2011-09-15
> **tallpaull7723 said:**
> Hi All Novice/ Newbee here!

I have a Dell Studio 1535 with a duel boot of Windows Vista and Ubuntu 10.04,
I want to reinstall the dell factory Image so I can start again in the Vista side of thing. I have save what I want to keep on BOTH OS.
I have had a look around and read many posts on here and on windows forums, and they all seam to say the same thing of "press f8" or "press f11" or "press ctrl + f11" during the boot up sequence and you will be able to enter the advance boot menu to be able to select the  Repair Your Computer option to then be able select the Dell Factory Image Restore. 
Yet my laptop one doesn't have the "f8" option and non of the others above bring up the advance options. can some one tell me how to get to the menu please?


Also i have gone in to the "window recovery partition" and gone through and found and program icon which give me the  option to "reinstall the dell factory image" and when I select the the tick to confirm that this process will wipe everything and install the factory image. and I click next it start the process and then stops and come up with and "error" with no explanation what the error is and then freezes! 

Any help offers much needed!!! thanks:mad:

Are you sure you havent removed the hidden partition where the restore is ?

And did you create or can you create the restore disks from the windows menu ?

here for factory restore [http://supportapj.dell.com/support/topics/global.aspx/support/kcs/document?c=ap&l=en&s=gen&docid=DSN_336966&isLegacy=true](http://supportapj.dell.com/support/topics/global.aspx/support/kcs/document?c=ap&l=en&s=gen&docid=DSN_336966&isLegacy=true)

and here for restore from disc [http://supportapj.dell.com/support/topics/global.aspx/support/kcs/document?c=ap&l=en&s=gen&docid=DSN_339949&isLegacy=true](http://supportapj.dell.com/support/topics/global.aspx/support/kcs/document?c=ap&l=en&s=gen&docid=DSN_339949&isLegacy=true)

If this doesnt help you might be better off in a Windows Forum

---

### Post by tallpaull7723 on 2011-09-15
hi there no i have not removed the as I can still access from the my computer in windows. and no i did not/ have not created a restore disc.

---

### Post by haqking on 2011-09-15
> **tallpaull7723 said:**
> hi there no i have not removed the as I can still access from the my computer in windows. and no i did not/ have not created a restore disc.


So create a restore disc set then if you can, usually a menu option on progams menu.

Also see here [http://supportapj.dell.com/support/topics/global.aspx/support/kcs/document?c=ap&l=en&s=gen&docid=DSN_370461&isLegacy=true](http://supportapj.dell.com/support/topics/global.aspx/support/kcs/document?c=ap&l=en&s=gen&docid=DSN_370461&isLegacy=true)

---

### Post by tallpaull7723 on 2011-09-16
had a good look around but couldn’t find anything to do with making the discs, so I tried the "f8" approach for once last time and low and behold it worked!!! how ever after installing the factory image, the grub was all messed up but I was able to sort this out due to another problem I had hat to sort out several months ago.. Now the problem is the boot load is unable to find the windows OS, saying it no longer is where it says it is. any ideas anyone please??:(

---

### Post by haqking on 2011-09-16
> **tallpaull7723 said:**
> had a good look around but couldn’t find anything to do with making the discs, so I tried the "f8" approach for once last time and low and behold it worked!!! how ever after installing the factory image, the grub was all messed up but I was able to sort this out due to another problem I had hat to sort out several months ago.. Now the problem is the boot load is unable to find the windows OS, saying it no longer is where it says it is. any ideas anyone please??:(


I am confused ? you did a factory restore ?

if you did there should be no grub menu and no Linux anywhere.

if you have done something since the factory restore like you say you have then that is probably why it cant find windows anymore, and you need to edit the boot.ini file for windows.

A factory restore puts it back to how you bought it, which wont include Ubuntu.

So i suggest to ease pain in editing the boot.ini etc that you do a factory restore again so it works.

Were you expecting to do a factory restore and have Vista and Ubuntu on there working fine ?

I am confused

---

### Post by tallpaull7723 on 2011-09-16
Hi i did the factory restore and was expecting to just find vista!!! and NO Ubuntu!!

When it restarted! but in stead i was meet with black screen and whit txt with grub error! so i booted off ubuntu live cd! and in the terminal 1) sudo fdisc -l,  2) sudo mkdir /media/sda5, 3) sudo mount /dev/sda5 /media/sda5, 4) sudo grub-install --root-directory=/media/sda5 /dev/sda

Then close it all down and restarted and was able to load Ubuntu fine but on a restart I chose to load windows vista and was meet with "error unable to find drive" and "error drive not there" or words to that effect! tried several time and have been unable to load vista and keep getting the same errors :(

---

