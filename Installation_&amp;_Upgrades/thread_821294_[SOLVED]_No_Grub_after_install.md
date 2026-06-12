---
title: "[SOLVED] No Grub after install?"
date: 2008-06-07
forum: Installation &amp; Upgrades
---

### Post by crypticgeek on 2008-06-07
I just used 8.04 desktop install disc to resize the NTFS partition of my windows xp install and install ubuntu in the freed space. However, upon reboot it just loads windows. No grub, no nothing. How do I go about fixing the MBR up with some grub goodness?

The live CD finds my 3 hard drives. The IDE drive which is my boot drive is detected as sdc, while my 2 storage drives on SATA are sda and sdb. 

Partitioning on sdc looks something like:
```

/dev/sdc1 *     1 11301 90775251  7  HPFS/NTFS
/dev/sdc2   11302 14593 26442990  5  Extended
/dev/sdc5   11302 14451 25302343+ 83 Linux
/dev/sdc6   14452 14593  1140583+ 82 Linux swap

```
Oh, and find /boot/grub/stage1 returns (hd2,4)

I'm not really familiar with grub or ubuntu, so I wanted to be sure I didn't kill my MBR by running some of the grub commands I've seen elsewhere on the forums.

Thanks!

---

### Post by meierfra. on 2008-06-07
```
sudo grub
root (hd2,4)
setup (hd2)
quit
```


This installs grub to the MBR of boot drive.

After reboot the grub menu should appear, but you probably will get a Grub error when you try to boot into ubuntu. If this happens:

Select Ubuntu at the grub menu and press "e". At the new screen press "e" again. 
Change "root (hd?,4)" to "root (hd0,4)". Press "enter" and then "b" to boot.


This should boot you into Ubuntu. You need to make these changes permanent:


```
gksudo gedit /boot/grub/menu.lst
```

Change "#groot (hd?,4)" to "#groot (hd0,4)"

Change you Windows item to

title what ever
root (hd0,0)
chainloader +1


Save the file.

In the terminal

```
sudo update-grub
```

and you should be all set.

---

### Post by abhiroopb on 2008-06-07
Don't worry its very simple.

First load up a liveCD, open a terminal and type in the following:

```

    sudo grub

    > root (hd2,4)

    > setup (hd2)

    > exit

```
I have done root(hd0,1) because I am assuming that from your partition "Linux" is where Ubuntu is installed (and so is the /boot folder) and so it is the fifth parition on your THIRD hard drive. hd(0,0) would be first hard drive, first partition, hd(0,1) is first hard drive SECOND partition, and so on. after you do this and reboot you should have Grub back.

To add windows back to your grub:
```
sudo gedit /boot/grub/menu.lst

```
In the text editor put in the following:
```

title   Windows XP
root   (hd2,0)
makeactive
chainloader   +1

```
Save and restart

---

### Post by meierfra. on 2008-06-07
There is a second solution:

Change the boot order in the bios, such  that the Ubuntu Drive is last and /dev/sda is first. (No reinstalling grub or editing menu.lst is  required for this solution.)

---

### Post by abhiroopb on 2008-06-07
Not totally sure but this may not put Windows back in grub, again not sure. Editing menu.lst and reinstalling grub is really painless anyway, and it works easy enough.

Also there is an error, the windows one should be 

title what ever
root **(hd2,0)**
chainloader +1

as I think he said this is the third hard drive.

---

### Post by meierfra. on 2008-06-07
Since abhiroopb seems to  disagree with my solutions, here is a short explanation:

As you can see from fdisk Ubuntu thinks that sda is the first hard drive and so installed Grub to the MBR of sda.
It also wrote menu.lst accordingly. So menu.lst currently uses (hd2,4) for Ubuntu and (hd2,0) for Windows.


You have two options: 

1)  Keep your Ubuntu drive as the boot drive. Then you have   to install Grub to the MBR of the Ubuntu drive. But  grub always sees the boot drive as (hd0). So menu.lst needs to be changed,  Ubuntu becomes (hd0,4) and Windows (hd0,0).

2)  Order the hard drives  in the bios in the  same way Ubuntu sees them. Then you will not have to reconfigure grub. (Since Ubuntu was installed after Windows, it should have detected Windows, and added it to menu.lst)

---

### Post by crypticgeek on 2008-06-08
> **meierfra. said:**
> 
1)  Keep your Ubuntu drive as the boot drive. Then you have   to install Grub to the MBR of the Ubuntu drive. But  grub always sees the boot drive as (hd0). So menu.lst needs to be changed,  Ubuntu becomes (hd0,4) and Windows (hd0,0).


Thanks for that. abhiroopb's instruction's I carried out, but didn't initially work to fix booting into ubuntu because they each had a seperate root line. When you said grub sees the boot drive as  hd0 it clicked that I needed to change the root line of all the other boot entries. All is well now though, and I learned a bit about grub in the process...so that's not so bad is it? :D

---

### Post by meierfra. on 2008-06-08
Did you change  "#groot (hd?,4)" to  "#groot (hd0,4)"

Otherwise all you "root ...' changes will be undone during the next kernel update.

---

### Post by matre on 2008-06-09
I had exactly the same problem on a new vista machine I am dual booting with hardy.  I have two HD's and grub did not appear at all after installation,just booted directly into Vista. 

The solution from meierfra to change the HD boot order in bios was a quick and easy solution for me.

---

