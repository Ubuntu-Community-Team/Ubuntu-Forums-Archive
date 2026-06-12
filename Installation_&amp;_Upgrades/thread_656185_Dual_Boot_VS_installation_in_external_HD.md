---
title: "Dual Boot VS installation in external HD"
date: 2008-01-02
forum: Installation &amp; Upgrades
---

### Post by siretfel on 2008-01-02
Hello all, I am new to ubuntu though i have installed previous versions on my notebook. I would like to ask your opinion whether to install Ubuntu as dual boot with windows XP (SP2) or do  an external installation to an external usb Hard Drive.
Should you have any suggestions about pros and cons please let me know.
I must say that i don't mind that much having a dual boot system. I've tried it and worked. I'm just stuck with the idea to leave my notebook as it is and have Ubuntu elsewhere. 
The question is, will it work properly in external HD? For example the drivers etc? Will it be slower with ext.usb?
Well, if you have anything to say please let me know.

Thanks to all!

I'm so excited with Ubuntu right now! I want to thank all of you out there doing this amazing work to provide us with a free operating system which i must say is by far the most advanced i 've seen so far!Keep it free! Keep it for all! 

"I am because you are!!!";)

---

### Post by logos34 on 2008-01-02
Either way...it's really up to you.  The only advantage to putting ubuntu on usb is more disk space for xp on internal and system redundancy in case one OS gets borked--i.e. you'll always have an OS that boots.  (Make sure to install Grub to USB drive's MBR, not lappy).  Grub usually works extremely well as dual boot loader, but things can happen.  USB is not all that much slower--on a 7200 rpm desktop drive connected via usb that is.  My rates average ~35 MB/s vs. 50-55 MB/s for same drive on internal IDE cable.  But the diff is hardly noticeable in everyday use.

Having it on USB also means you can connect it to other computers, usually with only some minor config changes (graphics, etc).

---

### Post by ksmiff on 2008-01-02
hi. this is something i have been trying to do...just HOW do you load the grub on the external hd? I have followed some threads and it seems very complicated to a newbie like me. Thanks

---

### Post by logos34 on 2008-01-02
> **ksmiff said:**
> hi. this is something i have been trying to do...just HOW do you load the grub on the external hd? I have followed some threads and it seems very complicated to a newbie like me. Thanks

(using the live CD) When you come to the 'Ready to install' screen (step 7 of 7 I think), click on 'Advanced' button lower right, and change default Grub bootloader location from '(hd0)' to **(hd1)** or whatever your usb drive is. (you can also use the format '**/dev/sdb**', etc.)

---

### Post by ksmiff on 2008-01-02
Thanks for the quick reply...i took out my harddrives which was recommended in another posting and also went into preferences - removable drives and removed the checks so that the usb external would not mount (another thread) and changed the hd0 to sba1 but it would not work...got an error message..so i tried it again and left the setting at hd0 figuring i didn't have a harddrive except for the external one and it went all the way through the install and even loaded up at startup with a grub line recognized in the external drive but THEN just when i thought i had it made the install FROZE....now what is THAT all about.....i am gonna keep trying till it hurts...and my wife is not talking to me since i discovered linux cause all i do is try to tweak this thing...please help....thanks

---

### Post by logos34 on 2008-01-02
> **ksmiff said:**
> Thanks for the quick reply...i took out my harddrives which was recommended in another posting and also went into preferences - removable drives and removed the checks so that the usb external would not mount (another thread) and changed the hd0 to sba1 but it would not work...got an error message..so i tried it again and left the setting at hd0 figuring i didn't have a harddrive except for the external one and it went all the way through the install and even loaded up at startup with a grub line recognized in the external drive but THEN just when i thought i had it made the install FROZE....now what is THAT all about.....i am gonna keep trying till it hurts...and my wife is not talking to me since i discovered linux cause all i do is try to tweak this thing...please help....thanks

disconnecting the internal drive is certainly one way to do it, but by changing it to 'sda1' you put grub on the bootsector of the linux root partition rather than the **mbr** where it's needed, which is why it didn't work.  You did it right the second time, sounds like you need to use some boot options on the kernel line.  Can you boot the recovery mode kernel?  What notebook do you have (sys specs)?

---

### Post by Uolirod on 2008-01-02
I'm thinking about doing the same thing, installing on USB drive. I have an XP box with RAID 0 and I didn't want to go through the trouble of installing drivers to recognize the array and backing it all up. I'm getting some stuff cleaned up and then I'm going to install Kubuntu 7.10.  I'll check back in and update on the progress.

---

### Post by Uolirod on 2008-01-02
Well...I installed it fine to the external drive. However, it will not boot. It POSTs and then starts to boot and hangs after GRUB 1.5 and declares error 18. I'm going to try to google around and see if I can get this figured out.](*,)

---

### Post by siretfel on 2008-01-07
Thank all of you for your replies. I'm using Ubuntu in my notebook for days now in dual boot with XP. This week i hope i'll get my new external HD and try an external installation.

I'll let you know how it goes and the problems i had.

As for my current Ubuntu installation gutsy in my HP laptop i had these problems:

1. USB mouse didn't work after hibernation and i think it is fixed now (I think so let me try it a few times and i ll let u know)

2. So far when i insert an empty dvd disk to burn it says it can not mount it. This is perhaps due to the fact the disk is empty and unformated. So i'm not sure if this is a problem. WHen i insert a written dvd works fine.

3. The burning speed of a dvd was very slow with k3b and Gnomebaker. WIth graveman it is working very well and i had no problems at all so far.

4. Amarok was not working but after i installed some codecs from synaptic manager everything goes smooth so far.

Well that's all for now...

Keep it free, keep it for all, keep it updated, SPREAD THE WORD: LINUX IS HERE TO STAY!!!!

---

### Post by logos34 on 2008-01-07
> **siretfel said:**
> 1. USB mouse didn't work after hibernation and i think it is fixed now (I think so let me try it a few times and i ll let u know)

If you were having the trouble after suspend I'd say look at whitelisting usb controller line 15 /etc/default/acpi-support.  But for hibernation not sure...

> 2. So far when i insert an empty dvd disk to burn it says it can not mount it. This is perhaps due to the fact the disk is empty and unformated. So i'm not sure if this is a problem. WHen i insert a written dvd works fine.

yes, you're correct.  It's empty so doesn't have any filesystem on it.

> 3. The burning speed of a dvd was very slow with k3b and Gnomebaker. WIth graveman it is working very well and i had no problems at all so far.

For k3b you can adjust the default burn speed in the burn dialog box, and save the settings.

---

### Post by siretfel on 2008-01-07
> ]If you were having the trouble after suspend I'd say look at whitelisting usb controller line 15 /etc/default/acpi-support.  But for hibernation not sure... 
After i did this: 
```
cd /etc/default
sudo cp -p acpi-support acpi-support.bak
sudo gedit acpi-support
```

and then i 
Changed MODULES="" to MODULES="ehci_hcd"

Everytime i come back from hibernation i put this code and every usb device i have it runs:
```
 sudo modprobe -r -v ehci_hcd && sudo modprobe -v ehci_hcd 
```

Unfortunatelly i don't understand how this works or how to make it work automaticaly everytime.I just inpute the code in terminal and....voila, everything ok.
Any suggestions on that?

```
yes, you're correct.  It's empty so doesn't have any filesystem on it
```.

Thanks for veryfying this. It seems obvious but for me as a newbi....it was not!


> For k3b you can adjust the default burn speed in the burn dialog box, and save the settings.

I did that but nothing happens. I have tried it 4 times so far but the max speed it gets is 0,6X.
So i'll use graveman since it worked twice so far with no problem.


Again many thanks for your help!!

---

