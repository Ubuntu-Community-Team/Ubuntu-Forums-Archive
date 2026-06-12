---
title: "New installation of Ubuntu 14.04"
date: 2014-07-02
forum: Installation &amp; Upgrades
---

### Post by Robert_Lambert on 2014-07-02
Hi

I am completely! new to linux and ubuntu.
I have installed Ubuntu 14.04 onto an ASUS laptop running windows 8.1, from a CD.
The installation went well, everything seemed to work, it got right to the end, said
installation complete now reboot to start using Ubuntu.
So i switched off the laptop, re-booted, expecting to see a choice between windows 8.1 and
Ubuntu. But no, laptop booted straight into windows.
I have searched the web for a solution to this problem, i.e. how do i start Ubuntu,
but to no avail - lots of solutions offered, but none that I could get to work.
Can anybody tell me what I have to do, to actually get Ubuntu to run.
I would be very grateful. I have run out of options.

many thanks for any help

Robert

---

### Post by mastablasta on 2014-07-02
first run the boot info script and post the results here so we can see how Ubuntu is installed. it might also help if you can boot into live session and then post a picture of partitions in gparted.


if install realyl went ok it means grub (that loads Linux as well as Windows) did not replace the Windows boot loader for some reason.

i do not have any experience with UEFI but this site is a good place to start: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Robert_Lambert on 2014-07-02
Hi

thanks for the reply. I am afraid I do not know how to run the boot info script.

The installation did say it had finished successfully, and that I should re start the computer.

I have tried to install boot-repair using the ubuntu terminal, run from the demo version of ubuntu, 
using the following command:
sudo add-apt-repository ppa:yannubuntu/boot-repair

however this outputs an error message saying that the ppa format is incorrect. I have tried this several times,
always with the same error being reported, and this is where I am stuck.How can the format be incorrect, it is
shown like this on several websites, so something else must be wrong. I am using an ASUS N56V laptop, fairly new,
with windows 8.1, 930GB HDD hardly any data on it. Once I find out how to do a boot info script I will send it 
to you. Any further suggestions would be appreciated.

many thanks

Robert

---

### Post by 0N3 on 2014-07-02
```
https://launchpad.net/~yannubuntu/+archive/boot-repair
```

Get Boot Repair .deb from the above link and install it and run that.

---

### Post by Robert_Lambert on 2014-07-02
HI,
got boot repair. Do I run it from windows or ubuntu demo ?
I tried using frisk as per internet instructions, and got: warning GPT
detected on 'dev/sda'! Fdisk does not support got Use GNU parted. 
Now I am lost.

cheers

---

### Post by 0N3 on 2014-07-02
Try run it from within Ubuntu or if you can't get into Ubuntu boot up your cd/dvd/usb media device (whatever you used to install Ubuntu) and install it there and run it. It's only temporary.

Have a look here too.

```
http://askubuntu.com/questions/226061/how-to-install-the-boot-repair-tool-in-an-ubuntu-live-disc
```

---

### Post by yancek on 2014-07-02
The bootinfoscript downloaded on your Ubuntu Live CD/flash will be in the ubuntu user Downloads directory.  Right click on the bootinfoscript-061.tar.gz and select "Extract here" which will create a bootinfoscript-061 folder.  Open the folder (double-click) and the bootinfoscript is there.  Right click the bootinfoscript and select Properties and then select the Permissions tab to verify that the Allow executing file as a program is checked.  Open a terminal and change to the Downloads/bootinfoscript-061 directory and then run:

```
sudo ./bootinfoscript
```

You can watch output in the terminal and it will tell you where the RESULTS.txt file is, most likely in the bootinfoscript-061 directory.  Review it or if it doesn't mean anything to you, post it here.

---

### Post by JeQhdMD on 2014-07-02
When you installed it to the laptop, where did you install it?  Did you create a partition and format it to ext4 via the install disk?  Or did you pre-setup the hard drive ahead of the install running (defragging windows twice, shrinking it using windows tools, disabling secure and fast-boot via the uefi/bios setup)?   Did you use the 64 bit version of Ubuntu?



Did you notice where the bootloader was going to be installed?

---

### Post by Bucky Ball on 2014-07-02
Welcome. No, you don't use Boot Repair in Windows. See here for full, official instructions:

[https://help.ubuntu.com/community/Boot-Repair#Getting_Boot-Repair](https://help.ubuntu.com/community/Boot-Repair#Getting_Boot-Repair)

Get Boot Repair:
[http://sourceforge.net/projects/boot-repair/?source=directory](http://sourceforge.net/projects/boot-repair/?source=directory)

Use BR:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Yannbuntu's thread:
[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

Run it first before dashing down any dark alleys and report back. You can also easily run the bootinfoscript with boot repair (it will give you a pastebin location where it has stored your file; write it down and post back here if Boot Repair doesn't fix things).

---

### Post by Robert_Lambert on 2014-07-03
Hi,

sorry, I think I am about to give up. Almost everything I have tried has failed.

I can not run boot repair, either by using terminal (ppa format error) or by by downloading to disc ( the
disc will not boot (please load bootable medium). I tried linux secure which has boot repair with it,
but this will not boot either, (remember the ubuntu disc DOES boot).
I can run ubuntu demo, no problem. But it can not see the software (boot repair) on my disc (dvd), although
I can see it when reading the disc from windows 8.
I now have a windows 8 machine, with half of its disk space allocated to ubuntu which I can not use.
don't know what else to try.
Just to be clear what I did in the first place:
I disabled secure boot, and fast boot. I inserted the ubuntu 14.04 disc (obtained from a friend who recommended
it to me. Started the laptop, pressing the esc kay at the same time. Selected the option for the dvd player. Ubuntu 
loaded, and ran through to the , connect to internet, run ubuntu alongside windows options. Selected these. 
It displayed a partition option which I left unchanged. The system ran through various displays asking for location etc.
 After about 10mins, it reported ubuntu installed successfully, please remove disc and restart to run Ubuntu. I did this.
 System just booted straight into windows 8.1, which thankfully still runs as before.
I am unable to get ubuntu to load and run. Cant run boot repair ....etc.
What now ??
 
thanks, and sorry for this sorry story - thought it was a good idea at the time.

many thanks 

Robert

---

### Post by Bucky Ball on 2014-07-03
*Thread moved to **Installations & Upgrades.***

Perhaps a move to a more appropriate section of the forum will jog things along.

---

### Post by Robert_Lambert on 2014-07-03
hi

 thanks for all your help, to anyone who replied. I will continue trying and post back when I get 
further

Robert

---

### Post by Robert_Lambert on 2014-07-03
HI,
 I have got a little further, in fact I have got ubuntu running OK. I downloaded a new copy of Ubuntu desktop,
which worked OK. However, I now have the opposite problem.
I can no longer boot windows 8.1.
I have tried to run boot repair, but without any success. The recommended sudo commands for the terminal,
prompt me for my password, but when I enter it it is not accepted. I have tried changing my password, but
the new (accepted, and functioning correctly when I log in), is not accepted either.
I tried an alternative method using fdisk, which prompts for my password and does accept it (same password),
but then outputs: "GPT detected on '/dev/sda' ! The util frisk does  not support GPT. Use GNU parted".
At this point I am completely stuck. I have no idea what to do with GNU parted. 
Also do not understand why my password is sometimes accepted and other times rejected.

help !

Robert

---

### Post by Bucky Ball on 2014-07-04
You're saying your password is not accepted at the login screen and terminal? If not, try delete ICEauthority and Xauthority and reboot.
```

    sudo rm -rf .Xauthority*
    sudo rm -rf .ICEauthority*
```

... should do it, then reboot. Any better?

---

### Post by mastablasta on 2014-07-04
how do they use sudo command if password is not accepted?

---

### Post by Robert_Lambert on 2014-07-04
Hi 

thanks, yes that has fixed the password problem, much obliged.

But I am still unable to run boot repair successfully. I get the following message:
"failed to fetch [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-)
i386/Packages  404 Not found (recognise this number from windows)
Any ideas - obviously something missing somewhere.
So I still can not launch my windows 8 anymore.
I have boot-repair on a disc, but my pc will not boot from the CD anymore, it will only
launch Ubuntu. There is no boot device option for the CD.

thanks

Robert

---

### Post by mastablasta on 2014-07-04
404 means the page does not exist or cannot be found:
see number two here:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


so yes that link is wrong. for saucy it is here: [http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/saucy/main/](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/saucy/main/)

but you need to insall it using instrucitons i gave in link above.

---

### Post by JeQhdMD on 2014-07-04
Just a couple things to check:
>  are you absolutely sure you're using 64 bit version of Ubuntu iso?  The 32 bit (from what I've read does not support uefi/gpt disks.
>  remember, in linux, case matters.  You password must be typed exactly using the proper case - a lower case r is not the same as uppercase R.

I wish ubuntu would clarify which option newbies should use when asked how to install - - - installing "alongside" is not a good way to do it (it pre-supposes the user has some experience and things are set up correctly).   INSTEAD, you use the custom install which reads something like "something else" . . . . 

If you check and find you're good on the first two points, perhaps another install using "something else" will work (on my install screen, it was the last option - - like number 4 of 4)

---

