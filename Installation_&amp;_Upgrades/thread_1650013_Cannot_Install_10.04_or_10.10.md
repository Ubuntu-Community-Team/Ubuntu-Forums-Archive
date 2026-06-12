---
title: "Cannot Install 10.04 or 10.10"
date: 2010-12-20
forum: Installation &amp; Upgrades
---

### Post by lifeinoleg on 2010-12-20
I've installed Ubuntu on a variety of systems since Gutsy Gibbon and have never run into anything that has been quite as frustrating as my situation now. 

Whenever I try to install Ubuntu, it gets stuck at a random point in the "Copying Files" process (first it got stuck on 58%, then 62%, now I don't even know...). I've tried 10.10, 10.04, I even dug  7.04 out of the drawer (but it had trouble recognizing the CD-ROM after booting from it). 

There have been a few different errors, but the most common one...the last one I got (from a 10.10 image checked with winMd5Sum and burned with InfraRecorder at the lowest possible speed) was a SQUASHFS error (this I read from the scroll before it stopped responding).

Just now I rebooted and tried to check the disc, but it never got there, instead it says:

```
BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: input/output error
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs
```

I've searched all over the forum and maybe I'm missing something but in every thread with similar problem people are told to check the md5sum and burn at lowest speed OR boot off USB which I tried but though the bios sees that the flash drive is there and USB boot is enabled, it refuses to boot from it (I created the stick using both UNetbootin and usb-creator.exe, same result).

I've never had any problems with either optical drive (neither my laptop which I'm using to burn the discs nor the desktop I'm trying install Ubuntu on). I've been at this for hours and at this point, the desktop (P4 1.7GHz, 512MB RAM, (according to the bios:) DVD-ROM BDV316B, Maxtor 15.4GB HD) has no OS. 

Back when I first installed Gutsy, the folks here were very helpful. I would appreciate any help I can get at this point. Thanks.

---

### Post by PhantmKllr on 2010-12-21
Even if you've never had problems with the optical drive, it sounds like it's finally crapped out. There's really no rational explanation for the issue you're having. But to be sure, try the discs on a different computer.

---

### Post by lifeinoleg on 2010-12-21
PhantmKllr, thanks for the reply. That's the answer I was dreading.

The strange thing is that it boots using the discs and the install begins just fine then randomly gets stuck while copying files, usually past the midway point. 

Just got rid of my external drive too. 

I'll try to live-boot my laptop...

---

### Post by PhantmKllr on 2010-12-21
Sorry to be the bearer of bad news. If you have another computer available, then you can make a live USB.

---

### Post by Quackers on 2010-12-21
Try cleaning the laser

---

### Post by lifeinoleg on 2010-12-21
PhantmKllr, is a live USB different from taking a regular USB and using UNetbootin or usb-creator.exe to install the image on it? If not, then for whatever reason bios just skips over the flash drive (even though it recognizes that it's there when it checks the HD/CD-ROM etc.).

Quackers, I'll see about the laser, though I'm not optimistic since the install poops out only after an extended period of the drive working. 


Just now I was able to live-boot my laptop from the newest 10.10 disc (looks so smooth!) so the disc is okay. 

Will see about procuring another drive to stick into the desktop. And here I thought I would get to avoid the holiday shoppers this year. smh

---

### Post by PhantmKllr on 2010-12-21
> **Quackers said:**
> Try cleaning the laser

But only with a laser lens cleaner disc. Cleaning mine with a cloth is what ruined it.

---

### Post by PhantmKllr on 2010-12-21
> **lifeinoleg said:**
> PhantmKllr, is a live USB different from taking a regular USB and using UNetbootin or usb-creator.exe to install the image on it? If not, then for whatever reason bios just skips over the flash drive (even though it recognizes that it's there when it checks the HD/CD-ROM etc.).

Have you changed the boot order in the BIOS?

---

### Post by lifeinoleg on 2010-12-21
There isn't actually a USB option in the boot order, there's only removable disc (which may just be the floppy). 

There's an option to allow USB boot which is enabled. I've tried rearranging the order in all directions, even disabling everything just to see if it would use the USB or leaving only removable disc, but nothing seems to access the flash drive. Or at least not so that I can see -- I've left the cursor blinking for long enough to figure it wasn't doing anything. 


Maybe there's an update for the bios that will have the necessary option but looking for bios updates, in past experience, has always been a royal pain.

---

### Post by PhantmKllr on 2010-12-21
Try making a new USB with the Pen Drive Linux utility for Windows.

[http://www.pendrivelinux.com/]("http://www.pendrivelinux.com/")

---

### Post by lifeinoleg on 2010-12-21
Just made the USB using Pen Drive. Will try it tomorrow since roommate is asleep in the room with the desktop now. Also, if it doesn't work, I may punch screen in. Better to calm down and wait till morning. 

Thanks for your help, will post Pen Drive results in the AM.

---

### Post by PhantmKllr on 2010-12-21
I'll be eagerly awaiting the results. :popcorn:

---

### Post by lifeinoleg on 2010-12-21
Didn't feel like waiting till morning.

Result: Same deal, the computer just ignored the USB, fooling around with boot order notwithstanding.

---

### Post by dino99 on 2010-12-21
[http://ubuntuforums.org/showthread.php?t=1573406](http://ubuntuforums.org/showthread.php?t=1573406)

but why this squashfs choice ?

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by lifeinoleg on 2010-12-21
> **dino99 said:**
> [http://ubuntuforums.org/showthread.php?t=1573406](http://ubuntuforums.org/showthread.php?t=1573406)

but why this squashfs choice ?

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

I'm not sure I understand what you're telling me here. The threads you've linked seem unrelated to this thread. Am I missing something?

---

### Post by dino99 on 2010-12-21
hm, 

all is about what you can do with squashfs & what you cant do (squashfs is a compress format & read only, so all the updates are virtual ( into ram, and lost aftera reboot)

have you read the link i've provided ? (and understood it)

( like in Hollywood, virtual LOL)

---

### Post by lifeinoleg on 2010-12-21
I've read the links you provided but as per my reply I can't say I understood them. I'm not a programmer, just a guy who does some light tinkering, so I haven't a clue how squashfs relates to my problem other than the error message I posted originally (though now I know a little about what it is). 

If you don't mind, you'll have to treat me like an idiot and explain step-by-step what I need to do in relation to your links. I've read them, but am not sure what to do now.

---

### Post by PhantmKllr on 2010-12-21
Try updating your BIOS.

---

### Post by lifeinoleg on 2010-12-24
PhantmKllr, you were right. I went to the store and dropped just 20 USD on a new optical drive and BOOM...I'm typing this in Ubuntu. 

Thanks for your help. Ubuntu wouldn't exist for me without this forum and nice people (like you) who answer questions.

---

### Post by Farstanley on 2010-12-25
Seriously
All you have to do is enter your username completely in lower case and the forward button will come to life
Worked for me twice this very afternoon

---

### Post by PhantmKllr on 2010-12-25
> **lifeinoleg said:**
> PhantmKllr, you were right. I went to the store and dropped just 20 USD on a new optical drive and BOOM...I'm typing this in Ubuntu. 

Thanks for your help. Ubuntu wouldn't exist for me without this forum and nice people (like you) who answer questions.

That's why we're here. Glad to be of service.

---

