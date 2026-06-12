---
title: "GRUB Confusion!!!!"
date: 2008-10-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by finch127 on 2008-10-05
You know, I was on ubuntu 8.04 a few hours ago./

I just did the beta transition to Intrepid, and it screwed up my drivers,etc

I wanted to go back to 8.04 so i pulled out my live CD, installed and then I tried to boot

Everytime I selected the kernel i wanted, it gave me Error 17

When I selected my windows drive, it said grub stage 2, and then it loaded back into the same menu

I then installed 8.10 from a live cd.

Same problem, except now I cant even see the windows drive or boot into it. Im writing from a livecd and im screwed. I cant even boot into Linux regularly from the hard drive, having done a full install

My layout is as follows (i dont know much about this linux and drives stuff)

first disk:
Seagate SCSI, 18 gigs
Windows on sda1

second disk:
Maxtor SATA, 40 gigs
Linux on sdb1 i think

I dont know where the bootloader is but I want to wipe all the records of one and reinstall the boatloader or whatever I can do so that I can dual boot again!!!! or even just into linux!!!! Thanks in advance, and please reply!!!!

---

### Post by caljohnsmith on 2008-10-05
To start with, how about posting:
```
sudo fdisk -lu
```
And also please identify all your partitions that are listed.

---

### Post by finch127 on 2008-10-05
thank you for replying friend

here is the output:

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 18.3 GB, 18351959552 bytes
255 heads, 63 sectors/track, 2231 cylinders, total 35843671 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6c6c6c6c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    35824949    17912443+   7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9c849c84

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    74862899    37431418+  83  Linux
/dev/sdb2        74862900    78156224     1646662+   5  Extended
/dev/sdb5        74862963    78156224     1646631   82  Linux swap / Solaris

---

### Post by finch127 on 2008-10-05
i think sda1 is windows

and the rest are linux related

---

### Post by caljohnsmith on 2008-10-05
So do you know which HDD you are booting from on start up?

Also, please post the output of:
```

sudo dd if=/dev/sda bs=512 count=1 2>/dev/null | strings | grep -i grub
sudo dd if=/dev/sdb bs=512 count=1 2>/dev/null | strings | grep -i grub
sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump
sudo dd if=/dev/sdb bs=1 skip=1049 count=2 2>/dev/null | hexdump

```

---

### Post by caljohnsmith on 2008-10-05
Finch127, I've got to get going and won't be around again until tomorrow morning (~10 hrs). So in the meantime, if you want to try reinstalling Grub to your Ubuntu HDD, just do:
```
sudo grub
grub> find /boot/grub/stage1

```
That command should return your Ubuntu partition as (hd1,0), and if it does, continue with:
```

grub> root (hd1,0)
grub> setup (hd1)
grub> quit
```
That will install Grub to the MBR (Master Boot Record) of your Ubuntu HDD. If you are instead booting from your Windows drive on start up, you can install Grub to the MBR of the Windows drive by using "setup (hd0)" in the above commands instead of "setup (hd1)". Good luck, and if you need some more help, I'll be around tomorrow. :)

---

### Post by finch127 on 2008-10-05
thank you for your help my friend, but i will need to try these tomorrow as well, however i am clueless as to which drive it tries to boot from.

i will post all of the outputs and try reinstalling grub tomorrow and i will let you know if it works

also just curious but do you think intrepids installer can link to a windows bootloader like hardy? b/c my original hardy install had both ubuntu and windows flawlessly but the new intrepid didnt even detect windows drives or partitions

---

### Post by finch127 on 2008-10-06
ubuntu@ubuntu:~$ sudo dd if=/dev/sda bs=512 count=1 2>/dev/null | strings | grep -i grub
GRUB 
ubuntu@ubuntu:~$ sudo dd if=/dev/sdb bs=512 count=1 2>/dev/null | strings | grep -i grub
GRUB 
ubuntu@ubuntu:~$ sudo dd if=/dev/sda bs=1 skip=1049 count=2 2>/dev/null | hexdump
0000000 8100                                   
0000002
ubuntu@ubuntu:~$ sudo dd if=/dev/sdb bs=1 skip=1049 count=2 2>/dev/null | hexdump
0000000 ff00                                   
0000002
ubuntu@ubuntu:~$ 




those are the outputs

---

### Post by finch127 on 2008-10-06
i tried installing grub on hd1 like you said above but it did not work, it returned error 17 cannot mount partition

also I will be going out of town until friday, so anything you post I will not be able to test (bad timing, I know)

thank you for help so far though!

---

### Post by caljohnsmith on 2008-10-06
According to the output of those commands you posted, you have Grub installed to the MBR of both your drives, so there is still ambiguity of which drive is being booted on start up. Can you go into your BIOS and set it so the linux drive sdb is the first to boot up? That would be the most ideal, because then you can reinstall a Windows MBR to your Windows drive sda, and both drives will be independent of each other; then if have problems with your Ubuntu drive (or disconnect it), you can still boot your Windows drive, and vice versa. 

Try changing your BIOS to boot sdb first, and then when you get the Grub menu on start up, press "c" to get the Grub CLI. Then do:
```
grub> geometry (hd0)
```
That will show you which is the boot drive; if it shows your sdb drive (you should see three partitions listed), you're all set, and we can tweak your Grub's menu.lst file so that you can boot either Ubuntu or Windows.

Next, to boot into Ubuntu, first reboot and get the Grub menu, select Ubuntu, hit "e" to edit it, select the line that says "root (hdX,0)" where X is either 1 or 0, press "e" to edit it, and if X is 1 then change X to 0, or if X is 0 then change X to 1. Press return to save the change, then press "b" to boot. Based on the info you gave, I think that should be all it takes to boot Ubuntu. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent if it works. 

So if it works, when you get into Ubuntu, just do:
```
gksudo gedit /boot/grub/menu.lst
```
And change the line that says "#groot=(hdX,0)" to use whichever (hdX,0) you found that worked. Save, quit gedit, and then run:
```
sudo update-grub
```
And you should be all set about booting Ubuntu at least. If you can get this far we can then tweak your Grub menu to boot Windows too, but let me know how it goes or if you run into problems. :)

---

### Post by finch127 on 2008-10-06
my god that worked!!! thank you so much, i can actually boot now, into ubuntu at least, thats great

i love intrepid, but man ive been beating my brains out over this

i cant thank you enough!!

---

### Post by caljohnsmith on 2008-10-06
That's great news--I'm glad you can boot Ubuntu now. :) So which (hdX,0) worked? I hope it was (hd0,0), because that would mean you are booting the Ubuntu sdb drive on start up. If that is the case, you can add the following entry to your menu.lst to boot Windows, and it should work if there are no other issues with Windows:
```
title	   Windows
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
One more thing you will probably want to do is restore a Windows MBR to your Windows HDD so you can boot into Windows from that drive independent of your Ubuntu drive. But first let me know what happens when you choose the above Windows entry from Grub on start up.

---

### Post by finch127 on 2008-10-06
well ubuntu works good now, i can keep booting in and out

but windows, whenever I select windows it says

starting up...
GRUB _


i presume because there is no bootloader?

---

### Post by finch127 on 2008-10-06
(I will be leaving shortly so I think that about does it, but I presume all I would need to do is restore the windows bootloader to my drive SCSI? I have the cd with windows and i know how to use fixmbr, so i think thats the way to go.)

Again thank you very much!

---

### Post by caljohnsmith on 2008-10-06
If you used the Windows entry from post #12, it tries to boot the Windows partition; so if you are getting that strange Grub behavior, I would start by reinstalling the boot sector of the Windows partition, which you can do with:
```
fixboot
```
And like you mentioned, be sure to also run:
```
fixmbr
```
To install a Windows MBR into that drive. Also, I would also run:
```
chkdsk /r
```
To make sure there aren't other file system issues. If you still can't boot Windows from Grub after doing the above commands, then try changing your BIOS to directly boot the Windows drive and see if Windows boots that way. Let me know what happens and we can work from there.

P.S. I'm going to also be leaving in about half an hour and won't be back until tomorrow morning probably. We can pick up from there if you are still having problems.

---

### Post by finch127 on 2008-10-18
alright, so sorry to bother you again

but man...

after some time of great linuxing, i was in a system update and the power went out right when it was doing my kernel headers etc.

now when ever i try to start up in grub, it says error 15 file not found!

(and i decided to ditch windows, so the other issue is not longer a concern)

---

### Post by finch127 on 2008-10-18
oh and for some reason, memtest 86+ works?

 i tried it, it did some stuff and rebooted

---

### Post by caljohnsmith on 2008-10-18
Sorry to hear you ran into problems again. Is Ubuntu still the same as before, on the sdb drive? If so, from your Live CD first do:
```
sudo fsck -y /dev/sdb1
```
Let me know if that returns any errors, and then continue with:
```
sudo mount /dev/sdb1 /mnt
sudo blkid
ls -l /mnt/boot
cat /mnt/boot/grub/menu.lst

```
Note the "-l" is a lowercase L, not a one. Please post the output of all the above commands, and we can work from there.

---

### Post by finch127 on 2008-10-18
actually, dont worry about it, thanks to what you taught me i fixed it

i realized that the only way that would happen is if menu.lst was not updated after the headers were installed so sure enough, i booted with livecd and i looked at the /boot folder

i saw vmlinuz blah-blah.7-generic and img blah blah.7-generic

but when i went to menu.lst, there was a 5 instead of a 7 on the entry just like i thought, so i used sudo gedit and replaced the 5's with 7's and rebooted

the error 15 was because it was trying to boot from the earlier kernel and the new one was there but it did not know about it, i suppose

but then everything worked like a charm, ill just re update and plug up the battery just to be sure :D

thanks for your help though man!

---

