---
title: "Cannot access WinXP after having deleted partition"
date: 2006-07-27
forum: Installation &amp; Upgrades
---

### Post by jdolan on 2006-07-27
Hello, 

I'd really appreciate any help as it seems I have caused a bit of a problem. I have two hard disks, on one is Windows XP, on the other I installed Ubuntu. It worked fine. However, I recently decided to uninstall Ubunutu by deleting every partition on the hard disk to which it was installed and reformatting the disk.

(Done through Windows XP Computer Management console.)

However, now when my computer boots up I still get GRUB but it says please loading and then ERROR 22. How can I regain access to WinXP and why was GRUB not deleted when I reformattted the drive?

Many thanks,
Jord

---

### Post by murph2481 on 2006-07-27
> **jdolan said:**
> Hello, 

I'd really appreciate any help as it seems I have caused a bit of a problem. I have two hard disks, on one is Windows XP, on the other I installed Ubuntu. It worked fine. However, I recently decided to uninstall Ubunutu by deleting every partition on the hard disk to which it was installed and reformatting the disk.

(Done through Windows XP Computer Management console.)

However, now when my computer boots up I still get GRUB but it says please loading and then ERROR 22. How can I regain access to WinXP and why was GRUB not deleted when I reformattted the drive?

Many thanks,
Jord

I just did this the other day check this out:  You are going to have to run this in the recovery console for windows....

[http://danieltmurphy.com/blog/?p=44](http://danieltmurphy.com/blog/?p=44)

---

### Post by jdolan on 2006-07-27
Thankyou for the response. 
However, how am I able to get this executable onto my PC if I cannot boot into Windows? I have a recovery disk for my computer, with that I can either restore windows (re-install) but would lose my data or I can enter the command prompt. Is it possible to recover Windows (data in tact) from the command prompt?

Jord

---

### Post by Herman on 2006-07-27
Hi, jdolan, When we install Ubuntu, we write one part of GRUB boot loader (stage1) to MBR, another part to the first track of the hard disk (stage 1.5), and the rest of GRUB lives in the Ubuntu partition.
The part that is in the Ubuntu partition (stage 2) is the largest part of GRUB.

When we delete our Ubuntu partition, we delete the main part of GRUB, and stage 1.5, the part that is left, gives us the error message.
Stage 1, the part in the MBR, is very small, only 446 bytes, and is basically just a pointer, to point the BIOS to whatever operating system has the bootloader you want to use.

One solution is to use [GAG Boot Manager]("http://users.bigpond.net.au/hermanzone/p12.htm") to boot Windows with for now, the how-to in the link I just gave you has all the instructions you need, if you need help, just ask.

Another solution is to re-install Ubuntu or any other Linux, and that will give you a new GRUB again.

 As murph2481 suggested, if you are quiting Linux for good, you can put your old Windows 'IPL' (pionter, or first stage), back in your MBR and overwrite the GRUB one with either your Windows Installation disk or a Windows boot floppy.
The following links has more links in it with all the details about that. It isn't very hard. [Uninstall Ubuntu]("http://www.users.bigpond.net.au/hermanzone/p18.htm")
I hope that helps you, please ask any more questions you like, regards, Herman :)

---

### Post by murph2481 on 2006-07-27
Can you get to the recovery console in WindowsXP?

---

### Post by Herman on 2006-07-27
murph2481, That looks like it could be great program you've got there, it might be a lot easier than methods I know about so far. I'd like to give that a try. Can you provide a little more information first? I just want to know a little about what to expect it will do, that's all.
Can I download it in Ubuntu and run it, or how?
Regards, Herman :D

EDIT, sorry, murph2481, for the simultaneous post, I'll just sit quietly for a while and wait and see...

---

### Post by jdolan on 2006-07-27
Hi,

Many thanks for your help.
I have inserted my Windows Recovery disk and have two options to re-install Windows or to access the command prompt. I can access the command prompt but not the recovery console. How can I do this? Can I access the recovery console from the command prompt?

Jord

---

### Post by murph2481 on 2006-07-27
> **Herman said:**
> murph2481, That looks like it could be great program you've got there, it might be a lot easier than methods I know about so far. I'd like to give that a try. Can you provide a little more information first? I just want to know a little about what to expect it will do, that's all.
Can I download it in Ubuntu and run it, or how?
Regards, Herman :D

It is a windows executable file that you download and run in windows.  So what I did is downloaded the file, ran the little code snippet in command prompt (of which looks like it does nothing it just goes to the next line) then I rebooted my computer and GRUB was gone and it went straight to windows.  After that you can delete the file you downloaded

Then using Partition Magic I deleted and recovered the linux partition to windows and it was all gone.

Came in very handy when I had to hand in my work laptop last week to get a new one!

---

### Post by murph2481 on 2006-07-27
> **jdolan said:**
> Hi,

Many thanks for your help.
I have inserted my Windows Recovery disk and have two options to re-install Windows or to access the command prompt. I can access the command prompt but not the recovery console. How can I do this? Can I access the recovery console from the command prompt?

Jord

Try downloading the file on my blog to a pen drive or burn to a CD.  Go to command prompt on windows and go to that drive and try running that program with the code snippet.  See if that works.  It will look like nothing happened when you press enter you will have to reboot to see if it worked.

---

### Post by murph2481 on 2006-07-27
> **murph2481 said:**
> Try downloading the file on my blog to a pen drive or burn to a CD.  Go to command prompt on windows and go to that drive and try running that program with the code snippet.  See if that works.  It will look like nothing happened when you press enter you will have to reboot to see if it worked.

You can also try running the live CD of Ubuntu, downloading the file and saving it to your hard drive....

---

### Post by jdolan on 2006-07-27
I stuck that executable onto a floppy disk, inserted the floppy disk and then tried to run the executable from within the command prompt but to no avail. Just got a 'Bad command or file name' error. Do I need to burn that GAG manager to disk and then boot from that? However, this will not sort out the problem permanently will it?

I really appreciate all your help thus far, thanks.

Jord

---

### Post by Herman on 2006-07-27
> Do I need to burn that GAG manager to disk and then boot from that? However, this will not sort out the problem permanently will it? You can use GAG Boot Manager either just temporarily to boot Windows for you until you get murph2481's solution organised, or you can use it for as long as you like.
GAG Boot Manager can be run from a floppy disk or a CD, or installed to MBR and the first track of your hard disk. 

EDIT: I guess having the 'IPL' or 'first stage' (pointer) of any boot loader written to your MBR is about is permanent as they get. Your MBR on the first sector of you hard disk is stll just another sector on your disk though. It can be written to and erased/overwritten as many times as you like the same as any other sector of your disk.
Since GAG Boot Manager has its main part written to the normally vacant first track though, it is 'operating system independant', meaning you can delete any operating system (including Windows if you want),and GAG will still be there to boot the other systems you may have still installed.

Regards, Herman :D

---

### Post by Herman on 2006-07-27
murph2481, Thank you, I just gave MbrFix.exe a test run and it worked well for me. 

Is there any special place people should copy and paste their MbrFix.exe file to before they run it? I'm not very familiar with Windows, and I tried it in 'My Documents', but the 'Command Prompt' program opens in C:\Documents and Settings\Username. I felt a bit lost because I don't know the filepaths in Windows. The 'ls' command wasn't recognised either. I have an old book here called 'DOS for Dummies, but it has cobwebs on it. :D ( I mean that really!) I guess I should get it down and dust it off, just for fun.

For me the simplest way was to copy and paste the file to the root of drive C: and then 'cd ..' two times until I got a plain C:\ prompt and then I ran the command.
It worked fine! Thanks again, Herman :D

---

### Post by jdolan on 2006-07-28
I've sorted it, thankyou for everyones help.
After much research I used the following command at the command prompt and it cleared the master boot record wonderfully and cleared grub. My comp now boots into XP again. :)

**fdisk /mbr**

Thanks,
Jord

---

### Post by murph2481 on 2006-07-28
> **jdolan said:**
> I've sorted it, thankyou for everyones help.
After much research I used the following command at the command prompt and it cleared the master boot record wonderfully and cleared grub. My comp now boots into XP again. :)

**fdisk /mbr**

Thanks,
Jord

Yes you could have also fixed it with fdisk.  The reason I have that little program was because I was using Windows2000 which doesn't have fdisk.  Glad to hear you solved you problems

---

### Post by Scythe!? on 2006-07-28
From the Windows Recovery Console, you can type fixmbr which will write it to the MBR

---

### Post by Herman on 2006-07-28
Hello, Scythe!?,
The following sentence contains a link you can click on with more information about fdisk/mbr.>  _For Windows XP_
        Just put in your Windows XP install CD, and boot into the [recovery console]("http://www.kellys-korner-xp.com/win_xp_rec.htm") and use the fixmbr command. The paragraph below contians a link to a web-stie where Windows 98 Boot disk self-extracting files can be downloaded. When the file is in a Windows computer you just double-click on it and it wil copy itself to a blank formatted floppy disk automatically. (If my memory serves me correctly).
>          You can download a self extracting file to make your own Windows 98 boot floppy disk from [Bootdisk.com]("http://www.bootdisk.com/").  The one I use is called 98SE OEM and I have used it to restore the bootsector on both my Windows XP Home Edition computer and also my Windows 98SE computer.  Just pop the floppy in the drive and boot your computer to the     A:\_   prompt and use the command fdisk /mbr and your 'boot sector' will be back to normal again.
  Regards, Herman. :D

---

### Post by ALainONE on 2007-01-13
Please help... searching for a way to delete GRUB and restore XP... google pointed me to this post..

I have tried to use this solution, but when I press "R" to go to the Recovery Console... it tells me that it can not find my harddrive?!

I tried booting with a Linux LiveCD to delete the partition - although it did the job, I think all I need to do now is to fix my MBR.  I wanted to try the "FixMBR" thingy but (as I've said) whenever I try to go the recovery console... windows tells me that it can not find my harddrive.

Any way I can do this?  Please help?

---

### Post by tomzx on 2007-03-04
> **ALainONE said:**
> Please help... searching for a way to delete GRUB and restore XP... google pointed me to this post..

I have tried to use this solution, but when I press "R" to go to the Recovery Console... it tells me that it can not find my harddrive?!

I tried booting with a Linux LiveCD to delete the partition - although it did the job, I think all I need to do now is to fix my MBR.  I wanted to try the "FixMBR" thingy but (as I've said) whenever I try to go the recovery console... windows tells me that it can not find my harddrive.

Any way I can do this?  Please help?
I get the exact same problem. Is it possible that you're running on a SATA hard drive? I believe it's because your drive isn't recognize since the drivers aren't loaded in the loading sequence.

For my part, I have made a special win xp boot CD with sata drivers and when I get to the moment where I should have the option screen (with the possibility to select the recovery console), there's none showing up. I'm automatically redirected to the selection screen, asking me which partition to install WIN XP to. If I select 1 partition, it is not even able to tell that there's already another installation of WIN XP already there....

---

