---
title: "Overwritten Windows MBR by mistake, can't boot XP"
date: 2006-02-22
forum: Installation &amp; Upgrades
---

### Post by Jaidee on 2006-02-22
Hello all,

Please forgive my first post being in need of help.

I have a scary-ish problem with my MBR.

Upgraded Breezy to Dapper recently, adn it seemed to change my grub menu.lst file. I then ran the command, sudo grub-install (hd0,1) or something (had help).

By the way, hda2 is my Windows partition, and is the bootable partition (has a star next to it in fdisk -l). I get the feeling I've overwritten my Windows MBR.

In my grub menu.lst file, I have added:

title windows
root  (hd0,1)
makeactive
chainloader +1

but when I select this entry in grub it just boot right back into grub. I once again get the feeling i've overwritten my windows MBR when i did the sudo grub-install (hd0,1) command. 

So, question is, how do i boot into Windows? I NEED my windows partition as it has all my documents, and I can lose the Linux partition, hda3. 

Please help me!

edit:

OK, I've done some more work and found that I can rebuild the mbr on the windows partition using a fixmbr command at the recovery console (booting from Windows CD). I did this, but the same problem remains. I feel that grub now sits at a higher level, possibly hda? I feel also the running fixboot at recovery console might fix this  but it's too scary to do without the all clear from someone else.

---

### Post by ajgreeny on 2006-02-22
I'm a bit concerned that windows does not appear to be on the primary partition on the disk as I think it will only boot from there and not from a secindary one.  I'm sure someone else will tell you if I'm wrong about that.

If not you could simply copy your grub to a floppy if you have one.  From Ubuntu type sudo grub-install fd0 and it should work.  Make sure you have an entry for floppy in your device.map file in /boot/grub as follows "(fd0)	/dev/fd0" or you will get an error about BIOS entries.  Later you can install grub back to the hard disk if needed.

Now use the windows installation disk to repair your MBR.

Now you should be able to boot to windows from the had disk or to ubuntu from the floppy.  best of luck.

---

### Post by lha on 2006-02-22
[QUOTE=Jaidee]Hello all,

Please forgive my first post being in need of help.

I have a scary-ish problem with my MBR.

Upgraded Breezy to Dapper recently, adn it seemed to change my grub menu.lst file. I then ran the command, sudo grub-install (hd0,1) or something (had help).

By the way, hda2 is my Windows partition, and is the bootable partition (has a star next to it in fdisk -l). I get the feeling I've overwritten my Windows MBR.

In my grub menu.lst file, I have added:

title windows
root  (hd0,1)
makeactive
chainloader +1

but when I select this entry in grub it just boot right back into grub. I once again get the feeling i've overwritten my windows MBR when i did the sudo grub-install (hd0,1) command. 

So, question is, how do i boot into Windows? I NEED my windows partition as it has all my documents, and I can lose the Linux partition, hda3. 

Please help me!

edit:

OK, I've done some more work and found that I can rebuild the mbr on the windows partition using a fixmbr command at the recovery console (booting from Windows CD). I did this, but the same problem remains. I feel that grub now sits at a higher level, possibly hda? I feel also the running fixboot at recovery console might fix this  but it's too scary to do without the all clear from someone else.[/QUOTE]

You have installed grub on the *boot sector* of hda2 with 'sudo grub-install (hd0,1)'.

When you booted up your computer, grub was loaded from *mbr*. Then that windows-entry with chainloader loaded that other instance of grub from hda2's boot sector. This is the source of your problems. Then you replaced grub-on-mbr with Windows' boot loader. Windows' boot code searces for a bootable partition and loads its code. It should have Windows' next stage of boot loader, but you overwrote it with 'sudo grub-install (hd0,1)', so grub comes up.

To repair your system, see [#6: Fix a corrupt partition boot sector]("http://techrepublic.com.com/5100-10877-6031733.html").

Because you already overwrote grub-on-mbr with Windows' boot loader, you'll boot directly into Windows after following those instructions. To get back dual-booting, you have to reinstall grub. (But do not install it to hda2's boot sector.)

---

### Post by Jaidee on 2006-02-22
Many, many thanks to ajgreeny and lha for your help, I am very grateful.

Thankyou lha for correcting my use of terms also, now I hope I can explain myself better.

I have performed the command "fixboot" from a windows recovery console. Unfortunately, I now get the message "Disk Error. Press any key to reboot." 

Quite scary I'm sure. But not to worry, I connected the HD to my other computer and could still access the windows partition. I'm backing it up now before I try again.

It looks like I've really screwed up both the MBR and maybe also the boot sector of the windows partition (hda2). Should I perhaps try a "fixboot c:" command? Are there any third-party programs I could buy to repair the MBR whilst I've got the drive attached to another PC?

Many thanks,

Jaidee.

---

### Post by lha on 2006-02-22
[QUOTE=Jaidee]Many, many thanks to ajgreeny and lha for your help, I am very grateful.

Thankyou lha for correcting my use of terms also, now I hope I can explain myself better.

I have performed the command "fixboot" from a windows recovery console. Unfortunately, I now get the message "Disk Error. Press any key to reboot." 

Quite scary I'm sure. But not to worry, I connected the HD to my other computer and could still access the windows partition. I'm backing it up now before I try again.[/QUOTE]

Backing up is good. :)

[QUOTE=Jaidee]It looks like I've really screwed up both the MBR and maybe also the boot sector of the windows partition (hda2). Should I perhaps try a "fixboot c:" command? Are there any third-party programs I could buy to repair the MBR whilst I've got the drive attached to another PC?

Many thanks,

Jaidee.[/QUOTE]

In my previous post, I meant exactly that 'fixboot c:'. I just wanted you to look at that page and see a bit more than just one magic command.

I say third party programs are a waste of money. Sure, if you find one that fixes your troubles, great. But I know you already have all the programs you need for this.

---

### Post by Jaidee on 2006-02-22
Thanks again. Backup is still in progress, will perform "fixboot c:" when complete and report back!

Rest assured if I get this working I will be very happy and start the transition from Windows to Linux in my business and home life.

---

### Post by hartunnoo on 2006-02-22
have you try using partition magic to repair your mbr?

---

### Post by lettas on 2006-02-23
Try fixmbr, that should replace mbr with XPs original one.

---

### Post by bigken on 2006-02-23
go to win xp repair console type config /rebuild ;)

---

### Post by Jaidee on 2006-02-23
Status update:

One day on and I still have no working laptop. Shame, but progress is being made I feel.

I have performed the following commands from Windows Recovery Console:

fixmbr \device\harddisk0

fixmbr \device\harddisk0\partition1

fixmbr

fixboot c:

fixboot

bootcfg /rebuild


All to no avail. I still get the error,

Disk error
Press any key to restart

when I boot the machine.

Any further ideas? Please help.

---

### Post by bigken on 2006-02-23
boot from winxp cd when asked press r to go to repair console when in console select your partion usually 1 then enter admin password if you have one type config /rebuild enter then type exit enter reboot pc ;)

---

### Post by bigken on 2006-02-23
if this fails do repair install winxp then run ubuntu disc and repair grub

---

### Post by Jaidee on 2006-02-23
OK, haven't tried that yet but here's a quick update.

Ran a program called 7Tools Boot Corrector, which tried to rewrite boot sector and MBR. It seemed to do both, but I still get the same error message,

Disk error
Press any key to restart

I have also noticed that if I ask Boot Corrector to redo the drive letters in the registry it stops, as it say my Disk Signature is 00000000 and it tells me to reinstall Windows.

Any ideas on redoing the disk signature?

Cheers.

---

### Post by bigken on 2006-02-23
look at this link
[http://www.michaelstevenstech.com/r_c_cmds.htm#Chkdsk]("http://www.michaelstevenstech.com/r_c_cmds.htm#Chkdsk")

run all the chkdsk commands if this fails do yourself a favour and do a repair install ;)

---

### Post by Jaidee on 2006-02-23
Repair install it is,

5% complete so far...

---

### Post by bigken on 2006-02-23
you will have to repair your grub menu after this look it up on the forum its an easy process

---

### Post by Jaidee on 2006-02-23
After repair install of Windows,

still get error

Disk error
Press any key to restart

I can access the disk when mounted in another PC.

---

### Post by bigken on 2006-02-23
mount hdd on another pc backup data run virus scan 1st defrag 
and clean all temp files ect also try running spyware and adaware 
if this dont work do a tolal reformat

---

### Post by ssam on 2006-02-23
might this help [http://josephhall.org/grub_install_hda1.html](http://josephhall.org/grub_install_hda1.html)

---

### Post by Jaidee on 2006-02-25
Glad to report that I'm booting back into windows, as it was before linux.

I'm sorry to say that the whole experience has scared me a little and it'll be a while before I try using Linux again. It'll also be a while before I forget to backup again.

Fixing the boot sector was a matter of following ssam's link and manually deleting the first 512 bytes of the windows partition.

Unfortunately, this is where the guide falls right over. It never talks of replacing this bootsector. Instead, it recommends performing the operation sys a: c:, but performing this will DAMAGE YOUR SYSTEM. Copying system files after the deletion of the bootsector will copy the files to empty space, and will corrupt the data when you do finally replace the bootsector.

Far better an idea is to remove the bootsector, and then boot using an XP CD, load the recovery console and use fixboot c: to replace the bootsector. All the files (including system files) should be back where they were and the partition table generated will mean everything works ok again. At this stage I found it neccessary to reboot and run bootcfg /rebuild to point the windows bootloader to the right place. 

Because I wrote the system files to a partition with no bootsector, upon replacing the bootsector I found many files corrupt and had to format the partition and replace all the contents of the partition from a backup i'd luckily made yesterday when I found I could still mount the partition.

A very, very close call, and no amount of XGL is going to calm these jittery nerves.

Many thanks to ssam for his link, it was the be all and end all piece of information I needed.

---

### Post by Jason_25 on 2006-02-25
You might want to look into just getting another computer to play with.  People have no concept of the value of old computers and will gladly give them away or at a very cheap price.  I have learned so much by being able to have different os's on different computers and being able to easily use one computer to troubleshoot another.  If that isn't an option, The Dapper Drake live CD now supports persistent sessions, meaning you can run it off a cd and use a usb key to store your personal files and settings.

---

### Post by Jaidee on 2006-02-25
Yeah, living in a fairly tight apartment I don't think many machines is really an option.

Since I started to play around with my MBR and bootsector on the laptop I've realised I could probably do a lot of cleaning up. Just let me get over the terror of nearly losing ALL my files and I'll be right back to dual booting on the laptop.

My desktop however, with three versions of Windows, one of which is archaic, needs so much tidying it's not funny.

I'll be back with Dapper Drake soon!

---

### Post by bigken on 2006-02-26
i think running fdisk mbr and bootcfig /rebuild in console with out any of the other stuff would have done it pleased to hear you are up and running sad  that your giving up on linux its alot more fun than winxp ;)

---

