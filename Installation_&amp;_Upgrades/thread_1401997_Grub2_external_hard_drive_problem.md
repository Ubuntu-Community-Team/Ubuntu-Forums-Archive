---
title: "Grub2 external hard drive problem"
date: 2010-02-08
forum: Installation &amp; Upgrades
---

### Post by Poirot on 2010-02-08
Hi all,

I've tried to be clever but as usual I didn't think before acting and missed a small detail.

I have recently installed karmic (dual booting with Vista) on my dell xps laptop. The install went fine, I'm very happy with my new OS.

I bought a new Seagate 500GB portable external HDD. I got a bit over-excited and installed karmic on the external drive. This worked fine and I got a lovely (but slow to appear) Grub2 menu showing my vista and both ubuntu options.

My problem is that now, when I unplug the external drive, Grub fails and I get a grub rescue> prompt. So I need the external drive to be plugged in if I want to boot.

It seems I have done something to the grub configuration. I have read around the subject but I am not confident about how best to proceed.

I understand there is an 'advanced' option in the installer which will allow me to choose where to install grub. Presumably I want it on the internal drive so that I can boot without the external one plugged in.

Am I right in thinking I can just pop in my install disk and redo the installation? 

If I indicate I want to install Grub on the internal drive, which partition should I aim for?

Am I in danger of making things worse?

Will I get a grub option for booting to the external drive?

Will I be able to plug the external drive into a different machine and boot from it?

I haven't done anything with the fresh install on the external drive so I don't mind losing that.

Advice would be very much appreciated.

---

### Post by darkod on 2010-02-08
Hold on, don't do anything or you can really make things worse. :)

Here is a short basic explanation: After doing the install on the ext hdd, in fact you DO have grub on your int hdd. The thing is that only a small part of grub is put on the hdd MBR to get it going. The grub config files are usually on the ubuntu partition (unless you have separate /boot partition, different story), and that is on your ext hdd where you installed ubuntu.
Hence, with the ext hdd disconnected, gub is starting from your int hdd and when looking for the config files, it can't find them. Error. End of story. :)

This is easily fixable. Only you need to specify whether you have only windows on your int hdd (because I didn't understand that clearly from your post), or you also have ubuntu too on your int hdd, plus on your ext hdd.

If you only have windows on the int hdd and you want it to boot directly when the ext hdd is not present, we will restore windows bootloader to the int hdd. And that will sort it out.

Then we will also put grub2 on the ext hdd MBR, and you can boot it when is it connected and you choose to.

Makes sense? :)

---

### Post by Poirot on 2010-02-08
Thanks Darkod,

This is kind of what I thought was going on. I'm still a bit hazy as to what it all means but it will be a good exercise.

So, I have Vista on my internal drive. I shrunk down the Vista partition and installed Ubuntu in the remaining space. So I do have a dual boot system even without the external drive.

I set up the external drive as a nice way to show people what Linux can do on their own machines. Not sure if it will work but I'll worry about that once I have my internal drive sorted.

So, ideally I would like the laptop to give me the option of Vista or Ubuntu (internal) by default and to give me the extra option of Ubuntu (external) when the external drive is plugged in.

Worst case scenario I'd like to just get the GRUB menu back when the external drive is not plugged in.

---

### Post by darkod on 2010-02-08
No problem, we'll get it going in no time. Just to remind you that you can always show ubuntu as live desktop from a cd or usb without actually having to use your ext hdd. But yes, it would be nice if you could also show some software installed on the ext hdd ubuntu.

Now... Connect your ext hdd but if you can boot from the ubuntu cd, Try Ubuntu option, into the live desktop. So, we will not use any of the two ubuntus you have installed, we will use the live desktop instead. It should give you internet so you can post from it here.

In terminal execute:

sudo fdisk -l

that will show you your partitions and disks. Post the results here and you might as well wait on the live desktop, I'll post back what to execute after I see the fdisk results.

---

### Post by Poirot on 2010-02-08
OK, I'm in the live CD. Here's the output

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2f46cc71

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16411   131820333+   7  HPFS/NTFS
/dev/sda2           16412       30401   112374675    5  Extended
/dev/sda5           16412       29827   107763988+  83  Linux
/dev/sda6           29828       30401     4610623+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x05a1b7e5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       26108   209712478+  83  Linux
/dev/sdb2           26109       32635    52428127+   b  W95 FAT32
/dev/sdb3           32636       42847    82027890    5  Extended
/dev/sdb5           32636       36282    29294496   83  Linux
/dev/sdb6           36283       42361    48829536   83  Linux
/dev/sdb7           42362       42847     3903763+  82  Linux swap / Solaris

---

### Post by darkod on 2010-02-08
OK, /dev/sda is your int hdd, /dev/sdb your ext hdd. On the internal you can clearly see your windows on /dev/sda1, and ubuntu on /dev/sda5.
On the external it's not so clear because you have linux partitions /dev/sdb1, /dev/sdb5, /dev/sdb6 but usually the first /dev/sdb1 would be the root partition.

To reinstall grub2 on the int hdd MBR that is connected with the ubuntu on the int, in terminal execute:

sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

So, first you are mounting your ubuntu root partition (/dev/sda5) and then installing grub on the MBR of /dev/sda.

After this, if you reboot without the cd and the ext hdd connected, you should get your grub2 menu from the int and boot both vista and the int ubuntu successfully.

Try this first, we'll deal with the ext after.

---

### Post by Poirot on 2010-02-08
Fantastic! Thanks Darkod. 

I'm logged back in without the external drive plugged in. The Grub menu was exactly as it used to be (with three versions of the kernel and Vista and memtest etc.).

---

### Post by darkod on 2010-02-08
Excellent. If you want to take it further, I need your help too. As you saw from fdisk, there are three Linux partitions on the ext hdd (not counting the Swap).
Usually the root partition would be the first on the disk if there is no other OS, which means /dev/sdb1.
Did you create any additional linux partitions yourself? Did you install more than once on the ext hdd? That would explain more than one Linux partition on the ext hdd.

We need to know which partition to mount. It would be for example:

sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb

Again you would have to execute this from the live desktop and it will install grub on the ext hdd so you can boot from it when you want to. But this is under the assumption that the root partition is /dev/sdb1.

PS. And the ext hdd will have to be connected too so the commands can find it.

---

### Post by Poirot on 2010-02-08
Yeah, I made a few data partitions when I first got the disk. So I am pretty sure...

sdb5 is /
sdb6 is /home.

Is there any way to be certain of this?

Just to clarify. Do I need to do this from the live CD?
If I can't do it from my internal hdd Ubuntu install, why not?

---

### Post by darkod on 2010-02-08
You can't do it from the int hdd ubuntu because the grub-install command will use your int hdd ubuntu as root partition, while we want the ext hdd root to be used. That's why you have to:
Connect the ext hdd and boot again from the cd into the live desktop.
Then, if /dev/sdb5 is root as you say, execute in terminal:

sudo mount /dev/sdb5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb

After that you should be able to boot from the ext usb hdd even a computer that has no internal disk.

Note: When your ext hdd ubuntu was installed, it probably detected you have vista and another ubuntu on the int hdd. Don't be surprised to see them in the grub boot menu. But if you plug the hdd in another computer it will still show the same menu but obviously you can't use the vista entry.

---

### Post by meierfra. on 2010-02-08
> You can't do it from the int hdd ubuntu
I disagree. Just do it from the internal drive.

Edit:  grub-install gets "root" from  the "--root-directory=/mnt"  statement. So it does not matter from where one runs "grub-install"

---

### Post by darkod on 2010-02-08
> **meierfra. said:**
> Nonsense. Just do it from the internal drive.

Oops. I wasn't sure so I just took the safe way. :) Didn't want the wrong root to be used.

---

### Post by Poirot on 2010-02-08
Thank you so much, my problem is not a problem but a learning opportunity for myself and for others.

Everything works as you said and now I know a bit more about what I'm doing.

Thanks darkod

---

### Post by meierfra. on 2010-02-08
There is one more step:

To avoid that the MBR of the internal drive gets overwritten during the next kernel update, you have  to let the Ubuntu on the external drive  know that Grub should be installed to /dev/sdb:

Boot into the Ubuntu on the external drive and run the following command:


```
echo "SET grub-pc/install_devices /dev/sdb" | sudo debconf-communicate
```

---

