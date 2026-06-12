---
title: "how do i modify where grub installs?"
date: 2013-02-24
forum: Installation &amp; Upgrades
---

### Post by americancliche on 2013-02-24
I have a raid set up 1Tb (500Gb x2) HP Envy 17. I have an Ubuntu 12.10 Live CD that i am attempting a clean install on. The installation goes great until it goes to install grub onto /dev/sda. When i do a boot repair, i have four different /dev/(insert name here). to be honest I dont know which one I should install the grub on, or even how to change it when i go to install in the first place. As far as I can tell SDA is a location that Ubuntu just imputs and hopes exists because it doesnt on my system, nor does SDB. If someone could A. tell me how to correctly select where to install my GRUB during install, and how to automatically do that I would be grateful. Option B is to tell me how to manually install it thru the GRUB GNU. 
A couple of other things, I have NO experience in Linux, so please if you help me, break it down as simple as possible. Im in infancy as far as this is concerned. 

When I get the Executing 'grub-install/dev/sdta' failed.  This is a fatal error box, I hit OK. This takes me to the  "Bootloader Install failed" box, which asks me how to proceed, to which i can "Choose different device to install", Continue without bootloader, or Cancel Install.  As soon as i choose another device which I have the option of about 9; the "okay" box is no longer clickable so it doesnt give let me change the device from there.

Thats about all I guess. If you need more info, Its not difficult for me to replicate this.

Also I can screen shot my entire process if anyone wants to key me on how to Screen Shot in Ubuntu.

---

### Post by Laiquendi on 2013-02-24
To determine where you want to istall GRUB, try running in a terminal in* try linux* mode on live cd:
```
df -h
```which will show you your partitions/discs.
Having partitions like *xyz1* (and other numbers) means that you have *xyz* disc.
It is usually ok to put grub in the first disc.

To screen shot simply press the screenshot key on your keybord :)

---

### Post by darkod on 2013-02-24
If that is a fakeraid device, which is most common, the raid array itself and the partitions on it will be named like /dev/mapper/blahblah_VolumeX or similar.
The partitions would have the same name but will end with one more number to specify the partition number, or with 'pX'.

In fakeraid, the device for the bootloader installation is the array itself. So, you need to compare the /dev/mapper/... device and "strip down" the partition designator at the end, so that you have the array name, not a partition. In most cases it would end with 'Volume' or 'Volume0'.

That is the grub2 destination.

During install you can specify the grub destination if you use the manual method. If you use the auto method to install it might try /dev/sda first and fail, when it asks you where to install you should be able to specify the array.

If you don't know the array name, you can always check it first from live mode (Try Ubuntu) option. Open terminal and activate the array with:
```
sudo dmraid -ay
```

That will show the activated devices (the array and partitions). Compare them and you have the array name that you need.

---

### Post by americancliche on 2013-02-24
Somehow last night while incredibly tired and frustrated with the whole process I split my TB into 2 partitions. 1 is 256Mb, the other is the remainder. 

'RAID set "isw_eaijcjjffg_RAID-0" already active
RAID set "isw_eaijcjjffg_RAID-0p1" already active
RAID set "isw_eaijcjjffg_RAID-0p5" already active'

Describes what I imagine is the array? and the 2 partitions? Im not sure. RAID-0p5 is the larger partition and 0p1 is the smaller. IF anyone can describe how to make that into one partition. Thats not incredibly important to me at this point, but I am now stuck where the installer (manual mode says) "No Root File system

---

### Post by darkod on 2013-02-24
The two partition p1 and p5 are normal. The default install is one root partition and one smaller swap partition. The p1 is root and p5 is swap.

If you want to set up manually on existing partitions, when you reach the partitioning stage, select the p1 partition, hit the Change button below. Then set the Use As to ext4 (filesystem), mount point as /, tick the format box to delete the existing installation.

But if only grub2 failed, you should be able to add it from live mode, no need to reinstall. In that case, from live mode in terminal, it would be like:
```
sudo mount /dev/mapper/isw_eaijcjjffg_RAID-0p1 /mnt
sudo grub-install --root-directory=/mnt /dev/mapper/isw_eaijcjjffg_RAID-0
```

That will use the p1 partition as parameter (so that grub-install knows where is root) and install grub2 to the array MBR (mote the second command doesn't have the p1 in the array device name).

Reboot and see if that helps.

---

### Post by americancliche on 2013-02-24
The 0p1 partition is the smaller partition of 256Mb. wouldnt that then be the swap partition?  and 0p5 which is 994GB  be the root partition? I tried putting up a screen shot but it wont upload ping. Im going to try your suggestion for just root2. see if that solves it. and if so cheery-oh!

---

### Post by darkod on 2013-02-24
OK, in that case use the 0p5 in the first command, you are right.

---

### Post by americancliche on 2013-02-24
Okay so, if i type in line one, and press enter of that code (while swapping 0p1 to 0p5) it replies with
> mount: unknown filesystem type 'LVM2_member'

---

### Post by americancliche on 2013-02-24
What if i wiped my partitions, disabled my RAID array, and installed on one of my drives, could I use the other drive as like an internal extra HDD like an external usually works?

---

### Post by presence1960 on 2013-02-24
> **americancliche said:**
> What if i wiped my partitions, disabled my RAID array, and installed on one of my drives, could I use the other drive as like an internal extra HDD like an external usually works?

Absolutely. I have on my desktop machine a 250 GB for OSs, 1 TB for data, 1 TB for backups, 500 GB for images of my desktop OSs, my daughter's desktop OSs and our laptop OSs. All of them are internal Seagate disks.

P.S. Before installing after wiping the disks boot to Live CD/USB desktop and check that those goofy partition names are gone.  open gparted.  If you get a drive with a funny name like nvidia_ahahdhjdfsjkf then you have mounted a raid drive that you don't want.

To get rid of it, Open a terminal and type ```
dmraid -E -r /dev/sdX
``` 
Note you want the disk name not the partition name.  You can see your disk names in gparted.

---

### Post by americancliche on 2013-02-25
I dont know what magic I did, but i suspect it was when I unlocked the 0p-1 and deleted it using the partition editor, and then I restarted the computer, and instead of selecting "try ubuntu" i just went to install, and did a erase everything and install ubuntu 12.1 and viola! 
So thanks for that. now I dont need that dumb disc. My pc was running hot as the Sahara until i downloaded "Jupiter". Next thing to do is find a way to appropriately switch between my GPU's. Alas I spose that is another thread in itself. Thanks so much for the help. Ultimately the information you gave me I believe may have been the start to my solution

---

### Post by presence1960 on 2013-02-25
> **americancliche said:**
> I dont know what magic I did, but i suspect it was when I unlocked the 0p-1 and deleted it using the partition editor, and then I restarted the computer, and instead of selecting "try ubuntu" i just went to install, and did a erase everything and install ubuntu 12.1 and viola! 
So thanks for that. now I dont need that dumb disc. My pc was running hot as the Sahara until i downloaded "Jupiter". Next thing to do is find a way to appropriately switch between my GPU's. Alas I spose that is another thread in itself. Thanks so much for the help. Ultimately the information you gave me I believe may have been the start to my solution

Enjoy Ubuntu!

---

