---
title: "Need help with partitions"
date: 2011-07-28
forum: Installation &amp; Upgrades
---

### Post by grautskaahl on 2011-07-28
Hey guys. I hope I'm posting this in the right part of the forum...

I'm currently running Ubuntu 11.04 alongside Windows Vista and I'm running out of space on my Ubuntu partition, so I have to resize it. I did some reading here and found other threads about it, but I couldn't find anyone who had the same problem as me.

I've attached a screenshot of GParted for information. My problem is that it won't let me increase the size of the Ubuntu partition. When I decrease the size of the Windows partition it gives me unallocated space - why can't I use that to grow the Ubuntu partition?

---

### Post by vanadium on 2011-07-28
Your Ubuntu system files are in an extended partition (a trick to overcome the limitation of max 4 partitions). You are restricted to the confines of that extended partition.

3.5 GB is extremely small for an Ubuntu partition. I would try to add some space of sda7 to it, which would give you a 6-7 GB system partition, which is more workable.

- Run Ubuntu from the live CD
- Open gparted
- Delete sda7. You might first need to right-click, then select "swapoff" on order to be able to delete the partition. Click the "Apply" button to effectively commit the changes to disk.
- Delete sda5
- Expand sda6 to the right, but leave about 1 GB for a swap partition.
- Use the remaining space (up to sda4) for a swap partition (right-click, create partition - swap). Do not forget to use the "Apply" button.

This will give you more room for the system. I advise you, under your dual boot setup, to keep all user data (Documents, Movies, Audio, ...) on ntfs partitions, where you can also acces them from within Windows.

You will need to correct your swap. The easiest will be to boot into Ubuntu - the swap won't work though.
- Open a terminal, use the command "sudo blkid"
- Open /etc/fstab with root privileges: "gksu gedit /etc/fstab"
- Locate the line with "swap" in it, e.g.
```

UUID=92cd3425-35f2-901c-736g-121jhc9f8ec4 none            swap    sw              0       0

```
Replace the UUID= part of that line with the UUID="..." listed in the output of "sudo blkid" (the line of the swap partition will end with "TYPE="swap"". Just copy the UUID=... part and paste it into your /etc/fstab.

Save and exit gedit. Check whether all is OK with the command "sudo mount -a". No error should appear. After that, your swap will be in use.

---

### Post by Quackers on 2011-07-28
From a Live cd/usb desktop you can open gparted and extend the extended partition (sda3) to the left (so that no free space is before it) then resize your Ubuntu partition (sda6) into that new free space which is now within the extended partition. The second stage may take a while.

---

### Post by grautskaahl on 2011-07-28
That sounds good - I'll try it out shortly. Is that the only way to increase the size of the Ubuntu partition, though? I have some free space on the Windows partition - is it not possible to use some of that?

EDIT: that was directed at vanadium.

---

### Post by vanadium on 2011-07-28
There are different ways to go to Rome. My suggestion is a minimal suggestion, that is fast, and leaves all your Windows partitions untouched. With Quackers suggestion, you could gain more space for your Ubuntu system. It would allow you to reclaim the 3 GB after your sda2. The draawback is that you would need to move your system partition, which takes a lot of time (and may not successfully complete). At the very end, you also have unallocated space. You could extend your second Windows partition, sda4, into that.

Bottom line is that your linux partitions are within an extended partition sda3, indicated by the light blue lines. Quackers sugggests you to move the boundary of that one more in front. Then you can also move sda6, which is inside that extended partition, to the front and after that, expand it to the right.

---

### Post by grautskaahl on 2011-07-28
Ok, I tried your suggestion and removed the swap partitions, but when I went to boot back into Ubuntu, I just get this message:

```
error: unknown filesystem
grub rescue>
```

Any idea what happened?

---

### Post by YesWeCan on 2011-07-28
Backup any vital files before you do anything.
This guide may be a helpful reference: [http://www.dedoimedo.com/computers/gparted.html#mozTocId309606](http://www.dedoimedo.com/computers/gparted.html#mozTocId309606)

As has been said, you have to do this using live CD (you cannot move or resize an active partition).

---

### Post by grautskaahl on 2011-07-28
Yeah, I have backup of everything I need, so if I have to wipe the drive and reinstall the operating systems, it won't be the worst thing to happen :)

---

### Post by YesWeCan on 2011-07-28
Grub won't work now. No problem. You can either boot directly from the rescue> prompt or you can use a live CD to reinstall it.
The latter is probably slightly easier to explain.
Just identify what the partition name is of your root partition, still sda6?
Then boot a CD
[COLOR=Navy]sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
[/COLOR] 
Grub is in several parts. The part at the front of your disk has to find files in your root partition to do anything. If the root partition name has changed or if the uuid has changed it won't find it. There may be other changes that it doesn't like. When the first part of grub works but it can't find its files in /boot/grub then it stops and gives a rescue prompt.

---

### Post by grautskaahl on 2011-07-28
I tried your latter method, but the terminal just says "install_device not specified" and gives me a list of commands. I'm not getting any wireless connection with the live cd - is that why?

---

### Post by Quackers on 2011-07-28
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by YesWeCan on 2011-07-28
> **grautskaahl said:**
> I tried your latter method, but the terminal just says "install_device not specified" and gives me a list of commands. I'm not getting any wireless connection with the live cd - is that why?
Wireless has nothing to do with it. You mean the grub install command produced that error message? Make sure you put all the spaces in the right places:
sudo grub-install --root-directory=/mnt <space> /dev/sda

If that's not it then from the live CD run [COLOR=Navy]sudo fdisk -l [/COLOR]and post the result.

---

### Post by grautskaahl on 2011-07-29
> **YesWeCan said:**
> Wireless has nothing to do with it. You mean the grub install command produced that error message? Make sure you put all the spaces in the right places:
sudo grub-install --root-directory=/mnt <space> /dev/sda

If that's not it then from the live CD run [COLOR=Navy]sudo fdisk -l [/COLOR]and post the result.

Yeah, the install command gave the message. I'm pretty sure I included the spaces, but I'll give it another go.
EDIT: Now it said that the installation finished with no problems. Is there anything more or can I try to reboot now?
EDIT2: grub is back now and everything works except the wireless. It says "wireless disabled by hardware switch" - is this the wireless swith on my keyboard or something else? I tried pushing it, but nothing happens.
FINAL EDIT: Wireless is back after I booted into windows and switched the wireless on from there. I guess it's still good to keep it... Marking the thread as solved - thanks for all the help, guys!

Quackers, I can't get internet with the live cd - wired or wireless (I'm posting this from a different computer). I'm using the latest live cd with 11.04. I'll try and get the boot script onto Ubuntu otherwise.

---

### Post by Quackers on 2011-07-29
Glad you got things worked out. The boot script doesn't matter now.
Not sure what's happening with wireless in the live desktop though.

---

