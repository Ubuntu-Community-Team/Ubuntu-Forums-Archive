---
title: "Unable to fix dual boot"
date: 2008-04-20
forum: Installation &amp; Upgrades
---

### Post by robertsaron on 2008-04-20
I have 2 hard drives (actually more but only working with 2), i bought a SATA pioneer dvd burner. I have 8 on board SATA controllers. I wiped all my drives, then installed linux onto the drive attached to SATA 1.

 All my drives were plugged into SATA controllers on the board 1-4, the SATA burner was plugged into sata controller 5. I then wanted to install windows vista. How ever windows would not recognize the drive partway through the install.

I then moved some of the drives to sata controllers 5-6, and then moved the sata burner to sata controller 3. my linux drive is on sata controller 1, and i wanted my windows drives on sata controller 2.

In order to install vista I had to disconnect my linux drive. Only reason I want vista installed is to play games, as some of the games do not work through wine. To boot to my linux drive, I have to flip the drive order in the BIOS. According to my boot order when booting to my linux drive, it still sees XP. How do I get rid of that and set up a dual boot for vista?

I have tried the command from a live CD and from with my linux partition. 

sudo grub
find /boot/grub/stage1
root (hd0,o)
setup (hd0)

Does not fix grub to see vista. I really dont want to wipe my and reinstall my linux partition though I know that would fix it.

---

### Post by jnorthr on 2008-04-20
Dunno about this - just a guess, but i remember reading that you need to install windows on the first possible drive of the first controller, Only then would linux successfully take it's place as the second installation on your system. Doing it this way, grub becomes resident in your MBR (wiping out the M$ boot loader) and it has the smarts to see the first o/s - vista in your case -  and offer you the choice at boot time as to which o/s you want.

---

### Post by martrn on 2008-04-20
At  a guess you might have the wrong hd numbers listed in your grub config files.:

Type
    ```
 ls /dev/disk/by-id -lah
```
To list your  hard drive devices.

Check your /boot/grub/menu.lst file to check this matches your new device listings.
ad retry and check that your devices match what you are telling grub to actually do..

Look at grub:
```
nano /boot/grub/menu.lst
```

---

### Post by robertsaron on 2008-04-21
Ill try these options that were posted. I had the vista drive connected to Sata ctroller 3, and the burner to controller 2. I have since switched it them. I must say if it wasnt for video games, i wouldnt even use windows. 

some thing i am going to try and do, is command prompt at vista install, and then fix mbr, and then the find grub command.

---

### Post by confused57 on 2008-04-21
> **robertsaron said:**
> Ill try these options that were posted. I had the vista drive connected to Sata ctroller 3, and the burner to controller 2. I have since switched it them. I must say if it wasnt for video games, i wouldnt even use windows. 

some thing i am going to try and do, is command prompt at vista install, and then fix mbr, and then the find grub command.
You could set your Ubuntu drive first in bios...then try different menu.lst entries to boot Vista:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```
Then try several different Vista entries, e.g.
```
title  Windows Vista as (hd1)
root  (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

```
title  Windows Vista as (hd2)
root (hd2,0)
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1
```

```
title  Windows Vista as (hd3)
root (hd3,0)
makeactive
map (hd0) (hd3)
map (hd3) (hd0)
chainloader +1
```

You could add the above & keep the one that hopefully works.

---

### Post by robertsaron on 2008-04-21
Thanks for all the help everyone. 

Some new developments. 

I changed the drives around on the SATA controllers. my linux drive is on SATA 1, vista drive was changed from sata controller 3 to 2, which then allowed me to boot straight into linux, i no longer had to go into the bios.

I then loaded the vista ultimate dvd, and then had it do a repair on the  MBR. Of course after rebooting, it gave me a kernel error. I then loaded my live cd, and fixed grub (sudo grub  find /boot/grub/stage1 ... etc) and my linux drive is hd3.

I can post the output of my menu.lst file if anyone wants to look at it. According to the menu.lst my windows drive is (hd1,0) though it still shows it as xp.

Am I correct in saying that if I found out what drive my vista drive is, and properly modded my menu.lst, then I could boot to my vista drive? 

If that is the case I do not know how to do it.

---

### Post by confused57 on 2008-04-21
> **robertsaron said:**
> Thanks for all the help everyone. 

Some new developments. 

I changed the drives around on the SATA controllers. my linux drive is on SATA 1, vista drive was changed from sata controller 3 to 2, which then allowed me to boot straight into linux, i no longer had to go into the bios.

I then loaded the vista ultimate dvd, and then had it do a repair on the  MBR. Of course after rebooting, it gave me a kernel error. I then loaded my live cd, and fixed grub (sudo grub  find /boot/grub/stage1 ... etc) and my linux drive is hd3.

I can post the output of my menu.lst file if anyone wants to look at it. According to the menu.lst my windows drive is (hd1,0) though it still shows it as xp.

Am I correct in saying that if I found out what drive my vista drive is, and properly modded my menu.lst, then I could boot to my vista drive? 

If that is the case I do not know how to do it.

Open a terminal(Applications---Accessories---Terminal), then you can just copy & paste the commands I gave you in my other reply...Add the Vista entries I've listed to the very end of your menu.lst(after the line ###END DEBIAN AUTOMAGIC KERNELS LIST).  One of the entries "should" work...keep the one that works & delete the others.

---

### Post by robertsaron on 2008-04-22
That worked, thanks for the help. it was hd2. so in theory i could take a drive with an OS on it, and pop it into my computer, and then modify the menu.lst, and it should boot?

---

### Post by confused57 on 2008-04-23
> **robertsaron said:**
> That worked, thanks for the help. it was hd2. so in theory i could take a drive with an OS on it, and pop it into my computer, and then modify the menu.lst, and it should boot?
In theory, yes...I don't have personal experience doing this, but it shouldn't be a problem with Ubuntu or Windows(never used OSX).  For other Linux distros, you may need to edit the root=???? in the kernel line of the distro's menu.lst or grub.conf.

---

