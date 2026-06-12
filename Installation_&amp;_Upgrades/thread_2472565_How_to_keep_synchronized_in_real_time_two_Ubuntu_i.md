---
title: "How to keep synchronized in real time two Ubuntu installations?"
date: 2022-03-03
forum: Installation &amp; Upgrades
---

### Post by marietto2008 on 2022-03-03
Hello.

I'm looking for the better tool /method / technique that can help me to keep synchronized in real time two Ubuntu installations. I want that every change I make to one of them will be immediately applied to the other one. Now I'm going to explain how is configured my setup. Let's start saying that my primary OS is FreeBSD and that I'm using bhyve to virtualize Ubuntu,using the following parameters :

```
bhyve -S -c sockets=1,cores=2,threads=2 -m 4G -w -H -A \
-s 0,hostbridge \
-s 1,ahci-hd,/mnt/da3p2/bhyve/nvme.img \
-s 2,passthru,1/0/0 \
-s 3:0,passthru,2/0/0 \
-s 3:1,passthru,2/0/1 \
-s 3:2,passthru,2/0/2 \
-s 3:3,passthru,2/0/3 \
-s 8,virtio-net,tap1 \
-s 9,virtio-9p,sharename=/mnt/nvd0p7 \
-s 30,xhci,tablet \
-s 31,lpc \
-s 29,fbuf,tcp=0.0.0.0:5901,w=1440,h=900 \
-l bootrom,/usr/local/share/uefi-firmware/BHYVE_BHF_CODE.fd \
-l com1,stdio \
vm1
```

Actually I have installed Ubuntu 21.10 physically on my nvme disk and it is partitioned like this :

```
root@marietto:/usr/home/marietto # gpart show

=>        34  1953525101  nvd0  GPT  (932G)
          34        2014        - free -  (1.0M)
        2048     1748992     1  efi  (854M)
     1751040  1113507840     2  ms-basic-data  (531G)
  1115258880   833185547     7  ms-basic-data  (397G)
  1948444427         245        - free -  (123K)
  1948444672     1318912     3  ms-recovery  (644M)
  1949763584        2048        - free -  (1.0M)
  1949765632     1310720     4  ms-recovery  (640M)
  1951076352        2048        - free -  (1.0M)
  1951078400     1265657     5  ms-basic-data  (618M)
  1952344057           7        - free -  (3.5K)
  1952344064     1179641     6  ms-basic-data  (576M)
  1953523705        1430        - free -  (715K)
```

Ubuntu 21.10 is installed on the slot ```
/dev/nvd0p7
```. What I wanted to do at the beginning was to boot that Ubuntu physical installation directly on bhyve,pointing it to ```
/dev/nvd0
```but there is a bug and it does not work for the easiest way. So,I found a "workaround" ; I have cloned my nvme disk with dd and I've created an img / raw file called "nvme.img" and I've copied it to my 2 TB size disk. Now,when I want to boot and use Ubuntu 21.10,I can do it directly when I'm running FreeBSD and bhyve. The real Ubuntu installation and its img file are almost identical. Actually when I boot the nvme.img file with bhyve,I have also share the partition where I have mounted the physical installation of Ubuntu in FreeBSD,using this parameter :

```
-s 9,virtio-9p,sharename=/mnt/nvd0p7 \
```

So,the real partition where are all the files of the physical Ubuntu installation is available when I boot the Ubuntu image created with dd while I'm using FreeBSD and bhyve. Good. at this point you have all the elements to understand what I want to do. While I'm using the image of Ubuntu created with dd,some files of this installation will change. What I want to do is to keep them synchronized with the files stored on the physical installation of Ubuntu,mapped at ```
/mnt/nvd0p7
``` ; doing this,when,in the future I will boot the physical installation of Ubuntu,I will have all the files updated correctly. If everything will work correctly there will be no need to boot Ubuntu physically,but it could happen. So,which kind of tool / method you suggest me to accomplish this task ? thanks.

---

### Post by TheFu on 2022-03-04
Use a devops tool, like Ansible.  Only make changes using this tool. This will work if both systems are running concurrently. If both systems AREN'T running concurrently, you can use a multitude of other methods.  It isn't clear if the OS running is a requirement or not during the updates.

You can also look at ClusterSSH, which will let you type 1 command but have it run on 1-1000 systems. Turns out this is less than ideal, because systems **are** slightly different, if only due to hostnames and IP address differences.

No experience with bhyve.

It is very important that Linux systems no have the same GUID or UUIDs for disks, partitions, file systems. Using dd to clone forced the UUIDs to be identical too. If those drives are ever in the same physical computer, chaos (or extreme random results) will happen.

Having both cloned image files with the same UUIDs, but booted into separate VMs should be fine.

If you want to keep the base installs identical, at least with Linux, you can use a CoW file system with overlays for new stuff. This is how the large VPS providers do it.  I think they use LVM + thin provisioning to accomplish it.  This is why they can have to many VMs on much less storage ... the base OS is all fed from the same SSD (or RAM cache), with only the differences written to the CoW overlay.

Doesn't ZFS have this capability to clone a disk pool? Doesn't BSD have ZFS?

---

### Post by MAFoElffen on 2022-03-05
Yes. ZFS does have this capability between remote computers, through ssh... Using 'zfs send' and 'zfs receive'. You can do this with Ubuntu with ZFS. I have several Ubuntu Server and desktop on zfs-on-root... If you just Google ZFS Replication, you will find many resources on that. 

Ubuntu is not the only flavor of Linux that has ZFS capability. Yes, BSD does have ZFS, which is based on OpenZFS, which OpenZFS is a reboot after some time between. It is currently trying to catch up and incorporate changes, enhancements, features and the developement from ZFS Linux, which started while ZFS was still closed source, to what it is today... I won't say one is better than the other, but all the opensource intidties are trying to be cliant with each other on this.

Have you looked into and thought about DRBD? (Distributed Replicated Storage System) Look at these: 
[Ubuntu Server Manual- Ubuntu HA-DRBD]("https://ubuntu.com/server/docs/ubuntu-ha-drbd")
Note that this has an external link to the Ubuntu Wiki page for more information. Go elsewhere. (That page is blank and says it will be...(future))
[DRBD Website]("https://linbit.com/drbd/")

---

### Post by TheFu on 2022-03-06
If you are using LVM, you could link a mirror, then split that mirror to make identical copies. But only 1 OS can be active or disk corruption is likely.  I would think the same issue would happen with DRBD when both systems were running and trying to access the same files concurrently.  With file-level locking, you might get lucky to avoid corruption, but I'd bet that a few times years, there would be a deadlock condition for any heavily used files.

But we still don't know if there is a requirement for both systems to be running concurrently or not. That answer drastically changes the best solution.

---

### Post by MAFoElffen on 2022-03-07
??? 

I always thought on the idea/concept of a replication server or cluster, is that there is a primary/main/Master that is running up front... and all changes are going to other connected nodes, sort of like in shadow... They are the others (secondary/slave/etc)... That when the Main goes awry, then the fail-over rules apply. No one accessed the other nodes of a replication server or cluster, unless it hits those rules. 

But since, in the case of a cluster, or server farm, they are seen as just one entity, so if something does access something that just happens to be somewhere else, the file locks are synced between and updates are resolved. On multi-user databases, you have an intricate sync of those record locks, to handle multi-user access. I can see the same concept. 

I think how ZFS does Replication to remote pools, is the local pool that is being replicated is mounted to the local system, but even though the remote pools are being updated during the replication process, they are not actually being mounted by the system updating it. It sounds a little odd... But that is what it said in the Doc's.

When I read the first post from the OP, I was wondering if a local mirror, such as RAID1 or mirrors in LVM or ZFS would suit his needs. I know that these would be on the same (singular) hardware device, but fulfills a lot of what he was looking for. That does not cover hardware failure of more than storage, but is step in-between.

Just as when doing virtual replication servers on a Virtual Host, sometimes you might want to put the secondary server VM in another storage pool (or on another Virtual Host) for the just in cases... I used to do clusters and replication just on metal... But there are so many things you can do in virtual, and for a whole lot cheaper. That and the management of is so much easier. For example, you want to migrate to "something else", spin up some new machines and migrate to them.

In Virt, this is what I used to do on failover machines. If I wanted a clone of something, I made a clone and kept it up to date on changes... Every so often, I had a cron job that re-cloned that machine. if the original failed, I spun up a clone of that clone, as the original. That is how I kept some VM servers and user VM machines going. This kept my overall network overhead a lot lower. Those kinds of updates don't take as much of a load, and are not as constant. 

Or if you are updating to a cluster or replication servers, making network links to each other on their own sub-net, or fiber channel backbone between them.

---

### Post by TheFu on 2022-03-07
I've deployed active-secondary and active-active clusters both for VMs and on real hardware.  The OP is using VMs on BSD, but has never said that the 2nd system wasn't active too.

There are a few different solutions, depending on the details. Until we are told more, it is just spinning in a circle. 1 post, 3 days ago tells me this isn't actually that important.

---

