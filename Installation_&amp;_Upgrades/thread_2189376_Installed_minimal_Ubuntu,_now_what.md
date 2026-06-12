---
title: "Installed minimal Ubuntu, now what?"
date: 2013-11-22
forum: Installation &amp; Upgrades
---

### Post by MibunoOokami on 2013-11-22
I went with the install of minimal Ubuntu rather than trying to remove stuff from a full version per my recent thread. When I got to the option for software selection, I only chose the first program which was basic Ubuntu server or some such. After that I get the terminal like screen that I can log into, the only thing is, once logged in I have no idea what to do or where to go. I tried apt-get of firefox but it wouldn't let me.

Please tell me what I need to do to start using minimal.

---

### Post by Bucky Ball on 2013-11-22
You shouldn't have installed anything, not server either. I would start again, when the kernel has finished installing, machine will restart back to a terminal like window. 

With an ethernet cable plugged in, you then do a 'sudo apt-get' of the apps you want installed. Here's a suggestion:
```

sudo apt-get install xfce4 firefox synaptics lxterminal
```

That is pretty much it for the moment. xfce4 is a desktop environment, lxterminal is a terminal and the other two are self explanatory. You can then install whatever you want from terminal or Synaptics. To the install line above, though, you could append whatever you like; add firefox, thunderbird, vlc, gimp, whatever you fancy. (More like whatever you know you are going to use and NOTHING superflous.)

A minimal install takes some research and planning. You should make a list of the apps *you* want/need and know what you're doing before commencing. It is an extremely flexible way of configuring your machine just how you want it so you want to get it right. No bloat! ;)

This part:

> To install, boot your computer from the the Minimal CD and type "cli" (command line install) at the prompt.

Is all good. This part:

> You can then follow the instructions from the text-based installer. After the base system is installed, log in, and type "sudo tasksel" to select the system to install. 

You do not need to select a predefined setup (like server). That's not really what you want. Main thing: You need to be online to get this up and running (or you can't install anything). You are only installing the kernel, nothing else, no apps or desktop. They are ALL up to you.

V IMPORTANT: DO NOT install *buntu-desktop anything on a minimal. This effectively installs Ubuntu and defeats the purpose (you may as well have installed Ubuntu). For instance, installing xubuntu-desktop is effectively installing Xubuntu, all apps, dependencies and everything else that is Xubuntu. Not the idea.

PS: I am running minimal install (that's all I do nowadays) with xfce4 desktop environment and what I need/want on an i3 CPU/4Gb RAM and it flies. ;)

---

### Post by MibunoOokami on 2013-11-22
> **Bucky Ball said:**
> You shouldn't have installed anything, not server either. I would start again, when the kernel has finished installing, machine will restart back to a terminal like window. 

A minimal install takes some research and planning. You should make a list of the apps *you* want/need and know what you're doing before commencing. 


The window that was there said I had to select at least one item otherwise install couldn't continue, I have limited knowledge about what I'm doing so went for the first choice thinking it would be safest.

The apps I want are, firefox, thunderbird, skype, vlc, audacity and libreoffice off the top of my head...

Edit: Nope there's more, I want Fspot, gimp and gkrellm also.

---

### Post by Bucky Ball on 2013-11-22
```
sudo apt-get install xfce4 firefox thunderbird skype vlc audacity libreoffice fspot gimp gkrellm synaptic lxterminal pcmanfm
```

That would do it. This is presuming xfce4 (as used by Xubuntu and lightweight, but there are plenty of others) and lxterminal and pcmanfm, the terminal and file manager respectively used by Lubuntu, also lightweight. These are my preferences, you may have others. This is why you need to make a plan. Best to get it up then install what you will discover is missing as you go.

Essentially, you are going to need a desktop environment, file manager, probably synaptics and a terminal at the bare minimum. Then you're off and running.

It takes a little while to tweak a minimal to perfection (at least to suit your individual needs) but worth the effort, IMHO. ;)

---

### Post by MibunoOokami on 2013-11-22
> **Bucky Ball said:**
> ```
sudo apt-get install xfce4 firefox thunderbird skype vlc audacity libreoffice fspot gimp gkrellm synaptic lxterminal pcmanfm
```


I've reinstalled and didn't get the same software option this time. I entered the command above and it said "reading package lists... done, building dependency tree, reading state info... done, E can'T locate package skype or fspot. This is probably a stupid question but do I reboot now and see what happens or are there further things I need to do in terminal first? Thanks.

---

### Post by Bucky Ball on 2013-11-22
That should be fine. Boot it up! Those errors were  just about the fact that those probably aren't the correct command line names for fspot and skype. Oddly enough, that is the reason I've logged on: to mention I wasn't sure about the command line names of the apps you mentioned, only the apps I suggested. 

If you get to a terminal again after reboot, issue:

startx

... and that should get you to a desktop. You can then install skype and fspot from synaptics. ;)

(With any luck, you should either get the grub menu or go straight to the login screen on boot. Fingers crossed.)

---

### Post by Bucky Ball on 2013-11-22
BTW, were the fspot and skype errors the only ones and you ended up back at a cursor and all was normal? Then I would think you'll have no issues on reboot. Either way, reboot. ;)

PS: Maybe you could time how long it takes to get to the login screen. I'd be curious ...

---

### Post by MibunoOokami on 2013-11-22
> **Bucky Ball said:**
> BTW, were the fspot and skype errors the only ones and you ended up back at a cursor and all was normal? Then I would think you'll have no issues on reboot. Either way, reboot. ;)

PS: Maybe you could time how long it takes to get to the login screen. I'd be curious ...

Yea just went back to the cursor as if finished. Just installing xinit now so that I can run startx. Will time it after doing startx unless that takes me straight to login.

Edit: Ok startx has now made 25% of the screen into a white screened terminal, the other 75% is black screen with an X for my pointer. Is that normal?

---

### Post by steeldriver on 2013-11-22
Try 'startxfce4' instead of 'startx' (plain 'startx' will only start an xfce4 session if you tell it to via a ~/.xinitrc or ~/.xsession file - otherwise it will just start an xterm on a plain gray root window iirc)

The package name for fspot appears to be f**-**spot. For skype, you will need to enable the partner repository - you could do that by editing /etc/apt/sources.list, but you will probably find it easier to wait until you have a working desktop session and use synaptic to do that.

---

### Post by MibunoOokami on 2013-11-22
> **steeldriver said:**
> Try 'startxfce4' instead of 'startx' (plain 'startx' will only start an xfce4 session if you tell it to via a ~/.xinitrc or ~/.xsession file - otherwise it will just start an xterm on a plain gray root window iirc)

The package name for fspot appears to be f**-**spot. For skype, you will need to enable the partner repository - you could do that by editing /etc/apt/sources.list, but you will probably find it easier to wait until you have a working desktop session and use synaptic to do that.

I've got a desktop now useing startxfce4, there is a home folder and file system, both are asking for a default file manager. I must have over looked a command somewhere.

---

### Post by Bucky Ball on 2013-11-22
Yes, you did. You left out 'pcmanfm'. Just sudo apt-get it or install from synaptics.

You can install others if you want (Thunar is also lightweight) but pcmanfm I've found zippiest.

Glad you got to the desktop. Thanks steeldriver, my mistake. ;)

---

### Post by MibunoOokami on 2013-11-22
> **Bucky Ball said:**
> Yes, you did. You left out 'pcmanfm'. Just sudo apt-get it or install from synaptics.

You can install others if you want (Thunar is also lightweight) but pcmanfm I've found zippiest.

Glad you got to the desktop. Thanks steeldriver, my mistake. ;)

Hmm, it actually looks like none of those software packages installed earlier. I just installed pcmanfm it worked, then tried launching web browser and it said there's an input/output error and the mail reader says no default program selected, nor can I find any of the other programs.

I'm going to re-install them and will post an update. Before that though, I would like to thank you Bucky Ball and steeldriver.

---

### Post by Bucky Ball on 2013-11-22
All good. Just install using Synaptic or terminal. But puzzled that those programs didn't install. But xfce4 did as you have a desktop. Strange. 

Yes, keep us updated. ;)

Ah, hang on. If you open a terminal and type 'thunderbird', does it open then? You may just not have a default set. As I say, they can take some tweaking to get sweet.

Either way, try to reinstall it and you'll soon find out.

---

### Post by MibunoOokami on 2013-11-22
> **Bucky Ball said:**
> All good. Just install using Synaptic or terminal. But puzzled that those programs didn't install. But xfce4 did as you have a desktop. Strange. 


My mistake, I forgot to say when I tried to run startxfce4 it made me install xfce4-session. I'm installing them one at a time and all say packages will be newly installed, but just now I have a message saying no space left on device!? The partition I installed on is 230GB give or take and I told it to use max. This is odd.

---

### Post by Bucky Ball on 2013-11-22
Very odd. Please open a terminal and give the output of this command:
```

df -l
```

You can have a look also with gparted but it probably won't let you install it (that should have been on the original install line, incidentally, my mistake). Good idea to do a manual partition I've found. Then you know what is going where and how big your /swap is, etc ...

Hope you're enjoying the learning curve. ;)

Just a note: the partition you installed it on? Did you have 230Gb of free space to start with rather than any partitions? If you had an existing NTFS partition Ubuntu won't install to that. Instead it may have installed to whatever free space it could find which is why you are getting this error.

I'm guessing something has gone amiss at the install line right at the start because xfce-session should be installed with xfce4, so not sure what desktop environment you're using. The absence of xfce-session is why you are not getting to a desktop at boot. If that line at the start had installed everything you would be getting directly to the login then desktop at boot.

---

### Post by MibunoOokami on 2013-11-22
> **Bucky Ball said:**
> Very odd. Please open a terminal and give the output of this command:
```

df -l
```

It won't open firefox for me so I had to type it all out on another computer. Probably due to no space LOL.
```
~/Desktop$ df -l
Flilesystem    1K-blocks    Used         Available   Use% Mounted on
/dev/sda9      2511664     2471984     0              100%     /
none             4               0              4               0%       /sys/fs/cgroup
udev             12017812    4              1017808     1%       /dev
tmpfs            205304       585           204720      1%       /run
none             5120          0               5120         0%       /run/lock
none             1026516     72             1026444     1%      /run/shm
none             102400       8              102392       1%      /run/usr
overflow        1024          32             992           4%      /tmp

```

Again I went with the first option yesterday of a guided install on /sda7 because I knew it was my Lubuntu partition and I'm not familiar with the options that were available, normally on an install I select do something else. I don't know why it says /dev/sda9 up there.

> **Bucky Ball]You can have a look also with gparted but it probably won't let you install it (that should have been on the original install line, incidentally, my mistake). Good idea to do a manual partition I've found. Then you know what is going where and how big your /swap is, etc ...[/QUOTE]

Great minds think alike, I was going to apt-get remove some of what I installed so I could have space to put gparted but it needs space even for removing stuff. I'll see where I put mu Ubuntu or Lubuntu liveCDs and have a look, but to be honest I think I'll be better off just starting from scratch again.

[QUOTE=Bucky Ball]Hope you're enjoying the learning curve.  said:**
>  

You know what? I actually am. Normally by now I'd be getting really frustrated and want to give up, but I find this kind of cool.

[QUOTE=Bucky Ball] Just a note: the partition you installed it on? Did you have 230Gb of free space to start with rather than any partitions? If you had an existing NTFS partition Ubuntu won't install to that. Instead it may have installed to whatever free space it could find which is why you are getting this error.

I'm guessing something has gone amiss at the install line right at the start because xfce-session should be installed with xfce4, so not sure what desktop environment you're using. The absence of xfce-session is why you are not getting to a desktop at boot. If that line at the start had installed everything you would be getting directly to the login then desktop at boot.

I'm pretty sure it said the partition size was 230GB and it sounded right, but on the line where you can enter your own value it said 120GB so I typed max. There should have been about 5 partitions on there, Lubuntu /, /home and swap, then windoze 7 and its recovery partition.

---

### Post by Bashing-om on 2013-11-22
et al,
I have subscribed to this thread. I also run minimal with xfce4 as my DM. Very pleased and impressed. I have learned a lot from the experience and it prompts me to learn more.

@ Bucky Ball; I boot in @ 5seconds ! AMD dual core Athlon 4 gigs ram on an obsolete Abit mother board.

[INDENT][INDENT]Happy "Trials" to you
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2013-11-22
Yep, that doesn't look good at all. You should have gone for manual partition rather than guided install. You should be getting something like this:

```
Filesystem     1K-blocks     Used Available Use% Mounted on
**/dev/sda12      15375760  7733056   6861648  53% /**
udev             1946828        4   1946824   1% /dev
tmpfs             782256      928    781328   1% /run
none                5120        0      5120   0% /run/lock
none             1955640      108   1955532   1% /run/shm
[B]/dev/sda2       41943036 34842752   7100284  84% /media/S3A8406D004
/dev/sda1        1535996   195108   1340888  13% /media/System
/dev/sda9       15420408  3645160  11775248  24% /mnt/Misc
/dev/sda6      163440624 92009500  63129088  60% /mnt/storage
/dev/sda8       15203776 13902240    529216  97% /mnt/12.04
```[/B]

See all my /dev/sda* partitions (I've marked them in bold)? You should have them to for your various installs. I only see sda9, no /swap, Lubuntu, /home or anything else. That is definitely *not* good ... Also, note how my sda12 is /? That's the install I'm running from. Your / is set at sda9 so that's where you installed to, using the entire disk by the looks. 

I would boot from a LiveCD, open Gparted and have a check. Plug in a cable so you can get online and post what you have. Looks to me horribly like you've wiped the drive somehow, except for /dev/sda9. I thought it was strange when things didn't install from the install line at the beginning. I'm guessing they couldn't as there was nowhere for them to do so. No sda7 there and sda9 takes up the entire drive and is completely full!

You say you have five partitions? That could be the problem because generally four is the max and if you try adding more it turns it into a dynamic disk, which is trouble and you don't want. I know nothing about that issue, though.

Heya, B-Om. ;) What do you think so far?

---

### Post by MibunoOokami on 2013-11-22
Perhaps it's a bad install disc? I definitely recall the install saying swap was going to sda5, though I don't recall an option to manually change things. I'm going to reinstall it again, it's not going to beat me.

---

### Post by Bucky Ball on 2013-11-22
Good for you. At the partitioning section, use manual partition (not guided) and set them up yourself. You don't want more than four partitions. One of these (or more) can be an extended partition into which you can put as many virtual partitions as you like, which overcomes the limitation. Ubuntu is happy to be installed inside an extended on a virtual partition.

It pays to make a plan re. your partitions and sizes prior to doing it. Any existing partitions you will see (and can avoid) when you get to the partitioning part of the install.

PS: This might help:

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

You will see a pic of the partition window a little down that page. Below guided is manual. You used 'Guided - use entire disk' which explains everything. You wiped the lot and installed to sda9 but something went wrong somewhere along the way. (I have attached that screenshot for you.)

---

### Post by MibunoOokami on 2013-11-22
> **Bucky Ball said:**
> 
I would boot from a LiveCD, open Gparted and have a check. Plug in a cable so you can get online and post what you have. Looks to me horribly like you've wiped the drive somehow, except for /dev/sda9. I thought it was strange when things didn't install from the install line at the beginning. I'm guessing they couldn't as there was nowhere for them to do so. No sda7 there and sda9 takes up the entire drive and is completely full!

Whoops, I have already started the reinstall. I don't think the drive was completely wiped because I had the options of booting into Ubuntu, Ubuntu advanced options, windoze and windoze recovery. This morning when I first powered up, my desktop was full of images of hard disks and their sizes which for the most part matched what I knew to be on the drive plus a few extras.

I'm not trying to be argumentative because I know you know more than I do, I'm just typing my thoughts which could very well be wrong. Afterall as you said and I agree with, something has gone awfully wrong.

[QUOTE=Bucky Ball]You say you have five partitions? That could be the problem because generally four is the max and if you try adding more it turns it into a dynamic disk, which is trouble and you don't want. I know nothing about that issue, though.[/quote]

I say that but in all honesty, some could very well be the virtual ones. I was once instructed to setup three partitions (perhaps they are virtual) one as /, one as /home and the other as swap. Plus there are two for windows already on there.

---

### Post by MibunoOokami on 2013-11-22
Oh, I'm at the partitioning stage now and just deleted about five 2GB partitions, I have no idea where they came from, perhaps something with the mini install.

I'm now at the point of deciding the partition type, logical or primary. IIRC, I need to make them logical right? Does logical = virtual? Sorry for the dumb questions, I'm now starting to doubt myself so would like clarification. Thanks

---

### Post by Bashing-om on 2013-11-22
MibunoOokami; Hi !

Allow me to jump in.
Partitions .. legacy MSDOS partitioning is a max of 4 primary partitions. The way this limitation is overcome is to make an extended partition as that 4th primary partition. Now within that extended partition one may make as many logical partitions as one desires.
As stated ubuntu is happy to run in these extended partitions.

I too prefer to set up a separate partition for /home ( in your case probably in that extended partition ).
To the best of my poor memory in the install partition editor set up that extended partition and then choose to make logical partitions within that extended partition. 

example:
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00065f5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    10242047     5120000   83  Linux
/dev/sda2        10244096    30724095    10240000   83  Linux
/dev/sda3        34207742   976771071   471281665    5 [color=red] Extended[/color]
/dev/sda5       443795688   443811689        8001   82  Linux swap / Solaris
/dev/sda6       443811753   597409154    76798701   83  Linux
/dev/sda7       597409792   976771071   189680640   83  Linux
/dev/sda8        34207744    44447743     5120000   83  Linux

as per above posts:
sysop@1304mini:~$ df -l
Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/sda1        4908544 2121196   2531348  46% /
none                   4       0         4   0% /sys/fs/cgroup
udev             1982400       4   1982396   1% /dev
tmpfs            2024912      24   2024888   1% /tmp
tmpfs             404984     380    404604   1% /run
none                5120       0      5120   0% /run/lock
none             2024912    1024   2023888   1% /run/shm
none              102400       0    102400   0% /run/user
/dev/sda2        9948012 1097800   8338212  12% /home
/dev/sda8        4908544  515304   4137240  12% /var
sysop@1304mini:~$

```
My partitions 5,6,7, and 8 are logical partitions within that extended partition 3.

does this help ?

[INDENT][INDENT]just my little bit
[/INDENT][/INDENT]

---

### Post by MibunoOokami on 2013-11-22
I undid the changes to deleted partitions, now I can list my partitions.

#1 Primary 208.7MB ntfs
#2 Primary 53.7GB ntfs
#5 Logical 3.1GB swap
#6 Logical 20.5GB ext4
#7 Logical 237.2GB ext4
#9 Logical 2.7GB ext4
#8 Logical 2.7GB ext4
#4 Primary 108MB fat32

I can answer my own question now, logical is virtual.

---

### Post by MibunoOokami on 2013-11-22
> **Bashing-om said:**
> MibunoOokami; Hi !

Allow me to jump in.
Partitions .. legacy MSDOS partitioning is a max of 4 primary partitions. The way this limitation is overcome is to make an extended partition as that 4th primary partition. Now within that extended partition one may make as many logical partitions as one desires.
As stated ubuntu is happy to run in these extended partitions.

does this help ?[INDENT][INDENT]just my little bit
[/INDENT]
[/INDENT]


Hi Bashing-om, 

If I understand correcty I should use my free space of about 260GB to make Primary #4 and somehow re-partition that into logical partitions? I'll try do that now and report back. Perhaps I can get rid of the two small windoze primary partitions, I know at least one is just for recovery.

---

### Post by MibunoOokami on 2013-11-22
OK good news, I've reinstalled minimal Ubuntu, this time only installed xfce4 first and the installation via terminal was completely different from yesterday and after a reboot worked perfect.
I've also got a panel notice which I didn't get yesterday, it wants to know if I want to use default config or empty panel. I don't know which to choose.
It's definitely looking much better with this install.

---

### Post by Bashing-om on 2013-11-22
MibunoOokami; You do good.
Post #25 -> -and this is what you probably did - is that unallocated space as an extended partition and the logical (yes, virtual) partitions within.

 Your last post: Choose "default" ... xfce4 prides itself on customization ! .. You may make all kinds of alterations at a later time.
edit: partition layout:
terminal code:
```

sudo fdisk -lu

```
shows a better representation of the partitioning.


And Hey ! Welcome to xfce4
see:
[http://www.xfce.org/](http://www.xfce.org/)
[https://wiki.archlinux.org/index.php/Xfce](https://wiki.archlinux.org/index.php/Xfce) 
[http://wiki.xfce.org/recommendedapps](http://wiki.xfce.org/recommendedapps)
[http://www.linuceum.com/Distros/osDesktopConfigXfce.php](http://www.linuceum.com/Distros/osDesktopConfigXfce.php)
For all kinds of help and howto's and pointers to other means.

[INDENT][INDENT]cheers
[/INDENT][/INDENT]

---

### Post by MibunoOokami on 2013-11-22
> Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8c890b7d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS/exFAT
/dev/sda2          409600   105267199    52428800    7  HPFS/NTFS/exFAT
/dev/sda3       105269246   624928767   259829761    5  Extended
/dev/sda4       624928768   625139711      105472    c  W95 FAT32 (LBA)
/dev/sda5       617115648   624928767     3906560   82  Linux swap / Solaris
/dev/sda6       144263168   617115647   236426240   83  Linux
/dev/sda7       105269248   144261119    19495936   83  Linux

Partition table entries are not in disk order



I just copied and pasted that in my new mini ubuntu :D.
Edit: If I understand that code properly, sda3 is primary and sda5 swap, sda6 root (20gb) and sda7 home (242gb) are logical. Is that correct?

---

### Post by Bashing-om on 2013-11-22
MibunoOokami; Well.

Semi so ..
While it is probably  true:
sda3 is the extended partition that is counted as primary
sda4 logical as a data partition w/Windows format
sda5 logical and used as swap
sda6 logical - I should hope this is /home NOT root, as it has the most space
sda7 logical  - I should hope is / as it has the lesser not needed space for expansion.

let's get confirmation what we are looking at:
terminal code:
```

df -h

```
edit: We will continue this discussion and confirmations with the next posting ! get comfortable.

[INDENT][INDENT]ain't nothing but a thing[/INDENT][/INDENT]

---

### Post by MibunoOokami on 2013-11-22
Oh no, this looks similar to last time except 2 partitions are here instead of 1.
>  df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda7        19G  2.7G   15G  16% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            994M  4.0K  994M   1% /dev
tmpfs           201M  576K  200M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none           1003M   72K 1003M   1% /run/shm
none            100M  4.0K  100M   1% /run/user
/dev/sda6       222G  112M  211G   1% /home



---

### Post by Bashing-om on 2013-11-22
MibunoOokami; Hey,

Looks OK to me .. partitions as I had hoped they were.
Mine for reference:
```

sysop@1304mini:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       4.7G  2.1G  2.5G  46% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           2.0G   40K  2.0G   1% /tmp
tmpfs           396M  380K  396M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            2.0G  1.1M  2.0G   1% /run/shm
none            100M     0  100M   0% /run/user
/dev/sda2       9.5G  1.1G  8.0G  12% /home
/dev/sda8       4.7G  504M  4.0G  12% /var
sysop@1304mini:~$ 

```
I have /var and /tmp separated to their own partitions, that is the only difference I see.

You are in good shape.

Ok next step in file system  comprehension.
What is mounted ?
```

mount

```
does it match with what the system thinks is mounted ?
```

cat /etc/mtab

```
and is all in accord with what we want mounted and where ?
```

cat /etc/fstab

```
and all matches this:
```

sudo blkid

```

And I am now open to your questions for discussion and comprehension.

---

### Post by Bucky Ball on 2013-11-22
You want to run the install line again, now, removing any apps you already have installed.

```
sudo apt-get install firefox thunderbird skype vlc audacity libreoffice fspot gimp gkrellm synaptic lxterminal pcmanfm gparted
```

---

### Post by MibunoOokami on 2013-11-22
I've spent a little trying to make sense of this and to see if everything is where and how it should be. Don't really understand it at all but it looks OK to me. I'll do some searching of the forum first to try and understand all the info within those outputs.

One last question, I can't get hear any sound and even though there's a sound mixer already installed, it doesn't seem to do anything. IIRC, there's something called alsa mixer or there abouts, is that what I need to install for sound? Or could it be I need to find out what drivers I require and download them?

```
/dev/sda7 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
/dev/sda6 on /home type ext4 (rw)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=mno)


```

```
~$ cat /etc/mtab
/dev/sda7 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/cgroup tmpfs rw 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
tmpfs /run tmpfs rw,noexec,nosuid,size=10%,mode=0755 0 0
none /run/lock tmpfs rw,noexec,nosuid,nodev,size=5242880 0 0
none /run/shm tmpfs rw,nosuid,nodev 0 0
none /run/user tmpfs rw,noexec,nosuid,nodev,size=104857600,mode=0755 0 0
none /sys/fs/pstore pstore rw 0 0
/dev/sda6 /home ext4 rw 0 0
systemd /sys/fs/cgroup/systemd cgroup rw,noexec,nosuid,nodev,none,name=systemd 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfsd-fuse /run/user/1000/gvfs fuse.gvfsd-fuse rw,nosuid,nodev,user=mno 0 0


```

```
~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda7 during installation
UUID=10a82441-ac40-45d3-87d4-3febef9d36b0 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=05440f14-8880-4f60-ab50-8ded2f44bd28 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=881ca603-b308-4a6e-8e57-134139702cb9 none            swap    sw              0       0
/dev/sr0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

```
/dev/sda1: LABEL="SYSTEM" UUID="7838AF9038AF4BC6" TYPE="ntfs" 
/dev/sda2: UUID="804C6C7D4C6C6FB8" TYPE="ntfs" 
/dev/sda4: LABEL="HP_TOOLS" UUID="E8BD-D438" TYPE="vfat" 
/dev/sda5: UUID="881ca603-b308-4a6e-8e57-134139702cb9" TYPE="swap" 
/dev/sda6: UUID="05440f14-8880-4f60-ab50-8ded2f44bd28" TYPE="ext4" 
/dev/sda7: UUID="10a82441-ac40-45d3-87d4-3febef9d36b0" TYPE="ext4" 


```

A big thank you to everyone who has taken the time to help me through this. It hasn't been nearly as frustrating as some past problems I've encountered. I'll mark thread solved and leave a note in the first post if I can directing people to the point where things started going right.

---

### Post by MibunoOokami on 2013-11-22
> **Bucky Ball said:**
> You want to run the install line again, now, removing any apps you already have installed.

```
sudo apt-get install firefox thunderbird skype vlc audacity libreoffice fspot gimp gkrellm synaptic lxterminal pcmanfm gparted
```

Hi Bucky,

I reinstalled from scratch, got my partitioning right and installed everything one at a time after getting xfce4 at the very beginning. As far as I can tell it has worked very well this time. Thanks a lot for your help with this.
Just remembered I haven't installed gparted.

---

