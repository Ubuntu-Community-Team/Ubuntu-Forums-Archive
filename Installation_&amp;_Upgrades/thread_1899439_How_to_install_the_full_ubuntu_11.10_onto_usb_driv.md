---
title: "How to install the full ubuntu 11.10 onto usb drive"
date: 2011-12-23
forum: Installation &amp; Upgrades
---

### Post by yackar on 2011-12-23
to have all the features, i like to install the whole OS onto it.
requirements-2 usb drives (one must have enough memory to hold liveusb, the other must be 8 gb or more)
liveusb creation tool
ubuntu 11.10 iso

make the liveusb drive ready with liveusb software
boot into it
select install ubuntu from the sidepanel
when it asks how you want to install it, choose the one that allows you to choose your own settings(i already forgot)
choose the selection that represents your usb's partition
select the change button
click format and select one of the exts from the upper dropdown
select / from the lower dropdown
click apply or whatever button it is
let it partition it and do whatever
then select the same partition from the dropdown to install grub to
click install
have fun!
i tried it myself that's how i know.

---

### Post by Hipster Doofus on 2011-12-23
Let us know [yackar]("http://ubuntuforums.org/member.php?u=1516008") how you go after all updates are done.

I tried using an 8gb stick after the references to it said the OS on the hard drive would not be touched.

After the updates I unplugged the usb & I lost my windows mbr. Could not get it back. So that little experiment didn't last long at all.

---

### Post by oldfred on 2011-12-23
If you originally installed grub2's boot loader to sda and then fixed it, it will remember to install to sda on updates. You need to be sure it knows to install to the same drive as you want it to.

#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

---

### Post by yackar on 2011-12-24
it worked for me, i had recently formatted my whole hard drive and put win 8 DP on it, which removed any possible thing to do with linux so i guess that you must do it on a computer that hasn't had or has been formatted and reloaded with windows ubuntu. so this is to be done on computers that don't have anything to do with linux, i guess. probly when i did it it worked because i did'nt install ubuntu to hdd first. i had ubuntu on that computer before i loaded it with win 8 developer preview. i love open source OS's. especially when they're hidden ways to download the whole os to a usb.

i'm typing this using the ubuntu i installed to the usb drive on a completely different computer. epic! it includes grub and everything!

if that isn't the reason i have no explaination to what the *** happened to uyour computer
                                                                                          /^\
                                                                     I censored he-doublel

---

### Post by yackar on 2011-12-24
and since your windows is gone, maybe you can try 8 dev preview as a temp recovery from the bottom of the tank. it works great and (if you have to run old apps) it's got 16 bit app support like the DOS emul in win XP. :guitar:<-- it's rockin' awesome!

did you know that i signed up for this just to post this? well that's how good it worked

---

### Post by Hipster Doofus on 2011-12-24
Yea this was a clean install of ubuntu. Only windows loaded. Don't know why it happened but it did. I was aiming for the same thing you are doing. It made a 30mb partition on one of my drives & killed windows mbr at the same time. Maybe the usb drive was getting full? Who knows.

Anyway windows is back up & running.

---

