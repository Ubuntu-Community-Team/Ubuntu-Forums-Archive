---
title: "Installing from second hardrive?"
date: 2008-07-13
forum: Installation &amp; Upgrades
---

### Post by jake2k on 2008-07-13
Is it possible to install ubuntu from a second hdd? It set up as a slave but I can change the boot order to boot from it first so it seems like it would be possible.

I have the live cd but for some reason im unable to boot from my disc drive (probably a computer problem) and there is no option to boot from usb device so it looks like this is my only hope.

Any help or info is appreciated, thanks for reading.

---

### Post by clanky on 2008-07-13
Yes it is possible, you can even install linux and boot from a USB drive if your computer supports booting from USB.

When you go through the install process you can tell set where you want to install linux from, the boot manager will even allow you to choose whether to boot from linux on 1 drive or windows on another without changing the boot order in BIOS (although i haven't figured that out for booting from a USB drive yet!)

---

### Post by jake2k on 2008-07-13
well i know it's possible to install it _on_ the second hdd but what i want to do is install it _from_ the second hdd. 

So what I need are the files to stick on the hdd so that when I boot from that hdd I'm presented with the option to install Ubuntu just like the live cd would. I hope that makes more sense.

---

### Post by clanky on 2008-07-13
Makes more sense, but unfortunately I don't have the answer, sorry.

At a guess, make an ISO image, copy that to the blank HDD and then like you said, change the boot order, but that is strictly a guess, get someoene else's advice before you go messing with your system.

---

### Post by tech0007 on 2008-07-13
check this out: [http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html](http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html).  its for edgy but i guess you just have to find the link for your ubuntu version.

---

### Post by jake2k on 2008-07-13
Thanks for the link but there are a couple dead links on that page and it's kinda confusing. Is it possible to boot the hdd if I put the iso image on there?

---

### Post by confused57 on 2008-07-13
See the install without a cd instructions:
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by munkyeetr on 2008-07-13
If you are currently running a linux OS, and you have a floppy drive, this thread may be helpful for you: [http://ubuntuforums.org/showthread.php?t=666267](http://ubuntuforums.org/showthread.php?t=666267)

If you are running Windows currently, I am not sure the translation to cat the iso image onto a disk drive in the windows environment. :( Probably possible somehow.

Hope this helps.

---

### Post by jake2k on 2008-07-13
Thanks for all the links and info guys but im still having trouble figuring out what I need to do. If anyone could just give me a list of files that need to be on the hdd so I can boot and install it from and to that hdd. 

I have a live cd plus lots of other files I've downloaded while trying to get this to work so chances are I have all the files I need, I just need to know which ones go on the hdd. Thanks again for dealing with me :D

---

### Post by jake2k on 2008-07-14
Anyone know what files I need?

---

### Post by jake2k on 2008-07-15
hmm interesting...

After downloading some Ubuntu files to my download folder to try and get this thing working I'm now being presented with a dual boot option when I restart my computer, Ubuntu or Windows XP, so I guess that means I'm close to getting it to work.

Here are the files I have in my dl folder:

[img]http://www.imgsync.com/data/img/24207931.png[/img]

plus I have all the files from the live cd in another folder.

When I choose the Ubuntu boot option there's some more options that look like file paths and some of them go to a screen that says "GRUB:" and some says I can type "TAB" for options or something.

Can anyone help me along with getting this installed please. Thanks

---

### Post by jake2k on 2008-07-16
I'm sorry if im getting annoying now but I'd really like to get this done, thanks.

---

### Post by confused57 on 2008-07-16
> **jake2k said:**
> I'm sorry if im getting annoying now but I'd really like to get this done, thanks.
I don't have any experience with installing without a cd, but the easiest way appears to be using UNetbootin:
[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

---

### Post by jake2k on 2008-07-16
Thanks for the reply, I have used that but it didnt work:(

---

### Post by shadohman on 2008-07-17
Two questions.

When you were in the BIOS did you verify that the cd drive was set as the first boot drive?  Some versions of Windows hide this option.

Are you sure the Live CD was burned as an .iso file and not as a data file.

---

### Post by jimv on 2008-07-17
THIS *SHOULD* WORK (it works for my thumbdrive, and the only difference I can think of is that the HD should already have an MBR):

Format your 2nd HD, or the first partition as FAT

```
sudo apt-get install syslinux
sudo syslinux /dev/whatever-your-2nd-hd/first partition-is
```

OR from Windows:

Get syslinux: [http://www.kernel.org/pub/linux/utils/boot/syslinux/syslinux-3.70.zip](http://www.kernel.org/pub/linux/utils/boot/syslinux/syslinux-3.70.zip)

Open a cmd window and type:

```
cd wherever-you-put-syslinux.exe
syslinux.exe D: (or whatever your 2nd HD is)

```


Then copy the contents of the Ubuntu ISO to that first partition on the 2nd drive.
Rename the isoinux folder to syslinux, then open that folder and rename isolinux.cfg to syslinux.cfg

Then cross your fingers and try booting from that drive.

---

### Post by jake2k on 2008-07-18
I think I did it right when you type in the command is something supposed to happen?

---

### Post by jimv on 2008-07-18
It does something, but it doesn't give you any feedback to say, "Hey, I did it!", it just does it.

Try booting from the drive.

---

