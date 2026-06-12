---
title: "I want to install ubuntu 10.10 with the ability to dual boot with windows 7"
date: 2011-05-01
forum: Installation &amp; Upgrades
---

### Post by ajlinzey on 2011-05-01
I found these [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu) instructions for installing an ubuntu /windows 7 dual-boot. I have a separate 500 Gb hard drive that I want to load ubuntu onto. These instructions say 'do not press the advanced button and make changes' which is the only way to put ubuntu on separate hard drive. My bios lets me hit f10 and pick the drive to boot from that way. The drive  I want to put ubuntu on shows up as /dev/sda so I think I should pick that drive as the location for both ubuntu and the boot loader? is that right?
-Andy

---

### Post by Dutch70 on 2011-05-01
If you want to be 100% sure you don't botch windows, temporarily disconnect the hard drive that contains windows until you get ubuntu installed. 

Once you make sure Ubuntu is working, Shut it down & reconnect your other hdd. 
Then boot into Ubuntu and run the following command.
```
sudo update-grub
```
That will cause the Grub boot loader to pick up windows, and you'll be able to boot to either from the grub menu. 
I'ts very little trouble to unplug an hdd, and the method is nearly fool proof. That's why I use it. :P

tips...
1. After unplugging the power cord, hold the power button in for a couple seconds.
2. Touch the power supply before touching anything else inside your computer. (to discharge static ele. in your body)

---

### Post by oldfred on 2011-05-01
+1 on Dutch's disconnect drive. 

If you cannot disconnect drive you have to use manual install and partitioning, which for a second drive I recommend.

Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by ajlinzey on 2011-05-02
Thanks I'll give it a try. I probably won't get to it till the weekend. Do I have to worry about how the bios sees the hard drives i.e. which one is /dev/sda and /dev/sdb
-andy

---

### Post by oldfred on 2011-05-02
For windows it seems to make more of a difference. Not sure if win7 is better or not.
With Ubuntu it does not really make a difference as it uses UUIDs. It will think it is installed to sda , but search by UUID to find correct partition to boot from.

Just be sure to reconnect windows drive to same (first) connection. Do not switch them. In BIOS after installing and reconnecting you make the Ubuntu drive the boot drive. Then the update-grub command will find windows and add it to your boot menu.

---

