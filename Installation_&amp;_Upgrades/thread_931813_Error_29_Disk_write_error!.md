---
title: "Error 29: Disk write error?!"
date: 2008-09-27
forum: Installation &amp; Upgrades
---

### Post by 2BSS on 2008-09-27
Hello all,

I decided to install Ubuntu on my computer, and did the following in this very order (list ends with problem).

1. Downloaded 8.04 LTS .iso
2. Burned to CD
3. Ran CD in Windows, chose "demo and install" option
4. Ubuntu booted just fine, looked around the Live version a bit, and clicked on the install icon
5. Chose to install it on a 120GB external hard drive (not a new hard drive, but it was completely empty and freshly formatted)
6. Installation was successful, chose to reboot
7. Bios ran, got to a boot menu, chose to boot "Ubuntu 8.04.1, kernel 2.6.24-19-generic" (other options were "Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)", "Ubuntu 8.04.1, memtest86+", and of course, "Windows Vista/Longhorn (loader)")
8. Ubuntu booted up just fine, looked around a bit to get familiar with it, and decided to go back to Windows for a little bit to do some stuff

Here is where my problem beigns

9. Went to shut down menu in Ubuntu, chose to restart
10. When restarted and reached the boot menu again, selected "Windows Vista/Longhorn (loader)"
11. When I pressed enter, I was given a screen with this message:

"Error 29: Disk write error
 Press any key to continue..."

I guess my question is simply: What happened? I desperately need and will appreciate any help that anyone can give me regarding this, because basically I can't access my computer! (unless I boot Ubuntu, of course)

If I didn't give enough details, feel free to ask me for more details.

Thanks very much in advance!!

---

### Post by Pumalite on 2008-09-27
From Super Grub (hermanzone)

This error can also occur when the 'savedefault' command is used to try to write to the file called /boot/grub/default so GRUB will remember the last operating system you had booted.  If the file called 'default' does not exist, or you are using GRUB from a CD-ROM (CDs can't be written to), or WINGRUB (GRUB for WIndows, it may be in an NTFS partition, so can't be written to) then you may see this error.
To continue booting anyway, you can press 'e' for edit, select the line of the 'savedefault' command, press 'd' for delete, and 'b' for boot.
If this problenm will re-occur, it would be best to either hash out, or delete the 'savedefault' commands from the menu.lst file involved. They aren't often important anyway. You may be better off without them.

---

### Post by 2BSS on 2008-09-27
Thanks for the reply, but now I have a new problem. The GRUB menu won't load. When I just turned on my computer to do what you told me, when my BIOS got to the part where it would normally say "GRUB Loading stage1.5", it says it, and then continues repeatedly down my screen, repeating itself forever.

Just my luck that the moment I get help, a new problem arises...Help again please? haha

---

### Post by Herman on 2008-09-27
Is there any possibility it could be some kind of a hardware problem?
Is the hard disk properly detected and set up in the BIOS?
Is your power supply producing 12v smoothly? (Check 'PC Health Status' in your BIOS).
Is the hard drive spinning up okay? (Put your ear close to it and listen while your computer is starting up, or use a stethoscope if one is available).
Is the hard drive cable plugged in securely at both ends? (The motherboard end and the hard drive end?)

---

### Post by 2BSS on 2008-09-27
No. All of my hardware has been working perfectly fine.
Yes, both my internal ("Hard Disk") and my external ("Removable") hard drives are being detected in the BIOS.
Yes.
Yes, both my internal and external hard drives are spinning just fine.
Yes, both my internal and external hard drives are plugged in securely.

My initial problem was that I everything was running fine except Ubuntu, and that I couldn't boot Windows. When I went to try out what Pumalite suggested, I was struck with a new problem in that I could not reach the GRUB menu because instead of saying "GRUB Loading stage1.5 Please wait..." and then going to the GRUB menu, it now just says

GRUB Loading stage1.5
GRUB Loading stage1.5
GRUB Loading stage1.5
GRUB Loading stage1.5
GRUB Loading stage1.5
GRUB Loading stage1.5
GRUB Loading stage1.5
GRUB Loading stage1.5
GRUB Loading stage1.5

And keeps repeating for all eternity. **NOTE: I did not do ANYTHING with my computer between posting this topic and receiving Pumalite's advice.**

---

### Post by Herman on 2008-09-28
:) Okay then, Ihope I didn't upset you too much, sorry if I did, I just wanted to clear up those possibilties first becsue in the past I have made the mistake of assuming everything's fine with the hardware and after a very long and tedious thread, finding that a hardware problem has happened to appear co-incidentally to the installation.
Thanks for your co-operation. :)

First, lets help you boot Vista again. 
I am assuming that you installed GRUB to MBR in your internal hard disk.
I recommend that you should now install GRUB to the MBR, and possibly also to the boot sector of your Ubuntu partition in your external hard disk drive.
You can use your Ubuntu Live CD for doing that with.
Boot your Ubuntu live CD and open up a terminal and type 'sudo grub'.
```
sudo grub
```Use GRUB to find out what hard disk and partition GRUB is installed in
```
find /boot/grub/stage1
```Use the answer you received from the command above for the input for the next command, (below) to tell GRUB which GRUB files you want to use, (some people have more than one GRUB in their computer),
```
root (hd1,0)
```Where: (hd1,0) is your Ubuntu partition in your USB drive. If it's (hd1,5) then replace the (hd1,0) part with (hd1,5) instead, or something else, whatever it is.

Now write GRUB's stage1 and stage1_5 to MBR and the first track of your USB drive,
```
setup (hd1)
```Where (hd1) is your external USB drive's MBR.
```
quit
``````
exit
```Now you don't need the internal hard disk's MBR to boot your external hard disk anymore. You can if you want, but you should now be able to boot the external hard drive directly from your BIOS, [How I boot from my BIOS]("http://www.users.bigpond.net.au/hermanzone/p1.htm#How_I_boot_from_my_BIOS_with_my_F12_key").

If you can do that, boot Ubuntu up and try fixing your Vista hard disk's MBR this way,
```
sudo apt-get install ms-sys
``````
sudo ms-sys -m  /dev/sda
```From now on, if your external hard drive is not plugged in when you boot your computer, your computer should just boot Vista.
Whenever you have your external USB hard disk plugged in, you can boot the external hard drive directly from your BIOS, [How I boot from my BIOS]("http://www.users.bigpond.net.au/hermanzone/p1.htm#How_I_boot_from_my_BIOS_with_my_F12_key").
If that doesn't work or if you have a hard time or if you have a problem understanding anything, please post right back here and I'll see what I can do to help you more.

Another way to boot your external hard disk will be from GRUB in your CD drive or floppy disk drive, [How to make your own personalized GRUB Floppy Disk]("http://users.bigpond.net.au/hermanzone/p15.htm#grub_floppy_howto_make"). - or, [How to make your own personalized GRUB CD-RW]("http://users.bigpond.net.au/hermanzone/p15.htm#HOW_TO_MAKE_A_GRUB_CD"). 
Or you might like [Super Grub Disk]("http://www.supergrubdisk.org/") instead.

Regards, Herman :)

---

### Post by 2BSS on 2008-09-28
I did all of your steps (thank you so much, by the way!) up until I booted from my external hard drive, and it was successful. However, when I got to the GRUB menu, when I selected "Ubuntu 9.04.1, kernel 2.6.24-19-generic" as I was able to do earlier (before the whole line-of-text-to-infinity problem) to boot Ubuntu, I now get a message saying:

"Error 17: Cannot mount selected partition"

So this leaves me like this again haha -> :confused:

---

### Post by Herman on 2008-09-28
> "Error 17: Cannot mount selected partition"
Aha!
Okay, maybe your file system needs checking, try booting your Ubuntu Live CD and [Running a filesystem check on an ext3  filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem").
```
sudo e2fsck -C0 -p -f -v /dev/sdb1
```Where: sdb1 is your Ubuntu partition.

I'm just guessing all these partition numbers, so I hope I'm doing okay, if I'm wrong, please replace them with the correct partition numbers, found by running 'sudo fdisk -lu'
```
sudo fdisk -lu
```
If you post the output from that command I may be able to help you a little bit better.

---

### Post by Herman on 2008-09-28
Another thing it could be is, when you select the external hard disk from your BIOS, it might be making the external hard disk into your number one hard disk, (changing your hard disk numbering).
If that's what's going on, you should be able to change into [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli")
 by pressing your 'c' key from your GRUB menu, (if you're getting that far), and running GRUB from the command line.

If you don't want to do that, I recommend booting with [Super Grub Disk]("http://www.supergrubdisk.org/"), for now. The you may need to edit your /boot/grub/menu.lst once you get Ubuntu booted up.
We''l cross that bridge when we get to it...

---

### Post by 2BSS on 2008-09-28
Alright, here's the output:

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7ae6a347

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   312578047   156288000    7  HPFS/NTFS

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000098ec

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   224829674   112414806   83  Linux
/dev/sdb2       224829675   234436544     4803435    5  Extended
/dev/sdb5       224829738   234436544     4803403+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -v /dev/sdb1
/dev/sdb1 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? yes

/dev/sdb1: recovering journal
/dev/sdb1: clean, 107904/7028736 files, 790191/28103701 blocks


```

---

### Post by Herman on 2008-09-28
:oops: Oops, I forgot to mention that you should never run a file system check on a file system while it is mounted. 
Well, it looks like you may have gotten away with it this time, but always make sure in the future that you never mount your file system(s) before running a file system check, that's the reason why we prefer to use a Live CD.

When you boot the Live CD and take a look at in in Gnome Partition Editor, ('System'-->'Administration'-->'Partition Editor'), does it look okay?
It it's badly corrupted it will come up with a black rectangle around it and say something like 'file systems unknown' or something similar.

Thank you for the fdisk -lu output, I can see what I'm doing now. :D

You haven't mentioned whether or not Vista is booting okay now. I hope that ms-sys has enabled Windows to boot from the MBR of you insternal hard disk, at least.

Have your tied booting Ubuntu again yet? Are you still getting GRUB Error 17, or a different error now?

---

### Post by 2BSS on 2008-09-28
Oops! My bad :-# Good thing I got lucky :mrgreen:

Everything looks fine in there! No black bars, so I'll take that as a good sign.

However...
- When I boot from my internal hard drive, I still get the "GRUB loading stage1.5" repeating forever. 
- When I boot from my external hard drive and get to the GRUB menu, I can't choose the Windows Vista option because it still gives me the "Error 29: Disk write error".
- And I still can't choose the Ubuntu option because it's still giving me the "Error 17: Cannot mount selected partition"

---

### Post by Herman on 2008-09-28
> - When I boot from my internal hard drive, I still get the "GRUB loading stage1.5" repeating forever.  Aright, I don't know why ms-sys wouldn't have worked there, but you probably want to get your internal hard disk's MBR back to normal.

Here is a link where you can download a Visat recovery disc, [Windows Vista Recovery Disc Download]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") - Neosmart.net, thanks lswest for the link. Thanks for the download to Computer Guru, of NeoSmart Technologies (the developer of [EasyBCD]("http://neosmart.net/dl.php?id=1")).  
The command to use is, 'bootrec /fixmbr',
```
bootrec /fixmbr
```
Refer: lswest's and bodhi.zazen's thread, [HOW-TO restoring XP and Vista Bootloader & Restoring GRUB ]("http://ubuntuforums.org/showthread.php?t=740221")
You should be able to restore your internal hard disk's MBR to it's original condition with that for sure.

As for your Ubuntu in your external USB drive, did you download [Super Grub Disk]("http://www.supergrubdisk.org/") yet?
When you do, burn it to a CD, boot with that.
You should be able to find a way to boot your Ubuntu with that from Super Grub Disk's menus.
The best way would be to 'boot linux directly', if you can find that option in there somewhere.
Otherwise, just press your 'c' key from a menu to get into [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli"), and perform a [Direct (kernel) Boot]("http://users.bigpond.net.au/hermanzone/p15.htm#First_method:_direct_kernel_boot."). 
                                               
Take notes while you are doing that because you can use the same information for editing your /boot/grub/menu.lst file in Ubuntu after that, (when Ubuntu has booted.

If you can't boot Ubuntu from Super Grub Disk directly, then I don't know how else you will be able to, and the next resort is to try installing Ubuntu again, as it only takes about half an hour.
It would probably be best to install GRUB to MBR in the external hard disk next time, not to the internal hard disk's MBR, by pressing the 'advanced' button in step 7 of 7 in the installation, and choosing the right hard disk to install GRUB to.
Here's a  link to illustrate the Ubuntu installation procedures, [COLOR=#000000][Hardy Heron LTS / Windows XP Dual Boot Installation A.]("http://www.herman.linuxmaniac.net/p24.html") ( refer to the illustration number 020 there for how to choose where to install GRUB in step 7 of 7). - (hd1) in your case.
[/COLOR]

---

### Post by Herman on 2008-09-28
... just thinking, another easy way out of all this trouble would be to just install Ubuntu in your internal hard disk and write GRUB to MBR so you will have a standard dual boot installation with Vista.
It's a lot easier to do it that way than to install in an external hard drive. Ubuntu is made to be installed in an internal drive, or at least that's the easiest.
You could then just use your external hard disk for storing data.
I guess there might be special reasons why you need Ubuntu in the USB drive though...
...anyway, it's up to you but I feel sorry for putting you through all this trouble, and I just want to point out that installing Ubuntu isn't always this much work. 

Regards, Herman :D

---

### Post by 2BSS on 2008-09-28
Hazzah! I successfully fixed the MBR and can now boot Windows Vista from my internal! No more repeating-for-eternity text! Thanks so much!

As for the problem with Ubuntu on my external, how would I go about just removing that entirely? From all the difficulty I've had with the external business (I understand that it's not Ubuntu's fault and that this isn't always this much work :-D ) I think it sounds like it'd be much easier if I just installed it onto my internal hard drive. Would you please be able to help me go about that?

---

### Post by Herman on 2008-09-28
Sure, you could just boot your Ubuntu Live CD again and open Gnome Partition Editor, and delete all the partitions you made in the external hard drive. Then create a new partition or partitions, to occupy the whole disc or whatever you like.
You can choose any file system you like to format those partitions with. 
Most people who use Windows use FAT32 or NTFS.
Linux users usually prefer the ext3 file system or reiserfs.

Actually, I'm a little superstitious about installing an operating system in an external hard drive enclosure anyway. Those normally don't come with cooling fans as are normally found inside a computer case and help to cool internal hard disks. They're great for storing data in though, and I admit I do have Ubuntu Rescue Remix installed in an external USB Hard drive so I can use PhotoRec for recovering files easier. It is a little bit harder for new users to set up the booting in a USB device though. :D

I hope you'll be a lot luckier installing in your internal hard drive, and I'm sure that is a lot easier for almost anyone. 
There are some good how-tos and guides around aysiu has a good one, [Install Desktop CD Ubuntu]("http://www.psychocats.net/ubuntu/installing") , and of course mine own website has a few, (see my sig links).
The main thing for installing in an external is to be sure to remember the 'advanced' button in step 7 of 7.
For installing in an internal hard drive, it should be as easy as following one of those guides, just make sure you take your time and read about what you are about to do before you click or press 'enter'.
I keep forgetting now, it was so long ago for me, but I was very nervous the first time. (LOL) It's worth it when you have Ubuntu installed and you start learning how to achieve great things with it.  :D

Edit: Here's another link I found to a different how-to, [How to *dual*-*boot Vista* with Linux (*Vista* installed first)]("http://www.google.com.au/url?sa=t&source=web&ct=res&cd=1&url=http%3A%2F%2Fapcmag.com%2Fhow_to_dualboot_vista_with_linux_vista_installed_first.htm&ei=rw7gSLToIIG0sAPA-ZzaAw&usg=AFQjCNGNZDpFfL6GLbDmv7lUNIoqG-uWtQ&sig2=KGi8cffmt5PEPUBQXZ3GTQ")
In that how-to, the partitioning is done with Vista's own hard disk partitioner and EasyBCD is used as the boot loader, just in case you want to see what that way of doing things is like.

---

### Post by 2BSS on 2008-09-28
I'm in the Partition editor, and the following partitions were listed:

/dev/sdb1            ext3
/dev/sdb2            extended
   /dev/sdb5         linux-swap

However, I can't really do anything to them. When I select them, all options are greyed, and when I right-click them, all options are also greyed.

Edit: The /dev/sdb1 had a right-click option "unmount" that was not greyed. When I clicked it, I had the option to delete it, so I did. What do I do with the other two that still have all options greyed out (except a couple, /dev/sdb2 has "Manage Flags" available, and /dev/sdb5 has "Swapoff" and "Manage Flags" available)?

**Edit: Nevermind, I figured it out and deleted them. About to take the next step and install onto the internal.**

---

### Post by 2BSS on 2008-09-29
Great! I can now successfully boot Windows Vista and Ubuntu! Thanks so much for all of your help!:D:D:D

---

### Post by Herman on 2008-09-29
:D Oh, wonderful, and thank you so much too, for your co-operation! 
Congratulations and Welcome to Ubuntu! :D

---

