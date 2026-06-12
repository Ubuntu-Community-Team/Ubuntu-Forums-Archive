---
title: "Ubuntu dual boot with Windowsxp"
date: 2014-03-17
forum: Installation &amp; Upgrades
---

### Post by tomsubt on 2014-03-17
Hello Everyone,  I have had unbuntu on my pc for around 6 months or more and I installed it along side what I thought would be xp. but the xp did not have a recovery system it was deleted by the old owner of the pc. But I still had the choice to boot to Ubuntu or windows but when ever I tried to boot to windows it would get stuck with the message No Recovery system available and would not boot into windows, so I just used ubuntu, which all I need now anyway!
So just out of curiousity I tried t  use an xp file installation disk on the pc, thinking it would boot into windows, that was a big mistake (guess I was not thinking)!
Anyway I now no longer get the Dual boot options between ubuntu and windows xp, it just keeps bringing up windows recovery but does not recover.

I cannot get ubuntu to come up (No Dual Boot Anymore) at all Unless I put the ubuntu cd back in and it wants me to install it again.

Is there anyway to get back the installation of ubuntu that was on it before, I really need this because I updated all the ubuntu files and programs a week ago.
Hope someone can tell me how to get back the ubuntu installation without Re-Installing it??????? Thank You.

---

### Post by ubfan1 on 2014-03-17
You can try reinstalling grub to the hard disk.  Boot the Ubuntu live media and select the "try" option.  Then start a terminal (Ctrl+Alt+T) and type sudo grub-install /dev/sda1  (or whatever the right partition number is for your hard disk installation).  Try to reboot the disk and see if you get Ubuntu back.

---

### Post by tomsubt on 2014-03-17
I could not get the terminal to come up with the keys. but I went up to the top right hand corner and on the drop down menu clicked on System Update and it stated a sytem update was done 208 days ago and no further updates are available, so I would think its still on the pc, but cannot get the dual boot to come up so I can choose ubuntu!
but the screen is now saying Prepare to install.???
What else can I try?

---

### Post by ajgreeny on 2014-03-17
> **ubfan1 said:**
> You can try reinstalling grub to the hard disk.  Boot the Ubuntu live media and select the "try" option.  Then start a terminal (Ctrl+Alt+T) and type sudo grub-install /dev/sda1  (or whatever the right partition number is for your hard disk installation).  Try to reboot the disk and see if you get Ubuntu back.
NO!

Please do not use ```
sudo grub-install /dev/sda1
```  Grub needs to go on the MBR of the disk, not to a partition, and you need a few more steps than are given above.
First you need to find out what your drives are called. You can do this by going to a terminal in the live system and typing: ```
sudo fdisk -l
```From that you need to find the device name of your Ubuntu drive, something like &#8220;/dev/sda5&#8243;.
 So, still in the terminal, type:
```
sudo mkdir /media/sda5
sudo mount /dev/sda5 /media/sda5
```And then, to reinstall the grub```
sudo grub-install --root-directory=/media/sda5 /dev/sda
```
 
Push enter and you&#8217;re done! Of course you need to replace &#8220;/dev/sda5&#8243; and &#8220;/dev/sda&#8221; with what you found in the fdisk output.

However, having re-read your original post I have a nasty suspicion that when you tried restoring windows you may have wiped out your ubuntu installation.  I sincerely hope I am wrong, so let's see the output of ```
sudo fdisk -l
``` in terminal from a live system to be sure what we've got on disk to deal with.

---

### Post by tomsubt on 2014-03-17
I tried the Try Option but I only get a screen with three choices and the first is to Erase the 1204 I have on the pc and start new and I dont want to do that!
I tried the Terminal again from here and it would not come up either??? More suggestions please???? Thanks

---

### Post by ajgreeny on 2014-03-17
So are you saying you can not get a live DVD or USB to boot to a usable desktop?
I'm not sure if we are misunderstanding you, or you are misunderstanding us.

---

### Post by ubfan1 on 2014-03-17
Apologies for my earlier wrong grub inst, I don't know what I was thinking, I never install grub to a partition.

---

### Post by tomsubt on 2014-03-17
ubfan1,  thats ok no problem

I was asked So are you saying you can not get a live DVD to boot to a usable desktop<<<

Yes, thats what I mean if I put the live cd in it wants me to reinstall ubuntu and it says I would lose all the updates and files I already have on my 12.04 installation.

When start the pc now, I dont get my dual boot screen anymore, I just keep getting the windows partition that needs a recovery system to boot it. The old owner removed it by mistake

So the computer put the ubuntu next to the partial windows setup and now when I turn on the pc it tries to go straight into windows but keeps asking for the recovery file (which it does not have).

It never did this before I always got the dual boot choice but there is no choice now, I think I did something when
I tried to install by cd the xp backup files, I mistakenly thought it would put the recovery back on too, but it did not

 however ubuntu is still on the pc but cannot get it to offer the dual boot anymore or cannot go straight to ubuntu either.
I was hoping I could some how boot directly to ubuntu and by pass the windows partition??????

---

### Post by ajgreeny on 2014-03-17
Are you sure you have a live CD version and not the Alternate Install CD of a previous ubuntu version.  
You need to use a live CD/DVD/USB and boot to a live system desktop to reinstall grub.  There may be other ways, but I am not aware of them, and I can't help with windows any more, having not properly used it for many years.

---

### Post by tomsubt on 2014-03-17
Yes, its the original cd 12.04 I burned and installed on the computer.

Is there a way to erase the partial windows partition and not interfere with ubuntu?

---

### Post by tomsubt on 2014-03-23
Ok, I found and made a boot repair disk and it was successful but the last line of instructions I could not complete which was to make sure I change the bios to boot with ubuntu, I did not know how to get to the bios on ubuntu can some help me out, Please see the Results of the Boot Repair and notice the very last line that I was not able to do, I restarted the pc and am still getting the windows xp only, how to change the bios with ubuntu???>>>>

[http://paste.ubuntu.com/7141061/](http://paste.ubuntu.com/7141061/)

---

