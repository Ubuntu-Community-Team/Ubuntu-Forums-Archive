---
title: "Adding Older HDD to Fstab and Won't boot"
date: 2019-04-14
forum: Installation &amp; Upgrades
---

### Post by snowmanner on 2019-04-14
Hey I have been adding a Hdd that I had in the computer when it was a windows computer. I got to add this line to fstab and won't boot with the line added on.

UUID=177c797f-3c11-4d6e-8e8c-aeda02cbdd8d /home/Data_Drive [COLOR=#333333][FONT=UbuntuMono]ntfs-3g  auto,users,uid=1000,gid=100,dmask=027,fmask=137,utf8  0  0

the drive is ntfs and this is the info from when I do blkid and check the disk info

[/FONT][/COLOR]/dev/sdc1: LABEL="Data Drive" UUID="1A806E65806E477B" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="177c797f-3c11-4d6e-8e8c-aeda02cbdd8d"




 *-disk
       description: ATA Disk
       product: ST2000DM001-1ER1
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdc
       version: CC25
       serial: Z4Z3X7B7
       size: 1863GiB (2TB)
       capabilities: gpt-1.00 partitioned partitioned:gpt
       configuration: ansiversion=5 guid=b553bd34-840e-4527-b210-78ab7611768e logicalsectorsize=512 sectorsize=4096


Is there something I am doing wrong?

---

### Post by oldfred on 2019-04-14
Is this a mount point you created first? 
/home/Data_Drive

Did you copy fstab entry and leave an extra space in utf8 or is that the issue?
[COLOR=#333333][FONT=UbuntuMono]fmask=137,[/FONT][/COLOR][COLOR=#ff0000][FONT=UbuntuMono]ut  f8
[/FONT][/COLOR][FONT=UbuntuMono]
I have seen this as good parameters for NTFS:[/FONT][COLOR=#ff0000][FONT=UbuntuMono]
[/FONT][/COLOR][COLOR=#ff0000][FONT=UbuntuMono]       [/FONT][/COLOR] defaults,nls=utf8,umask=000,uid=1000,windows_names 
            [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336) 
    
[COLOR=#ff0000][FONT=UbuntuMono][/FONT][/COLOR][FONT=UbuntuMono][/FONT][COLOR=#333333][FONT=UbuntuMono][/FONT][/COLOR]

---

### Post by snowmanner on 2019-04-14
Ya I did make the directory "/home/Data_Drive" and the space is not supposed to be there. I will try again and see if that I am adding that space on accident.

when I made the directory it is in the home directory for the account.  Is that the right location for that string" /home/Data_Drive"?

---

### Post by snowmanner on 2019-04-14
o.k I tried and correcting it and used a copy of the template on the link. That unfortunately did not work. I keep getting an error for "IDM_parsetocblock(): CANNOT FIND TOCBLOCK, database might be corrupted.

---

### Post by snowmanner on 2019-04-14
Well, as long as that line is not put in it does not go to maintenance console.

---

### Post by Dennis N on 2019-04-14
> when I made the directory it is in the home directory for the account. Is that the right location for that string" /home/Data_Drive"?
No, if you added Data_Drive in your home folder, then to mount a file system there you need **/home/user/Data_Drive** in the /etc/fstab line. Put your user name in place of 'user'.

---

### Post by snowmanner on 2019-04-14
I am trying with this

UUID=177c797f-3c11-4d6e-8e8c-aeda02cbdd8d /home/admin/Data_Drive [COLOR=#000000]defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0

I am still having that issue. [/COLOR]

---

### Post by yancek on 2019-04-14
In addition to the suggestions above, I would try changing the UUID in fstab from the current entry to what blkid output shows:   1A806E65806E477B

---

### Post by snowmanner on 2019-04-14
I was able to get in contact with the one hosting the server and he went on the gui and fixed it and seems to be that the shortened one Yancek suggested worked.

---

