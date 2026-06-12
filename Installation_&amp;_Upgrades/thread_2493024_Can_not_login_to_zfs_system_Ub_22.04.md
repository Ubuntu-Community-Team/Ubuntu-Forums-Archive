---
title: "Can not login to zfs system Ub 22.04"
date: 2023-11-30
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2023-11-30
I tried to login today into my zfs system. There is a fault that was not there before.  Ubuntu 2204 does load but a number of programs are missing such as new Software and firefox and can not be run. Thunderbird is showing as an available app. I opened it and it is showing all emails.

The zfs system was installed within Ubuntu 22.04 and has been working ok for a number of months.

The hard drives are accessible, but the nvme0n1 drive is not loading properly.  It has 4 partitions. The following are the partition numbers:

1 =fat 32 mounted ok into /boot/efi

2= Unknown fs  flag=swap 2gib

(Gparted indicates possible reasons that the system is not fully detecting some of the partitions on tnvmeon1   unable to detect file system. The three  most likely reasons are there is  no filesystem  available  to gparted , or unformulated or device entry missing 

Disks indicate p2 is a linux swap.)

3=zfs bpool 2gib
4= zfs rpool 927gib
(Disks  indicates for both 3 and 4 contents unknown (zfs member 5000) not mounted. Partition type Solaris Boot.I am the only user of the desktop. I am surprised that admin is allocated to member 5000, Is this standard?)

How should I proceed to restore full access to p2 and p4 without a fresh install. Currently I am running Ubuntu 22.04 off a usb stick.

Robin

---

### Post by MAFoElffen on 2023-11-30
Please run the system-info script from my signature line. When you go to start the script, do it like this
```

./system-info --details

```

---

### Post by Robbyx on 2023-12-01
I ran the following command:

wget -N -t 5 -T 10 [https://github.com/UbuntuForums/system-info/raw/main/system-info](https://github.com/UbuntuForums/system-info/raw/main/system-info) && chmod +x system-info && /system-info

I had difficulty in following your instructions so as to  get the output  file uploaded to this conference. II tried a few times to follow your instruction "to run the system-info script from my signature line". It took me to the github page but did not cause the system -info file  to be uploaded. As a compromise I went ahead with the command line: wget -N -t 5 -T 10 [https://github.com/UbuntuForums/system-info/raw/main/system-info](https://github.com/UbuntuForums/system-info/raw/main/system-info) && chmod +x system-info && /system-info. This produced a system-info file in my home directory. 

At this stage how can I upload the file for your attention?

PS I run the script from a live usb. Is that ok. Will the script look beyond what is on the usb to the installed but not running desk top system?

---

### Post by Robbyx on 2023-12-02
I think I have been able to upload the report you asked for. Its reference is  [https://termbin.com/cd7h](https://termbin.com/cd7h).

I had a look at the report and it seems all drives on the system are reviewed. If you need other information please ask. 
In the meantime I thank you  for your help. 

Robin

---

### Post by MAFoElffen on 2023-12-02
Robin...

When you try to boot, when it gets past the grub2 menu, it will go to a black screen, then splash screen right? On those screens, hit the <Down-Arrow> key and watch the boot messages...

Do you see any errors? Where does that stop at?

---

### Post by Robbyx on 2023-12-03
I realise now that I put misleading subject heading to this thread.  

As I stated in the body of that first post,  I can login, but partitions p3 and p4 are not loading. 

Following your advice I confirm that there were no error messages when starting the  system. As mentioned in the first posting, the desktop does load, but there are missing apps including firefox.  

Is the failure to mount p3 and p4  (see posting 1)  due to zfs user  number 5000 not being  recognised. If so how do I change it and to what?

---

### Post by MAFoElffen on 2023-12-03
How do you not mount partitions 3 & 4 (bpool & rpool), but still boot? Is there more than one installed Ubuntu system there?

Does the boot dump you to a root maintenance prompt? Does it dump you to an initramfs prompt? Does the graphics not start and go to a console prompt? Does it go to a graphical login, and do a login loop?

You say is does not recognise "zfs user 5000" take a photo (or video if it scrolls by) of that from your phone and post it as an attachment or a link to it posted somewhere...

For that, i need you to rerun the report... with the differnt starup option that I asked you to do. Go to where you downloaded the script and do
```

./system-info --details

```

---

### Post by Robbyx on 2023-12-03
Your hunch was correct.

I had been changing the bios to ensure that the desired boot disk is first presented. So if the usb stick is to be the boot disk I made sure it was the first option. Likewise if the nvme was to be the boot disk I would bring it to the fore in the boot disk order list. . When running the nvme drive I left the usb stick in the usb slot. It was the second option and I had done that many times before in ubuntu  with my old MB. For reasons not clear leaving the usb stick plugged in even though the primary boot disk was set at the nvme, in caused my problems. I removed the usb drive and the computer booted correctly without the error messages to which I refer in the first posting here. 

I had to reinstall Firefox and for that I used flatpak. Snap said it was already installed even though it was not opening.  FF is now working but at present I can not get it to use  the old history, installed addons, or bookmarks!. I presume  it has created a new profile. I will check that next.

Thank you for your help and support,

Robin

---

### Post by MAFoElffen on 2023-12-03
You are welcome. Glad all things worked out.

So now you can mark this as "Solved" right?

---

