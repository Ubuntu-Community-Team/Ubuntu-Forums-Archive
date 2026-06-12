---
title: "Unable to boot after attempted 10.10 -&gt; 11.04 upgrade"
date: 2012-07-17
forum: Installation &amp; Upgrades
---

### Post by dceola on 2012-07-17
Hello folks. I've been scouring the net for the past day and a half trying to find some sort of solution to my issue. I seem to have hosed my company's production Nagios monitoring system after attempting to do a version upgrade.
 
This is all with the server version, text only installation, in a virtual system on a VMware ESXI host.
 
The system started as version 9.10, I then upgraded to 10.10 and had a functional system. At that point, I attempted another update to 11.04. 
 
I entered these commands both times when I attempted the upgrades:
 
```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install update-manager-core
[I changed the upgrade prompt to normal in /etc/update-manager/release-upgrades at this point]
sudo do-release-upgrade

```
 
I did this all yesterday. After the attempted 10.10->11.04, the system booted up to a screen which says:
 
> GNU GRUB version 1.97~beta4
Minimal BASH-like line editing is supported. For the first word, TAB 
lists possible command completions. Anywhere else TAB lists possible 
device/file completions 
Sh: grub > _ 

 
[SIZE=2]I searched quite a bit and found a site that suggested doing this:[/SIZE]
 
> Grub version 1.97 was what came with Karmic. Lucid and Maverick came with 1.98, and Natty/11.04 with 1.99. You have version 1.97 in the mbr and embedding area, but 1.99 in the root partition, sda5. There have been a number of developments in 1.99 and my guess is that the older code in the mbr is incompatible with the later code in the root partition. But why or how the updater managed not to upgrade grub in the mbr in the upgrade process is beyond me.
I suggest this, although no guarantees it will work. You will need a Natty/11.04 live CD. Boot up the 11.04 live CD and choose "try Ubuntu". When you get to the desktop, open a terminal, and: 
 
 
Code:sudo mount /dev/sda5 /mnt
 
 
Then: 
 
 
Code:sudo grub-install --boot-directory=/mnt/boot /dev/sda
 
 
Please note that the --boot-directory switch is new in version 1.99 of grub. It will not work in earlier versions, so you must use the Natty live CD. Besides, you need to use the Natty live CD and not an earlier version to install the 1.99 code to the mbr. 
 
Once you've run those commands, reboot and see if you can boot from the hard drive. You might need to run this command to refresh grub.cfg once you've safety booted into your permanent Ubuntu installation. 
 
 
Code:sudo update-grub

 
 
 
 
[SIZE=2]This suggestion worked for this person which seemed to have the same issue as I do. I downloaded the 11.04 live disc, booted from it, performed the steps and now when I boot the system the screen reads:[/SIZE]
 
 
 
> GNU GRUB version 1.99~rc1-13ubuntu3
[SIZE=2]Minimal BASH-like line editing is supported. For the first word, TAB [/SIZE]
[SIZE=2]lists possible command completions. Anywhere else TAB lists possible [/SIZE]
[SIZE=2]device/file completions [/SIZE]
[SIZE=2]grub> _[/SIZE]

 
 
So, at this point - I can at least boot off of the live CD and recover all of my nagios config and plugin files; and I've been down long enough that I may attempt to spin up another ubuntu vm while I keep hoping to find a solution for getting this fixed.
 
If anyone has any suggestions, for something I should try, I would greatly appreciate it.

---

### Post by dceola on 2012-07-17
I just spoke to my VMware admin, he said we do have a snapshot of the system in a functional state, but it would probably be back at version 9.10 which would at least get me back online; but then I'd still need to upgrade the system. So I guess finding a fix for this isn't overly critical, but I'd still like to find one...

---

### Post by darkod on 2012-07-17
Suggestion 1. Stop upgrading servers from one release to the next. And try to use the LTS (Long Term Supported) versions, with which you can upgrade from one LTS to the other. That is usually once every 2 years and you don't even need to do that since a LTS server is supported for 5 years.

Almost no one upgrades ubuntu servers every 6 months after every release.

If you can, backup your data, and consider making a 12.04 LTS clean install, putting the data back and configure the server as you need to.

Suggestion 2. Even though the grub 1.99 documentation says to use the --boot-directory option I still prefer the --root-directory, unless you do have separate /boot partition. So, try something like:
```
sudo grub-install --root-directory=/mnt /dev/sda
```Since this happened during an upgrade, it might be that something else happened, I don't believe reinstalling grub2 to the MBR will sort it out. But you can give it a try.

---

### Post by dceola on 2012-07-17
I was actually trying to get it to a LTS version. I didn't set up the system from the start or it would have been done with an LTS. From what I can tell, the system at 9.10 was already outdated when they first installed this system...  When it got to 10.10, with the /etc/update-manager/release-upgrades not set to 'normal' it told me there was no update available..
 
anyways - can't take back my screwup now, lol. 
 
I'm currently in the process of trying to install a fresh VM with 12.04 but im having trouble getting it to boot from the iso.  i'll get that sorted eventually.
 
Will try your suggestion2 now.  Thanks for the tips.

---

### Post by dceola on 2012-07-17
No change after running the command from your suggestion above.
 
I also was attempting to access my files to back them up and when I attempted to open the drive from the computer browser app thing, there was a green VG icon over the drive, and attempting to open it gave me an error message "Error starting job: Failed to execute child process "vgchange" (No such file or directory)" I attempted to google that error but so far haven't found anything helpful.  I'm not going to spend too much time trying to access the files since the VMware admin did say he would restore yesterday morning's snapshot to a new VM for me.

---

### Post by darkod on 2012-07-17
A non-LTS version should only upgrade to the next release. So, the original 9.10 should have upgraded to 10.04 (which by the way is LTS) and not to 10.10. Not sure what happened there. Or maybe there were two upgrades, not one, like 9.10 -> 10.04 -> 10.10.

The vgchange message is about LVM. You usually run:
sudo vgchange -ay

to activate all LVM volumes. Provided the disks are OK, it should activate the LVM devices.

---

### Post by dceola on 2012-07-17
I'm not entirely sure what happened myself; but it was definitelyat 9.10 and then upped to 10.10, from there i tried to up it to 11.04 as stated.  Only performed two separate upgrades.
 
I'll give that command a try in order to access the files. Ended up having to re-download the 12.04 install disc as it apparently got corrupted.. will try the suggestion for acessing the files in a bit.
 
thanks again :)

---

### Post by darkod on 2012-07-17
Note that if trying to access LVM from live mode, the live cd doesn't have the lvm2 package. You need to install it into the live environment first:
```
sudo apt-get install lvm2
```

Here is a more detailed guide:
[http://quonn.wordpress.com/2010/12/01/how-to-mount-lvm-partition-on-ubuntu/](http://quonn.wordpress.com/2010/12/01/how-to-mount-lvm-partition-on-ubuntu/)

---

