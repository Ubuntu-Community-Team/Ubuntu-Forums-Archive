---
title: "Terminated with status 127"
date: 2010-07-03
forum: Installation &amp; Upgrades
---

### Post by ulao on 2010-07-03
So I installed gadmin-samba and during install it wanted to basically replace the entire system. I would never have though it needed so many dependencies reinstalled. So after it did this it wanted X to be restarted and first try was no good. I then ran startx and it came right up, now KDE4 ( was 3 I think ). I then ran a few apps and it died with error 11. Running startx stalled after that, and common commands like reboot where no longer available. So I forced it down. Now I get Terminated with status 127 on boot up in normal and recovery mode. 

What I would like to do is upgrade to the latest server version. but I'm not sure ubuntu has an in place upgrade option. I see my 7.04 disc has a recover broken system but I dont know what to try. If I could get to a terminal would apt-get -f upgrade help? Worse case I could try a live cd and get the files I need off, any suggestions?


---Another thought.

I figured I could just go in to my Kubuntu desktop and look at the drive. but it has only a lost and found and grub folder with a few files on the root named config-[version]-server (note this is a SCSI).  

When i do a fdisk -l I see 3 sdb 1,2,3 2 and 3 are large but when mounting them I get wrong fs type. I was sure its ext3 ? I just left the default 7.04 fs.

---

### Post by ulao on 2010-07-03
So I installed a new server in hopes to recover the data. This were going great got it all up and configure and figure I'd try gadmin-samba again. Would you believe the same thing happened? As soon as I rebooted it was broke in the same way. Bewared gadmin-samba breaks ubuntu.


BTW: if anyone come along here the above could be related to this bug

[https://bugs.launchpad.net/ubuntu/+source/sreadahead/+bug/432360](https://bugs.launchpad.net/ubuntu/+source/sreadahead/+bug/432360)

It fixed the second go at it. "ureadahead-other main process terminated with status 4" the bug fix is to do at 

sudo aptitude purge ureadahead sreadahead

but there was still more wrong , getting fsck terminated with status 1 ( I'm told this is ok ) however that made my system lockup at gui.

I then found this:
[http://www.sucka.net/2010/04/how-to-install-nvidia-video-driver-in-10-04-lucid-lynx/](http://www.sucka.net/2010/04/how-to-install-nvidia-video-driver-in-10-04-lucid-lynx/)

and it fixed it up.

---

