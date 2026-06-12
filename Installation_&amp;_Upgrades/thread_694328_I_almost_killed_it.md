---
title: "I almost killed it"
date: 2008-02-11
forum: Installation &amp; Upgrades
---

### Post by OneWingedAngel0164 on 2008-02-11
I have no Idea how I managed it, but I screwed something up. I can't install updates, actually I can't install anything. I first noticed there were problems actually when I pressed ctrl-alt-F1 and expected a login screen and got some random stuff and was unable to type. Same for F2-F6. 

the F1 one says: 

kinit: name_to_dev_t (/dev/disk/by_uuid/c45c5e9a-07e1-4b28-a102-e6638ea48ed5 = sda5(8,5)
kinit: trying to resume from /dev/disk/by_uuid/c45c5e9a-07e1-4b28-a102-e6638ea48ed5
kinit: no resume image, doing normal boot...


I am completely baffeled.

---

### Post by OneWingedAngel0164 on 2008-02-13
Ok no one knows whats wrong? How about this: How would I go about basically reinstalling ubuntu without nesicarily removing anything?

---

### Post by FrozenFox on 2008-02-13
That kinit stuff is actually not an error state, if i'm not mistaken. It has something to do with (as it says) resuming the state of your system to what it was during the prior reboot, afaict. Mine says that too while booting. As for why it wont let you type on any of the f# sessions, I have no idea.

It sounds like you can boot into the system from your post, though you say you can't install anything.. so please tell us what terminal/console output you get from sudo apt-get update and sudo apt-get install. My guess is during an update sequence, something did not download or install right and caused problems, but we can hopefully fix such. :)

As for the reinstall w/o deletion: I'm not sure, but I think ubuntu defaults to installing the /home piece as part of the same partition as /  root instead of separately. If it installed /home to a separate partition, you could easily just overwrite the installed (/  root) partition and tell the installer not to format the /home one. If you chose to do this during installation (ie manually partition the drive instead of let it automatically do so), you could easily do such. Again, though, I -think- ubuntu defaults to using the same partition for both (i don't have enough room for more than the 2 primary partitions for ubuntu, so it perhaps just only made 2: root, swap instead of all 3: root, home, swap. i have no idea). In short, I'm not sure if you can! You can find out though if your stuff is on the same partition via installing/running gparted and looking at your partition setup. If you only have 2 linux partitions instead of 3, you probably have /home installed as part of the root install directory.

Also: are you on Gutsy or Hardy?

---

### Post by OneWingedAngel0164 on 2008-02-13
I am using gutsy, and I just tried to apt-get gparted. This is what I got after I answered yes.

After unpacking 9236kB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main gparted 0.3.3-2ubuntu6.1 [346kB]
Fetched 346kB in 1s (285kB/s)  
(Reading database ... 118063 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.22-14-generic ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: error processing linux-ubuntu-modules-2.6.22-14-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.22-14-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by FrozenFox on 2008-02-13
Aha, dpkg is messed up, because something happened with the kernel modules package. 

I don't know really how to help, but you might get better results by making a new topic with a more descriptive title including error updating kernel modules to get the attention of more experienced forum-goers and give them the same info from above (plus whatever other info you got before pressing  Y, suggesting which stuff is to be upgraded, removed, installed, etc). My only suggestion is to try sudo apt-get clean then sudo apt-get update then just sudo apt-get install. I don't think it'll work, but you can try. if it doesn't, as i expect, please make a new post as described.

---

