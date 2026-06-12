---
title: "Ubuntu dual boot, 10.04 and 11.04. Uninstall only the 11.04 release."
date: 2011-04-16
forum: Installation &amp; Upgrades
---

### Post by half-newbie on 2011-04-16
Hello,

I have been using ubuntu 10.04.2, and I have recently installed ubuntu 11.04 beta next to it. The new release doesn't work well for me (my old laptop becomes slow on this release) and i would like to uninstall it. How can i do that?

If it helps, this is the picture of what gparted shows. The large partition has the release that i want to keep.
[http://www2.picturepush.com/photo/a/5464870/1024/Anonymous/Screenshot--dev-sda---GParted.png](http://www2.picturepush.com/photo/a/5464870/1024/Anonymous/Screenshot--dev-sda---GParted.png)

Thanks a lot.

---

### Post by admkbc on 2011-04-16
Why do you have 2 swap? Only one is good. 
Which version have GRUB?

---

### Post by half-newbie on 2011-04-16
Thanks for the quick reply.
Well, i have no idea why i have 2 swap. I installed 10.04 by choosing the "use the entire disk" option. And i installed 11.04 by choosing the "install side by side" (or something like that) option. So, as you can see, it was all done automatically, I didn't not configure the partitions manually. I don't know where the grub is installed.

---

### Post by Dutch70 on 2011-04-16
The best way I know to tell you to make sure grub2 is installed to 10.04 is to boot up the live cd/usb, and run the following commands.
```
sudo mount /dev/sda1 /mnt
```
and...
```
sudo grub-install --root-directory=/mnt /dev/sda
```
Those are specific to your set up. The link is here.
[[COLOR="Red"]Reinstalling Grub2 from LiveCD[/COLOR]]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

Then login to 10.04 and run...
```
sudo update-grub
```

The easiest way that I see to get your space back from 11.04 is to delete the entire extended partition, recreate ONE swap partition & extend /dev/sda1.

Edit: Actually, you may be able to delete sda6 & sda7, shrink sda2 down to nothing but your swap prtn. & extend sda1.

---

### Post by half-newbie on 2011-04-16
Thank you, i will try that now, and i will return to tell you my progress.

---

### Post by half-newbie on 2011-04-16
I installed grub from the live cd following your instuctions. Then i logged in to 10.04 and updated the grub. I restarted my system to check if anything is different. Now, the 10.04 version is first in the multi boot list so i guess that means that grub is now installed in the partition i want. Doesn't it?

Then i tried to delete the whole unnecessary partition, but it only let me delete the /dev/sda6 and /dev/sda7. The others i cannot delete, it shows a small picture of a key next to it. Does that mean that i have to have root privileges? What can i do to delete the whole /dev/sda2?

Thanks in advance

Edit: It wont even let me resize it. I can do anything with the whole /dev/sda2 partition.

---

### Post by Dutch70 on 2011-04-16
Yes, you have grub installed to 10.04 now. 

The key next to it means that it's mounted. You can't work on it while it's mounted. You can try to right click it & select swapoff, but I think it would be best to do everything else from the live cd/usb.

---

### Post by half-newbie on 2011-04-16
I deleted the whole partition from the live cd after i selected swapoff. It worked with no problems there.

Then after restarting, i saw that the partition that i have just deleted was still in the multi-boot menu, so i figured that this will be solved if i updated the grub from the terminal, and it did.

It worked perfectly, my system is as it was before i install the 11.04 release.

Dutch70, thank you very much, you 've been amazingly helpfull. Take care. I'll mark this as solved

---

### Post by Dutch70 on 2011-04-16
Great! glad to hear it. 

I would suggest that you consider creating a separate partition for /home one of these days though.

---

### Post by half-newbie on 2011-04-16
I will search this forum and the ubuntu help to find out how can i do that without loss of data. I guess i will find something. If not, i will post another thread asking about it.

But what is the benefit of having separate /home?

---

### Post by Dutch70 on 2011-04-16
Double Post

---

### Post by Dutch70 on 2011-04-16
/home is similar to documents & settings in windows. The most important benefit is you can reinstall (as opposed to upgrading) without losing your data or your settings. Also, if you have a problem you can't seem to fix, a reinstall would be no biggie at all really.

Personally I couldn't imagine not having a separate /home. Although I didn't realize how great it was until I went to upgrade from 8.04. The upgrade failed miserably, so I had to reinstall. I was very surprised to see that I still had my wallpaper first of all, and then all of my other settings too. Of course I had to reinstall some apps, but when I did, the settings for those were already there also. :)

[[COLOR="RoyalBlue"]http://www.psychocats.net/ubuntu/separatehome[/COLOR]]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by half-newbie on 2011-04-16
That 's what i will do then!
The tutorial you linked is very detailed, i think it will be very easy to follow! Thanks again, your help was great! :)

---

### Post by Dutch70 on 2011-04-16
> **half-newbie said:**
> That 's what i will do then!
The tutorial you linked is very detailed, i think it will be very easy to follow! Thanks again, your help was great! :)

Your welcome.

Yes, psychocats is a great site. If you need any help with it, just start a new thread. 
Feel free to send me a PM if you want & I'll have a look at it.

---

### Post by half-newbie on 2011-04-16
> **Dutch70 said:**
> 
Feel free to send me a PM if you want & I'll have a look at it.

I appreciate it! I will keep it in mind :)

---

