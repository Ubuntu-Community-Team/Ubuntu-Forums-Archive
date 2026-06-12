---
title: "a gparted question...."
date: 2012-05-15
forum: Installation &amp; Upgrades
---

### Post by shantiq on 2012-05-15
[ATTACH]218020[/ATTACH]


ok not sure what to do here and need advice as i know it is serious business:KS


screenshot of my gparted on the 500Mb internal drive


precise is on /dev/sda2      and now i want to remove all the 11.10 still on the drive


in /dev/sda1   with the unallocated

i shrank the oneiric section so i could add it to precise but see it is not an option



how do i remove all of sda1     and free the space to add to precise   on sda2?


i have changed sda2   to be  boot  [changed the flag option]



**Can i now safely ** delete sda1 and free the space    and still be able to boot sda2        and what happens to the unallocated    will it then be able to be added to sda2



I need advice from someone who really knows all of this



thanx in advance    shan

---

### Post by jadtech on 2012-05-15
> **shantiq said:**
> [ATTACH]218020[/ATTACH]


ok not sure what to do here and need advice as i know it is serious business:KS


screenshot of my gparted on the 500Mb internal drive


precise is on /dev/sda2      and now i want to remove all the 11.10 still on the drive


in /dev/sda1   with the unallocated

i shrank the oneiric section so i could add it to precise but see it is not an option



how do i remove all of sda1     and free the space to add to precise   on sda2?


i have changed sda2   to be  boot  [changed the flag option]



**Can i now safely ** delete sda1 and free the space    and still be able to boot sda2        and what happens to the unallocated    will it then be able to be added to sda2



I need advice from someone who really knows all of this



thanx in advance    shan

why didnt you just format the whole disk to start with ???

---

### Post by darkod on 2012-05-15
First, before deleting 11.10 you need to make sure grub is from the 12.04. To make sure, just boot 12.04 and in terminal do:
sudo grub-install /dev/sda

After that you can safely delete /dev/sda1 without creating issues with grub.

Once /dev/sda1 is deleted and all of that is one bug unallocated space, you can either create new ext4 partition from it and use it in 12.04, or you can expand your 12.04 root to include the unallocated space.

If expanding, you will have to do it from live mode, swapoff the swap partition so there are no keys symbols, expand /dev/sda2 first to include the unallocated space, and only then expand /dev/sda6.

If you ask me, a much better option is simply creating new ext4 partition from the unallocated space and use it like that.

With every partition resize there is some small change of danger to your data. You don't need that. Linux works just fine with many partitions, it doesn't need to be whole in one.

---

### Post by shantiq on 2012-05-16
ok thank you darko for complex info


now i have done  sudo grub-install /dev/sda     and stopped there as i want to make sure



i then did    this


> grub-install -v
grub-install (GRUB) 1.99-21ubuntu3
shantiq@shantiq-00000000000000000000000:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-24-generic
Found initrd image: /boot/initrd.img-3.2.0-24-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 11.10 (11.10) on /dev/sda1
done




does it look right?     may i proceed to remove sda1?   ** why are sda2   and 12.04 not in the list   ????**

will then go that way > better option is simply creating new ext4 partition from the unallocated space and use it like that.



excuse the nervousness and doublecheck but i have made a mess before :KS:KS:KS



y muchas gracias por todo su ayuda         shan

---

### Post by darkod on 2012-05-16
Yes, looks fine. When you run update-grub, by default it first finds the linux kernels from the installation it is connected to. In this case, the 3.2.0 which is 12.04.

Then after the memtest it finds all secondary OSs, in this you can see it reported your 11.10.

So, the primary is 12.04, just like we want it.

You can safely delete /dev/sda1 now.

---

### Post by shantiq on 2012-05-16
ok thanx done it    this is what i have now


[ATTACH]218059[/ATTACH]




so now when i go to places / 196 GB file system [the new section] it does not open

do i need to mount it or something?     not clear how i access that extra space now:KS

---

### Post by darkod on 2012-05-16
By clicking on it in places, it should mount and open. In any case, to make a permanent mount, open your /etc/fstab and make a mount at /data for example:

gksu gedit /etc/fstab

Make a new line:
/dev/sda1   /data   ext4   defaults   0   2

Save and close /etc/fstab. Test if it will mount correctly with:
sudo mount -a

After that you should see it mounted at /data. You can see all mounted devices with:
df -h

If you don't like /data, you can create your own path and folder, and use that as mount point. But you have to create it first, like:
sudo mkdir /path/foldername

Then use that mount point in /etc/fstab instead of /data.

---

### Post by shantiq on 2012-05-16
ok thanx again    a very simple way was to reload the computer  :KS:KS



so now i have my 500Gb  in two parts with Precise 196Gb on one side and the rest on other side  and i can easily navigate from one to the next


> df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda6       276G  120G  142G  46% /
udev            1.3G  4.0K  1.3G   1% /dev
tmpfs           502M  964K  501M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.3G  1.1M  1.3G   1% /run/shm
/dev/sda1       183G  2.9G  171G   2% /media/777a9ed8-803f-42d0-af07-c03b98c26ba2



As you say much safer than risking the live disc manipulation and the fact that it is not in one block matters little


Thank you for your crystal-clear instructions; this is a **fast** and efficient way to do this;      i simply did not trust the new Version [Precise] and wanted to test it for  a few weeks before removing 11.10


This way allowed me to do that


[B]
PS[/B]    ha    i spoke too soon    there is still a problem    ** icannot move documents in and out of that section     tells me i am not the owner**


that cures it

>  sudo chown shantiq /media/777a9ed8-803f-42d0-af07-c03b98c26ba2


---

### Post by mastablasta on 2012-05-16
also make sure that your user can access it.
 
i added new disk and it was kind of strange at first until i figured out i need to assign access (+read&write) rights to user.

---

### Post by shantiq on 2012-05-16
thank you mastablasta i think from terminal



 > sudo chown yourname  /media/the new section     

fixes that i hope    seems ok:KS

---

