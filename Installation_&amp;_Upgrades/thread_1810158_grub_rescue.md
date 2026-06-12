---
title: "grub rescue"
date: 2011-07-22
forum: Installation &amp; Upgrades
---

### Post by CM7 on 2011-07-22
Hello!

My old ibm R32 laptop specification:
CPU Type: Pentium 4
CPU Speed: 1.60GHz
Installed memory: 512MB

I have already posted about my installation error here: [http://ubuntuforums.org/showthread.php?t=1807491](http://ubuntuforums.org/showthread.php?t=1807491)
, but this is different.

I have installed xubuntu 11.04. During the installation there was a crash but i don't know why. To be specific it was during retrieving some files. I could not check it because i must have restarted laptop after installation (it has freeze. Well, it has ended successfully.

I have made partitions: /boot (1GB), swap (2GB), /home(125GB) and /(20GB).

Now when i turn on my laptop there is a IBM logo, then blinking cursor and:
"error: file not found.
grub rescue> ".

I can't reinstall os because of:
"Unable to find a medium containing a live file system."
I had this problem before installing xubuntu (see link on the top if u want) but i solved it. Now i don't have ability to solve it. I can't boot from usb too by the way.

I guess i can only type sth into grub rescue> (console, terminal right?)

So i've readen about grub rescue and when i type "ls" i can see this:
(hd0) (hd0,5) (hd0,4) (hd0,3) (hd0,1)
typing "set":
prefix=(hd0,1)/boot/grub
root=hd0,1

I'm not sure is it helpful but this is a start, isn't it?
Can you help? Please?
I apologise for my language :).

---

### Post by Quackers on 2011-07-22
A separate boot partition is not normally required and it just serves to complicate matters.

Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script. This will give you a zip file which should be extracted in the same directory as it was downloaded. This produces a folder which contains the script and a changelog file.
You then need to cd to that directory in the terminal (for example ```
 cd Downloads/boot_info_script060
``` if you downloaded it to your Downloads folder). You don't need to do that if you downloaded it to your home folder.
Then enter
```
sudo bash boot_info_script.sh
```

This will produce a results.txt file in the same directory as the downloaded boot script. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by CM7 on 2011-07-23
Maybe i didn't write exactly what i mean.
I can choose try xubuntu/ubuntu or whatever like install but i will always get: "Unable to find a medium containing a live file system."
I can't boot from USB. So i think that the only option is this console thing. But i'm totally green in Linux so please advice what to do :).

---

### Post by Jose Catre-Vandis on 2011-07-23
Then how did you install the first time? 

Can you select Install Xubuntu from the screen list? What happens then?

Sounds like your hard disk installation is borked / incomplete so a full reinstall is probably preferable

Try the ALT CD for Xubuntu which places less demands on the machine no fancy graphics but it works.

Unless you are desperate to have separate home and boot, just do the default and use the whole disk with a swap file.

---

### Post by CM7 on 2011-07-23
Thanks for reply!

I didn't encounter any problems during the first install. I mean the one with ubuntu 10.04. Afther that i had problems with xubuntu installation. Finally, i run unetbootin, then create /boot partition and run xubuntu from a cd - it worked i could have choosen "try xubuntu" or even "install" without error. So i did it. Now i can't acces the system, only the grub rescue thing is available.

When i choose "install xubuntu" i get the same message/error.

I will try to do this alt(alternative right?) install. Whole disk for a swap file? You mean logical partition? I thought i MUST create at leat one primary. But if not, ok i'll try. If only i will be able to start the installation .

---

### Post by CM7 on 2011-07-23
I can't get through detecting cd-rom and mounting cd. It says that cd is probably not in the drive and asks me to insert it. But it IS inside. 

I get this message when i choose install xubuntu or repair damaged system (emergency mode).

Does anybody have any idea?

---

### Post by Jose Catre-Vandis on 2011-07-23
Sorry didn't explain my self clearly re partitioning. If you let the install do it's default it will reformat the whole disk and create a partition for the ubuntu/xubuntu install and a logical partition within which is the swap partition.

Just so I am clear about your problem, your computer will boot the cd, but when you go to install the installation cannot then find the cd?

Can you try another boot cd, something like parted magic, gparted or puppy linux (these can run in ram), or any other live cd you might have to see if they will boot up OK ( Am thinking it might be your Xubuntu CD that is the problem? before we look at hardware failure?)

---

### Post by CM7 on 2011-07-24
Here is what is happening afther default boot and boot to RAM.

After booting gparted live i get some messages (i mean lots of text on the black screen) but afther that there is a blinking cursor. My cd-drive doesn't sound very well. It's like trying to boot CD but it looks similar to putting finger on CD when it starts trying to run. Sorry for descriptrion level but i don't know how to explain it :).

And afther that i get:
Boot failed! This Debian Live image failed to boot.
...
The error message was: Unable to find a medium containing a live file system.
...
/bin/sh: can't access tty; job control turned off
(initframs) here is blinking cursor and i can type sth here.

---

### Post by Jose Catre-Vandis on 2011-07-24
**Unable to find a medium containing a live file system**

This site seems to explain the reason quite well (with a bias towards gparted)

[http://gparted-forum.surf4.info/viewtopic.php?id=9790](http://gparted-forum.surf4.info/viewtopic.php?id=9790)

You mentioned you used unetbootin earlier in the thread, what was that for? Your error often occurs when usb sticks are used to boot with.

I would suggest trying a fix you can find over on pendrivelinux, where you use a boot cd to get the PC going, then it allows a usb install to take over.

Anyway, problem looks like hardware - try resetting bios defaults, or swap out the CD drive?

---

### Post by CM7 on 2011-07-26
I have used unetbootin because i didn't have internet access on my ubuntu 10.04 for some reason. I lost it during tries of installing other os.

I have tried reseting BIOS to default but that did not work out.

Swap out the CD drive? I would need a new one right?

I can not find this fix on pendrivelinux. Can u write sth more about it?

I have readen this site about gparted but i don't know what do to first. I mean you want me to find this fix on pendrivelinux first or try to use gparted? I'm a bit confussed.

---

### Post by Jose Catre-Vandis on 2011-07-26
As swapping out the Cd drive might be a bit tricky (unless you have a USB CD drive (but then problems with booting from USB!)) suggest we try the other possible options first. I am working on the assumption that your CD drive is not working, and that you have checked the md5 and tested the CDs on another system - you might want to do this first!!!.

Here is the link to the pendrivelinux page

[http://www.pendrivelinux.com/category/usb-boot-cds/](http://www.pendrivelinux.com/category/usb-boot-cds/)


This might help (although legacy grub and a bit out of date now):

[http://ubuntuforums.org/showthread.php?t=374555](http://ubuntuforums.org/showthread.php?t=374555)

or this

[http://ubuntuforums.org/showthread.php?t=992426](http://ubuntuforums.org/showthread.php?t=992426)

---

### Post by CM7 on 2011-07-28
This PLoP worked! I have installed xubuntu from usb. I have choosen default installation without internet connection. There were no problems during install.

Afther that i have downloaded language something because xubuntu told me that this is incomplete or sth like that. I did it and restarted system. No problems.

So i thought it's time to upgrade software - there were 134 upgrades (important upgrades and recommended upgrades). So i did it. After reboot i got black screen and nothing wanted to show. The laptop was working actuallty. When i pressed ctrl+alt+delete it showed it working but still nothing showed.

I have turned it off manually and turn on. Now i see this:
"GNU GRUB version...

Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

grub> blinking cursor"

I guess this upgrades did this, didn't they?

I think i will be able to install xubuntu again. But what about upgrades? Should I don't install them or install only part of them? Or maybe i shouldn't reinstall system and type sth into this grub terminal thing?

---

### Post by Jose Catre-Vandis on 2011-07-28
Round and round we go!

Look here for operating at the grub command line:

[https://help.ubuntu.com/community/Grub2#Command%20Line%20and%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20and%20Rescue%20Mode)

---

### Post by CM7 on 2011-07-30
I started to type as they said in "GRUB 2 Troubleshooting Preparation". Thank's for the link by the way :).

I think sth is very wrong. Check this out:

grub> set
...
prefix=(hd0,**msdos1**)/boot/grub
root=hd0,**msdos1**

grub> ls
(hd0) (hd0,**msdos1**)

grub> ls (hd0,**msdos1**)/
lost+found/...(regular files).../ initrd.img vmlinuz cdrom/ initrd.img.old vmlinuz.old

grub> ls (hd0,**msdos1**)/boot
results such as: initrd.img-2.6.38-10-generic vmlinuz-2.6.38-10-generic and more of others

grub> ls (hd0,**msdos1**)/boot/grub
includs numerous *.mod files and the grub.cfg file, as well as various *.img files.

And further in section ''grub>'' Prompt Booting. I have used this steps for wubi later on. Was this corrects? Anyway:

grub> configfile (hd0,**msdos1**)/boot/grub/grub.cfg
it results in clean screen - i mean all previous commands are gone and i have now "grub>" only

grub> set root=(loop0)
nothing happens

grub> linux /vmlinuz root=/dev/sdXY
i don't know what to type instead of XY. i've tried sdo0, sd**msdos1**, sd1, sd0 ro but it results in error: no such disk.

Everytime i type **msdos1** i bolded it here. I just don't think this is right. It should have been a number like 5 or 1 or sth but no msdos1 right?

---

### Post by CM7 on 2011-08-02
Does anyone have any idea what to do?

---

