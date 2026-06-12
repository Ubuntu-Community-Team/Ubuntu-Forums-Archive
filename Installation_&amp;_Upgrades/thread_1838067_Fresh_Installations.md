---
title: "Fresh Installations"
date: 2011-09-02
forum: Installation &amp; Upgrades
---

### Post by nipunshakya on 2011-09-02
Hi there folks, i have been using Windows 7 since the day it released. Now i want to taste Ubuntu. Recently i downloaded the ubuntu 11.04 amd64 on my dell inspiron 1440 laptop (solely a 64-bit machine). Using wubi, i tried to install the ubuntu 11.04 amd64. But i failed(Problem no 1.). Then i tried to install ubuntu 11.04 i386 and it did install. Now i got confused:confused: here : when i tried to install windows xp couple of months back, it showed a blue screen error, and the technician said my that its due to switching from 64 bit back to 32 bit....but isn't ubuntu 11.04 i386 a 32-bit thing?? (problem no. 2).

Here's how my partitions are: got a c: for windows(60gb) , b: for linux only(60 gb) and rest 177 gb as drive e: for backup. i realised that b: can also be used to store other datas and documents like drive e: . :confused:
next, i would hate to see that there is ubuntu listed on the "add/remove programs" options on the control panel. so what i wanna do is i want to remove windows totally and make a fresh installation of my ubuntu 11.04 amd64 if possible(problem no. 3) coz i hate crashes in windows 7. 

So, any guide regarding ubuntu installation or any suggestions would be helpful....i really would like to get a knowledge on grub, kernel thing...and other stuffs related to ubuntu... 

Regards, NeptuneTech:)

---

### Post by 2F4U on 2011-09-03
Did you already look at the official installation document?

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

problem no. 2: Ubuntu is available in 32 and 64 bit. Just download the appropriate installation cd

problem no. 3: If you want to remove Windows completely, this can be done by installing from one of the install cd's and tell the installer to use the entire hard disk.

---

### Post by sidzen on 2011-09-03
[SIZE=2]"  . . . so what i wanna do is i want to remove windows totally and make a fresh  installation of my ubuntu 11.04 amd64 if possible(problem no. 3) coz i  hate crashes in windows 7."

[System Rescue CD]("http://sourceforge.net/projects/systemrescuecd/files/sysresccd-x86/2.3.0/systemrescuecd-x86-2.3.0.iso/download") -- download and burn to CD at no more than 8X

Get to multi-colored prompt after hitting *default *(Enter) a couple times[/SIZE]
NOTE: page will ask User to enter either "wizard" or "startx"
[SIZE=2]Enter the command

[/SIZE][PHP]dd if=/dev/zero of=/dev/sda bs=4096 conv=notrunc,sync[/PHP]

[SIZE=2]After this is done (it will take a while, so go do something for about half hour and check back),
type [/SIZE][PHP]startx[/PHP][SIZE=2] which will bring up a yellow-colored terminal.  In this terminal type and enter[/SIZE] [PHP] gparted
[/PHP]  [SIZE=2]and partition the hdd, which is now completely wiped with zeros, containing no nasty NTFS.

Best wishes![/SIZE]

---

### Post by nipunshakya on 2011-09-03
> **2F4U said:**
> 

problem no. 2: Ubuntu is available in 32 and 64 bit. Just download the appropriate installation cd

 
thanks for the link....i would be following its steps.....and btw what i meant by my 32/64 bit problem was that my machine is a 64 bit machine...no doubt...but why doesn't it install ubuntu 11.04 amd64?? rather it installs i386 which is 32-bit os.....really confused about that...because i used wubi for installing both one after another...but only i386 got installed....any idea mate?

---

### Post by nipunshakya on 2011-09-03
> **sidzen said:**
> [SIZE=2]"  . . . so what i wanna do is i want to remove windows totally and make a fresh  installation of my ubuntu 11.04 amd64 if possible(problem no. 3) coz i  hate crashes in windows 7."

[System Rescue CD]("http://sourceforge.net/projects/systemrescuecd/files/sysresccd-x86/2.3.0/systemrescuecd-x86-2.3.0.iso/download") -- download and burn to CD at no more than 8X

Get to multi-colored prompt after hitting *default *(Enter) a couple times[/SIZE]
NOTE: page will ask User to enter either "wizard" or "startx"
[SIZE=2]Enter the command

[/SIZE][PHP]dd if=/dev/zero of=/dev/sda bs=4096 conv=notrunc,sync[/PHP][SIZE=2]After this is done (it will take a while, so go do something for about half hour and check back),
type [/SIZE][PHP]startx[/PHP][SIZE=2] which will bring up a yellow-colored terminal.  In this terminal type and enter[/SIZE] [PHP] gparted
[/PHP]  [SIZE=2]and partition the hdd, which is now completely wiped with zeros, containing no nasty NTFS.

Best wishes![/SIZE]

mate, i really appreciate your help but if i do all those now, i really won't be able to understand what i am doing now...and i dont mind myself calling a noob in ubuntu here...im in a learning phase...so please, details would be helpful......and i appreciate ur help..
thanks:P

---

### Post by bcbc on 2011-09-03
You can install either 32-bit or 64-bit ubuntu on a 64-bit computer. The reason it failed to install 64-bit? No idea, but could have been a bad burn on the CD? If you want to try it again and the post your log file, we can see. But there's really no point if you want to setup Ubuntu as your ONLY operating system.

As for sidzen's advice, there really is no reason to waste your time writing /dev/zero to your entire drive. It's pointless. 

If you want to install Ubuntu as your only OS, then burn an Ubuntu CD (check it), boot from it, and install it and select your entire drive.

I recommend dual booting - especially if you're new to Ubuntu, but obviously you can do as you wish. Here's a dual booting guide though: [http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

### Post by nipunshakya on 2011-09-03
> **bcbc said:**
> You can install either 32-bit or 64-bit ubuntu on a 64-bit computer. The reason it failed to install 64-bit? No idea, but could have been a bad burn on the CD? If you want to try it again and the post your log file, we can see. But there's really no point if you want to setup Ubuntu as your ONLY operating system.

As for sidzen's advice, there really is no reason to waste your time writing /dev/zero to your entire drive. It's pointless. 

If you want to install Ubuntu as your only OS, then burn an Ubuntu CD (check it), boot from it, and install it and select your entire drive.

I recommend dual booting - especially if you're new to Ubuntu, but obviously you can do as you wish. Here's a dual booting guide though: [http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")

Ya u were right regarding bad burn on the CD. i had it messed up with my first burn of Ubuntu 11.04 amd64. i figured that out....

I think im gonna follow the tutorials prescribed in the link u  sent...i might be enjoying my dual boot now and then.....but one thing if u could make me clear, please see the image below and tell me what does that 18gb fine mean...and what does that root.disk mean.....my laptop has 320 gb HDD while only those in image 1 (299 gb. approx.)are in action.....still no idea about the missing 20gb(approx.)

---

### Post by Hakunka-Matata on 2011-09-03
> **NeptuneTech said:**
> Ya u were right regarding bad burn on the CD. i had it messed up with my first burn of Ubuntu 11.04 amd64. i figured that out....

I think im gonna follow the tutorials prescribed in the link u  sent...i might be enjoying my dual boot now and then.....but one thing if u could make me clear, please see the image below and tell me what does that 18gb fine mean...and what does that root.disk mean.....my laptop has 320 gb HDD while only those in image 1 (299 gb. approx.)are in action.....still no idea about the missing 20gb(approx.)

Thumbnail 1 shows the third partition as 64GB NTFS, Linux install wants and EXT4 partition type, not NTFS.  Once you get booted to your LiveCD, use gparted to change that.

---

### Post by nipunshakya on 2011-09-03
^^^^^^ Sir, i had used Wubi to install the current version 11.04 to run on my laptop because i had no idea what ext2, dev, etc meant.I wanted to learn ubuntu and so found this easy way to install. And since windows uses NTFS partition , i installed it in a seperate D:(64gb space) just to make sure i get enough space for my ubuntu expansion and upgrades....but i didnt know that the OS would be installed onto the drive as just an application and could be removed from the Add/Remove Programs feature available in Windows. Im getting a slow pace on understanding the terminals and still in absolute beginner phase.  This installation was an experiment for me to learn how ubuntu works...now that im into it, i think bcbc 's suggestions regarding dual boot would work fine.  

Could you please tell me what the 18 gb allocated in the 2nd thumbnail indicate?? can it be reformatted  and will this formatting harm my laptop? I guess it hasnt been mounted to anywhere and ofcourse, none of my OS(windows 7 nor ubuntu ) could detect this space until i ran the disk utility feature of ubuntu....can this space regained?

---

### Post by Hakunka-Matata on 2011-09-03
18 GB File, root,disk **A Peripheral Device**
It is an external drive, a usb portable hard drive maybe?,
or a large ssd style memory card plugged into the side of your computer???
IT is physically not part of your 320 GB drive.
yes, go away from WUBI, it's good to "test drive" Ubuntu, but a dual boot works much better, is fast, snappy, and does not crash because of Windows.

---

### Post by bcbc on 2011-09-03
The 18GB root.disk is the Wubi install's virtual disk. This is a file (under windows you can find it as \ubuntu\disks\root.disk) that is loop mounted (a [loop device]("http://en.wikipedia.org/wiki/Loop_device")).

So you don't have to worry about it. If you uninstall Wubi it will be gone. 

You don't need to partition to install Wubi - it doesn't care that you made a separate 'drive' for it - and all it will use is that virtual disk (the size you specified during the installation).

Please output the following (lower case -L):
```
sudo fdisk -l
```

(Use the ```
 tags to enclose the output when you post it here (press # above))

While you're at it, also give the output of:
[CODE]df -h
```

---

### Post by Hakunka-Matata on 2011-09-03
Thanks bcbc, another piece to the puzzle.  You taught me something this morning.  Is this OP wanting to install to Wubi?,

---

### Post by nipunshakya on 2011-09-03
> **bcbc said:**
> The 18GB root.disk is the Wubi install's virtual disk. This is a file (under windows you can find it as \ubuntu\disks\root.disk) that is loop mounted (a [loop device]("http://en.wikipedia.org/wiki/Loop_device")).

So you don't have to worry about it. If you uninstall Wubi it will be gone. 

You don't need to partition to install Wubi - it doesn't care that you made a separate 'drive' for it - and all it will use is that virtual disk (the size you specified during the installation).


I thought of the drive as the same,....i am happy with my guess...:) but sorry i uninstalled wubi because im going to install fresh copy of ubuntu and use it as dual boot along side windows 7. thanks for your help....:P i appreciate it

Regards, NeptuneTech

---

### Post by bcbc on 2011-09-03
> **Hakunka-Matata said:**
> Thanks bcbc, another piece to the puzzle.  You taught me something this morning.  Is this OP wanting to install to Wubi?,

No prob... best way to figure out Wubi is to play with it (it doesn't hurt - however it does require Windows ;) ). Also I find that the disk utility is pretty confusing at the best of times.

The OP has already installed with Wubi, but wants a proper (partition) install of Ubuntu.

---

### Post by bcbc on 2011-09-03
> **NeptuneTech said:**
> I thought of the drive as the same,....i am happy with my guess...:) but sorry i uninstalled wubi because im going to install fresh copy of ubuntu and use it as dual boot along side windows 7. thanks for your help....:P i appreciate it

Regards, NeptuneTech

You're welcome :) Enjoy!

PS check if you already have 4 primary partitions. If you do the installer won't be able to automatically dual boot. In that case you can remove one and then create an extended partition in that space. (That's why I wanted to see the 'fdisk' output). Anyway - that link I provided has in-depth details of how to partition and install (with screenshots) - so you can figure it all out from there. Good luck.

---

### Post by nipunshakya on 2011-09-03
> **bcbc said:**
> 
The OP has already installed with Wubi, but wants a proper (partition) install of Ubuntu.

What does that even mean? please be clear here....:confused::confused::confused:

---

### Post by bcbc on 2011-09-03
> **NeptuneTech said:**
> What does that even mean? please be clear here....:confused::confused::confused:

OP = original poster = you

I was saying that you had already installed Ubuntu with Wubi, but wanted to switch to a proper Ubuntu install - direct to partition.

That was in response to Hakunka-Matata asking: *Is this OP wanting to install to Wubi?*

---

### Post by nipunshakya on 2011-09-03
> **bcbc said:**
> OP = original poster = you

I was saying that you had already installed Ubuntu with Wubi, but wanted to switch to a proper Ubuntu install - direct to partition.

That was in response to Hakunka-Matata asking: *Is this OP wanting to install to Wubi?*

Oh yes yes!! sorry for misunderstanding...since i began posting lately, i don't really have the ideas of abbreviations working around here....

n btw i have just uninstalled wubi, haven't installed lunux with a fresh copy yet as i am grabbing some ideas from the link you have given....seems like those tutorials are more than sufficient to understand installation process:):):)
my partitions like the following....guess that should work....

---

### Post by bcbc on 2011-09-03
> **NeptuneTech said:**
> Oh yes yes!! sorry for misunderstanding...since i began posting lately, i don't really have the ideas of abbreviations working around here....

n btw i have just uninstalled wubi, haven't installed lunux with a fresh copy yet as i am grabbing some ideas from the link you have given....seems like those tutorials are more than sufficient to understand installation process:):):)
my partitions like the following....guess that should work....

It's my fault for using abbreviations ;)

That partition setup looks good. If you only have 3 you could replace the big Ubuntu one with an extended (or just deleting it and making the space will let the installer create an extended. The guide should explain it best.)

---

### Post by sidzen on 2011-09-04
> **NeptuneTech said:**
> mate, i really appreciate your help but if i do all those now, i really won't be able to understand what i am doing now...and i dont mind myself calling a noob in ubuntu here...im in a learning phase...so please, details would be helpful......and i appreciate ur help..
thanks:P

When I was a n00b I just cut and pasted, then learned by doing and reading up.
To quote:  "It's easier to act your way into a new way of thinking than to think your way into a new way of acting."

Download a PDF file[* Linux Command Lin*]("http://sourceforge.net/projects/linuxcommand/files/TLCL/09.12/TLCL-09.12.pdf/download")e, if interested

Best wishes!

---

### Post by nipunshakya on 2011-09-04
i look forward for your support guys, and i am heartily thankful that i choose to ride a powerful beast called Linux.... hope i shall be enjoying the ride....i shall thoroughly go through all the suggestions you guys have been imparting on me and shall create a clear vision on your teachings....


Thanks bcbc and sidzen with all my heart...
Regards, NeptuneTech

---

### Post by sidzen on 2011-09-04
> **NeptuneTech said:**
>  . . . Thanks bcbc and sidzen with all my heart...
Regards, NeptuneTech

You are welcome, and come back!

---

### Post by ramartz on 2011-09-04
I'm also on the process of migrating to Ubuntu and this thread helps a lot to prepare what needed to be done.. 

just wanted to say thanks as well.. keep it up! :)

---

### Post by nipunshakya on 2011-09-04
^^^^Keep it coming buddy and if your problems or anything related to installation relates similar to mine, write it down here....maybe we might end up with same results....:)

---

### Post by nipunshakya on 2011-09-04
> **bcbc said:**
>  Anyway - that link I provided has in-depth details of how to partition and install (with screenshots) - so you can figure it all out from there. Good luck.

Reading the link you sent, i came up with this conclusion : 
1. I need a ext4 partition with a "/" as a mount point and
2. need a swap area of size of my RAM. 
so far so good understanding the tutorial....and now i guess i will stick to my partition plan (see image 1) and go for the 178 gb to install my ubuntu after i make it a free space and repartition it in favor of ubuntu(as points 1 and 2). Just curious, but am i going the right way?

And another question, Boot Loader "what does the device for boot loader" mean? (refer image 2)?. Does that Boot Loader have more options in its dropout ? i am sorry if its totally a foolish question but it came to my mind due to curiosity....i have finished the detailed studies and so think of going for installation....and need a final verdict regarding my setup plans....

Regards, NeptuneTech

---

### Post by Hakunka-Matata on 2011-09-05
> **NeptuneTech said:**
> Reading the link you sent, i came up with this conclusion : 
1. I need a ext4 partition with a "/" as a mount point and
2. need a swap area of size of my RAM. 
so far so good understanding the tutorial....and now i guess i will stick to my partition plan (see image 1) and go for the 178 gb to install my ubuntu after i make it a free space and repartition it in favor of ubuntu(as points 1 and 2). Just curious, but am i going the right way?

And another question, [COLOR=Red]Boot Loader "what does the device for boot loader" mean?[/COLOR] (refer image 2)?. Does that Boot Loader have more options in its dropout ? i am sorry if its totally a foolish question but it came to my mind due to curiosity....i have finished the detailed studies and so think of going for installation....and need a final verdict regarding my setup plans....

Regards, NeptuneTech

Bootloader device:  Where (sdx, or rarely sdxy)

sdx example: sda, sdb, sdc = i.e. the MBR of sda, sdb, ...........

sdxy example: sda1, sda2, sd5 = i.e. a partition of sda,

---

### Post by bcbc on 2011-09-05
> **NeptuneTech said:**
> Reading the link you sent, i came up with this conclusion : 
1. I need a ext4 partition with a "/" as a mount point and
2. need a swap area of size of my RAM. 
so far so good understanding the tutorial....and now i guess i will stick to my partition plan (see image 1) and go for the 178 gb to install my ubuntu after i make it a free space and repartition it in favor of ubuntu(as points 1 and 2). Just curious, but am i going the right way?

And another question, Boot Loader "what does the device for boot loader" mean? (refer image 2)?. Does that Boot Loader have more options in its dropout ? i am sorry if its totally a foolish question but it came to my mind due to curiosity....i have finished the detailed studies and so think of going for installation....and need a final verdict regarding my setup plans....

Regards, NeptuneTech

That's more than enough space for / and swap. You might even think about splitting that into a separate partition for / and /home. I'd add 1GB to your RAM when calculating the size of SWAP e.g. if you have 3GB RAM make it 4GB SWAP (sometimes you need an overflow amount to hibernate)

Regarding the bootloader device, /dev/sda is your hard drive  and installing the bootloader to it will replace the windows boot loader that is currently in the MBR (master boot record). This is recommended. It's easy to repair the MBR e.g. restore the windows boot loader or grub later if you need to. Make a windows repair cd before you install, and your Ubuntu CD will also do the trick.

---

### Post by nipunshakya on 2011-09-05
> **Hakunka-Matata said:**
> Bootloader device:  Where (sdx, or rarely sdxy)

sdx example: sda, sdb, sdc = i.e. the MBR of sda, sdb, ...........

sdxy example: sda1, sda2, sd5 = i.e. a partition of sda,

I actually understood what you meant....thank you Matata...:)

---

### Post by nipunshakya on 2011-09-05
> **bcbc said:**
> That's more than enough space for / and swap. You might even think about splitting that into a separate partition for / and /home. I'd add 1GB to your RAM when calculating the size of SWAP e.g. if you have 3GB RAM make it 4GB SWAP (sometimes you need an overflow amount to hibernate)


OMG, i made a slight mistake here.....since my internet connection is slow here, i disabled the internet cable before performing the installations to avoid update....and so i didn't go through your suggestions. In a hurry, i used entire space for / and had just 2gb for the swap area........so now, is there any alternative way to get a /home partition in ubuntu?? and can i add some more space to my swap area?? Like before, any instruction or a guide would be helpful..... 

When i googled about the partition management in ubuntu, i got results regarding the gparted....please don't mind my noobish questions here but being new to the beast(ubuntu) makes me aware of the consequences of trying to get to wrong result without knowing what is right......


Regards, NeptuneTech:)

---

### Post by bcbc on 2011-09-05
You can make adjustments using GParted, but you have to do this from a liveCD/USB because you can't shrink a partition while it's mounted. But it should be pretty snappy as you have a clean install.

But it's a pain to redo the swap and /home as there are a lot of little things that you need to do:
For example, assuming your new swap is /dev/sda7:
$ sudo blkid /dev/sda7
/dev/sda7: UUID="xxxxxx" TYPE="swap"

You need to edit /etc/fstab (gksu gedit /etc/fstab) and replace the old UUID with xxxxx. 
$ cat /etc/fstab | grep swap
UUID=xxxxxx none swap sw 0 0

And also the resume file (gksu gedit /etc/initramfs-tools/conf.d/resume):
$ cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=xxxxxx

Once you've done that, you need to update the initial ram disk.
$ sudo update-initramfs -u

For /home you'll need to copy your current /home (and the rename/delete the old one) to the new partition and then modify the /etc/fstab. You'll have to use a command like rsync with the -a option and also exclude the .gvfs folder(s).

Personally... since you just installed, my advice is to do it all again and this time specify the partitions manually.

---

### Post by nipunshakya on 2011-09-05
> **bcbc said:**
> 
Personally... since you just installed, my advice is to do it all again and this time specify the partitions manually.


I think im gonna go with this option at this instance because terminal is just like a ghost to me right now.....some time in future, i shall really do what you've taught me in your above post( if required )...

Thanks to you sincerely.
Regards, NeptuneTech

---

