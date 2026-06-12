---
title: "Problems with installing Ubuntu through already existing hard disk"
date: 2008-07-20
forum: Installation &amp; Upgrades
---

### Post by orphefs on 2008-07-20
Hi there,

I am new to the Linux world, and Ubuntu was recommended to me by a friend as an excellent distribution. I downloaded the Ubuntu .iso (specifically ubuntu-8.04.1-desktop-i386.iso) and since I have no blank cdr's handy at the moment, I decided that it would be rather educational to try and install ubuntu through using my existing hard disk. I searched online and bumped into this article: [http://www.instantfundas.com/2007/08/install-any-linux-distro-directly-from.html]("http://www.instantfundas.com/2007/08/install-any-linux-distro-directly-from.html")

I partitioned my hard disk as follows:


- NTFS partition for Windows (c:\)
- Ext3 partition
- Swap partition
- Shared FAT32 partition   (d:\) (drive letter as it shows from windows xp)

I went through the necessary steps of extracting the kernel and ram disk files from the ms-dos grub zip file, placed them into c:\boot along with the .iso file. Modified the GRUB menu.lst as described in the article; Then, I modified boot.ini to boot select GRUB. 

When booting, GRUB loads fine, however when I select the option 'Install Linux', it seems as if stuff loads up to a certain point, but then everything stops, this thing called BUSYBOX shows up and the command line starts with 'initramfs'!

What to do next? I am kind of disappointed, as the article mentioned that this way of installing should work with all Linux distros!

Thank you for taking the time to read this, and excuse me for my ignorance!

---

### Post by sisco311 on 2008-07-20
try to download the vmlinuz and initrd.gz from:
[http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/cdrom/](http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/cdrom/)

and change the menu.lst to:
>                               title Ubuntu Installer (hd0,0)
kernel   (hd0,0)/boot/vmlinuz vga=normal ramdisk_size=14972 root=/dev/rd/0 rw --
initrd   (hd0,0)/boot/initrd.gz

---

### Post by orphefs on 2008-07-20
Hey, thanks for the reply!

If you have the time, could you maybe explain to me what "/dev/rd/0" points to, what "rw --" means and why ramdisk size is set to that number?

I tried this out, everything works until the installer does a CD check, and since I dont have the cd and the .iso file is on my hard disk, the installation can't proceed! Any help on that? Maybe I should try this link for vmlinuz and initrd.gz ? --> [http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/hd-media/]("http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/hd-media/")

Anyways, thank you very much for taking the time!

Regards :)

---

### Post by sisco311 on 2008-07-20
move the iso file to the root of the partition:
c:\ubuntu-8.04.1-desktop-i386.iso

the hd-media kernel is for the alternate cd
(text based installation)

---

### Post by orphefs on 2008-07-20
tried it, the installer still displays the following msgbox:

------------------------------------------------
Detect and mount CD-ROM

Your installation CD-ROM couldnt be mounted. This probably means that the CD-ROM was not in the drive. If so you can insert it and try again.

Try again to mount the CD-ROM?
------------------------------------------------

What next?

---

### Post by sisco311 on 2008-07-20
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

Try to mount manually the iso.
Open a terminal
Applications -> Accessories -> Terminal
and type:
```
sudo mount -t ntfs /dev/sda1 /mnt
sudo mount -o loop /mnt/ubuntu-8.04.1-desktop-i386.iso /cdrom

```Or try to install it with the alternate cd image:
download the Alternate CD image from the Ubuntu web site
and the vmlinuz and initrd.gz from hd-media.
[HowTo]("http://users.bigpond.net.au/hermanzone/p3.htm")

Or mount the iso in Windows with daemon tools(or other
image mounting software) and install it from windows.
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
Note: wubi will install ubuntu on a virtual disk on your 
Windows partition.

You can transfer the wubi install to a real partition:
[**LVPM: Upgrades Wubi installs to dedicated-partition Ubuntu installs**]("http://ubuntuforums.org/showthread.php?t=438591")

:lolflag:buy a blank cd.

---

### Post by orphefs on 2008-07-23
Hi again,

I installed Ubuntu after all, using the alternate CD and the hd-media kernel file...However, I did something stupid :???: :

When it asked me to install the graphical desktop environment, I accidentally pressed no! Now I tried the command:

sudo apt-get install ubuntu_desktop

and bash comes up with the following message:

E: Couldn't find package ubuntu_desktop

The ubuntu .iso is available on my windows c drive, which I have mounted successfully...Is there a way I can add the .iso file to the sources.lst of apt? Or is there another way to install the graphic environment?

p.s.: I also tried the command 'startx', but it says that it is not installed, and that I have to try installing xinit first, of which the package cant be found either!!!

Thanks :)

---

### Post by sisco311 on 2008-07-23
Hi.

try:
```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

---

### Post by orphefs on 2008-07-23
:lolflag:, i haven't even set up my internet connection yet!!! How do I do that?

I have a Speedstream Router with USB and Ethernet plugs...What commands should I use?

It's hard for a Windows user to get into Linux, but it's fun!!!:popcorn:

---

### Post by sisco311 on 2008-07-23
how do you connect to the router?
pppoe, dhcp or static ip?

take a look here: [http://ubuntuforums.org/showthread.php?t=571188&highlight=network](http://ubuntuforums.org/showthread.php?t=571188&highlight=network)
ask if you have any question.

---

### Post by orphefs on 2008-07-23
When I look at [http://192.168.254.254/](http://192.168.254.254/) on windows, it says:

Point to Point Connection Summary:
	PPPoE(00) 8/35	91.140.16.137

Does that help?:)

---

### Post by sisco311 on 2008-07-23
try:
```
sudo pppoeconf
```
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by sisco311 on 2008-07-23
maybe you should start a new thread with a descriptive title.
like:
*howto configure internet connection without GUI?*

---

### Post by orphefs on 2008-07-23
I connected the modem via ethernet and executed that command, but I says:

"Sorry, I scanned 1 interface, but the Access concentrator of your provider did not respond.......may also be another running pppoe process which controls the modem."

Then I tried: 

sudo lshw -C network

and the thing I noted is that it says "*-network DISABLED"...

How can I enable the network?

---

### Post by sisco311 on 2008-07-23
post the output from:
```
ipconfig
```
from WINDOWS

---

### Post by orphefs on 2008-07-23
there you are:

[[IMG]http://img381.imageshack.us/img381/3924/ipconfignk9.th.png[/IMG]](http://img381.imageshack.us/my.php?image=ipconfignk9.png)

however i think you can ignore the first two connections, my existing windows installation needs to go to the recycle bin for being so messy :lolflag:

---

### Post by sisco311 on 2008-07-23
edit the interfaces file
```
sudo nano /etc/network/interfaces
```add this lines:
> 
# The primary network interface
auto eth0
iface eth0 inet dhcp
(save the file and exit, Ctrl-o, Ctrl+x)

edit the resolve.conf:
```
sudo nano /etc/resolv.conf
```add this line:
> nameserver 192.168.254.254(save, exit)

restart the network
```
sudo /etc/init.d/networking restart
```and post:
```
ifconfig
```

---

### Post by orphefs on 2008-07-23
edited the files, when restarting the network, it still displayed messages like 'send_packet: network is down'..

Here is the output of ifconfig:

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:2 carrier:3
          collisions:0 txqueuelen:0 
          RX bytes:1296 (1.2 KB)  TX bytes:1296 (1.2 KB)

---

### Post by sisco311 on 2008-07-23
3 hours lost
30 minutes to reinstall ubuntu with gui:lolflag:

try to mount the iso in the /cdrom folder and install ubuntu-desktop:
```
sudo mount -t ntfs /dev/sda1 /mnt
sudo mount -o loop /mnt/ubuntu-8.04.1-desktop-i386.iso /cdrom
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

---

### Post by orphefs on 2008-07-23
not only 2 hours, more than that!!! However, i think its a way for me to learn Linux well! Do you know of any good tutorials I can use??? :)

---

### Post by sisco311 on 2008-07-23
> **orphefs said:**
> not only 2 hours, more than that!!! However, i think its a way for me to learn Linux well! Do you know of any good tutorials I can use??? :)
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)
[https://help.ubuntu.com/](https://help.ubuntu.com/)
[http://www.ee.surrey.ac.uk/Teaching/Unix/](http://www.ee.surrey.ac.uk/Teaching/Unix/)

i didn't found any tutorial about using the GUI. 
maybe because it's banal:)

---

### Post by orphefs on 2008-07-23
thanks man! 

nah, no worries, I always wanted to know other command lines except MSDOS!!! If I wanted a GUI, I'd remain inside windows!!! Thanks for your help again, it's appreciated!!!:)

---

### Post by doomslagen on 2008-07-23
have similar problem...please see my thread and help me!!!

---

