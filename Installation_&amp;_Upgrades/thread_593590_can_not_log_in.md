---
title: "can not log in"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by anthonyteg on 2007-10-27
I am new to Linux. I installed Ubuntu 6.10 on my PIII 933 and was running very good. i did the updates that said was available and now i can not get past the login screen. I put in my user name and password then the screen goes black for about 5 sec then back to the login screen. there is NO message of a wrong name or password.  I have some files i need and i dont know what to do. plz help.

---

### Post by qbox on 2007-10-27
hi
try this first
reboot and pres escape. on the meny go to second choice end pres 'e' on next screen go to second shoice and press 'e'. there is one command line.delete everithing after RO and write "single" (supose to look like "some tekst with numbers and letters **ro single**". that supose to login you like root user. change your password and try again
(I write this as much as i remember, so another users can correct me)

If this not work..... try to make recovery(on the same way) if not work at all... reinstal ubuntu

---

### Post by anthonyteg on 2007-10-27
Still no help. I even tried rewriting my xorg.conf file thinking maybe a video driver wasn't right.  What can I post that may help.  I am at a loss but I really don't want to re install.  Thanks for any help.

---

### Post by pieisgood4589 on 2007-10-27
This is what happened to me. I tried everything, but found that nothing worked. So do this- get some kind of external, or internet storage. Slap in the Ubuntu LiveCD, get to your Harddrive, and copy EVERY important or every file you want to the storage media. I personally used xdrive.com, but that's my preference. Then do a clean install. Once you are done, just retrieve all the files from the external or internet storage! Simple! Good luck! :popcorn::guitar::guitar::guitar::guitar::guitar::guitar::popcorn:

---

### Post by anthonyteg on 2007-10-27
One off the files that I need is my pass word file for gpass or otherwise known as password manager.  I cannot find where the passwords are stored to save this to another location.  By using a live cd, i have saved most of the information to a usb drive.  I used the  package manager to get the list of files that was created by the install of the password manager, no joy.  I tried searching the HD for a file after adding  a new password. Again, no joy... :(  Again, thanks for any help.

---

### Post by taurus on 2007-10-27
While you are in recovery mode, post the output of this command here?

```
df -h
```

---

### Post by anthonyteg on 2007-10-27
ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
unionfs               789M  658M  132M  84% /
varrun                157M   80K  157M   1% /var/run
varlock               157M     0  157M   0% /var/lock
procbususb             10M   64K   10M   1% /proc/bus/usb
udev                   10M   64K   10M   1% /dev
devshm                157M     0  157M   0% /dev/shm
lrm                   157M  7.6M  150M   5% /lib/modules/2.6.17-10-generic/volatile
tmpfs                 157M   12K  157M   1% /tmp
ubuntu@ubuntu:~$ 






Right now i am using a live cd to this.  I ran the command given in a terminal.  Thank you very much for the help!

---

### Post by taurus on 2007-10-27
> **anthonyteg said:**
> ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
unionfs               789M  658M  132M  84% /
varrun                157M   80K  157M   1% /var/run
varlock               157M     0  157M   0% /var/lock
procbususb             10M   64K   10M   1% /proc/bus/usb
udev                   10M   64K   10M   1% /dev
devshm                157M     0  157M   0% /dev/shm
lrm                   157M  7.6M  150M   5% /lib/modules/2.6.17-10-generic/volatile
tmpfs                 157M   12K  157M   1% /tmp
ubuntu@ubuntu:~$ 

Right now i am using a live cd to this.  I ran the command given in a terminal.  Thank you very much for the help!

That is no good.  I want to see your disk space on your harddrive so you need to boot into recovery mode, not from the LiveCD.

You can boot your machine with recovery mode, single mode, right?

---

### Post by anthonyteg on 2007-10-27
Ok, I had to go to another machine and write all this in by hand.  looks like I need to delete some or get a bigger hard drive!!!

Filesystem              size   used  avail use%   mounted on
/dev/hda1               8.8G  8.6G      0     100%      /
varrun                      157M   16K  157M    1%       /var/run
varlock                     157M   0      157M     0%      /var/lock
procbususb               10M   64K     10M   1%       /proc/bus/usb
udev                           10M   64K     10M   1%      /dev
devshm                  157M   0          157M  0%      /dev/shm
lrm                           157M   18M     140M  11%  /lib/modules/2.6.17-10-generic/volatile
root@--III_933:~#

Thanks for your help.

---

### Post by anthonyteg on 2007-10-27
Please mark this one solved!!!!!  I deleted some files, got 400M room and rebooted... Log in fine!   Thanks everyone for your help!!!!  Get rid of more and will be fine.   Thanks  once again..

---

### Post by taurus on 2007-10-27
```
sudo apt-get clean
```
Will clean out your cache, giving you some more space.

---

