---
title: "RAID problems with name"
date: 2011-07-23
forum: Installation &amp; Upgrades
---

### Post by kjuergen on 2011-07-23
My RAID-1 array failed and I had to replace both drives (fortunately I had a 99.88% backup and only lost a few emails!).

I installed the new drives and used disk utility to set them as raid autodetect. then with mdadm I created the array (/dev/md0) and mounted it with mount /dev/md0 /raid and everything looked fine.
During reboot I got the message that the device /raid wasn't ready and I skipped ,ounting.
When I checked the raid array was /dev/md127. When I stop the array and start it again it all of a sudden has the correct name /dev/md0 again but reboot generates Alzheimer again and it's toast. By placing the UUID in fstab it meanwhile mounts it automatically again but its a real pain.

Another problem is that if I remove one of the disks to simulate an error the remaining disk doesn't get mounted (but that's only for one of them, the other one works fine).

Somehow something is broken but despite several hours of googleing I haven't found any hint.

How can I fix this????

Thanks!

---

### Post by kjuergen on 2011-07-23
OK, one step further.... I stopped the array and started it again so it had the correct /dev/md0 name.
Then I ran as root:
mdadm --detail --scan > /etc/mdadm/mdadm.conf

Now it boots at least sometimes as /dev/md0 but still more often as md127....
----

Edit:
did a lot more (trashed the Saturday ;-( ) and the behaviour is crazy. I boot and my two SATA drives are sda and sdb and the EIDE which I use for the system is sdc. Then I install the RAID as /dev/md0 and when I reboot the SATA drives are sdb and sdc and the array has the name /dev/md127. If I stop and then start it again it comes with it's real name /dev/md0.

I then re-created the RAID array while the drives were still sdb and sdc and yuck, at reboot they went back to sda and sdb. Looks like something gets confused when I create a RAID array.

Is there any way to tell the OS to stick to one or the other naming??? I am close to the point where I give up in having a bit of security for my data.

---

### Post by kjuergen on 2011-07-24
anyone has a clue what happens? Or am I the only one having this problem?

---

### Post by YesWeCan on 2011-07-24
Would you post the outputs of
cat /etc/mdadm/mdadm.conf
sudo blkid

---

### Post by kjuergen on 2011-07-24
blkid:
/dev/sda1: UUID="ee3e095d-596f-4fe9-a093-35f257ea8f89" TYPE="ext4" 
/dev/sda5: UUID="3ff2a6b2-f019-412c-b666-7044aa9a5949" TYPE="swap" 
/dev/sdb1: UUID="7cde3764-c580-878b-ed2a-dfe9162aba7b" LABEL=":md0" TYPE="linux_raid_member" 
/dev/sdc1: UUID="7cde3764-c580-878b-ed2a-dfe9162aba7b" LABEL=":md0" TYPE="linux_raid_member" 
/dev/md127: LABEL="raid" UUID="a04d0f22-dc50-4771-b725-343431dbaf5f" TYPE="ext4"

mdadm.conf:
ARRAY /dev/md/:md0 metadata=1.2 name=:md0 UUID=7cde3764:c580878b:ed2adfe9:162aba7b

as you can see above the array is currently md127 but sudo mdadm --detail --scan gives me what it really is:
ARRAY /dev/md/:md0 metadata=1.2 name=:md0 UUID=7cde3764:c580878b:ed2adfe9:162aba7b

In both cases, md0 and md127, the UUID is the same.

Found a temporary fix (not what I like).

Made the array, rebooted and it naturally failed. Then I entered the UUID in fstab and now it mounts no matter whether it boots as md0 or md127.

Major problem is that if one of the drives fails (or is removed) it won't mount the remaining one as it should. If I then put the removed drive back on and add it back to the array it complains that size is to small yet it is exactly the same size (to the bit) as the other one and it worked before.

Major problem is now that in the event of a RAID1 failure it won't recover any more. I have to backup the entire running drive, assemble a new array with a new drive and move the backup back onto the array.
As I have my home directory on the RAID it's a disaster as I won't be able to log in. Made a spare account with admin rights which allows me to do the backup, new RAID install and restore of data. Not what I want as an easy safety thing.......

---

### Post by YesWeCan on 2011-07-24
I have a question about using a : in a device name. I am not sure whether that is kosher or not.

The mdadm.conf file is incorrect if you want the array to be /dev/md0. You should have something like this (I've removed the superflous specifiers):
```
DEVICE partitions
ARRAY /dev/md0 num-devices=2 level=raid1 UUID=7cde3764:c580878b:ed2adfe9:162aba7b
```

and then put a /dev/md0 mount command in fstab in place of the UUID one you put in.
Unmount the array and then remount it [COLOR="navy"]sudo mount -a[/COLOR]
For good measure run [COLOR="Navy"]sudo update-initramfs -u[/COLOR]

---

### Post by kjuergen on 2011-07-24
Thank you so MUCH!

The : was only in from the last attempt and to my surprise it didn't make a difference. I re-did the entire RAID setup and then followed your sequence and what a surprise: it works! Haven't pulled a drive yet to see whether that will screw it up again but for now I am just tired of it and will do some work first before I ruin it again..

Thanks again........

Edit:

pulled one drive to simulate a failure, it booted up degraded. Then put in the drive, added it to the array and it's synching it! Perfect and thanks to YesWeCan!!!!!

Btw: all the RAID setup can be done with Disk Utility (Palimpsest) which is in the repository. Makes live a lot easier (Hint: to make a raid device go to File -> create)[U]
[/U]

---

### Post by YesWeCan on 2011-07-25
Glad to hear it. You are welcome.

---

