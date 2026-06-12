---
title: "Reseting Grub during boot"
date: 2010-11-16
forum: Installation &amp; Upgrades
---

### Post by ck007 on 2010-11-16
Hi,

I have installed Ubuntu 10.10 on my external hard disk but now when am booting it on another machine am not able to do as grub wont find new machine as the original one.

I want to know if there is any command which i can run during boot only on os selection page which would rebuilt grub and the menu list so that i can use my external hdd more friendly way.....!!!

Thanks

---

### Post by Rubi1200 on 2010-11-16
Hi and welcome to the forums :)

It sounds as if GRUB was likely installed to the MBR of the internal hard disk during installation.

I think what you need to do is install GRUB to the MBR of the external disk. However, this is also likely to lead to a situation where you have to set BIOS to boot from the external device every time you want to use it.

In any event, to make sure we are on the same page, plug in the external as you would normally use it and then follow the instructions in the link at the bottom of my post.

Post the results of the boot info script back here so we can take a look and advise you further.

Thanks.

---

### Post by ck007 on 2010-11-16
Thanks Rubi...

But this wont work for me....
My external harddisk is showing list of os to load but is not able to load ubuntu (not even others)so i cant boot into to download file.
I am getting an option to go into command line mode ie "grub>"  prompt, so if i can do anythin from there?
Also, i have configured the pc to boot from my external HDD as first boot device so my device menu list is also showing up thus making it clear that it is able to take my device boot..

Hope this helps in understanding better...Please ask me for anythin more.....

Thanks

---

### Post by Rubi1200 on 2010-11-16
Thanks for clarifying the situation.

Yes, there are some things you can try:
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1594052](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1594052)

Read the information carefully, but you may want to go straight to the section entitled > 'grub rescue>' Boot Procedures 
If this gets you into Ubuntu, then run the script I mentioned before.

---

### Post by ck007 on 2010-12-04
Thanks :)

but problem is stil unsolved...have just posted issue... copying same here....

I installed Ubuntu on an external hard disk and took it to connect it to another system, but it is failing to boot and getting an error:


```

Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdine)
   - Check rootdelay = (did the system wait long enough?)
   - Check root = (did the system wait for right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/sdc1 does not exist. Dropping to a shell!

BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built in shell (ash)

```

Please let me know how to rectify this error.

Hope to get this rectified soon, dont want to reformat my drive, want to learn how to recityfy this error...!!!

---

### Post by wilee-nilee on 2010-12-04
Plug the hd drive in to the computer that it works on your regular setup and follow these instructions.

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between.

Script can be run from a ubuntu install if there is one on the regular working setup. If that is a wubi install use a live Ubuntu cd.

---

### Post by ck007 on 2010-12-04
i don have any system on which that is working now and also dont have live cd....can connect to internet but don think that would help anyhow as i am getting this error while boot.!!!

---

### Post by wilee-nilee on 2010-12-04
> **ck007 said:**
> i don have any system on which that is working now and also dont have live cd....can connect to internet but don think that would help anyhow as i am getting this error while **boot**.!!!

Did you notice that it is called the **boot**script, hmmm, now is this coincidental or maybe it is relevant.;)

Can you plugin the HD into a working computer and run the script?

What you want to do is not really possible the way its described. Actually it is difficult to decipher what your problem is, the description and schema of wants really make no sense.

---

### Post by ck007 on 2010-12-04
ya i can connect it to working pc but am not getting how do i run that script??? i need to boot my system on my hd??? also the computer is windows.....my hd is only linux and as am getting this error so how to get file on my hd and how to run it???


Sorry to bug u....but pretty new to this stuffs so.... :(

---

### Post by wilee-nilee on 2010-12-04
> **ck007 said:**
> ya i can connect it to working pc but am not getting how do i run that script??? i need to boot my system on my hd??? also the computer is windows.....my hd is only linux and as am getting this error so how to get file on my hd and how to run it???


Sorry to bug u....but pretty new to this stuffs so.... :(


No its just a matter of understanding, thanks for making it more clear.;)

So you need a Ubuntu live cd, or thumb drive loaded that will boot to a live environment, these are not installs.

Get there=live cd, come back to the thread or save that link of the bootscript download the script drag it to the desktop on the live Ubuntu cd, then open a terminal from menu-accessories-terminal then copy and paste this command to the terminal.
```
sudo bash ~/Desktop/boot_info_script*.sh 
```

This will generate a new file copy all the text from it and open a reply in this thread, click on the # in the reply panel, and paste all the text between the code tags. If you look in my signature there is the bootscript link and a manual method of setting code tags. If you look at the signature you will also see what code tags look like.

---

### Post by wilee-nilee on 2010-12-04
Did you install Ubuntu to the external hard drive from a live windows session.?

---

