---
title: "grub rescue&gt; ls (hd0,1) . . . boot from grub command line ?"
date: 2010-02-11
forum: Installation &amp; Upgrades
---

### Post by jenaniston on 2010-02-11
Ever since I tried Karmic 9.10 grub2 has messed me up good . . .

I now just want to go back to 9.04, but now with a new install to USB drive of Ubuntu 9.04 or Xubuntu 9.04  with
 the **good ole' grub** - well - things have changed  leaving me with a  boot to the "  **grub rescue>** " prompt . . .

Any ideas ? . . . for the way to finish the boot from here . . .

I have used these commands alright . . .
```
grub rescue> ls
(hd0) (hd0,5) (hd0,1) (hd1) (hd1,5) (hd1,4) hd1,3) (hd1,1)
grub rescue>
```and following the advice from a google search I set prefix but that was obviously wrong so I tried this improvement . . .
```
grub rescue> set prefix=(hd0,1)/boot/grub
grub rescue>
```and now get . . .
```
grub rescue> set
prefix=(hd0,1)/boot/grub
root=hd0,1
grub rescue>

```But . . . should I set prefix different though  . . . ?  These are **ls** results . . .
```
grub rescue> ls (hd0,1)/boot
./ ../ System.map-2.6.28-11-generic abi-2.6.28-11-generic config-2.6.28-11-generic
memtest86+.bin vmcoreinfo-2.6.28-11-generic vmlinuz-2.6.28-11-generic 
grub/ initrd.img-2.6.28-11-generic
grub rescue>
``````
grub rescue> ls (hd0,1)/boot/grub/
./ ../ device.map stage1 stage2 e2fs_stage1_5 fat_stage1_5 jfs_stage1_5 
minix_stage1_5 reiserfs_stage1_5 xfs_stage1_5 default installed-version menu.lst
grub rescue>
```Any ideas as I experiment to further nudge this along to the usual and expected 9.04 boot screen ?

Thank you very much.

P.S. . . . obviously ***NOT ***a very *fast* boot sequence, eh ?

---

### Post by kansasnoob on 2010-02-11
> **jenaniston said:**
> Ever since I tried Karmic 9.10 grub2 has messed me up good . . .

I now just want to go back to 9.04, but now with a new install to USB drive of Ubuntu 9.04 or Xubuntu 9.04  with
 the **good ole' grub** - well - things have changed  leaving me with a  boot to the "  **grub rescue>** " prompt . . .

Any ideas ? . . . for the way to finish the boot from here . . .

I have used these commands alright . . .
```
grub rescue> ls
(hd0) (hd0,5) (hd0,1) (hd1) (hd1,5) (hd1,4) hd1,3) (hd1,1)
grub rescue>
```and following the advice from a google search I set prefix but that was obviously wrong so I tried this improvement . . .
```
grub rescue> set prefix=(hd0,1)/boot/grub
grub rescue>
```and now get . . .
```
grub rescue> set
prefix=(hd0,1)/boot/grub
root=hd0,1
grub rescue>

```But . . . should I set prefix different though  . . . ?  These are **ls** results . . .
```
grub rescue> ls (hd0,1)/boot
./ ../ System.map-2.6.28-11-generic abi-2.6.28-11-generic config-2.6.28-11-generic
memtest86+.bin vmcoreinfo-2.6.28-11-generic vmlinuz-2.6.28-11-generic 
grub/ initrd.img-2.6.28-11-generic
grub rescue>
``````
grub rescue> ls (hd0,1)/boot/grub/
./ ../ device.map stage1 stage2 e2fs_stage1_5 fat_stage1_5 jfs_stage1_5 
minix_stage1_5 reiserfs_stage1_5 xfs_stage1_5 default installed-version menu.lst
grub rescue>
```Any ideas as I experiment to further nudge this along to the usual and expected 9.04 boot screen ?

Thank you very much.

P.S. . . . obviously ***NOT ***a very *fast* boot sequence, eh ?

In order to get a better look at your system I need you to boot a Live CD with all drives, including the USB drive, connected and then post the results of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by jenaniston on 2010-02-11
> **kansasnoob said:**
> In order to get a better look at your system I need you to boot a Live CD with all drives, including the USB drive, connected and then post the results of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

A live version would be great if it would boot a live version - 
but the "BusyBox" is what I get - I can press escape to see what happens before it stalls though.


sda1 is a SATA hard drive with Windows XP - but the XP recovery utility did a destructive process
(the OS is still there but only because linux and freebsd have told me it is there)
There is a logical and extended fat32 partition sda5

The full install USB OS is currently Xubuntu 9.04 64 bit . . . has always been dev/sdb -
with grub rescue it looks like it lists as (hd0,1) 

grub was installed to that sdb device at sdb1 with the live CD installer . . .
along with a logical 1GB swap area at sdb5
[B]
What file is needed by the grub rescue ?[/B]
. . . grub was installed to the sdb1 partition by the live installer utility.

Thanks for any suggestions you can offer.

---

### Post by kansasnoob on 2010-02-11
> **jenaniston said:**
> A live version would be great if it would boot a live version - 
but the "BusyBox" is what I get - I can press escape to see what happens before it stalls though.


sda1 is a SATA hard drive with Windows XP - but the XP recovery utility did a destructive process
(the OS is still there but only because linux and freebsd have told me it is there)
There is a logical and extended fat32 partition sda5

The full install USB OS is currently Xubuntu 9.04 64 bit . . . has always been dev/sdb -
with grub rescue it looks like it lists as (hd0,1) 

grub was installed to that sdb device at sdb1 with the live CD installer . . .
along with a logical 1GB swap area at sdb5
[B]
What file is needed by the grub rescue ?[/B]
. . . grub was installed to the sdb1 partition by the live installer utility.

Thanks for any suggestions you can offer.

If BIOS is set to boot from CD first you should never get to grub booting an Ubuntu Live CD. 

If you installed using a Live CD the BIOS settings are probably OK, but can you eject the CD tray? 

And then can you fully reboot? I think Ctrl + Alt + Delete should reboot you if stalled at grub.

Have you tried other Live CD's? (Age doesn't matter)

We really need a look at just what's installed where, not just operating systems, but boot files, etc.

---

### Post by ratcheer on 2010-02-11
You know what, I was just doing this, today. I did not succeed, but here is what the instructions said to do:

You have correctly set the prefix and root stuff.

Then, you "insmod /boot/grub/linux.mod". This is the part that failed on me.

Then, "linux /vmlinuz root=/dev/sdXY ro" where, based on your OP, XY would be "01".

Next, "initrd /initrd.img"

Finally, if all the above worked, "boot".

These changes will be temporary and, if you do get back up, successfully, you should run "sudo update-grub" to fix it, permanently.

Good luck,
Tim

---

### Post by darkod on 2010-02-11
Also, if you are sure grub is installed on /dev/sdb1 (with a number, that's a partition), and not /dev/sdb (the MBR of the disk), you can't expect to boot from it. That's why the default location for grub is the MBR of a disk, that's where bootloader should be.
If it's installed on a partition you need to call it from another bootloader.

---

### Post by darkod on 2010-02-11
> **ratcheer said:**
> 
Then, you "insmod /boot/grub/linux.mod". This is the part that failed on me.


Wasn't that supposed to be

insmod ext2

?

---

### Post by kansasnoob on 2010-02-11
> **darkod said:**
> Also, if you are sure grub is installed on /dev/sdb1 (with a number, that's a partition), and not /dev/sdb (the MBR of the disk), you can't expect to boot from it. That's why the default location for grub is the MBR of a disk, that's where bootloader should be.
If it's installed on a partition you need to call it from another bootloader.

That's why you must always be able to boot from some external media (or access from another computer) if things go haywire!

Grub will never stop you from booting a Live CD or USB. That occurs in BIOS before GRUB ever appears.

---

### Post by ratcheer on 2010-02-11
> **darkod said:**
> Wasn't that supposed to be

insmod ext2

?

Well, the instructions I was following did not say that. I was following the official grub2 documentation on ubuntu.com.

Tim

---

### Post by jenaniston on 2010-02-11
> **kansasnoob said:**
> . . .
We really need a look at just what's installed where, not just operating systems, but boot files, etc.

Well sorry to be confusing  . . . all live versions (or operating systems) are USB pendrive . . . no CD on the laptop.
 BIOS was happy before U9.10 with the USB boot - and bios is still ok with it.

Everything is on the USB OS dev/sdb - partition 1 - but **what file and command does grub rescue need **to look there ?

The install of the full OS to the USB was on a different machine using a live CD running on that machine . . . and ported to a "virtually thin" laptop 
(the hard drive Windows XP partition is not bootable/accessible - well, yet - at least until I get a linux or freebsd unix up on a USB OS)
It worked ok this way *until *Karmic and grub2 was tried . . . now i get the **grub rescue>** prompt.

So yes, boot files and the entire OS from the live version were installed to the sdb1 partition  . . . 
the USB OS primary partition - the only other on the USB is a swap area partition sdb5..

Where does the grub rescue need to go to boot the grub on partition sdb1 ?

---

### Post by darkod on 2010-02-11
> **ratcheer said:**
> Well, the instructions I was following did not say that. I was following the official grub2 documentation on ubuntu.com.

Tim

It might depend on grub version too. Now with the transition from grub1 to grub2 one has to read real carefully all the instructions/tutorials. Most of them would be for grub1 without specifically saying that because earlier that was the only grub around. :)

I'm almost sure with grub2 you need to use insmod ext2, in fact that's one of the lines in grub.cfg in the ubuntu entries.

---

### Post by jenaniston on 2010-02-11
> **ratcheer said:**
> You know what, I was just doing this, today. I did not succeed, but here is what the instructions said to do:

You have correctly set the prefix and root stuff.

Then, you "insmod /boot/grub/linux.mod". This is the part that failed on me.

Then, "linux /vmlinuz root=/dev/sdXY ro" where, based on your OP, XY would be "01".

Next, "initrd /initrd.img"

Finally, if all the above worked, "boot".

These changes will be temporary and, if you do get back up, successfully, you should run "sudo update-grub" to fix it, permanently.

Good luck,
Tim

OK Thanks alot . . .

I hadn't read your post as I wrote my last one above.

I'll try it -
Thanks again.

---

### Post by darkod on 2010-02-11
> **jenaniston said:**
> OK Thanks alot . . .

I hadn't read your post as I wrote the above.

I'll try it -
Thanks again.

For grub2 try
insmod ext2

not the other command in that list. Otherwise the rest should be the same.

And from what you wrote, you really have no grounds to blame 9.10 or grub2. It sounded pretty messy, creating a ubuntu installation on usb hdd on one computer, telling grub2 to install to a partition instead of the MBR, and then trying to boot it on completely another computer.
First of all, if that computer can boot from USB, the easiest way is just to use an ubuntu bootable usb stick or live usb if you want to call it that way. No need to have full ubuntu install on usb at all.
The live cd (live usb) is enough to boot any computer that can boot from usb and look around the hdd.

---

### Post by jenaniston on 2010-02-11
> **darkod said:**
> For grub2 try
insmod ext2

not the other command in that list. Otherwise the rest should be the same.

  no grounds to blame 9.10 or grub2.

Ian ubuntu bootable usb stick or live usb if you want to call it that way. No need to have full ubuntu install on usb at all.
The live cd (live usb) is enough to boot any computer that can boot from usb and look around the hdd.

Well, this ***should ***be just grub from the current 9.04 OS that is being booted . . . 
maybe all bets should be off though as Karmic has touched this system.

 . . . the live usb versions do NOT boot . . . the USB ported operating systems DOES . . .
 this is just a sad fact of this rescue mission.

Yes, I'll be fair to debian in that U 9.04 ***did*** work surprisingly well . . . BEFORE  9.10 and grub2 was tried . . . and touched any of this
but NOW going ***back*** to U 9.04 does NOT work . . . U9.10 and grub2 are central to this new problem.

I just want to get back at this rescue without grub2 and 9.10 - and any remnants it may have left behind.

All my praise is for Jaunty as it ***has*** been the real champ - but definitely*** not ***Karmic or grub2.

---

### Post by kansasnoob on 2010-02-11
Well I'd guess that legacy grub is on the mbr of sda (the internal) and who knows what's on the mbr of the external??????

When you installed Jaunty did you select where to put grub?

You've really painted yourself into a corner! One must always have a way to access a machine either by Live CD or USB, or through an SSH or FTP. Otherwise you're kind of screwed.

---

### Post by ratcheer on 2010-02-11
> **darkod said:**
> For grub2 try
insmod ext2

not the other command in that list. Otherwise the rest should be the same.



I tried that on mine. It didn't work, either. It did not give an error, but the following "linux" command was still not found, so it did not work. The documentation I was reading said the purpose of the insmod command was to enable it to find the linux command.

Tim

---

### Post by jenaniston on 2010-02-11
> **kansasnoob said:**
> Well I'd guess that legacy grub is on the mbr of sda (the internal) and who knows what's on the mbr of the external??????

When you installed Jaunty did you select where to put grub?

You've really painted yourself into a corner! One must always have a way to access a machine either by Live CD or USB, or through an SSH or FTP. Otherwise you're kind of screwed.

legacy grub is not on the internal drive - it never was - that is the XP that is crashed-
it has it's own problems and is why a live version can't be mounted to ramspace.

So, yeah . . . Ubuntu 9.10 Karmic sure got me painted me into **this **corner after I succumbed to the forum advice to try 9.10 -
I had held out for a while as I was quite happy with 9.04 Jaunty in Ubuntu and Xubuntu for this.

getting into the machine per se is not a problem . . . until Karmic anyway . . .
as I have always used a LAN PXE boot to get at this rescue mission of the hard drive
with **ploplinux LAN** giving me the choice of which drive to boot from . . .
hard drive or usb really the only choices . . .
but from there it is up to lilo or grub or (yeccch) grub2 as usual.

The PXE boot servers run on Fedora 12 KDE Live USB booted on a university computer - 
and can be stopped and disconnected as soon as the bios PXE boot sequence (ploplinux) 
then connects the USB full OS that is ported and bootable - 

[IMG]http://i372.photobucket.com/albums/oo161/sunblush/bootmngr5_1-1.jpg[/IMG]

(well, when Karmic hasn't apparently touched anything).

Thanks for the replies and good advice . . . I am still confident this can be fixed but
I'll have to continue this try again after classes tomorrow.

---

### Post by darkod on 2010-02-11
You're right. Here is what rescue mode says:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

While not all the following commands are necessary to boot to a linux  kernel, running all the commands will provide a better chance of success  by allowing the user to identify problems before the *boot*  command is executed.

```
ls  
set  prefix=(hdX,Y)/boot/grub  
set  root=(hdX,Y) 
set  
ls  /boot 
insmod  /boot/grub/linux.mod 
linux  /vmlinuz root=/dev/sdXY ro 
initrd  /initrd.img 
boot
```The only thing I can think of, is that you have to be careful to get the set prefix and set root commands right. Otherwise you're pointing it to a wrong location. If you are sure you did that correctly, I have no idea.

---

### Post by jenaniston on 2010-02-11
> **darkod said:**
> You're right. Here is what rescue mode says:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

While not all the following commands are necessary to boot to a linux  kernel, running all the commands will provide a better chance of success  by allowing the user to identify problems before the *boot*  command is executed.

```
ls  
set  prefix=(hdX,Y)/boot/grub  
set  root=(hdX,Y) 
set  
ls  /boot 
insmod  /boot/grub/linux.mod 
linux  /vmlinuz root=/dev/sdXY ro 
initrd  /initrd.img 
boot
```The only thing I can think of, is that you have to be careful to get the set prefix and set root commands right. Otherwise you're pointing it to a wrong location. If you are sure you did that correctly, I have no idea.

well for my case with legacy grub now . . .
the **ls **command
```
 grub rescue> ls (hd0,1)/boot/grub/
```mentioned  in my first post only lists certain files in that directory

**insmod** command is used to load modules - only the requested modules, no module dependencies like modprobe . . .
I think the full path including the partition have to be listed so for this file  /boot/grub/menu.lst in dev/sdb1
```

grub rescue> insmod (hd0,1)/boot/grub/menu.lst
error: invalid arch independent ELF magic
grub rescue>

```this is the 64 bit version - which worked best before -
so maybe the grub2 messed that up i.e grub2 for 64 bit Karmic has a bug . . .

more tomorrow - thanks everybuddy.

---

### Post by ratcheer on 2010-02-12
> **darkod said:**
> You're right. Here is what rescue mode says:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

While not all the following commands are necessary to boot to a linux  kernel, running all the commands will provide a better chance of success  by allowing the user to identify problems before the *boot*  command is executed.

```
ls  
set  prefix=(hdX,Y)/boot/grub  
set  root=(hdX,Y) 
set  
ls  /boot 
insmod  /boot/grub/linux.mod 
linux  /vmlinuz root=/dev/sdXY ro 
initrd  /initrd.img 
boot
```The only thing I can think of, is that you have to be careful to get the set prefix and set root commands right. Otherwise you're pointing it to a wrong location. If you are sure you did that correctly, I have no idea.

I agree. I was worried about that, but I am sure they were set correctly, in my case. I boot a kernel on sda5, so X=0 and Y=5. Also, when I set them to hd0,5 and used ls, I could see the kernel I wanted in /boot and I could see linux.mod in /boot/grub. But, "insmod  /boot/grub/linux.mod" always gave the error about grub_getcharwidth.

Anyway, I finally fixed things by booting to a Live CD and chroot'ing into my real system, then reinstalling grub.

Tim

---

### Post by darkod on 2010-02-12
> **ratcheer said:**
> I agree. I was worried about that, but I am sure they were set correctly, in my case. I boot a kernel on sda5, so X=0 and Y=5. Also, when I set them to hd0,5 and used ls, I could see the kernel I wanted in /boot and I could see linux.mod in /boot/grub. But, "insmod  /boot/grub/linux.mod" always gave the error about grub_getcharwidth.

Anyway, I finally fixed things by booting to a Live CD and chroot'ing into my real system, then reinstalling grub.

Tim

Actually the 0,5 is used only with hd0,5. If /dev/sd is used it would always be /dev/sda5 I think, never /dev/sd05. Maybe that held it up.

---

### Post by darkod on 2010-02-12
> **jenaniston said:**
> well for my case with legacy grub now . . .
the **ls **command
```
 grub rescue> ls (hd0,1)/boot/grub/
```mentioned  in my first post only lists certain files in that directory

**insmod** command is used to load modules - only the requested modules, no module dependencies like modprobe . . .
I think the full path including the partition have to be listed so for this file  /boot/grub/menu.lst in dev/sdb1
```

grub rescue> insmod (hd0,1)/boot/grub/menu.lst
error: invalid arch independent ELF magic
grub rescue>

```this is the 64 bit version - which worked best before -
so maybe the grub2 messed that up i.e grub2 for 64 bit Karmic has a bug . . .

more tomorrow - thanks everybuddy.

Actually those commands are for grub2 and you mentioned a lot of times already that you are using grub1, or legacy.

Are you trying to solve your problem or just complain about karmic and grub2? Because it's getting annoying, at least for me.
I don't know why you can boot grub2, but in your posts you also mentioned that you can boot 9.04 with grub1 either, so I don't see any grounds to keep complaining all the time about karmic and grub2. Jaunty doesn't seem to work for you either.

Also, the core of the problem is trying to repair a windows installation if I understood right. So, you are trying to repair windows by using linux and keep complaining about it? Why don't you use windows tools, or boot windows in live mode.

Now that I got that off my chest, lets get down to the problem:
1. I see you are using some LAN PXE. Why? Are the computers so old that they can't boot or are not able to boot from cd or live usb? If you can boot at leats from usb (without using PXE), just create a NEW usb stick on another computer and try it. Format the stick as FAT32 to start from scratch, and use 9.04 image since you hate karmic so much. If that doesn't boot your broken computer, the problem is not karmic and definitely not grub2.

2. Even if you do need to use PXE to boot from usb, create a new stick as recommended above, and try to boot it. Again, if a new jaunty stick doesn't boot, how it that karmic's fault?

3. You can try the above with a newly created karmic live usb too, just to see that it will work just fine, unless there is some hardware incompatibility.

4. You seem to want to repair broken windows install. Why are you tying to use commands to boot linux kernel??? To boot your ubuntu stick/hdd? Just forget about it, quit complaining and create another karmic/jaunty live usb stick. THAT'S ALL YOU NEED! Not an installation on a usb hdd, all you need is so called live usb of ubuntu. And boot from it.

And that's it, it's rather simple. You seem to be limited what you have to work with, but all these complains sound unfounded.

You have to take another thing into consideration: People are reading this, people ready to try karmic. And it doesn't sound right putting them off while you can't even boot jaunty too. Personally, if I want to try an OS I just do it, regardless of postings like this. But some people might be put off. And at the same time you're trying to repair windows with ubuntu. Do you think you are being fair to ubuntu here???

---

### Post by darkod on 2010-02-12
> **jenaniston said:**
> well for my case with [COLOR=Red]legacy grub[/COLOR] now . . .

I think the full path including the partition have to be listed so for this file  /boot/grub/menu.lst in [COLOR=Red]dev/sdb1[/COLOR]
```

grub rescue> insmod [COLOR=Red](hd0,1)[/COLOR]/boot/grub/menu.lst
error: invalid arch independent ELF magic
grub rescue>

```

I will say again, that list of commands is for rescue mode of grub2, not grub legacy!
Also, /dev/sdb1 in grub legacy can be (hd1,0) or (hd0,0) but it definitely can't be (hdX,1). Legacy is counting partitions from 0. But I guess that's karmic/grub2 fault too.

I suggest you sit down a little bit, settle down, because at this moment it doesn't sound like you know what you want to achieve at all. Don't just throw commands at your computer regardless whether they are for grub1, grub2, or whether they are needed at all.

Also try to explain more precisely and simply what you need, in order to receive help. Don't complain on karmic, tell us what you need.
I still don't understand why you need manual kernel booting commands to repair broken windows computer.

---

### Post by jenaniston on 2010-02-12
> **darkod said:**
>  Jaunty doesn't seem to work for you either.

Again, if a new jaunty stick doesn't boot, how it that karmic's fault?

**People are reading this, people ready to try karmic**.
And at the same time you're trying to repair windows with ubuntu. Do you think you are being fair to ubuntu here???

Yes, that is why people need to be aware of these and similar experiences . . .
that is how open source develops - NOT shovelling under the carpet and hiding the truth.

Jaunty USB OS only doesn't work after grub2 and Karmic were tried on some advice I took . . . 
I held off long enough using 9.04 that realize U9.04 and linux on this particular project can be successful 
as they have before on other projects with both Jaunty and Fedora 11 and 12  -
i expect that going back will be just fine with those other linux redhat or debain distributions besides Karmic.

so AFTER Karmic/grub2 were tried, yes - going back to Jaunty not working - yet - either.
Did work fine for me before Karmic though.

The mistake was in trying Karmic and grub2 - that is just a fact here whether you are a happy advocate of Karmic or not.

So as always . . . really just asking where to try continuing at the **grub rescue>** command -

**grub rescue>** is new to me . . .
 so Karmic has been a great help in learning this new frontier.  Thank you Karmic developers . . .
I will truely be better off in the long run knowing this abyss exists and to watch out for the Karmic land mines planted - 
enter Karmic land at your own peril is now my advice based on this unpleasant experience.

what does **grub rescue>** need ? Does it need some help to find the right file to load ?

No fret - but I promise never to take any advice to try Karmic or grub2 again -
for either this rescue or any of the other computers I am repairing.

---

### Post by darkod on 2010-02-12
> **jenaniston said:**
> Yes, that is why people need to be aware of these and similar experiences . . .
that is how open source develops - NOT shovelling under the carpet and hiding the truth.

Jaunty USB OS only doesn't work after grub2 and Karmic were tried on some advice I took . . . 
I held off long enough using 9.04 that realize U9.04 and linux on this particular project can be successful 
as they have before on other projects with both Jaunty and Fedora 11 and 12  -
i expect that going back will be just fine with those other linux redhat or debain distributions besides Karmic.

so AFTER Karmic/grub2 were tried, yes - going back to Jaunty not working - yet - either.
Did work fine for me before Karmic though.

The mistake was in trying Karmic and grub2 - that is just a fact here whether you are a happy advocate of Karmic or not.

So as always . . . really just asking where to try continuing at the **grub rescue>** command -

**grub rescue>** is new to me . . .
 so Karmic has been a great help in learning this new frontier.  Thank you Karmic developers . . .
I will truely be better off in the long run knowing this abyss exists and to watch out for the Karmic land mines planted - 
enter Karmic land at your own peril is now my advice based on this unpleasant experience.

what does **grub rescue>** need ? Does it need some help to find the right file to load ?

No fret - but I promise never to take any advice to try Karmic or grub2 again -
for either this rescue or any of the other computers I am repairing.

Again, you spent all this time complaining about karmic instead of providing some information and feedback. I gave you few suggestions including creating a jaunty live usb and trying to boot the broken computer with that, you never say whether you tried it or not.
I'm officially giving up, it's impossible to help you like this.

---

### Post by jenaniston on 2010-02-12
> **darkod said:**
> . . .still don't understand why you need manual kernel booting commands to repair broken windows computer.

Because I desire to get past the
```
grub rescue>
```all to get other linux or unix to boot now after trying Karmic versions of ubuntu -
it is an amd64 cpu computer . . . no windows still on it, but their is a windows fat32 partition I would like to get at using linux.

---

### Post by jenaniston on 2010-02-12
> **darkod said:**
> Again, you spent all this time complaining about karmic instead of providing some information and feedback. I gave you few suggestions including creating a jaunty live usb and trying to boot the broken computer with that,** you never say whether you tried it or not.**
I'm officially giving up, it's impossible to help you like this.

Read more then.

All you really seem to do is need to defend Karmic and try to exclude this information from others that want to try Karmic -
that info should be available.

creating ***any live*** jaunty or other linux doesn't work ever as I said earlier -
so post till you are blue in the face with that sorry suggestion -
live versions need some working hard drive partition to mount in ramspace -
**live versions don't *boot* on thin clients**.

But if you understand **grub rescue>** than great if you have any suggestion to try.

The suggestions to be kind to Karmic won't be very convincing to me or other readers -
at least until I get by the ```
grub rescue>
```

---

### Post by jenaniston on 2010-02-12
> **jenaniston said:**
> 
**insmod** command is used to load modules - only the requested modules, no module dependencies like modprobe . . .
I think the full path including the partition have to be listed so for this file  /boot/grub/menu.lst in dev/sdb1
```

grub rescue> insmod (hd0,1)/boot/grub/menu.lst
error: invalid arch independent ELF magic
grub rescue>

```this is the 64 bit version - which worked best before -
so maybe the grub2 messed that up i.e grub2 for 64 bit Karmic has a bug . . .

more tomorrow - thanks everybuddy.

**insmod** works in unix as well btw

> **darkod said:**
> 
Also, /dev/sdb1 in grub legacy can be (hd1,0) or (hd0,0) but it definitely can't be (hdX,1). Legacy is counting partitions from 0. But I guess that's karmic/grub2 fault too.

  

**darkrod** I appreciated your real suggestions . . . but you seem to have challenged that  I
shouldn't spill the beans on Karmic.

But you are wrong about (hd0,1) and the /boot/grub/menu.lst . . . 
that partition is definitely the new Jaunty USB OS menu.lst that I expected to boot to . . .
**dev/sdb1**  -or -** (hd0,1)**/boot/grub/menu.lst
```

# . . .
## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        cace50fb-fa66-41a8-a846-b8878b0fa69e
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=cace50fb-fa66-41a8-a846-b8878b0fa69e ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        cace50fb-fa66-41a8-a846-b8878b0fa69e
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=cace50fb-fa66-41a8-a846-b8878b0fa69e ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        cace50fb-fa66-41a8-a846-b8878b0fa69e
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
chainloader    +1


```

---

### Post by jenaniston on 2010-02-12
From original post . . .
These are **ls** results . . .
```
grub rescue> ls (hd0,1)/boot
./ ../ System.map-2.6.28-11-generic abi-2.6.28-11-generic config-2.6.28-11-generic
memtest86+.bin vmcoreinfo-2.6.28-11-generic vmlinuz-2.6.28-11-generic 
grub/ initrd.img-2.6.28-11-generic
grub rescue>
``````
grub rescue>** ls (hd0,1)/boot/grub/**
./ ../ device.map stage1 stage2 e2fs_stage1_5 fat_stage1_5 jfs_stage1_5 
minix_stage1_5 reiserfs_stage1_5 xfs_stage1_5 default **installed-version** menu.lst
grub rescue>
```Any ideas as I experiment to further nudge this along to the usual and expected 9.04 boot screen ?

and . . .

**dev/sdb1**  -or -** (hd0,1)**/boot/grub/installed-version
```
0.97-29ubuntu53
```

---

### Post by kansasnoob on 2010-02-12
OK I've done some studying, and the grub-rescue> prompt is a grub2 thing. Maybe grub2 is still installed to the mbr of a drive, anyway try:

grub-rescue> **normal**

And see if the prompt changes to:

grub>

If so try:

```
find /boot/grub/stage1
```

Whatever it shows, example (hdX,Y), use it in the next command (note: 0's are zeros):

```
root (hdX,Y)
```

```
setup (hdX)
```

Then hopefully you'll see:

```
Checking if "/boot/grub/stage1" exists... **yes**
Checking if "/boot/grub/stage2" exists... **yes**
Checking if "/boot/grub/e2fs_stage1_5" exists... **yes**
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...* 15 sectors are embedded.
**succeeded**
Running "install /boot/grub/stage1 d (hd0) (hd0)1+15 p (hd0,1)/boot/grub/stage
2 /boot/grub/menu.lst"... **succeeded**
Done. 
```

Then you can just:

```
quit
```

And if you're real lucky maybe you'll be able to boot.

---

### Post by jenaniston on 2010-02-12
> **kansasnoob said:**
> OK I've done some studying, and the grub-rescue> prompt is a grub2 thing. Maybe grub2 is still installed to the mbr of a drive, anyway try:

grub-rescue> **normal**

And see if the prompt changes to:

grub>

If so . . .

 . . . And if you're real lucky maybe you'll be able to boot.

I realize I threw you off by not being able to use live version - believe me I wish I could.
The grub rescue prompt is immediate . . . no time running behind a quiet splash screen with lots of boot info - instantaneous.

One advantage I do have though is that the USB OS can be unplugged then put in a USB drive port on a running live version . . .
so I ***can*** see the files there . . . but obviously the laptop "thin client" boot log won't be there as you requested originally to start troubleshooting.

Those files are the same as with the **> ls (hd0,1) /boot/grub/** 

I tried, but the** normal** command is not available . . .

```
grub rescue> normal
Unknown command 'normal'
grub rescue>
```I think you are definitely right . . .
something ***did*** get written in grub2 / by grub2 to the MBR of the hard drive . . .


yet still . . . from the grub rescue>** ls** command* all* the other partitions/drives ("slices" in unix terminology)
show the same error message . . . (except the (hd0,1) )

```
grub rescue> ls
(hd0) (hd0,5) (hd0,1) (hd1) (hd1,5) (hd1,4) (hd1,3) (hd1,1)
grub rescue>
grub rescue> (hd1,1)
error: unknown filesystem
grub rescue>
```I will say the mapping is messed up . . .
Here's a link to show where I am at - [http://www.gnu.org/software/grub/manual/html_node/Device-map.html](http://www.gnu.org/software/grub/manual/html_node/Device-map.html)

Could this be as simple as a device mapping error . . . I need to point grub rescue> to the correct file for Jaunty ?

Thanks for your interest . . . and do I think I will get lucky in the end with this.

More to try . . . but I do think it is important to post this stuff . . . 
as others will benefit in the future from this struggle.

---

### Post by bildr on 2010-07-04
working on this now, basically what happens is when you install from usb the installer screws up.  proper recovery is:
from grub-rescue>
ls
ls (hd0,1)
root=(hd0,1)
-----or whatever your root is-----
-----keep ls ing until you find your root---

[B]set root=(hdX,Y)
[/B][B]set prefix=(hdX,Y)/boot/grub
[/B][B]set
[/B][B]insmod /boot/grub/linux.mod
[/B][B]linux /vmlinuz root=/dev/sdXY ro
[/B][B]initrd /initrd.img
[/B][B]boot

[/B]--------the problem comes in when the module that provides getchar isn't loaded----
everyone else on the thread is being retarded by saying just reinstall
i had this problem and recovered from thumbdrive but this is a workaround not a solution
i am installing the debug packages to find the .mod file with getchar now...
i will update my response once i find it, don't hesitate to pm me if i forget to post the full answer.  this issue is NOT solved.

---

