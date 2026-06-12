---
title: "Install not booting from Hard drive"
date: 2008-03-31
forum: Installation &amp; Upgrades
---

### Post by jonwop on 2008-03-31
I'm posting this up here for my friend. I've done some searching on the site here and google trying to find a solution to his problem.

He just installed 7.10 the other day now when he tries to boot up w/o the cd in it goes through the normal start up and then gets to a blank screen.

After that is said something like "boot error please put cd in and press enter" 

So we did that, kept pressing enter and the error didn't go away and the cd wouldn't load. So we restarted with the cd in and ran off the cd and it was fine. 

I did a cd check to see if there might have been any missing files on the cd but it came out nice and clean. 

I went into the properties of the filesystem and it was a 10Gb partition with i think 3Gb taking up the space needed for ubuntu and the rest was free. So it seems that ubuntu is installed on the drive but it just won't boot up. 

I did eject the cd once while it was in the "live mode"? and it still ran fine but when I restarted it did the same error as mentioned above.

So I was wondering if anyone had some knowlage of this happening before or seen it themselves? 

Any idea on what it could be and how to fix it?

Should I have him just do a new fresh install? 

Or any advice you can give would be greatly appreciated, for myself and he are still very much linux noobs.

---

### Post by Mystix on 2008-03-31
Try hitting Clt-Alt-F1 to boot in the  text mode instead of the graphical mode.

Mystic - Ubuntu Free4All

---

### Post by dstew on 2008-03-31
> it goes through the normal start up and then gets to a blank screenWhat do you mean by this? Do you see the BIOS splash screen only? Do you get a grub menu? Do you see the Ubuntu splash screen? Do you get to the login page?

Did you install the grub boot loader onto the hard drive? If so, where (MBR or partition)? It sounds like your BIOS cannot boot the hard drive. That error message is probably coming from your BIOS, not from any part of Ubuntu or grub. Is the hard disk placed before the CD-ROM drive in the BIOS boot order?

---

### Post by jonwop on 2008-03-31
Thank you both for your replies. It does go to his BIOS splash screen. But it won't go anywhere else unless it's booting from the cd. 

I think the cd might be first in the boot order right now, if I get time tonight i'll go over his house and double check and if it's not put the HDD on first. I thought that might be the problem but I didn't have the time last night to do it. (we were brewing our own beer)

I'll try to get the best answers and information to the questions you asked me to help you help me lol. 

But like I said I'm still a noob and doing the best I can to help a friend wanting to let go from the grip of Micro$oft.

---

### Post by dstew on 2008-03-31
By all means, try to change the BIOS boot order, that might work. But, it also could be that grub was not installed at the end of installing 7.10. You can install grub from the Live CD, maybe that will get the hard disk to boot. Assuming your friend only has one hard disk, the way to install grub is like this.

First, boot the Live CD. Open a terminal window (Applications --> Accessories --> Terminal) and on the command line enter```
sudo grub
```That should get you the grub command line, with the **grub>** prompt. On the grub command line, enter```
find /boot/grub/stage1
```It should give you a partition name in grub-speak, like (hd0,1). Whatever the answer, use it as the argument for the grub root statement, then install grub into the first disk MBR with the setup command, then quit:```
root (hd0,1)
setup (hd0)
quit
```Remove the CD and reboot. Hopefully you will get the grub menu. If you do, try to boot Ubuntu. If you get an error, post back and we can try more.

---

### Post by ak4322 on 2008-03-31
I have the same problem. I installed using this thing called wubi and after it installed i resterted my computer the selected ubuntu and then i went to my bios splash screen. What do i do?

---

### Post by dstew on 2008-03-31
> i resterted my computer the selected ubuntuThat is not the same problem the original poster had. He does not get a grub menu, like you did. You probably only need to reconfigure grub by editing the /boot/grub/menu.lst file. Maybe start a new thread for that topic, or search for others who have done that.

---

### Post by jonwop on 2008-04-06
Well dstew I got some more info for you. I finally got over my friend's house this weekend to see what I could do with what you told me.

Well I asked him if he had changed the boot order and he said yea, it's back to the hdd.

I followed what you said to install grub and it went fine but it didn't fix it I guess. So after the install I took out the disk and then reboot. And it did the same thing as before.

Went to the BIOS splash screen. Then the disk raid utility for a moment. Last the PCI device listing and at the bottom it said ,
"disk boot failure, insert system disk and press enter"

Tried that again with the disk insterted and pressed enter, no go. So I went to reboot again and same as before with the disk in. 

I selected boot from hard disk and it does but only with the cd in. I even tried reinstalling just in case there were some windows files still on the system for some reason and still the same problem.

I hope this is enough information for you and I appreciate you time and help. Thanks again.

Cheers

---

### Post by dstew on 2008-04-06
My guess is that the BIOS is changing the disk enumeration depending on whether or not there is a CD in the drive, whether the CD boots or not. What I mean is, that with the CD in, the BIOS might number the CD as (hd0) and the hard disk as (hd1). But, when there is no disk in the drive, the hard disk becomes (hd0). When grub was installed, the hard disk was (hd1) because there was a CD in the drive (the Ubuntu Live CD). Grub is looking for its stage2 on (hd1). But, when there is no CD in the drive, grub is still looking for (hd1) but it is not there. Grub is not smart enough to look at all the drives and find its stage2, with only the boot loader and stage1.5 running.

In my opinion, to fix it, you would have to make a [grub boot floppy]("https://help.ubuntu.com/community/GrubHowto/BootFloppy"). Hopefully you have a floppy drive. Boot grub from the floppy drive, without any CD in the CD-ROM drive, and re-install grub as before. Then it might work properly.

---

### Post by jonwop on 2008-04-07
Thanks again dstew I will deffinately try that as soon as I get a chance this week. I don't think he has a floppy but I do so I'll just rip it outta my computer. But say that is the problem and it is fixed, I won't have to keep the floppy drive in there will I? (it doesn't sound like it but just wondering)

Thanks again for all your help. Cheers

---

### Post by dstew on 2008-04-07
> I won't have to keep the floppy drive in there will I?No, I don't think so. The problem you describe has to do with a BIOS that counts the CD-ROM as a hard drive. I don't think any BIOS counts a floppy as a hard drive, so you should be all right booting from the floppy, and then re-installing grub to the hard drive from there.

---

