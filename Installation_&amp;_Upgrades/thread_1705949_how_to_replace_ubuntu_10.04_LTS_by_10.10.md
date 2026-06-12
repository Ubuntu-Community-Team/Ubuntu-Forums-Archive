---
title: "how to replace ubuntu 10.04 LTS by 10.10"
date: 2011-03-13
forum: Installation &amp; Upgrades
---

### Post by kukkoo75 on 2011-03-13
dear friends,
I have vista and ubuntu 10.04 LTS loaded on my disk. i upgraded to ubuntu 10.04 LTS from the earlier version, after that i started using MTS Mblaze usb broadband stick as wired connections were not available. In order to get my usb stick working i messed up the ubuntu settings and now even wired connections are not working. i am frustrated and would like to replace it with 10.10 as it has MTS Mblaze default settings. In any case i never like the look and feel of 10.04 as compared to earlier versions. I have made the bootable CD for 10.10, but now how do i go about installation so as to replace 10.04.
I do not want to disturb my vista as there is lot of crucial data.

thanks for your help
kukkoo

---

### Post by Hedgehog1 on 2011-03-13
kukkoo75,

This is possible.  It can even be 'easy' *IF* you have your '/home' directory in it's own partition.

So we need to get a look at your disk partition layout to guide you.  From Ubuntu, please:

In the Terminal (Menu to: Applications >> Accessories >> Terminal), please run this command:  (the -'l' is a lower case 'L')
```
sudo fdisk -l
```
Then copy the text from the output and paste it into your next post.

***The Hedge***

:KS

---

### Post by molond on 2011-03-13
try this website 
[http://hubpages.com/hub/Ubuntu-Offline-Upgrade](http://hubpages.com/hub/Ubuntu-Offline-Upgrade)
it is upgrading for slow internet
you need the ALTERNATIVE NOT DESKTOP iso, i recommend asking connical to send it to you but you can download the 700mb iso off their site.
this method reduced my download from 800mb to 50mb when installing.
the site claims it will update standard, WUBI, Alpha, Beta and RC.
i have only tried it on wubi and it worked.

---

### Post by kansasnoob on 2011-03-13
Before using the Ubuntu 10.10 live-installer I'd particularly warn you of changes, in particular this bug as mentioned in the release notes:

> In dual boot installs, side-by-side partitioning can be overridden by the user, resulting in data loss. After selecting the "Install alongside other operating systems" option, clicking on either the "Use entire partition" of "Use entire disc" buttons will override the side-by-side partitioning and result in a loss of data.

[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Boot,%20installation,%20upgrade%20and%20post-install](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Boot,%20installation,%20upgrade%20and%20post-install)

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/655950)

I went into some detail describing changes/bugs here in post #1 and post #15:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

---

### Post by kukkoo75 on 2011-03-14
> **Hedgehog1 said:**
> kukkoo75,

This is possible.  It can even be 'easy' *IF* you have your '/home' directory in it's own partition.

So we need to get a look at your disk partition layout to guide you.  From Ubuntu, please:

In the Terminal (Menu to: Applications >> Accessories >> Terminal), please run this command:  (the -'l' is a lower case 'L')
```
sudo fdisk -l
```Then copy the text from the output and paste it into your next post.

***The Hedge***

:KS
hedge, thanks
i ran the command and here is the output
  Disk /dev/sda: 250.1 GB, 250059350016 bytes
    255 heads, 63 sectors/track, 30401 cylinders
    Units = cylinders of 16065 * 512 = 8225280 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disk identifier: 0xc1451210
     
   
     Device Boot      Start         End      Blocks   Id  System
    /dev/sda1               1        1298    10424320   27  Unknown
    /dev/sda2   *        1298       15958   117757112    7  HPFS/NTFS
    /dev/sda3           15959       28493   100685820    7  HPFS/NTFS
    /dev/sda4           28494       30401    15326010    5  Extended
    /dev/sda5           28494       30315    14635183+  83  Linux
    [SIZE=2][FONT=&quot]/dev/sda6           30316       30401      690763+  82  Linux swap / Solaris

@molond, thanx but that is not what i am looking for.
@kansas, thanx for the advice, i will keep that in mind.
[/FONT][/SIZE]

---

### Post by kukkoo75 on 2011-03-15
dear hedge,
i am waiting for reply
kukkoo

---

### Post by Hedgehog1 on 2011-03-15
> **kukkoo75 said:**
> [SIZE=1]hedge, thanks[/SIZE]
[SIZE=1]i ran the command and here is the output[/SIZE]
[SIZE=1]Disk /dev/sda: 250.1 GB, 250059350016 bytes[/SIZE]
[SIZE=1]255 heads, 63 sectors/track, 30401 cylinders[/SIZE]
[SIZE=1]Units = cylinders of 16065 * 512 = 8225280 bytes[/SIZE]
[SIZE=1]Sector size (logical/physical): 512 bytes / 512 bytes[/SIZE]
[SIZE=1]I/O size (minimum/optimal): 512 bytes / 512 bytes[/SIZE]
[SIZE=1]Disk identifier: 0xc1451210[/SIZE]
 
 
[SIZE=1]Device Boot Start End Blocks Id System[/SIZE]
[SIZE=1]/dev/sda1 1 1298 10424320 27 Unknown[/SIZE]
[SIZE=1]/dev/sda2 * 1298 15958 117757112 7 HPFS/NTFS[/SIZE]
[SIZE=1]/dev/sda3 15959 28493 100685820 7 HPFS/NTFS[/SIZE]
[SIZE=1]/dev/sda4 28494 30401 15326010 5 Extended[/SIZE]
[SIZE=1]/dev/sda5 28494 30315 14635183+ 83 Linux[/SIZE]
[FONT=&quot][SIZE=1]/dev/sda6 30316 30401 690763+ 82 Linux swap / Solaris[/SIZE][/FONT]

 
kukkoo75,
 
Your current partition layout for ubuntu is:
 
[SIZE=1]/dev/sda4 28494 30401 15326010 5 Extended[/SIZE]
[SIZE=1]__/dev/sda5 28494 30315 14635183+ 83 Linux[/SIZE]
[FONT=&quot][SIZE=1]__/dev/sda6 30316 30401 690763+ 82 Linux swap / Solaris[/SIZE][/FONT]
 
Because you have only one partition for Ubuntu (sda5) both your data and the OS are all mixed together.
 
You have two choices for a clean install:
 
Steps of choice one:
 
1) Backup your '**/home' **data to an extenal drive or DVD(s)
2) Us the manual configuration option when installing 10.10, and assign sda5 as your **'/'** location, and check mark it for formatting.
 
Steps of choice two:
 
1) Create a seperate parititon for you **'/home**' and move your data into it.
Here is a link on how to do that: [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving) the new partition would be called sda7
2) Us the manual configuration option when installing 10.10, and assign sda5 as your **'/'** location, and check mark it for formatting.
3) Assign sda7 as your **'/home'**, but **_DO NOT check mark it for formatting_**. Your data lives there and you want it left alone.
 
 
If you do choice #2, future upgrades/downgrades of Ubuntu  will be much easier.
 
But it is your PC and your choice.
 
***The Hedge***
 
:KS

---

### Post by Hedgehog1 on 2011-03-15
Once you have backed up your data, and/or moved your '**/home**' directory to it's own partition, this is where you choose the manual setup:

[IMG]http://img705.imageshack.us/img705/2588/hp4partitions09.png[/IMG]

If you have choosen not to make a seperate partition for your **/home**, you want to setup **sda5** & **sda6** like you see here:

[IMG]http://img857.imageshack.us/img857/6342/hp4partitions13.png[/IMG]

The above picture has sda3 at the extended partition.  In your case, sda4 is the extended partition.

Also, your boot loader should be the default **/dev/sda** (like you see in the picture)  - not sda1,2,3,4,5 - **just /dev/sda**.

***The Hedge***

:KS

---

### Post by kukkoo75 on 2011-05-28
thanks Hedge,
ultimately i could do it, thanks to your invaluable advice, i have followed the second option and things should be smooth now.

regards

---

