---
title: "Not all iso's use &quot;boot&quot;."
date: 2013-06-22
forum: Installation &amp; Upgrades
---

### Post by TNFrank on 2013-06-22
So, I'm still trying to make a multi boot USB using UNetbootin and the YouTube video that this guy posted.
[https://www.youtube.com/watch?v=MH-khdiXqYs](https://www.youtube.com/watch?v=MH-khdiXqYs)
and I'm finding out that not all of the iso's use "boot" as their go to folder to boot from.  Peppermint and Ubuntu are both wanting to use "casper" as their go to folder to boot to so that means that I'll have to change the name of the "casper" folder before I install the next iso if it's going to use "casper" too. That way each iso will have it's own folder to boot from which isn't the boot folder at all but a renamed "casper" folder. 
Is any of this making sense at all to anyone?

---

### Post by TNFrank on 2013-06-22
Well, that didn't go over very well. Renaming the "casper" files only threw everything into a kernal panic at reboot. I guess I'll just have to run one iso per USB drive until someone comes up with something like MultiBootUSB that's simple to use.

---

### Post by oldfred on 2013-06-22
I think I posted before, I just do it manually.

Yes you may have to go into ISO and see the path it expects and adjust your grub boot file to be that path. I also have to often review the boot parameters the ISO expects or needs and add them also. Each is different.

And not all ISO can be loop mounted but many can be.
Ubuntu uses casper (for desktops), Parted Magic used pmagic, and gparted used live. Each may be different as there is no standard.

These are from my hard drive as that is my most updated version. And drive is gpt partitioned so I have to insmod that for grub to work correctly.
      ```
 menuentry "Ubuntu 13.04 Raring ISO 64bit" {
    set isofile="/iso/raring-desktop-amd64.iso"
    insmod part_gpt
    loopback loop (hd2,4)$isofile 
    linux (loop)/casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper iso-scan/filename=$isofile nomodeset
    initrd (loop)/casper/initrd.lz
}

   menuentry "Parted Magic 2013 (Boot ISO Image via Grub2) " {

 insmod part_gpt
set isofile="/iso/pmagic_2013_02_28.iso"
loopback loop (hd2,4)$isofile
linux (loop)/pmagic/bzImage iso_filename=$isofile edd=off load_ramdisk=1 prompt_ramdisk=0 rw vga=normal loglevel=9 max_loop=256 vmalloc=384MiB nomodeset
initrd (loop)/pmagic/initrd.img

 }
   menuentry "gparted (Boot ISO Image via Grub2) " {

 insmod part_gpt
set isofile="/iso/gparted-live-0.12.1-5.iso"
loopback loop (hd2,4)$isofile

 #    linux (loop)/live/vmlinuz live-media=iso=$isofile keyb=us gl_kbd=us gl_lang=en_US gl_numlk=off gl_batch boot=live union=aufs  #toram=filesystem.squashfs noswap noprompt vga=791
#        linux (loop)/live/vmlinuz fromiso=$isofile boot=live noswap
        linux (loop)/live/vmlinuz boot=live config union=aufs noswap noprompt ip=frommedia findiso=$isofile toram=filesystem.squashfs
 initrd (loop)/live/initrd.img

 }
```

---

### Post by C.S.Cameron on 2013-06-22
So what is it you don't like about MultiBootUSB?
I used it to make a multi flash drive three years ago and now just exchange new iso's for old and edit grub when I want to update anything on it.

---

### Post by monkeybrain2012 on 2013-06-22
I use multisystem to make multiboot live usbs.

[http://liveusb.info/dotclear/index.php?pages/install](http://liveusb.info/dotclear/index.php?pages/install)

---

### Post by TNFrank on 2013-06-22
> **C.S.Cameron said:**
> So what is it you don't like about MultiBootUSB?
I used it to make a multi flash drive three years ago and now just exchange new iso's for old and edit grub when I want to update anything on it.

I had it installed last week but couldn't get it to see my USB drive. Not sure what the problem was.  I can use either UNetbootin or Startup Disk Creator to make bootable single iso USB's but I'd really like to have more then one iso on each USB if I can.

---

### Post by C.S.Cameron on 2013-06-22
Are we talking the same MultiBootUSB?
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
It only runs from a Linux that uses USB2, Like Ubuntu 9.10 and later.It is pretty simple to use:

1. Download the script from [https://sourceforge.net/projects/multibootusb/files/](https://sourceforge.net/projects/multibootusb/files/)

2. Extract it to your home folder (Right click --> Extract here)

3. Open terminal and move to the script folder (cd MultiBootUSB)

4. Provide root permission (su) and type ./MultiBootUSB.sh and hit enter (for Ubuntu just type sudo ./MultiBootUSB.sh with out issuing su command)

6. Here after follow on screen instructions

7. Screenshots can be found in doc folder for reference.

---

### Post by TNFrank on 2013-06-23
Is it the same one as this one:
[http://sourceforge.net/projects/multisystem/?source=recommended](http://sourceforge.net/projects/multisystem/?source=recommended)

---

### Post by TNFrank on 2013-06-23
> **C.S.Cameron said:**
> Are we talking the same MultiBootUSB?
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
It only runs from a Linux that uses USB2, Like Ubuntu 9.10 and later.It is pretty simple to use:

1. Download the script from [https://sourceforge.net/projects/multibootusb/files/](https://sourceforge.net/projects/multibootusb/files/)

2. Extract it to your home folder (Right click --> Extract here)

3. Open terminal and move to the script folder (cd MultiBootUSB)

4. Provide root permission (su) and type ./MultiBootUSB.sh and hit enter (for Ubuntu just type sudo ./MultiBootUSB.sh with out issuing su command)

6. Here after follow on screen instructions

7. Screenshots can be found in doc folder for reference.

Ok, this looks like a different one then the one I was talking about.  I followed the instructions as listed above and got a box that ask me to select a USB port then it ask if I wanted it to load automatically or manually.   I'm going to give this one a try with my 32GB Kingston USB drive and see if it'll work. Thanks. ;)

---

### Post by TNFrank on 2013-06-23
Gave it a try, tried to put 4 distros on the USB drive and only one, Peppermint, showed up and it didn't open. Not sure what the problem is, no big deal though, I'll just get a few 8GB USB drives and put each distro on a separate USB drive.

---

### Post by TNFrank on 2013-06-23
Yep, this is diffidently not working for me. I gave it another try with just 3 distros and none of em' came up on restart. I give up, I'm just going to put one distro per USB drive and not worry about making a multiboot USB.:(

---

### Post by oldfred on 2013-06-23
You seem to be having a lot of trouble with your flash drive. I wonder if it is just one of those that does not work.

 Post #14 some flash drives that did not work
[http://ubuntuforums.org/showthread.php?t=2120196](http://ubuntuforums.org/showthread.php?t=2120196)
More tests Flash drives post #5 -  C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2130234](http://ubuntuforums.org/showthread.php?t=2130234)

I have used Kingston (older one not the very newest) and Microcenter's house brand both USB2 & USB3 without issue.

---

### Post by TNFrank on 2013-06-23
The Kingston 32GB flash drive is new, just got it a couple weeks ago. It works if I use UNetbootin or Startup Disk Creator to put a single distro on it, it's when I try to do multiple distros that I run into trouble. 
 Like I said, I'm not going to worry too much about it, it's not like it effects my Op System on my laptop or anything. I just basically want to check out other distros and I can do that one at a time if I have to. 
 I really don't think I'll find anything that I like better then Ubuntu 12.04.2 anyway.

---

### Post by VMC on 2013-06-24
The one that I use is _[YUMI]("http://www.pendrivelinux.com/yumi-multiboot-usb-creator/")_. I have modified it so my own boot menu appears. I have several ISO installed that work perfectly.

---

