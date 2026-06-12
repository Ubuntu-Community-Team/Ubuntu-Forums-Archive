---
title: "Create an .iso from the ubuntu files."
date: 2007-07-12
forum: Installation &amp; Upgrades
---

### Post by tophor on 2007-07-12
I need to make a bootable .iso from the ubuntu files and folders. How can I do it? I tried just making the cd bootable in my burning program, but that didn't work.

Anybody?

A .iso file which I can then burn.

---

### Post by aysiu on 2007-07-13
Can you explain a bit more about your situation? Are you trying to make an installed Ubuntu into a live CD? Where did you get these "Ubuntu files and folders"?

---

### Post by tophor on 2007-07-13
I borrowed a friends disk (7.04) and simply copied all the files and folders from the disc. Now I want to make a bootable iso that I can then burn to install the OS.

P.S. If I did it again, what program would have made a correct .iso for me from the original disk. (Preferable freeware/open source)

---

### Post by lisati on 2007-07-13
A simple copy of the folders probably won't be enough. The copies of Nero I've used have a "copy disk" option which would suit better. I think software by Sonic bundled on some Compaq machines has a suitable "copy disk" option as well.

---

### Post by tophor on 2007-07-13
No way to rebuild the ISO? All I would need is the method of making the CD bootable again. ISOLINUX doesn't have anything to do with this does it?

---

### Post by aysiu on 2007-07-13
Next time you have the CD, you can use [InfraRecorder](http://infrarecorder.sourceforge.net/) to create an .ISO from it, and you can also [use InfraRecorder to reburn the .ISO as a disc image on to a new CD.](http://psychocats.net/ubuntu/iso#burning)

---

### Post by stchman on 2007-07-13
> **tophor said:**
> I need to make a bootable .iso from the ubuntu files and folders. How can I do it? I tried just making the cd bootable in my burning program, but that didn't work.

Anybody?

A .iso file which I can then burn.

Use Nero or whatever disc burning program you use and do a disc to disc copy.  This will copy the boot sector of the CD as well.

You could also just download the .iso from Ubuntu.

---

### Post by tophor on 2007-07-13
I don't get much bandwidth so I save where and when I can.


How can I create that boot sector. I've got the files and I need to burn the files, and a correct boot sector to that cd.

I truly appreciate the interest and replies so far. I know that re-copying the disc would fix it. I'm just wanting to figure out how the boot sector is produced in the first place so I can create my own disc with only the files and folders at hand, and not a true .iso. I know it must be possible.

There must be a way.

---

### Post by Herman on 2007-07-14
> I borrowed a friends disk (7.04) and simply copied all the files and folders from the disc. Now I want to make a bootable iso that I can then burn to install the OS.
P.S. **If I did it again, what program would have made a correct .iso for me from the original disk**. (Preferable freeware/open source)Hello tophor, 
If you have Ubuntu already or your freind has Ubuntu and you can get the use of his computer for a few minutes you can use a 'dd' command for that, something like this one, but replace where it says 'herman' with 'tophor'.  Just place the CD to be copied in the drive and type something like the following command into the terminal, 
```
sudo dd if=/dev/cdrom of=/home/herman/ubuntu-7.04-desktop-i386.iso bs=2048 conv=notrunc
``` This command will make an .iso file which is exactly the same as the original .iso file your friend downloaded from the internet in the first place, providing his CD-ROM drive lens is relatively clean. 
I have tested this and checked the results with the md5 checksum command and I am sure this works 100% perfectly, here is the md5sum command and under that is the result I got, which would be the correct md5sum. :)
```
md5sum ubuntu-7.04-desktop-i386.iso
``````
e296e3468358789904097fc8df29609a  ubuntu-7.04-desktop-i386.iso
```The only difference is it's owned by root because it was made with a sudo command, but that should be easy to fix with a chown command if needed. I didn't bother doing that to mine, I copied it to a CD-RW and booted it in another computer just to be sure. It boots fine, and passed it's own 'check cd for defects' self- integrity test. Then I booted it as a Live CD and it's running fine at the time of typing this. :)

>  How can I create that boot sector. I've got the files and I need to burn the files, and a correct boot sector to that cd.I also know that you can make a folder full of files into an .iso file using the mkisofs command, but when I type 'man mkisofs' in a terminal these days I get: genisoimage instead. That must be the new command that replaces the mkisofs command that I have used before to make plain files into .isos.
Actually, I'm just a beginner at that myself, but I'm sure we should be able to create .iso images that way for making bootable CDs if we learn the right options to put with one of those the commands.
To make a bootable GRUB CD, we copy the file called: [FONT=Bitstream Vera Sans Mono]stage2_eltorito [/FONT] out of our[FONT=Bitstream Vera Sans Mono]/usr/lib/grub/i386-pc directory. [/FONT] (It just so happens that Ubuntu comes with one of those in there, so it's easier than downloading one from somewhere on the internet.) Then we use the mkisofs command for making it into an .iso for a bootable CD. For example, here's a how-to for making your own GRUB boot disk, [                                                                           How to make your own personalized GRUB CD-RW]("http://users.bigpond.net.au/hermanzone/p15.htm#HOW_TO_MAKE_A_GRUB_CD"). When you get Ubuntu installed you can try that how-to if you're still interested. :)

The Ubuntu doesn't boot with a [FONT=Bitstream Vera Sans Mono]stage2_eltorito [/FONT]though, it looks like it boots by  isolinux instead. I don't know the mkisofs or genisoimage command to make an .iso file from that yet at this stage. Right now I'm googling to learn more.  
I also want to learn how to make one of those CDs that boot to a .html page when we insert the CD when the computer is already running. That would be cool I think. I'm working on it... 

Regards, Herman :)

---

### Post by tophor on 2007-07-14
Herman. Simply thanks for spending the time to answer my question. Its a linux method of doing it, but then again this is a linux forum. I do have a 6.10 install I could use to make the disc. 

If someone has a windows way of doing it......that wouldn't be a waste of typing either, if anyone knows of one.

Again, Thankyou. I'll give it a shot.

---

### Post by Herman on 2007-07-14
Hello tophor, :)
I'm typing to you right now from a Ubuntu Feisty Fawn CD I made by copying the files from another CD to a folder on my hard drive, then making an .iso out of  it and burning it to a CD-RW.
I had to try this lots of times before I got it right. One thing I think might be worth mentioning maybe, is this time before dragging and dropping the files from the CD to the hard drive directory, I clicked 'View'-->'Show hidden files'. There is a hidden directory called .disk which I'm not sure is important, but I would have been skipping that in previous attempts.

Then I applied the following command to the folder full of files,
```
mkisofs \
-r \
-V "ubuntu-7.04-i386" \
-cache-inodes \
-J \
-l \
-b isolinux/isolinux.bin \
-c isolinux/boot.cat \
-no-emul-boot \
-boot-load-size 4 \
-boot-info-table \
-o ubuntu-7.04-i386.iso ubuntu-7.04-i386
```EDIT: Where: ubuntu-7.04-i386.iso will be the name you want to call the new .iso file, and where ubuntu-704-i386 is the name of the directory you want use to make the .iso file from. 

I got that from the bottom of this web page, [UbuntuEdgy/Remaster - OSS Watch Wiki,]("http://wiki.oss-watch.ac.uk/UbuntuEdgy/Remaster")  and modified it to suit.
By the way in case you don't know already, but you can usually copy and paste these Linux commands into your computer and just modify any bits that you have to, it's easier than typing them yourself.

Well, it didn't produce an .iso with the correct md5sum, but it does pass it's own 'check CD for defects' test, and it boots, and it seems to work okay I'm typing on it now.  :guitar:

For me it has been useful and fun as an exercise for learning more about how to use the mkisofs command, which has been my main challenge for today. I still have a lot to learn, but at least I have been able to accomplish this little trick. I wish I could get the MD5sum to come out perfect, but I'm not good enough yet. I must still be doing something wrong.
Well, that's how to make a folder full of files into a bootable CD, now we know, (in Ubuntu at least).

I think you can buy programs to do that in Windows too, but I don't know how much you'll have to pay.

Another thing I found  out along the way is we don't really need a 'dd' command anymore these days to copy CDs to .iso files. This is a link I found, [Handy Hacks: How to create an ISO file image in GNOME « Alec the Geek]("http://alecthegeek.wordpress.com/2007/01/19/how-to-create-an-iso-file-image-in-gnome/")
Linux and especially Ubuntu is getting more user friendly all the time.

I'm not sure if that information will help you or not, maybe it will, but I had fun finding out that stuff anyway and maybe it'll help someone. :)

Regards, Herman :)

---

### Post by tophor on 2007-07-18
Thankyou so much everyone, for you wonderful replies. Thanks so very much.

---

### Post by tophor on 2007-07-24
I was able to do it just fine on Windows too.

I did the same exact commands on windows. Here are the commands I used.

I used the ported tools from this website. [http://smithii.com/cdrtools]("http://smithii.com/cdrtools")

Down the page is a toolset by MingW that does not require cygwin. [http://smithii.com/files/cdrtools-2.01-bootcd.ru-w32.zip]("http://smithii.com/files/cdrtools-2.01-bootcd.ru-w32.zip")


Anyway here is the commands I used on my XP machine. 

```
C:\Documents and Settings\PunchInFace>mkisofs -r -V "ubuntu-7.04-i386" -cache-in
odes -J -l -b isolinux/isolinux.bin -c isolinux\boot.cat -no-emul-boot -boot-loa
d-size 4 -boot-info-table -o ubuntu-7.04-i386.iso C:\Ubuntu7.04Folder
```


I ran into two problems.....NOTICE the BACK SLASH on the -c switch parameter. Without it mkisofs will complain.

Also don't save or run apps from the Ubuntu folder that you want to build. I ran mkisofs out of the ubuntu folder and mkisofs included the mkisofs.exe into the iso. The cd would still boot, but on disc verification one file would be erroneous. Guess which file that was.

Thanks a ton Herman. Now we have instructions for Windows and LINUX on how to build your own bootable Ubuntu iso.

---

### Post by Herman on 2007-07-24
Hey wow tophor, well done! :)
I wouldn't have though you could use the same command, or pretty near it in Windows. Well there you go eh? Thanks for reporting back letting us know too!   :)

I have been researching and experimenting and I have a few items to share too.

The mkisofs command is being replaced with the genisoimage command in Linux, I don't know why, but we're being encouraged to switch over to genisoimage from now on. The options seem to all be the same, and the manual pages look almost the same too.

Did you know you can install Ubuntu right off the hard disk, without making a CD, if you have the .iso file? Here's a thread about that, [grub-install says "Could not find device for /boot: Not found or not a block device."]("http://ubuntuforums.org/showthread.php?t=504678")
 I think it's better to burn the CD if we can though, because the LiveCD comes in handy now and again for special jobs like file system checking and that sort of thing.

I was eventually successful in making my CD that automatically opens like a website when you put it in a Windows computer. I was making it for a friend who is still a Windows user, and I wanted to impress, (it was for my boss actually). I don't think that will work the same in Ubuntu computers, they just open as a folder full of files, but that doesn't matter, we can look for the file called 'index.html. ourselves and click on it.

I also found a small improvement to the command I posted earlier, I added this to it: [FONT=Bitstream Vera Sans Mono]-input-charset iso8859-1  \ [/FONT] but I'm still not able to make an .iso with the right md5sum. It has to be perfect to get the right md5sum. Maybe it has something to do with another option I might be missing, I just started learning about,[ jigdo]("http://atterer.net/jigdo/"), I don't know how to use that one yet. :)

Thanks to you getting me interested, tophor, with this thread, I have added a new article about making .iso files here, [genisoimage commands for making .iso file to make CDs and DVDs]("http://users.bigpond.net.au/hermanzone/p10.htm#genisoimage_commands"), which links back to this thread again, by the way. :)

I have updated these two, [How To Build a Super GRUB Disk/GParted CD / DVD]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#How_To_Build_a_Super_Grub_DiskGParted").
and [How to make your own personalized GRUB CD-RW]("http://users.bigpond.net.au/hermanzone/p15.htm#HOW_TO_MAKE_A_GRUB_CD").

So thanks again for getting me interested, tophor, 

It would be great if we can keep adding to this thread or, even better, if someone else can add some information about more ways to use mkisofs or genisoimage commands or anything related somehow to making CDs or .isos. :)

Regards, Herman :)

---

