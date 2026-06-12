---
title: "Cloning and deployin double boot configuration for labs"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by mmingos on 2008-04-24
Hello, i am trying to promote Ubuntu in the computer labs of the university where i work.

I work with Ghost. I make a good configuration and then deploy it in all machines. So in the new version of the Image i include an Ubuntu 7.10 installation that works flawlessly in the prototype machine.

When i use Ghost 2003 to clone it and deploy it via DVD or disk to disk to other machines, the GRUB loads fine, the Windows XP boot is fine but Ubuntu doesn't boot.

In normal mode, it stops in the Ubuntu loading screen and once i see the console i get :

> Starting up...
Loading, please wait...

Check root = bootarg cat /proc/cmdline
or missing modules, device : cat /proc/modules is /dev
ALERT! /dev/disk/by-uuid/fb09cb39-ccf3-41f... does not exist. Dropping to shell!

Busybox v1.1.3 ...

(initramfs)

What can i do ? Can i do something before cloning the prototype so that it doesn't happen ? It seems like the OS is searching for the old hardware of the hard disk and is linked to its hardware id.

If you cannot help, can you give me an easy alternative how can i clone this dual boot system to 30 PCs via DVD and network ?

---

### Post by Patsoe on 2008-04-24
I don't have much experience with this (only just moved over to Hardy) but indeed it seems that something is looking up disks by uuid. I'm sure it used to be by /dev/hd* name though - for your purposes it's probably best to revert to that.

If you look at the original system, how is the boot device specified in /boot/grub/menu.lst? The other file to check is /etc/fstab. I *think* that's all...

---

### Post by mmingos on 2008-04-25
Anyone else ? Any alternative for cloning my prototype machine to the other pcs in the lab ?

Somebody in here must be a computer lab admin who has double boot in the pcs of the lab. 

We need to clone a double boot machine to other machines with the same configuration. How can we do this insted of Ghosting them ?

---

### Post by Patsoe on 2008-04-25
> **mmingos said:**
> Anyone else ?

No, really just those two files, I think :)

Actually you can do a system-wide search for that uuid using a combination of grep and find (see their man pages) if you want to be really sure you're not missing anything.

---

### Post by Aearenda on 2008-04-25
It sounds to me as though the Ghost process is changing the UUID for the partitions. I don't use Ghost, so I may be wrong. In other words, patsoe is right.

Assuming I'm right, here is what I would do to fix it (please read to the end first - there's an experiment you can do to see if I am right at the end, which draws on some of the explanation given further up).

The UUID is a unique identifier for the partition; using it means that the partition can be shifted physically from disk to disk and it will still work. Unfortunately, it also means the boot will fail if it cannot be found. So you need to replace the UUID entries in GRUB's config with partition names that will not change when the machine is cloned.

On your master machine, if you run
```
cat /etc/fstab
```
you should see a list of the UUIDs and a commented line **above** each one showing the equivalent device name /dev/sdxy - something like this:
```
# /dev/sda5
UUID=8a4a255a-c61f-452b-ad60-927b8c48ba70 / ext3 noatime,nodiratime,errors=remount-ro 0 1
```

Here my root partition is identified by UUID and /dev/sda5 is the device name.

On your master machine, you should **make a copy of /etc/fstab for later reference** and then edit /etc/fstab so that the UUID part is replaced by the /dev/sdxy name - so my entry from above would now be:
```
# /dev/sda5
/dev/sda5 / ext3 noatime,nodiratime,errors=remount-ro 0 1
```

Don't worry about exact layout, a space is as good as a tab. The device name for the partition may be hdxy instead of sdxy.
Do this for each partition that is identified by UUID.

Next, make a backup copy of /boot/grub/menu.lst, and then edit the original file looking for an entry like this:
```
# kopt=root=UUID=8a4a255a-c61f-452b-ad60-927b8c48ba70 ro
```

Change this to the appropriate /dev/sdxy for the UUID as shown in the copy you made earlier of /etc/fstab, like this:
```
# kopt=/dev/sda5 ro
```

Note that the '#' at the start of the line is important and must be there.

Further down the file, you will find at least two lines like this, but with different final options:
```
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=8a4a255a-c61f-452b-ad60-927b8c48ba70 ro quiet splash
```

You can either fix all the lines like this by saving the file now and then using update-grub, which will take the change you just made and fix all the relevant entries, or fix each line manually in the editor (which is what I do, since I have the device name in the clipboard by this time):
```
kernel		/boot/vmlinuz-2.6.24-16-generic root=/dev/sda5 ro quiet splash
```

Repeat for each line with a UUID, replacing with the correct device name, and save the file.

I think that's it. Reboot the master to make sure it works correctly, then clone it and test.

Note that you can also do an experiment before you start all this, to avoid wasting time if my guess is wrong - on an already CLONED machine, when it starts up, 
1. Press ESC if necessary to enter the GRUB menu
2. Move the cursor down to the 'recovery mode' entry and press 'e'. 
3. It will show you the relevant lines; move down to the kernel line and press 'e' again. 
4. It will allow you to use the cursor keys to replace the UUID=xxxx... with the /dev/sdxy syntax discovered from /etc/fstab on the master. Press <Enter> when done.
5. Press 'b' to boot off the modified entry. 
6. The clone should then start, but will stop again later complaining about the UUID in /etc/fstab on the clone. You may be able to get to a shell and edit that file too at this point; but it doesn't really matter since you will have proved that it is the UUID if you do get further than before, and you should really just go and modify the master.

I hope this helps! Please let us know how you get on.
BTW, have you tried Clonezilla?

---

### Post by Patsoe on 2008-04-25
Hi Aearenda, thanks for explaining uuids: I obviously completely misunderstood those. But now that (I think) I understand, I don't understand why you couldn't clone those along with the rest of the partition contents?

Wouldn't replacing Ghost by something else be a better solution then than my thought of replacing the uuid references?

---

### Post by Aearenda on 2008-04-25
Well yes, I do think the UUID should be kept unchanged during the clone process, and there are other tools that would preserve it, but maybe Ghost changes it for a reason - such as, on a Windows XP system, this would probably trigger reactivation along with a MAC address change on the network card, so there is a commercial reason for MS to want Ghost to do it. ** But this is just speculation on my part - I haven't experimented with Ghost **. I don't know where the UUID is actually stored. However, the whole point of a UUID is that it is a unique ID - so cloning it actually makes it not unique, and so maybe Ghost is doing it right! :-)

Actually with hindsight I'm not sure we are right - if it was the GRUB UUID entry that was wrong, I don't think it would get as far as it does. Maybe there is a resume parameter on the kernel line too. Or maybe it is actually the fstab one that it fails at.

I think it is sensible to persist with Ghost in this case since it is a familiar tool already in use in this lab, and presumably paid for. No reason to change unless what we have come across is a bug.

---

### Post by BatsotO on 2008-04-25
Was that the norton ghost? click here and there.. you can clone just by booting to any live cd and type dd if=/dev/hda of=/dev/hdb  (or /dev/sda and sdb) in terminal.
99.9 % works (I clone at least a hundred disk).

---

### Post by Aearenda on 2008-04-25
I use dd too sometimes - but only on small partitions! It copies empty space. I use partimage on bigger ones, in conjunction with clonezilla and PXE booting workstations - no need for a live CD or typing commands.

---

### Post by BatsotO on 2008-04-25
> **Aearenda said:**
> I use dd too sometimes - but only on small partitions! It copies empty space. I use partimage on bigger ones, in conjunction with clonezilla and PXE booting workstations - no need for a live CD or typing commands.

I clone the whole 80 gigs disk in about 45 minutes. but to be honest I never use it on dual boot disk. I'm 100% linux and a very patient man.

---

### Post by Greslore on 2008-04-25
mmingos:

I am in a very similar situation as you.  I need to dual boot a lab with both windows and ubuntu.  I tried to use ghost, but it would always mess up the dual booting.  I re-wrote the fstab, and even dd the mbr.  But ghost simply would not work.  I then tried the app partimage, but this did not work with dual booting as well.  So I gave up on cloning and decided to go with clean installing.

After several months here is how I do my dual boot set ups:
1) Boot off of the System Rescue CD.  [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)
2) Run gparted to remove all existing partitions.  Create three partitions:
-NTFS
-swap
-Remainder of space goes to EXT3 which gets mounted to /
3) Boot off of Ubuntu CD and install system to ext3 partition.
4) After machine is rebooted into Ubuntu, I have a post install shell script that I run that does the following:
-Installs all desired applications via apt-get. 
-Installs applications that are not in repository
-Sets up machine for IP Printing
-Copies over pre-configured files for customized KDE, fstab, menu.lst, etc etc.
5) Once Ubuntu is set up, I then use ghost to install my windows image to the NTFS partition.  

I tried to use preseeding to automate the initial Ubuntu install, but I couldn't find a good resource to help me get this to work yet.  I also have an internal local mirror of the repositories which makes the above much more feasible in terms of the time it takes to install the packages in step 4.

Feel free to send me a private msg if you need more info.  I am re-working all this with 8.04 to hopefully come up with something a bit more streamlined.  But so far, the above works the best for me.

---

### Post by firfin on 2008-07-31
> **Greslore said:**
> 
4) After machine is rebooted into Ubuntu, I have a post install shell script that I run that does the following:
-Installs all desired applications via apt-get. 
-Installs applications that are not in repository
-Sets up machine for IP Printing
-Copies over pre-configured files for customized KDE, fstab, menu.lst, etc etc.

I tried to use preseeding to automate the initial Ubuntu install, but I couldn't find a good resource to help me get this to work yet.

Sorry for the completely off-topic response. But how can I create such a post-install script? 
Did you find a way of streamlining this already?
And finally any luck with the pre-seeding ?:confused:

---

### Post by arod0405 on 2009-11-12
> **Greslore said:**
> mmingos:
After several months here is how I do my dual boot set ups:
1) Boot off of the System Rescue CD.  [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)
2) Run gparted to remove all existing partitions.  Create three partitions:
-NTFS
-swap
-Remainder of space goes to EXT3 which gets mounted to /
3) Boot off of Ubuntu CD and install system to ext3 partition.
4) After machine is rebooted into Ubuntu, I have a post install shell script that I run that does the following:
-Installs all desired applications via apt-get. 
-Installs applications that are not in repository
-Sets up machine for IP Printing
-Copies over pre-configured files for customized KDE, fstab, menu.lst, etc etc.
5) Once Ubuntu is set up, I then use ghost to install my windows image to the NTFS partition.  

Same situation here. In my school lab I want to install a dual boot system on 10 identical pc. Vista is preinstalled on every pc in a separate partition so all I have to do is create one "master" pc and clone the linux partition. I didn't try yet but I guess that fixing UUID stuff and network parameters all shuld work fine. I'm only a bit concerned about the bootloader. It is usually installed on MBR and it wouldn't be cloned when using partimage on the linux partition only. What do you suggest? Installing grub on the linux partition?

About point 5) in the procedure above why using ghost instead of partimage? What kind of settings do I have to care of when cloning windows? I guess license and other stuff should be fixed on every pc. Could you point me to some docs about that?

Thanks

---

