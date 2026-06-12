---
title: "Removing dual boot ?"
date: 2010-07-20
forum: Installation &amp; Upgrades
---

### Post by lucasart on 2010-07-20
Hello everyone,

I have installed Ubuntu 10.04 first. Then I installed another distribution, to play with it and see if I liked it: Lubuntu 10.04. That means my hard drive looks like this now

```

lucas@lucas-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
[COLOR=Green]/dev/sda1             358G  6.3G  333G   2% /[/COLOR]
[COLOR=Blue]none                  2.0G  296K  2.0G   1% /dev
none                  2.0G  116K  2.0G   1% /dev/shm
none                  2.0G   84K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
none                  2.0G     0  2.0G   0% /lib/init/rw[/COLOR]
[COLOR=Red]/dev/sda6              89G  1.6G   83G   2%  /media/9a57ce41-9d60-43be-a9ba-519fc6f331a4[/COLOR]

```

In green is my Ubuntu that I wish to keep. In red is Lubuntu that I want to remove. And in blue, I imagine is the part called "swap" when I installed Ubuntu, that would remain unchanged. So what I want to do precisely is as follows:

1/ Delete the partition /dev/sda6
2/ resize the partition /dev/sda1 to take the space that it freed
3/ reconfigure the GRUB so that I don't get asked to dual boot and it goes back directly in Ubuntu as it would prior to installing Lubuntu.

Any idea how to do all this ?

---

### Post by thahir1986 on 2010-07-20
I also installed dual boot (ubuntu 9.04 and 8.04). First i had the ubuntu 9.04 and after that i installed the ubuntu 8.04 for some specific reason. After i had removed the ubuntu 8.04 i can't boot into the ubuntu 9.04. and then i reconfigure the grub thru 9.04 live cd...

So u r correct.....

---

### Post by lucasart on 2010-07-20
> **thahir1986 said:**
> I also installed dual boot (ubuntu 9.04 and 8.04). First i had the ubuntu 9.04 and after that i installed the ubuntu 8.04 for some specific reason. After i had removed the ubuntu 8.04 i can't boot into the ubuntu 9.04. and then i reconfigure the grub thru 9.04 live cd...

So u r correct.....

Erm... So how do you first remove a partition ? is there a simple command to do it ?
I've looked at the manual page of the fdisk command, and it's typically written by geeks for geeks, and incomprehensible to humans...

Anf then resize ?

---

### Post by varunendra on 2010-07-21
> **lucasart said:**
> I've looked at the manual page of the fdisk command, and it's typically written by geeks for geeks, and incomprehensible to humans...
Soooo... funny ! :lol:

The easiest way to do what you want is to use GParted. Boot from CD, goto System>Administration>GParted.
Delete sda6 (make sure it is the one where Lubuntu is installed). Creating a new partition would be better than shifting/resizing the existing ones.

Now reboot into installed Ubuntu 10.04 and run:
```
sudo update-grub
```
Be careful while using gparted. While it is very easy to use, making a wrong selection can ruin both your installations. If you have any doubts or want to play safe, run and post the output of the following script:
                 [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
(courtesy of Forum member Meierfra)


**EDIT:** *Oh well.... the output of the above script is quite comprehensible to humans - be assured!! :D*

---

### Post by lucasart on 2010-07-21
> **varunendra said:**
> Soooo... funny ! :lol:

The easiest way to do what you want is to use GParted. Boot from CD, goto System>Administration>GParted.
Delete sda6 (make sure it is the one where Lubuntu is installed). Creating a new partition would be better than shifting/resizing the existing ones.

Now reboot into installed Ubuntu 10.04 and run:
```
sudo update-grub
```Be careful while using gparted. While it is very easy to use, making a wrong selection can ruin both your installations. If you have any doubts or want to play safe, run and post the output of the following script:
                 [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
(courtesy of Forum member Meierfra)


**EDIT:** *Oh well.... the output of the above script is quite comprehensible to humans - be assured!! :D*

Thanks for gparted. It doesn't seem to be able to modify mounted partitions so I have to do it from a CD live boot indeed: I can't just cut the grass under my feet obviously, but neither can I resize the lawn and make it bigger ;-) - that's more like human language, lol

Unfortunately it's a bit more complicated. Once the Lubuntu sda6 is removed and the Ubuntu sda1 is resized to take that space, I reboot... and... bad luck

I end up in a grub command line mode, where all I can do is type grub commands... Obviously I don't speak grub. Do you happen to know how to say in grub language that I want the default boot to happen on sda1 instead of sda6 ? (which is dead now, explaining the crash on hd boot).

---

### Post by oldfred on 2010-07-21
Your grub in the MBR must have used the Lunbuntu to boot??

You can reinstall grub from the liveCD

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Install from LiveCD install on sda5 and want grub2 in drive sda's MBR:
Find linux partition, change sda5 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
sudo mkdir /mnt/sda1
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sda

I am not one to like very large system partitions. Filecheck can take forever although ext4 is quicker. Many prefer a separate /home or I prefer seperate /data partitions as I do multiple installs, so far all Ubuntu.

---

