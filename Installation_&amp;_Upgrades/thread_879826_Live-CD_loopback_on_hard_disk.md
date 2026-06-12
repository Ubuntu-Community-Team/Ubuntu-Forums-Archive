---
title: "Live-CD loopback on hard disk"
date: 2008-08-04
forum: Installation &amp; Upgrades
---

### Post by nizam7 on 2008-08-04
Hi guys,

  I am a newbie with Ubuntu and am trying out the live cd to familiarise myself. I do have a bit of experience with linux earlier but am not a pro. I have been trying to persist the settings of the LiveCD on my hard disk using the link 
 
[https://help.ubuntu.com/community/LiveCD/Persistence?action=show&redirect=LiveCDPersistence]("https://help.ubuntu.com/community/LiveCD/Persistence?action=show&redirect=LiveCDPersistence")

but to no avail. my hard disk is at \media\disk and I am able to create the casper-rw file but when i try to boot with the persistent option I cant see any of my changes. I have also created a user but even that is not saved. I can also see a dev-save file on my primary HDD.

I am using Hardy Heron, what could be going wrong. I have tried the persistent argument at the end of the options (hit the F6 key) when booting and also in the middle just after casper but no joy with that. Should it be casper-rw at all

---

### Post by snowpine on 2008-08-04
Hi Nizam, if you read that document closer, it is a guide for 6.06 Dapper Drake, and it "doesn't work" with Hardy Heron. :(

---

### Post by nizam7 on 2008-08-04
thanks snowpine, I know that but isnt it supposed to work with  new versions as well. I would have thought that would be rudimentary but anyway can you point me to the right document or instructions as to how I can go about doing this.

 Appreciate your help

regards

---

### Post by nizam7 on 2008-08-05
I have now got 7.10 Gutsy Gibbon and booted with the liveCD. I tried out add user and changed a few things after logging on as that user. I then re created the casper-rw file and rebooted with the persistent option (splash -- persistent) in the end but no luck again. That web page says that persistance works with Gutsy Gibbon so why does it not work for me. What am I doing wrong

Thanks in advance

---

### Post by snowpine on 2008-08-05
I am sorry I don't have advice about the persistence feature, because I have never used it (and didn't know it existed until I read your thread), but why don't you just take the plunge and do a full 8.04 installation to your hard drive? It will be much faster than running the Live CD, and if you carefully set up a dual boot, you can keep Windows (or whatever is already running on that machine). Just a suggestion, because I worry you're wasting time playing around with old versions trying to get a feature to work that you won't even need once you install. :)

ps I'd suggest putting "live cd persistence" in the title of your thread if you want an expert on that feature to find your thread and give you advice.

---

### Post by nizam7 on 2008-08-05
Thanks snowpine, I cant do a full install coz its a machine at work that I am playing about with. I thought this was something trivial considering what Ubuntu is capable of. I was actually much impressed when I first booted of the live cd. I had never seen a Linux distro take so much strain off you and do effortless updates making life much easier.

---

### Post by snowpine on 2008-08-05
Yes, Ubuntu rocks! :)
I found a technical description of the bug, looks like there may be a fix: [https://bugs.launchpad.net/ubuntu/+source/casper/+bug/219192](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/219192)
Another option for you (assuming the computer can boot from USB) is to install it to a USB pen drive: [http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/](http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/)

I definitely understand not wanting to mess with your work computer!

---

### Post by nizam7 on 2008-08-10
Hi Snowpine,

Have been a bit busy this week due to office commitments but have seen the bug fix you pointed me to. I have extracted the contents of Hardy Heron into a folder and replaced the casper\initrd.gz with the updated one having the fix for persistence. I have tried to create an ISO using this folder but somehow it is not bootable. I have also tried to burn the iso to the disk but no luck there as well. I am sure I am burning the contents  of the folder and not the ISO on the CD. Also I can see the folders in the  drive. 

I would appreciate any help and guidance

---

### Post by nizam7 on 2008-08-11
Am I missing anything to make the ISO bootable...?? I thought that copying just the Ubuntu folders and files present on the root would be okay.

---

### Post by snowpine on 2008-08-11
> **nizam7 said:**
> Hi Snowpine,

Have been a bit busy this week due to office commitments but have seen the bug fix you pointed me to. I have extracted the contents of Hardy Heron into a folder and replaced the casper\initrd.gz with the updated one having the fix for persistence. I have tried to create an ISO using this folder but somehow it is not bootable. I have also tried to burn the iso to the disk but no luck there as well. I am sure I am burning the contents  of the folder and not the ISO on the CD. Also I can see the folders in the  drive. 

I would appreciate any help and guidance

Sorry, but I have never used the persistence feature before... I don't have any more tips for you. :(

---

### Post by nizam7 on 2008-08-12
Hi Snowpine,

   Thanks for your interest, actually I am not asking about the persistence. This is now about being able to modify a file present in the Ubuntu 8.0.4.1 ISO image and burning that back to an ISO (re creating a new ISO) or to a CD-ROM. I just cant seem to get a bootable ISO or CD ROM. Any ideas

Thanks again

---

