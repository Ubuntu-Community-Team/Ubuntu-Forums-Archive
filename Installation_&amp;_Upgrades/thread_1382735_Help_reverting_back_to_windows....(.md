---
title: "Help reverting back to windows....:("
date: 2010-01-16
forum: Installation &amp; Upgrades
---

### Post by bdws1975 on 2010-01-16
hi all,

I LOVE ubuntu and will never go back to windows.  My wife however....

I made the mistake of installing ubuntu on her laptop without really asking.  Now she's insisting that I put it back to windows.  I tried to convince her otherwise, but she's dead set on it.

When I installed Ubuntu on hers I reformatted the HD and had linux take over the whole thing.

I tried to put my windows XP image disk in and it will not do anything.  Please, please, please direct me to how to revert back.  I'm still very new with computers so please make sure it's the 'for dummies' version.

thanks for your help,

Brett

---

### Post by mhgsys on 2010-01-16
I guess the problem is that windows does not recognize the ext partitions ubuntu works with. 

There's an easy solution for this, (maybe even in System> administration partition editor? on live cd>)

Anyway ; 

Bootup a live cd of ubuntu , open a terminal (applications>accessories>terminal)  and run 
```

gksudo gparted

```

This will start up the Partition Editor
It will scan your disk(s) and will give you the option to delete all partitions so that the xp cd recognizes it as free space again, or you could make a ntfs partition wich you can edit with the Xp cd.

---

### Post by Leppie on 2010-01-16
why didn't you make the machine dual boot? or does it have one of those old tiny disks (<40gb)?
linux mint (another ubuntu distro developed especially for transition from windows to linux) together with windows could be a nice transition?
if you're already repartitioning the disk, set up half for windows and the other half to install ubuntu and make it dual boot.

---

### Post by leorolla on 2010-01-16
Yep, try Gparted.

You can even make an usb-bootable version of it.

Next time:
- ask your wife first
- make it dual boot
- test both boots a few times before you start really using it

---

### Post by Leppie on 2010-01-16
> **leorolla said:**
> Next time:
- ask your wife first
i totally agree :P

---

### Post by leorolla on 2010-01-21
Did it work with Gparted?

---

### Post by bdws1975 on 2010-01-22
hi folks,
..
Ok, here's a screen shot of what I see in gparted.

I'm VERY new to linux, etc so please speak slowly...:)

Thanks,
Brett

---

### Post by bdws1975 on 2010-01-22
yeah, you're completely right on asking her next time.  She's cool now, but has asked me several times when it will be back.

I'm stuck in the mud right now....

Thanks for your help,

brett

> **leorolla said:**
> Yep, try Gparted.

You can even make an usb-bootable version of it.

Next time:
- ask your wife first
- make it dual boot
- test both boots a few times before you start really using it

---

### Post by 73ckn797 on 2010-01-22
Delete the Ubuntu partitions from your drive using GParted on the LiveCD. Once that is finished create a new partition using the entire drive and format to ntfs. Then reboot with the Windows disk and install. I would recommend that you also allow Windows install to format the drive. I have had problems with Windows having problems installing on a drive formatted to ntfs with Gparted. The linux MBR was not deleted. A quick format will do the trick. This has happened twice in the last month on 2 different computers.

---

### Post by bdws1975 on 2010-01-22
what is a LiveCD?

Thanks,
BRett

> **73ckn797 said:**
> Delete the Ubuntu partitions from your drive using GParted on the LiveCD. Once that is finished create a new partition using the entire drive and format to ntfs. Then reboot with the Windows disk and install. I would recommend that you also allow Windows install to format the drive. I have had problems with Windows having problems installing on a drive formatted to ntfs with Gparted. The linux MBR was not deleted. A quick format will do the trick. This has happened twice in the last month on 2 different computers.

---

### Post by bdws1975 on 2010-01-22
ok!  I figured it out.  Livecd...duh...:)

I'll give it a shot.

Brett

---

### Post by 73ckn797 on 2010-01-22
> **bdws1975 said:**
> what is a LiveCD?

Thanks,
BRett

That would be the disk you used to install Ubuntu. You boot from it and select to try without installing, the first choice when the menu comes up after booting.

edit: YEP you figured it out.

---

### Post by bdws1975 on 2010-01-22
OK.  Not sure what happened.

I booted from the Livecd and then used gparted to format the 250g. Partition to ntfs 

When I rebooted with windows it says

Grub loading
Error: unknown filesystem 
Grub rescue>

---

### Post by 73ckn797 on 2010-01-22
> **bdws1975 said:**
> OK.  Not sure what happened.

I booted from the Livecd and then used gparted to format the 250g. Partition to ntfs 

When I rebooted with windows it says

Grub loading
Error: unknown filesystem 
Grub rescue>


Was that when booting from the Windows disk? I doubt Windows installed that quickly since the last message. That same thing happened to me and that is why I stated having the Windows installation format the drive also. That will wipe out the Linux MBR.

---

### Post by 73ckn797 on 2010-01-22
You may need to boot the Windows CD and select recovery mode. From the command prompt ```
C:\
``` enter ```
fixmbr
``` then reboot and install Windows.

---

### Post by bdws1975 on 2010-01-22
> **73ckn797 said:**
> Was that when booting from the Windows disk? I doubt Windows installed that quickly since the last message. That same thing happened to me and that is why I stated having the Windows installation format the drive also. That will wipe out the Linux MBR.

Ok, I understand each word you wrote, but it doesn't make sense to me.

All I did was boot the livecd, reformat the large partition, apply the changes, and then shut down the computer and stick in the windows xp cd and start it up.

I have no idea what to do beyond that.

Please help me but in dumbo english....:)  Sorry to be so stupid.

Thanks again!

brett

---

### Post by 73ckn797 on 2010-01-22
Does the Windows CD boot up to the installation menu? I assume the computer is set to boot from CD first and not the hard drive.

The Windows menu will list options to install and recover. Select recover and follow my last post, reboot again to the Windows install menu then install.

---

### Post by bdws1975 on 2010-01-22
every time I to boot from the cdrom I get the same erro: unknown filesystem.

> **73ckn797 said:**
> You may need to boot the Windows CD and select recovery mode. From the command prompt ```
C:\
``` enter ```
fixmbr
``` then reboot and install Windows.

---

### Post by bdws1975 on 2010-01-22
no matter what I do, I get the same black screen with the following:

GRUB Loading
error:  unknown filesystem
grub rescue>

---

### Post by bdws1975 on 2010-01-22
ok, here's where I am:

when I take the windows cd out and then put back in the livecd, it takes me to the ubuntu install.

I'm livebooting it again...

what did I do wrong?

Brett

---

### Post by Vignesh S on 2010-01-22
> **bdws1975 said:**
> what is a LiveCD?

Thanks,
BRett

It is when you put the Ubuntu CD into your computer, and it comes up with "Try Ubuntu without any changes to your computer" (or something like that) as well as other options. If left alone, Ubuntu will go into that by default. 

A LiveCD is pretty much an Operating system where you can try it out on the CD itself.

---

### Post by bdws1975 on 2010-01-22
hi again.  yeah, I know..pain in the ***..:)
I managed to boot from the livecd and am in gparted again.

I've attached a screen shot of what I see there.

Also, I'm using an xp disk image.iso for the windows cd...is that a problem?

Thanks again,

brett

---

### Post by Vignesh S on 2010-01-22
hmm.... I had the same problem. Well, on my sister's netbook, I just went into the XP install CD, then I just deleted the Ubuntu partitions. And it just started working after that. No commands, no complicated stuff. It was that dead simple. 

You have to make sure that you get up to the stage in the XP install where it asks you which partition you want to install it onto. That's where you delete the Ubuntu partitions :-).

[This]("http://ubuntuforums.org/showthread.php?t=1377841") thread could be helpful. That was when I had the same problem of getting rid of Ubuntu off the dual boot.

Not sure by what you mean when you said that you are using an XP ISO image. Could you please elaborate on that?

Sorry about my last post. I forgot to read the 2nd page of the thread :-)

---

### Post by bdws1975 on 2010-01-22
that's just the thing.  I'm not getting anywhere when I put in the windows cd.

the only thing I get is the error I have typed above.


Brett

> **Vignesh S said:**
> hmm.... I had the same problem. Well, on my sister's netbook, I just went into the XP install CD, then I just deleted the Ubuntu partitions. And it just started working after that. No commands, no complicated stuff. It was that dead simple. 

You have to make sure that you get up to the stage in the XP install where it asks you which partition you want to install it onto. That's where you delete the Ubuntu partitions :-).

Sorry about my last post. I forgot to read the 2nd page of the thread :-)

---

### Post by Vignesh S on 2010-01-23
hmmm...... So you are saying that when you put the XP cd into the computer, it doesn't come up with anything?

---

### Post by bdws1975 on 2010-01-23
that's exactly what I'm saying.

I get an error:

GRUB Loading
error:  unknown filesystem
grub rescue>



> **Vignesh S said:**
> hmmm...... So you are saying that when you put the XP cd into the computer, it doesn't come up with anything?

---

### Post by Vignesh S on 2010-01-23
Whoa whoa whoa, wait up a second here. I'm kinda getting lost :?

I mean putting the installation CD into the computer, not loading XP up that's already installed. I mean putting the XP install CD into the computer the same way you did with Ubuntu. Mind that you have to press any key to enter into the setup when prompted to, which might be why it comes up with the GRUB rescue prompt to begin with. 

Regardless, to change the boot loader to Windows or to delete the partitions or even just to reformat the whole computer with XP (which isn't necessary as far as I can see), you have to go into the XP setup via the XP installation CD. 

Whereas if you only have the ISO and not the actual CD, then that's something different altogether. If you have a CD burner, you can just go into Ubuntu (via USB if there's only 1 CD drive), double click on the ISO and burn it to disk from there.

---

### Post by bdws1975 on 2010-01-23
you're lost???  Try being me...;)

I already burned the .iso to a disk.  That should be good, right?  I can use that to install windows?

Thanks and take care,

brett

> **Vignesh S said:**
> Whoa whoa whoa, wait up a second here. I'm kinda getting lost :?

I mean putting the installation CD into the computer, not loading XP up that's already installed. I mean putting the XP install CD into the computer the same way you did with Ubuntu. Mind that you have to press any key to enter into the setup when prompted to, which might be why it comes up with the GRUB rescue prompt to begin with. 

Regardless, to change the boot loader to Windows or to delete the partitions or even just to reformat the whole computer with XP (which isn't necessary as far as I can see), you have to go into the XP setup via the XP installation CD. 

Whereas if you only have the ISO and not the actual CD, then that's something different altogether. If you have a CD burner, you can just go into Ubuntu (via USB if there's only 1 CD drive), double click on the ISO and burn it to disk from there.

---

### Post by Vignesh S on 2010-01-23
> **bdws1975 said:**
> you're lost???  Try being me...;)

I already burned the .iso to a disk.  That should be good, right?  I can use that to install windows?

Thanks and take care,

brett

Alright, that makes a LOT more sense :-). So you've got the .ISO burned to the disk. Before you do though, if you've got another computer to test this on, can you load up whatever OS is on that, put the CD in and find out whether there is a just a .ISO file there or folders of stuff i.e. something that's not just one .ISO file on the disk?

---

### Post by bdws1975 on 2010-01-23
okie dokie, I did that.  There's just the .iso on the disk.

Thanks again,

Brett

> **Vignesh S said:**
> Alright, that makes a LOT more sense :-). So you've got the .ISO burned to the disk. Before you do though, if you've got another computer to test this on, can you load up whatever OS is on that, put the CD in and find out whether there is a just a .ISO file there or folders of stuff i.e. something that's not just one .ISO file on the disk?

---

### Post by Vignesh S on 2010-01-23
> **bdws1975 said:**
> okie dokie, I did that.  There's just the .iso on the disk.

Thanks again,

Brett

That's our problem. The ISO's contents have to be extracted onto the disk via burning. Usually, this is achieved by double-clicking on the ISO file (ensuring it is on the computer and not on the CD if that's the only copy of the file left) and burning to disk via the utility that comes up (don't worry, its very easy to use). 

The .ISO file on its own is not going to do anything. No wander XP wasn't loading up when you put it into the computer.

---

### Post by Barriehie on 2010-01-23
> **bdws1975 said:**
> okie dokie, I did that.  There's just the .iso on the disk.

Thanks again,

Brett

Oops, it should have files and folders on it.  Do you still have the .iso file that was put on the CD?

---

### Post by Vignesh S on 2010-01-23
> **Barriehie said:**
> Oops, it should have files and folders on it.  Do you still have the .iso file that was put on the CD?

I presume he would, seeing that it wasn't all that long ago that he told us that the CD had the ISO file in it.

---

### Post by bdws1975 on 2010-01-23
okie dokie...got it.

so I did as you said and t here's a FOLDER that says XP Disk Image.  Should I burn that whole folder?

Thanks,
Brett

 > **Vignesh S said:**
> That's our problem. The ISO's contents have to be extracted onto the disk via burning. Usually, this is achieved by double-clicking on the ISO file (ensuring it is on the computer and not on the CD if that's the only copy of the file left) and burning to disk via the utility that comes up (don't worry, its very easy to use). 

The .ISO file on its own is not going to do anything. No wander XP wasn't loading up when you put it into the computer.

---

### Post by bdws1975 on 2010-01-23
I sent it to burn and it zipped it.  is that ok?> **bdws1975 said:**
> okie dokie...got it.

so I did as you said and t here's a FOLDER that says XP Disk Image.  Should I burn that whole folder?

Thanks,
Brett

---

### Post by bpalone on 2010-01-23
If you have the ISO image on your other computer with Ubuntu on it.  Just open Brasero (I am assuming that is still in the version of Ubuntu you are running.) and click on the Burn Image.  Then select the ISO you want to burn to a CD.

Once you do that, you should be good to go.

Good luck.

---

### Post by Vignesh S on 2010-01-23
> **bdws1975 said:**
> I sent it to burn and it zipped it.  is that ok?

You did make sure that there was a blank CD in the CD burner before you 'burnt' it right? If I take what you are saying as correct, then the ISO file got put in a ZIP file rather than burning it onto a blank disk ;-)

And these are instructions for Ubuntu, not Windows. Dang, should have asked first what OS you are running on the computer this is being burned on ;-). Well, I'll ask that now: are you using Ubuntu on the computer this is being burnt onto?

---

### Post by bdws1975 on 2010-01-23
howdy.

I unpacked the .iso and there was a folder there that said XP image.  I sent it to brasero (I'm burning it on ubuntu).  the files were larger than the 700mb blank disk.  So it automatically zipped the file.

Is it ok to burn the zip file and will it work?

brett> **Vignesh S said:**
> You did make sure that there was a blank CD in the CD burner before you 'burnt' it right? If I take what you are saying as correct, then the ISO file got put in a ZIP file rather than burning it onto a blank disk ;-)

And these are instructions for Ubuntu, not Windows. Dang, should have asked first what OS you are running on the computer this is being burned on ;-). Well, I'll ask that now: are you using Ubuntu on the computer this is being burnt onto?

---

### Post by bpalone on 2010-01-23
This ISO image that you are using, is it from a Backup?  The reason I ask, is I think XP fits on a single CD.  I know Home does, but not sure about Pro.

---

### Post by Vignesh S on 2010-01-23
> **bdws1975 said:**
> howdy.

I unpacked the .iso and there was a folder there that said XP image.  I sent it to brasero (I'm burning it on ubuntu).  the files were larger than the 700mb blank disk.  So it automatically zipped the file.

Is it ok to burn the zip file and will it work?

brett

Sorry, but I don't that will quite do :-(. The files have to be burned directly onto the disk. Strange :? I thought the XP ISO fitted into a CD and wasn't on a DVD. Do you happen to have a DVD burner on this computer? We could get the ISO onto a DVD.

Then, there is a thing called overburning i.e. burning a bigger file onto a disk that is smaller than the file, though I'm not too experienced with that. I wouldn't recommend it though, seeing that there are so many risks involved. 

One more thing: How big is the ISO file?

---

### Post by bdws1975 on 2010-01-23
ok guys,  here's where I'm at now:

I have several partitions now.  

1.  and empty NTFS 
2.  a swap, etc , ubuntu

I got ubuntu loading again and I'm all good there.

When I put in my XP iso disk and place it in the cd drive and then reboot, it still takes me right into ubuntu.  I hit F10 to change the boot order and cd drive is set to first.

As for the Xp iso, it fits on one disk if I just burn t he iso file and don't double click it, etc and  unpack it.

What am I doing wrong?

thanks,

Brett

---

### Post by Vignesh S on 2010-01-23
hmmm... nasty. There isn't any other way though: the ISO has to be extracted onto the disk. Nothing will happen if only the ISO is burnt to the disk. Can you burn DVD's on your computer? How about the computer you are trying to fix this on? Can that read DVD's?

If you answered no to the above queries, I suggest you contact Microsoft and ask them for another copy of your XP disk. That way, you won't have to worry about an burning XP ISO that don't fit onto a CD.

---

### Post by bdws1975 on 2010-01-23
what about a thumb drive?

Can I 'burn' it on a large thumb drive?

If so, I'm sure there's a tutorial somewhere.

Thanks again,

Brett

> **Vignesh S said:**
> hmmm... nasty. There isn't any other way though: the ISO has to be extracted onto the disk. Nothing will happen if only the ISO is burnt to the disk. Can you burn DVD's on your computer? How about the computer you are trying to fix this on? Can that read DVD's?

If you answered no to the above queries, I suggest you contact Microsoft and ask them for another copy of your XP disk. That way, you won't have to worry about an burning XP ISO that don't fit onto a CD.

---

### Post by Vignesh S on 2010-01-23
Do you know if the computer you are trying to install XP onto can boot from USB's? In my experience, any computer older than 7 years can't exactly do so.

---

### Post by Elfy on 2010-01-23
If you carry on getting problems with the xp disc try supergrub - it will sort out your xp boot too

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by bdws1975 on 2010-01-23
yep, i believe it can.  it's a laptop only 4 months old.

> **Vignesh S said:**
> Do you know if the computer you are trying to install XP onto can boot from USB's? In my experience, any computer older than 7 years can't exactly do so.

---

### Post by Vignesh S on 2010-01-23
Well, to install XP via USB, you'll need to have XP installed somewhere to begin with :? if extracting the ISO to the USB doesn't work. That didn't quite work out for me though, though you might have better luck. You'll need a USB that is around 1GB though.

---

### Post by robert shearer on 2010-01-23
Where is the  Win ISO sourced from ??
Is it a genuine MS disc ??

---

### Post by Vignesh S on 2010-01-23
> **robert shearer said:**
> Where is the  Win ISO sourced from ??
Is it a genuine MS disc ??

Yeah, I have my doubts about that too, robert shearer, though it isn't that hard to make an ISO out of a legitimate Windows XP disk (copy the contents onto the HDD then make it into an ISO), or so I think ;-)

---

### Post by leorolla on 2010-01-23
We need to isolate the problem to know what is going wrong.

Right now the suspiction is that your CD is not good. It seems to contain an ISO file and not the *contents* of that ISO file themselves.

If this is the case then you probably don't have any problems with the HD file system at all.

1. Can you boot any other PC with this same disk?

If not, then we will know for sure that this is the problem.

2. Can you get an original CD from someone?

Otherwise you will have to burn a CD again.

3. What is the size in bytes of the ISO file that you have inside the CD?

If it is less than 700MB, it means you probably can copy this file to your own laptop and burn it to a brand-new fresh recordable CD.

My personal recomendatiopn is that you don't give the full HD to WindowsXP or any other OS. 50 GB are more than enough. Then create another partition (prefereably FAT32) to leave your photos, music, and documents. This way you can play with OS partitions without messing up with your personal data (but keep a backup elsewhere, of course). Moreover, don't delete the  ext4 partition... leave it there so that in near future you will convince your wife and the Ubuntu installation will be painless and will not have to mess up with the Windows setting. In summary, you can leave (in that order): 50GB NTFS, 200GB FAT32, 47GB ext4. Just go to Gparted again, delete all the partitions and create one after the other in this order, starting from the left edge of the HD.

For my own interest and curiosity, how did you get that Gparted running?

---

### Post by Vignesh S on 2010-01-23
> **leorolla said:**
> We need to isolate the problem to know what is going wrong.

Right now the suspiction is that your CD is not good. It seems to contain an ISO file and not the *contents* of that ISO file themselves.

If this is the case then you probably don't have any problems with the HD file system at all.

1. Can you boot any other PC with this same disk?

If not, then we will know for sure that this is the problem.

2. Can you get an original CD from someone?

Otherwise you will have to burn a CD again.

3. What is the size in bytes of the ISO file that you have inside the CD?

If it is less than 700MB, it means you probably can copy this file to your own laptop and burn it to a brand-new fresh recordable CD.

My personal recomendatiopn is that you don't give the full HD to WindowsXP or any other OS. 50 GB are more than enough. Then create another partition (prefereably FAT32) to leave your photos, music, and documents. This way you can play with OS partitions without messing up with your personal data (but keep a backup elsewhere, of course). Moreover, don't delete the  ext4 partition... leave it there so that in near future you will convince your wife and the Ubuntu installation will be painless and will not have to mess up with the Windows setting. In summary, you can leave (in that order): 50GB NTFS, 200GB FAT32, 47GB ext4. Just go to Gparted again, delete all the partitions and create one after the other in this order, starting from the left edge of the HD.

For my own interest and curiosity, how did you get that Gparted running?

1. Instead of burning the ISO to the disk, he burnt the actual ISO file to the disk i.e. only the ISO was on the disk, because doing the former wouldn't fit onto a CD for some reason :-(. That's what's been happening for like the last 2 pages; establishing just that :-D

2. Up to bdws1975, though trying to burn it onto a DVD couldn't hurt either

3. As mentioned in 1., the ISO is clearly around 700MB, but extracted and burnt onto the CD, it quite isn't :?

As for the tips about how to partition the Hard Drive, that's also up to bdws1975 ;-)

Hope I haven't just stepped into bdws1975's shoes ;-). But I thought a little clarifying of the situation might help. The last 2 pages have been somewhat confusing ;-)

As for Gparted, I think its on the Ubuntu 9.10 LiveCD/USB. I managed to get into it running before.

---

### Post by leorolla on 2010-01-23
> **bdws1975 said:**
> howdy.

I unpacked the .iso and there was a folder there that said XP image. I sent it to brasero (I'm burning it on ubuntu). the files were larger than the 700mb blank disk. So it automatically zipped the file.

Is it ok to burn the zip file and will it work?

brett

No it is not OK. It should never have been unpacked. It should be burned directly from the ISO image.

Just to clarify. I guess you computer was doing the same boot with or without this CD. Is it the case?

> **bdws1975 said:**
> what about a thumb drive?

Can I 'burn' it on a large thumb drive?

If so, I'm sure there's a tutorial somewhere.

Thanks again,

Brett

I found interesting stuff at
[http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu:en-US:official&hs=kW0&ei=xe5aS465KcyutgeUxLmtAg&sa=X&oi=spell&resnum=0&ct=result&cd=1&ved=0CAYQBSgA&q=installing+windows+from+a+usb+pen+drive&spell=1](http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu:en-US:official&hs=kW0&ei=xe5aS465KcyutgeUxLmtAg&sa=X&oi=spell&resnum=0&ct=result&cd=1&ved=0CAYQBSgA&q=installing+windows+from+a+usb+pen+drive&spell=1)

Good luck. If you succeed I will be really happy to hear how you did it.

Otherwise, as I said above, you can try burning a new CD or borrowing one.

> **bdws1975 said:**
> ...

I got ubuntu loading again and I'm all good there.

...

As for the Xp iso, it fits on one disk if I just burn t he iso file and don't double click it, etc and unpack it.

What am I doing wrong?

thanks,

Brett

To burn the CD correctly you can see robert shearer's screen shots above.

> **Vignesh S said:**
> ... As for Gparted, I think its on the Ubuntu 9.10 LiveCD/USB. I managed to get into it running before.

Which one is LiveCD?
The one I got from ubuntu-9.10-desktop-i386.iso doesn't seem to have gparted preinstalled.
Thanks!

---

### Post by 73ckn797 on 2010-01-23
Looking at my Windows XP disks I see they are on DVD. I made a back-up of the original and had to place it on a DVD.

As mentioned, the image that the OP has will have to be burned to disk but using a blank DVD. That explains why they are getting an unknown file system message if the iso is only copied to disk.

Since the computer is so new, were there not any recovery disk(s) that came with the system?

---

### Post by leorolla on 2010-01-23
> **73ckn797 said:**
> ...

Since the computer is so new, were there not any recovery disk(s) that came with the system?

Nowadays they're coming often with a "recovery partition" (sic) which bdws1975 probably blew away when he installed Ubuntu on the whole HD.

---

### Post by 73ckn797 on 2010-01-23
> **leorolla said:**
> Nowadays they're coming often with a "recovery partition" (sic) which bdws1975 probably blew away when he installed Ubuntu on the whole HD.

I was thinking that may be the case. I have not bought a boxed computer in 15 years except for a laptop.

---

### Post by leorolla on 2010-01-23
> **73ckn797 said:**
> I was thinking that may be the case. I have not bought a boxed computer in 15 years except for a laptop.

I was indeed referring to laptops.

---

### Post by 73ckn797 on 2010-01-23
> **leorolla said:**
> I was indeed referring to laptops.
My Toshiba came with a recovery disk.

---

### Post by Vignesh S on 2010-01-23
> **leorolla said:**
> Which one is LiveCD?
The one I got from ubuntu-9.10-desktop-i386.iso doesn't seem to have gparted preinstalled.
Thanks!

Try this:

Type ALT+F2 and type in
```
gksu gparted
```

And tell me if something happens. 

And for the record, that is the ISO I also used too.

---

### Post by Vignesh S on 2010-01-23
> **leorolla said:**
> Nowadays they're coming often with a "recovery partition" (sic) which bdws1975 probably blew away when he installed Ubuntu on the whole HD.

Yeah, that is true. My laptop has that too, though if you would like, you can get recovery CD's from the manufacturer, though there might be a small cost involved. But still, for a peace of mind ;-)

---

### Post by presence1960 on 2010-01-24
Windows XP should fit on a CD if it is a legitimate Windows XP. Other than backups people have made I have never seen genuine Windows XP on a DVD.

The only way I can fathom XP being too large for a CD is if someone slipstreamed it with software to install along with windows or it is pirated version of windows.

---

### Post by bdws1975 on 2010-01-24
hi all,

well, I managed to get my wife to let me keep ubuntu and then install windows xp on a virtual machine.  I got it all done today and we're good.

thanks for all your help,

brett

---

### Post by Vignesh S on 2010-01-24
Good to hear that your problem is solved :-D. 
Virtual machines are awesome ;-).

---

