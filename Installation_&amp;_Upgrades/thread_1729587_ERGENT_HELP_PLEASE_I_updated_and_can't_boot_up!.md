---
title: "ERGENT HELP PLEASE I updated and can't boot up!"
date: 2011-04-15
forum: Installation &amp; Upgrades
---

### Post by amidamaru on 2011-04-15
Okay so I was previosly on kubuntu 10.10 and wanted to update to 11.04 halfway throughout the process the LAPTOP overheated and shut down now as I boot I reach a grub menu and I select the first option then it coma up with a blue  screen saying the disk drove for / is not ready yet press S to skip or M for manual. I pressed S and it says the disk drive for /tmp is not ready then it goes to a black screen and says mountall: Plymouth command failed then underneath it says Mountall: disconnected from Plymouth please help  I need all the files on the LAPTOP thanks in advance

---

### Post by Zorael on 2011-04-15
You can retrieve all files and probably even restore the system if you can get your hands on a live CD or USB pendrive. If you don't have a computer to do this with, you'll have to borrow someone else's.

It requires some extensive terminal work to restore it. I had to do this yesterday (for an altogether different reason) so I have it semi-fresh in memory. It really depends on how far into the installation you were when it crashed. You may want to ensure that it doesn't overheat this time too. :3

[list=1][*]Download a Kubuntu [10.10](http://releases.ubuntu.com/kubuntu/10.10/) (or [11.04](http://cdimage.ubuntu.com/kubuntu/daily-live/current/) or other) iso
[*]Prepare a live medium
[list][*]If USB pendrive, download [Unetbootin](http://unetbootin.sourceforge.net/) and use it to extract the iso onto the pendrive
[*]If CD, burn the iso onto it using your CD burning program of choice[/list]
[*]Boot it on the laptop that failed to upgrade
[*]Pick *Try Kubuntu* or whatever it says, to get to a desktop session
[*]Set up an Internet connection and test it to see it works
[*]Mount your root partition somewhere. You'll need to know the device node of it, like **/dev/sda1**. You can get this information in many places, like in any partition manager (eg. the great [**GParted**](apt://gparted) or the less powerful [**PartitionManager**](apt://partitionmanager)), or by merely running '**sudo fdisk -l**' in a terminal and trying to understand the output
[list][*]Example of mount procedure:```
ubuntu@ubuntu:~$ mkdir ~/root
ubuntu@ubuntu:~$ sudo mount **/dev/sda1** ~/root
```[/list]
[*]Set up a **[chroot](https://help.ubuntu.com/community/BasicChroot)** to that mountpoint. Example assuming you mounted the root partition to **~/root** (like above):```
$ sudo mount --bind /dev ~/root/dev
$ sudo mount --bind /dev/pts ~/root/dev/pts
$ sudo mount --bind /proc ~/root/proc
$ sudo mount --bind /sys ~/root/sys
$ sudo cp /etc/resolv.conf ~/root/resolv.conf
$ sudo nano ~/root/hosts   [i]# add **ubuntu** to the end of the lines beginning
                           # with **127.0.0.1** and **127.0.1.1**
                           # they should be near the top[/i]
$ **sudo chroot ~/root**
```
[*]At this point the terminal should be "inside" your normal installation, as the user **root** (so the **$** in the terminal prompt becomes a **#**), and not in your live CD/USB environment. So let's try to fix things;```
# export ARCH="$(if [ "$(arch)" == "x86_64" ]; then echo "amd64"; else echo "i386"; fi)"
# cd /tmp
# wget "http://mirrors.us.kernel.org/ubuntu//pool/main/a/aptitude/aptitude_0.6.3-3.2ubuntu1_${ARCH}.deb" -O aptitude_${ARCH}.deb
# dpkg -i aptitude_${ARCH}.deb
# apt-get update
# aptitude install -f
```
[list][*]If it throws any error at this point, we'll need to know it to proceed. It may take several extra commands. Notably if the **wget** line fails, the chroot does not have Internet access. If you can '**ping 8.8.8.8**' and it responds (Ctrl+C to stop it) but you can't '**ping ubuntu.com**', then you didn't manage to copy the **resolv.conf** file correctly in step 7. If neither works, you can try '**dhclient eth0**', or '**dhclient wlan0**' or whatever your network device name is, to make it try to set itself up by requesting DHCP informatino from your router (or from your Internet provider if connected directly)[/list]
[*]Enter '**exit**' to exit the chroot and return the terminal to your live environment
[*]If all went well, reboot and try booting normally
[list][*]If it doesn't, boot live environment again, return here and report
[*]If it does, return here and mark thread as solved[/list]
[*]Eat your fruit and vegetables[/list]

---

### Post by amidamaru on 2011-04-15
Will do thank you I have already installed another partition and am currently running of that but is there anyway I can get my emails off the other system or shall I just go through the what looks to be painfully long? Btw my entire home folder is safe

---

### Post by Zorael on 2011-04-15
Certainly. Where they're saved depends on what email program you were using, but it's somewhere in your home directory. Akonadi saves its stuff in **~/.config/akonadi**, I believe.

You should even be able to just copy your old home into (or next to) your new one, and upon relogin you should have your old settings.

---

