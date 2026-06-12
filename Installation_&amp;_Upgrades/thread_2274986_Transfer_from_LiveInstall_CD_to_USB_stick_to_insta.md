---
title: "Transfer from Live/Install CD to USB stick to install on notebook"
date: 2015-04-23
forum: Installation &amp; Upgrades
---

### Post by oceola2 on 2015-04-23
Have a Notebook computer without a cd player. Have a 16GB Kingston data traveler formated to ext4 with 14GB free space.
Also have the 14.04.01 Liveinstall CD.
Is there a way to transfer the information from the CD to the USB and have it boot.
Do I need to copy the files from the CD onto the USB and move some files or do I need to make further changes to the USB.
Tried a simple copy and boot but just got a blinking screen.

Thanks.

---

### Post by dino99 on 2015-04-23
the blinking screen is probably due to a graphic issue (14.04 & 14.10 are badly known about that).
so if you can easily download a mini iso, then it might be the better solution (vivid just comes out today)

---

### Post by oceola2 on 2015-04-23
@dino99 - Thanks for the input I solved it. Apparently just copying the LiveCD to the USB won't do.
I used Start Up DiskCreator and used the Ubuntu Live/install CD as source and sent it to the USB.
Couple of things threw me due to impatience, one was I couldn't figure out what the extra files slider was for and once the creation process seemed to be finished it started to create something called a persistence file which acted like it was stuck in an endless loop. Figured something was stuck and closed the panel and removed the stick. I tried to boot into the notebook with it but it gave me an intramfs error.  Started the process over again but stayed stayed patient while it completed.
Once it was done the install went flawlessly as it usually does with Ubuntu and now it's just a matter of updating.
I have a small folder type repository of the updates (1.7GB) so I should be able to catch up fairly quickly.
Thanks again.

---

