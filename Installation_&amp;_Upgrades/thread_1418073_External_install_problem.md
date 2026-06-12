---
title: "External install problem"
date: 2010-02-28
forum: Installation &amp; Upgrades
---

### Post by supersound on 2010-02-28
Hi all

After weeks of wrestling with Grub2 problems trying to get a 9.10 install on an external USB drive to work (as it did with 9.04) I have got this far and am now at a loss.

I have my external HDD partitioned 200Gb Fat32, 30Gb ext4 and 1.6 Gb Swap. Grub2 is installed to the external drive; it was brocken at first after install and I had to chroot using the live CD and reinstall. I have now managed to get it pointing to the correct partitions and Ubuntu starts to boot. However, the boot process hangs at the line kernel_thread_helper and wont go any further... 

I suspect this is due to non-standard arrangement of partitions etc but since grub is set up correctly now I cant think what else might be wrong. Any help??
Sorry if this is has been elsewhere but I couldnt find a solution anywhere. Thanks in advance.

---

### Post by supersound on 2010-03-01
Any ideas?

---

### Post by jahst on 2010-03-01
I did this without any problems... so my guess would be it is something wrong with your grub install.

Are you sure it was installed to the external hard drive?
Are you sure you are booting to the external hard drive?

Try removing it, and then booting the PC.. if it still shows grub, then grub is on the PC hard drive too.

So be sure you change your boot order in Bios to boot from external drive, or usually press F12 for boot menu during startup.

Then select external drive from menu.

If you have the time ( and since you first posted 21 hours ago I'm guessing you do ) you might just want to try and reinstall Ubuntu on your external drive.

Be sure in the final step where it gives you the "ready to install" prompt.. after setting up user name etc.. [see image here]("http://www.psychocats.net/ubuntu/images/installingkarmicthumb11.png")

Click the advanced button and change where grub will be installed.
Make sure you pick the external hard drive.

If it still doesnt work, try pressing "e" to edit the grub menu during boot. ( or is it ctl - x in the new grub.. whatever it tells you to edit at boot time.. as this does not permanently change grub so you can experiment with correct settings. 

get rid of the UUID line and change other lines to /dev/sdb1 or whatever you external partition is.

Also, if there is a line in there about floppy something or other.. try getting rid of that as well... sometimes that line has hung me up at boot.


then "b" for boot, or whatever the new button is.

---

### Post by supersound on 2010-03-01
Thanks for the suggestions. Grub is definitely on the external, since the internal boots Vista (without using Grub) if the external is not connected. 
I have tried editing the boot entries but everything seems to be pointing to the right place. This is also about the fifth time I have tried reinstalling, so I doubt that will help now!
The boot process does begin eith the current set up, so that would suggest that it is almost right...

---

