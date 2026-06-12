---
title: "GRUB 17 when a second drive is connected."
date: 2008-10-22
forum: Installation &amp; Upgrades
---

### Post by Gallo_Pinto on 2008-10-22
Hi all. I've read every bit of info on GRUB error 17 that I can understand, and I haven't managed to fix this problem.

I just decided to reinstall my OSs. On my 160-Gig SATA drive I first installed XP, creating a new MBR, then Kubuntu. Everythign was good so I connected up my 80-Gig IDE drive (in FAT32) which contained all my stuff- Photos, Music etc. Whenever I turned on the PC with this seecond drive I got GRUB error 17, without it everything is okay.

Suspecting that I had some wierd MBR clash, I backed up the 80-Gig drive to my Linux partition on the 160 drive. The 80-Gig drive has been reformatted in FAT32 and EXT3, and after both reformats GRUB was restored using the kubuntu live disc. None of these 4 variants worked.

So you see, I now am stuck without being able to reinstall to my 160 drive becuase it contains my important data, and I can't do anything at all with both drives connected. I'm quite at a loss.

Thanks very much for any suggestions.

---

### Post by Pumalite on 2008-10-22
You have a problem of mixzed IDE and SATA drives. Grub tends to boot IDE. Check this thread:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)
It might be that all you need to do is change the boot order in BIOS

---

### Post by caljohnsmith on 2008-10-22
Are you getting the Grub error 17 before you see a Grub menu or after you get the Grub menu and choose an OS?

Also, please open a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
So replace "sda" above with each of your drives. And finally, for each command above that returns "GRUB", please post:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] bs=1 skip=1049 count=2 2>/dev/null | hexdump
```
And replace sda with the drives that previously returned "GRUB". That will greatly clarify what your setup is like.

---

### Post by Gallo_Pinto on 2008-10-24
Thanks to both of you for your responses. I'm still looking through some links, Puma, and may find something useful yet.

-+ EDIT - Changing boot order in the BIOS does not make any difference. Following your links, someone suggests putting the MBR in the IDE drive. I would prefer not to have an MBR on my mass-storage disk, because that would undermine the purpose of keeping it separate. Interestingly to note, my BIOS has, I think, 3 or 4 boot device slots, meaning I can set 1st, 2nd, etc.. boot devices. With my previous setup (XP und ubuntu 7 installed in precisely the same way), all of the boot devices were set to "none" and an option called "boot other device" was enabled. At the time, that was the only way I could get it to work! It was 100% reliable, and my PC is switched on and off 2 or 3 times a day. +-

caljohnsmith; I have done as you said from the kubuntu live session. The returns from the commands look to be the same as they are installation, but since I can't get to the installation with both disks in use... I can't be positive. Anyway, here goes:


```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7ca2788c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   163846934    81923436    7  HPFS/NTFS
/dev/sda2       163846935   312576704    74364885    5  Extended
/dev/sda5       163846998   306504134    71328568+  83  Linux
/dev/sda6       306504198   312576704     3036253+  82  Linux swap / Solaris

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3e503e4f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   160071659    80035798+   b  W95 FAT32
ubuntu@ubuntu:~$ sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdum                                                                        p
0000000 ff04
0000002
ubuntu@ubuntu:~$ sudo dd if=/dev/sdb bs=1 skip=1049 count=2 2>/dev/null | hexdum                                                                        p
0000000 8105
0000002
```

I didn't post the code for that command, but both drives came back with "GRUB"

---

### Post by caljohnsmith on 2008-10-24
OK, if both of your HDDs returned "GRUB" when you did that dd command, that means you have Grub installed to the MBR of both those drives. But according to the second dd commands you ran, the Grub on your 80 GB data HDD points incorrectly to the wrong Kubuntu partition on your other drive; that means if you boot from your 80 GB drive, you would get the Grub error 17. But Grub appears to be correctly installed to the MBR of your SATA 160 GB drive, so I think your only problem is figuring out how to boot the SATA drive before your 80 GB IDE drive on start up. 

If for some reason you can't get your BIOS to boot the SATA drive before the IDE drive, one thing you could do that might help would be to get rid of Grub in the MBR of your 80 GB data drive, so then BIOS might default to booting the SATA drive since you have the "boot other device" option in your BIOS enabled. To do this, from your Kubuntu Live CD, run the following command:
```
sudo dd if=/dev/zero of=/dev/sdb bs=440 count=1
```
Make sure you copy and paste that command and get it exactly right, because the dd command can be quite dangerous if you're not careful. The above command overwrites Grub in the MBR of the sdb drive with all zeros. 

If that doesn't work to boot your SATA drive, then the other alternative would be to go ahead and install Grub again to the MBR of the IDE drive, but have it correctly point to Kubuntu on your SATA drive. Then you shouldn't get the Grub error 17. The disadvantage is that the drives will be dependent on each other; if one drive has any problems you might not be able to boot at all. Let me know how it goes though with deleting Grub from the IDE drive, and we can work from there. :)

---

### Post by Gallo_Pinto on 2008-10-24
-+ EDIT - I had posted a bunch of drivel, but now I'll get down to business

Removing GRUB from the IDE drive worked fine. However, problems persist. I'm feeling that perhaps having grub on the IDE is just a necessary evil, and I'm willing to try that. After all, I can always restore GRUB to the SATA later if needed.

A question on the side. When I installed kubuntu, there was a checked box in the "format" column for the main ext3 partition, but not for the swap. Is there a way to test, just to be sure that my swap is working correctly?

Thanks again to all responses.

---

### Post by meierfra. on 2008-10-24
You never answered this question from caljohnsmith

> Are you getting the Grub error 17 before you see a Grub menu or after you get the Grub menu and choose an OS?


[B]If your grub menu does not  appears:
[/B]

Are you still getting Grub Error 17?  Or Grub error 22?
 
Just a quick explanation why you are still getting a grub error:

Yours bios are set to boot from the ide drive, so the bios will report the ide  drive as the boot drive, even though it is the sata drive which does the actually booting.  Grub on the sata drive contains instruction to look for Grub's stage2 on "FF04",  which means on  fifth partition of the boot drive.    So Grub is looking for the fifth partition on the ide drive, which does not exists


Did you try switching the boot order in the bios?  That should be the easiest way to solve your problem.


Otherwise you  can either reinstall grub to then mbr of the sata drive via 

```
sudo grub
```
and at the grub prompt:

```
device (hd0) /dev/sda

device (hd1) /dev/sda

root (hd1,4)

setup (hd0)

```


or your can install grub to the MBR of the IDE drive via:

```
sudo grub
```
and at the grub prompt:

```
device (hd0) /dev/sdb

device (hd1) /dev/sda

root (hd1,4)

setup (hd0)

```


**If your grub menu appears:  **
you probably just need to edit the file "menu.lst".

---

### Post by Gallo_Pinto on 2008-10-26
Response to meierfra.:

I had been getting error 17 before seeing GRUB. Changing the BIOS boot order did not help. After following your command to  install on IDE exactly, I am now one step closer. I get error 22 after selecting ubuntu from GRUB.

I suppose I may have to figure out how to edit menu.lst on sdb (I believe the command I've used before will edit it from sda), or perhaps (hd1,4) is the wrong partition with the "root" command.

At any rate, thanks for the post. I'm definately a little further ahead now.

---

### Post by Pumalite on 2008-10-26
When you get to ubuntu in Grub; hit 'e' and 'e' again. Try different combinations unt5il you get it. Press 'Enter' to return to Grub, 'b' for boot. Then edit your menu.lst and make the changes permanent in 'groot' and 'root'

---

### Post by meierfra. on 2008-10-26
Follow Pumalite's advice. Change root to  "root (hd1,4)" or "root (hd0,4)".  To edit menu.lst (after you booted into ubuntu) use

```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by Gallo_Pinto on 2008-10-27
Alright soldiers, that hit it where it counts. I changed all lines reading "boot (hd0,4)" to (hd1,4). I didn't find any lines with "groot" but as long as it's working, I don't care.

I'd love to say "thanks" and call it case closed, but unfortunately I can't get into windows. I have tried all possible partitions on hd0 and hd1, most of the time it lets me press enter tog et back to GRUB but sometimes it just hangs.

But at least I can get my homework done for monday classes now :)

Sorry about the prolonged problems. All 3 of you have been very helpful.

---

### Post by meierfra. on 2008-10-27
> I didn't find any lines with "groot" but as long as it's working, I don't care.

"#groot=(hd0,4)"  is at  line 74 of menu.lst (or somewhere close to that).
Change it to "#groot=(hd1,4)", otherwise you will run into problems after the next kernel update.

> I can't get into windows. 

Change your Windows item in menu.lst to

```
title Windows XP
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```


If  that does not work, please describe exactly what happens after you selected Windows XP at the grub menu,

---

### Post by Gallo_Pinto on 2008-10-27
Ah, I had been looking for another "groot" entry without the "#"

Anyway, it looks like everything's under control. Thanks again for all the help. I'll stop bothering you now.

---

