---
title: "ubuntu installs but will not boot"
date: 2006-06-28
forum: Installation &amp; Upgrades
---

### Post by cryogenic on 2006-06-28
Apparently GRUB doesn't like my hard drive configuration or something here because no matter what I do in editing the command line, it absolutely will not boot. Suse 10.1 installs and boots fine, oddly. Basically, I have the following:

18GB SCSI boot drive (sda1, sda2), first partition is most of the drive and my windows boot partition, the remaining 140MB or so is what I generally use as /boot in Linux. 

80GB on IDE1, all of which is windows stuff (downloads, etc)
120GB on IDE2, first two partitions of 37GB or so each and 3rd partition of 5GB are all windows stuff, then a 12GB linux partition and a 512MB linux swap.

So what I want to do is use sda2 (140MB on SCSI) as /boot and then use hdb5 (12GB, IDE2) as my root partition. Problem is, grub configures itself incorrectly for some reason. Right after install, the first command in grub for either the regular boot or the safe boot is "root (2,1)" which isn't the correct partition. Leaving it as such gives me an error 17 saying the partition type is unknown and is of type 0x7, which is ntfs. Changing it to 2,4 gives me an error 18 saying that the selected cylinder is outside of my bios's limitations or something of that nature. Changing it to 0,1 or 0,2 (which should be the scsi) gives me the same error 18. Any other partitions used come up with the error 17 because they're NTFS. So what in the world should I do? Suse always booted fine and it uses grub as far as I know. 

My board is an Asus A8N-E (nforce4 ultra) board; AMD A64 3200+, 1GB RAM and the aforementioned hard drives. Any suggestions? Windows boots fine from grub with absolutely no issues. Do I need to do some sort of mapping command in grub to get it to recognize the higher partitions? Oh, and I do have the latest bios available for my motherboard.

---

### Post by cryogenic on 2006-06-28
nobody has a clue, eh? *sigh* I don't know enough about grub to actually figure this one out quickly, thus I was hoping for some help here. Kinda weird that suse's version of grub does quite fine. Why not Ubuntu's?

---

### Post by PudUK on 2006-06-30
Can't help, but I had same problem (error 17) in suse 10.1 & ubuntu

---

### Post by Herman on 2006-06-30
Hello, cryogenic, Have you tried booting from GRUB's Command Line? [*Click Here*]("http://users.bigpond.net.au/hermanzone/p15.htm#How_To_Boot_Linux_from_GRUBs_CLI") for    How To Boot Linux from GRUB's CLI
I'm just guessing, but I'd try the following series of commands to begin with:
```
grub> root (hd0,1)
grub> kernel /vmlinuz root=/dev/hdb5
grub> initrd /boot/initrd.img (and press 'Tab' for filename autocompletion)
grub> boot

``` Even if that doesn't work, you can use GRUB's Command Line to investigate your computer and find out what else to try. You should be able to boot it without too much trouble. Mkae notes of the correct information so you can later edit your /boot/grub/menu.lst file with the correct details.
  How to get GRUB's Command Line to investigate a computer, [*Click Here*]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_get_GRUBs_Command_Line_to_investigate_a_computer")
i hope that will be some help, Regards, Herman.

---

### Post by jtholmes on 2006-06-30
if you are getting the grub menu

enter the character 'c' (minus the quotes)
enter
  find vmlinuz

should tell you where the linux kernel(s) reside (in grub notation)

enter
  /sbin/init
should tell you what drives have /sbin/init

then
enter the following

root (hdN,N)
kernel (hdN,N)  vmlinuz....
init   (hdN,N)   init.....
boot

hdN  is one of the  disks (slices) from find above
,N  is the particular slice on that disk

you may also use find thus

find /boot/vmlinuz

I am on vacation in Alaska and dont have my PC
w/me or I could tell you exactly all the commands 
to use w/grub.  Look on google for  grub tutorials
lots of good ones there.

BOTTOM LINE IS
if you can get to the grub menu you CAN boot
Linux if vmlinuz is not hosed, which does not
appear to be the case here.

after you are able to boot then fix the 
/boot/grub/menu.lst file according to the
(hdN,N) commands you entered above
and reboot.
jt

---

### Post by Herman on 2006-06-30
> Look on google for  grub tutorials
lots of good ones there.
Thanks, jtholmes, that does clear up a couple of important points I left out. Your post prompted me to review my grub web-page already linked to, and I think I have improved that section of it quite a bit now. It can probably be improved a lot more too. I take advice or requests from fellow Ubuntu Forum members as to what else I can do to improve it, so be sure to let me know if you have any suggestions or spot an error.
There is also a very good website linked from mine that I recommend on the subject that I learned a lot from, [Grub Grotto]("http://www.troubleshooters.com/linux/grub/index.htm")
That web-site contains lots more good information on GRUB than I could ever provide. The 'Illustrated Dual Boot Site' is for those who like to see more illustrations than text, so it can't cover everything, but I do aim to be thorough and accurate in what is there.
Regards, Herman :)

---

