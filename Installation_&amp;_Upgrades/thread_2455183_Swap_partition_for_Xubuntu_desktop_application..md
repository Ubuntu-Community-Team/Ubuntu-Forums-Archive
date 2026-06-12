---
title: "Swap partition for Xubuntu desktop application."
date: 2020-12-14
forum: Installation &amp; Upgrades
---

### Post by gardenair on 2020-12-14
I have installed  Xubuntu on my core i5 Dell machine. I have 4 GB ram. During installation, I create the manual  partition as

```
/boot    500 MB
/swap    8 GB
/          60 GB
/home   (rest of the hard disk space)
```

I shall use GIMP and Kdenlive on this PC. _The question is, is the swap partition sufficient for such software? _ I never user hibernation on the laptop. Kindly guide me.

---

### Post by ActionParsnip on 2020-12-14
I'd put 1Gb on /boot but otherwise looks OK to me. Swap space is fine. Ubuntu uses a swap file now but using a swap partition is no bad thing (I prefer it but I'm very old school).

---

### Post by Impavidus on 2020-12-14
I don't know about kdenlive. It's video editing software, and as such I expect it to use a lot of memory, but it would depend on what videos you edit with it. For gimp 8GB swap is probably overkill. Unless you edit really big images with many layers, 4GB swap should be sufficient. If it's not, you want to install more ram.

Other than that, 60GB for root may be a bit much and 500MB for /boot a bit tight. Do you actually need a /boot partition?

---

### Post by gardenair on 2020-12-14
thanks for the replay. Well, what size of / may I keep? Suggest me. As to /boot I don't know much about it but in most Linux distro like Slackware, they create /boot partition during installation.
why we keep it separate " /boot " I don't have its answer. Technically Iif you guide me it will increase my Linux knowledge.  Maybe for the dual operating system but in my case, I only have Xubuntu on my hard disk.

Well 1 GB is sufficient for /boot partition? and if I do not create separate /boot partition what will be the drawback?

Example

```
/swap  8 GB
/root   40 GB
/home (rest of the space)

```

---

### Post by ActionParsnip on 2020-12-14
> **gardenair said:**
> Well 1 GB is sufficient for /boot partition? and if I do not create separate /boot partition what will be the drawback?

Nothing, /boot will just be part of your root partition rather than on it's own partition.

---

### Post by GhX6GZMB on 2020-12-14
The listing looks a bit odd.

Could you poat the output of lsblk, please?

---

### Post by ajgreeny on 2020-12-14
Although I am not necessarily suggesting you go this far down in root partition size, I have never had more then 20G for root, and normally use no more than 60% of that; at this moment I am using 11.5G of my 20G root partition in this laptop, and on my desktop machine, also Xubuntu-20.04, it uses 12.1G.

I am not a gamer so that may make some difference as they generally utilise a lot of disk space, but I do use Emby Mediaserver on the desktop, which can use a lot of space for its database of media files and I also occasionally edit video with openshot, not kdenlive, though as I understand it they are fairly similar.

I agree with other posters here than a separate /boot partition is not needed, and in fact,it can quickly complicate matters in certain situations, so my advice is to forget about that and stick to separate partitions for root, home, and if you feel you need it due to the applications that you use being big RAM users, a swap partition of up to 8G.  I assume you are aware that the most recent Ubuntu versions (of all DES) now all use a swap file of just 1G, created automatically at installation. For many users that is plenty in these days of large RAM amounts in many machines.

---

### Post by GhX6GZMB on 2020-12-14
@ajgreeny:

I'm almost 100% with you. I used to have 20 GB for / but after installing CAD programs (eg, KiCAD), I've found that 30 GB is more to the point. The libraries take up a lot of space and can not be moved easily (an upgrade kills the move).
/home on a separate partition? Yes, of course. It makes upgrading or reinstallation so much simpler.

Concerning swap: in my opinion, you only really need it if you need hibernate, and in that case only a swap partition works. I've never been able to get hibernate to work with a swap file, regardless of size.

SO-DIMM 667 MHz RAM costs around 5...6 Euro/GB today.

This is my very simple laptop partitioning (I need hibernate):
```
me@me-pc:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 223,6G  0 disk 
&#9500;&#9472;sda1   8:1    0  29,3G  0 part /
&#9500;&#9472;sda2   8:2    0 188,3G  0 part /home
&#9492;&#9472;sda3   8:3    0     6G  0 part [SWAP]
sr0     11:0    1  1024M  0 rom
```

---

### Post by grahammechanical on 2020-12-14
Please remember that if you ever need to re-install Ubuntu do not format the /home partition. You will lose all your data files. You could have a /home 30 - 50 GB and the remainder of the disc as a Data partition. Save all your work to the Data partition then you can re-install Ubuntu into the root partition and the home partition without messing up your data files on the Data partition.

And as you have noticed there are different opinions Difference is not wrong only Different.

Regards

---

### Post by gardenair on 2020-12-14
Thanks for the replies. Well  I shall reinstall my xubuntu on my test machine. Following is the output of  lsblk command

```
test@test-Latitude-E6430:~/Desktop$ sudo lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0    7:0    0  55.4M  1 loop /snap/core18/1932
loop1    7:1    0  97.9M  1 loop /snap/core/10444
loop2    7:2    0 217.9M  1 loop /snap/gnome-3-34-1804/60
loop3    7:3    0   2.2M  1 loop /snap/gnome-system-monitor/148
loop4    7:4    0 290.6M  1 loop /snap/kde-frameworks-5-qt-5-14-core18/4
loop5    7:5    0  87.8M  1 loop /snap/kdenlive/24
loop6    7:6    0  64.8M  1 loop /snap/gtk-common-themes/1514
loop7    7:7    0 175.8M  1 loop /snap/skype/160
loop8    7:8    0  31.1M  1 loop /snap/snapd/10492
sda      8:0    0 298.1G  0 disk 
&#9500;&#9472;sda1   8:1    0   476M  0 part /boot
&#9500;&#9472;sda2   8:2    0   7.5G  0 part [SWAP]
&#9500;&#9472;sda3   8:3    0 111.8G  0 part /
&#9492;&#9472;sda4   8:4    0 178.4G  0 part /home
sr0     11:0    1  1024M  0 rom  
test@test-Latitude-E6430:~/Desktop$ 

```


There is a new thing for me  which start from** loop0 to loop8 **what these are ?  The hard disk is [B]sda and i create 4 primary partitions.

[/B]Well  for video editing what is your experience with** Emby Media Server** ?

---

### Post by ajgreeny on 2020-12-15
Those loop entries are simply the snap applications that are installed on your system; these show as separate filesystems when running ***lsblk*** command.
They also show separately if you run ***sudo fdisk -l***
Nothing to worry about; just accept that's the way these things show.

I think there are ways to remove them from the output by adding options to the command but as I have no snaps I have not bothered to search any further.

[COLOR="#FF0000"]EDIT: Emby-Mediaserver.[/COLOR]
Regarding your query about Emby-mediaserver, I am not sure what you're asking.
It is not something that allows editing of videos, it simply serves videos, music and images over my LAN, allowing me to view any media on my hard disk to other devices such as my Android phone and tablet, other Linux computers (and I assume Windows, but don't have that any more), but most importantly, to my LG Smart TV.
In many ways it is very similar to PlexMediaserver, though in my opinion, better

---

### Post by DuckHook on 2020-12-15
> **gardenair said:**
> &#8230;Following is the output of  lsblk command
```
test@test-Latitude-E6430:~/Desktop$ sudo lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0    7:0    0  55.4M  1 loop /snap/core18/1932
loop1    7:1    0  97.9M  1 loop /snap/core/10444
loop2    7:2    0 217.9M  1 loop /snap/gnome-3-34-1804/60
loop3    7:3    0   2.2M  1 loop /snap/gnome-system-monitor/148
loop4    7:4    0 290.6M  1 loop /snap/kde-frameworks-5-qt-5-14-core18/4
loop5    7:5    0  87.8M  1 loop /snap/kdenlive/24
loop6    7:6    0  64.8M  1 loop /snap/gtk-common-themes/1514
loop7    7:7    0 175.8M  1 loop /snap/skype/160
loop8    7:8    0  31.1M  1 loop /snap/snapd/10492
sda      8:0    0 298.1G  0 disk 
&#9500;&#9472;sda1   8:1    0   476M  0 part /boot
&#9500;&#9472;sda2   8:2    0   7.5G  0 part [SWAP]
&#9500;&#9472;sda3   8:3    0 111.8G  0 part /
&#9492;&#9472;sda4   8:4    0 178.4G  0 part /home
sr0     11:0    1  1024M  0 rom  
test@test-Latitude-E6430:~/Desktop$ 

```
There is a new thing for me  which start from** loop0 to loop8 **what these are ?

> **ajgreeny said:**
> &#8230;there are ways to remove them from the output by adding options to the command&#8230;
Indeed, they are distracting. The way to suppress this output is to invoke with the -e flag and pass the parameter for the unwanted major device number, in this case, "7". Hence:```
sudo lsblk -e 7
```
Result will be:
```
test@test-Latitude-E6430:~/Desktop$ sudo lsblk -e 7
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 298.1G  0 disk 
&#9500;&#9472;sda1   8:1    0   476M  0 part /boot
&#9500;&#9472;sda2   8:2    0   7.5G  0 part [SWAP]
&#9500;&#9472;sda3   8:3    0 111.8G  0 part /
&#9492;&#9472;sda4   8:4    0 178.4G  0 part /home
sr0     11:0    1  1024M  0 rom  
test@test-Latitude-E6430:~/Desktop$ 

```

---

### Post by GhX6GZMB on 2020-12-15
Nice!
You should put this under "Tutorials" as well.
I don't have the issue, as my first action after an install is to send snapd to the trash, but others might profit.

---

