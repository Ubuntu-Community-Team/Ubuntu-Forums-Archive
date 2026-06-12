---
title: "Booting from usb"
date: 2015-11-30
forum: Installation &amp; Upgrades
---

### Post by Scott_ on 2015-11-30
I installed my Ubuntu 14.04 iso on a USB stick because it helps me with my IT work. I've been using an old version for many years because it's always worked for me, so why change.....  Since updating, it seems to do what I needed from the older version, but I noticed that the programs I install and settings I change don't stay when rebooting. It's like using a live cd..... I used to be able to have extra programs and I had my own username and password set up but none of those settings stick anymore. It would be horribly time consuming to reinstall each program after each boot when switching to a new computer, which I do many times a day as I goto each customers business. Can someone please tell me what's going on? This wasn't an issue on the previous version I was using.

---

### Post by sudodus on 2015-11-30
Welcome to the Ubuntu Forums :-)

There are different ways to run Ubuntu from a USB drive.

1. Live only, what you seem to be running now
2. Persistent live, where you can install programs and store files.
3. Installed system, like installed into an internal drive, but into a USB stick.

You had either of 2. or 3. previously. See these links for more details.

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)
[Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Scott_ on 2015-11-30
I think I've figured it out. The image burner I used didn't offer a persistence option. I don't remember the program I used before but I remember setting plenty of space for persistence. So I will have to find a new program and reinstall the image. I'll keep you updated, but it think I've figured it out.

---

### Post by Scott_ on 2015-11-30
Nevermind. I've reinstalled with 4 gigs of persistence however my settings still aren't saving...

---

### Post by sudodus on 2015-11-30
I'm developing mkusb, and I think it can do the job for you. It makes a casper-rw ***partition*** for persistence (instead of a casper-rw file), which is better than a casper-rw ***file*** in order to have plenty of space for persistence.

See this link: [help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

### Post by Scott_ on 2015-11-30
I'm finding that whole process to be a little confusing. I just need a program that will install the iso onto the USB with persistence and have it actually work. I just alloted 4 gigs of persistence on this install I tried and it's not working.

---

### Post by sudodus on 2015-11-30
- Which tool are you using to create the USB boot drive?

- Have you added the boot option **persistent**? You can try according to the following links (different depending on the boot method - syslinux or grub)

See this link: [Boot options](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808)

-o-

If you still have problems: mkusb does the job for you - just install it from the ppa, run it and let the graphical user interface guide you.

---

### Post by Scott_ on 2015-11-30
I first used Rufus 2.5 and then I used Lili USB creator. I use Windows as my normal os but Linux helps me with my job. I'm not terribly familiar with Linux so I have no idea how to use your program.  and I had just installed Ubuntu years ago and it worked... I didn't have to go through all this trouble.

---

### Post by Scott_ on 2015-11-30
Also, boot method is grub... Just stumbled into that info

---

### Post by sudodus on 2015-11-30
- Check that the boot option persistent is entered correctly.

If still no luck, I suggest that you try another tool. You can install mkusb temporarily into your live Ubuntu system and create persistence in another USB stick or USB hard disk drive or SSD (if you have one). ***Unetbootin*** is a reliable tool with versions for linux, Windows and MacOS, that I can recommend. It might be easier for you, because it works directly from Windows. But it will create a file for persistence, and the maximum size is 4 GB due to the file size limit in FAT32.

---

### Post by Scott_ on 2015-11-30
I will try unetbootin. 4gb is more than enough for me

---

### Post by sudodus on 2015-11-30
> **Scott_ said:**
> Also, boot method is grub... Just stumbled into that info

Edit the file **grub.cfg**,

At the end of the line starting with linux you should add persistent:

```
linux ... --
```

--->

```
linux ... persistent --
```

---

### Post by sudodus on 2015-11-30
> **Scott_ said:**
> I will try unetbootin. 4gb is more than enough for me

Good luck, Unetbootin should do the job (without manual tweaking) :-)

---

### Post by Scott_ on 2015-11-30
Adding persistent to the code seems to have worked. Unetbootin gave me no noticeable change. However, I have to add the persistent line to the code each time I boot, which isn't really an issue for me. Just will take a few extra seconds.

---

### Post by sudodus on 2015-12-01
It is strange that you have not been able to get that boot option persistent ;-) but if you are happy with your solution, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by C.S.Cameron on 2015-12-01
You Can edit a file to automatically add persistence each time you boot.
If you used UNetbootin to make your drive:

Open filesystem / cdrom and then opened syslinux.cfg with text editor.
Added "persistent" as shown below:
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent

For what it is worth the following is how I make a Persistent flash drive:

Boot Live CD or Live USB.
Plug in flash drive.
Start gparted.

Create 2 GB FAT32 partition, (on the left side of the bar). (size is optional, extra space can be used for file storage and transfer to Windows machines).

Create a 4 GB ext2 partition to the right of this, labeled it "casper-rw". (ext3 and ext4 also work).

Create a partition in the remaining space and label it "home-rw". (optional, creates a separate home partition).

Close gparted.
Un-mount and re-mount flash drive.
Start "Create a live usb startup disk", (usb-creator).
Select "Discard on shutdown".
Press "Make Startup Disk.
When usb-creator finishes, Go to the root folder of your Live USB
    Enter the syslinux directory, (or for UNetbootin the root directory).
    Make the syslinux.cfg file writeable
    Replace the contents of the file syslinux.cfg with:

```
    default persistent
    label persistent
      say Booting a persistent Ubuntu session...
      kernel /casper/vmlinuz
      append  file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz quiet splash noprompt --
```

Shutdown, remove CD, reboot.


First time booting go to users and groups and create an account with yourself up as an Administrator, with password if desired.

Note:
The above code will bypass the Try/Install and Language screens.



    default persistent
    label persistent
      say Booting a persistent Ubuntu session...
      kernel /casper/vmlinuz.efi
      append  file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz quiet splash noprompt --

---

### Post by Scott_ on 2015-12-01
I've figured it out! C. S. Cameron helped me figure it out. I had to turn on root then I went to /cdrom/boot/grub and used the terminal to edit the grub.cfg file, adding persistent just like C. S. Cameron said to do for sys Linux.cfg, but I did not mess with that file. It works perfect. Just like my old version did. 

Thanks so much for your help guys.

---

### Post by C.S.Cameron on 2015-12-01
If you should ever need to do an update-grub on that drive, you may need to reedit grub after.

---

