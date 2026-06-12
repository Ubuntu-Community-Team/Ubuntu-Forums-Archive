---
title: "Ubuntu 10.04 &amp; Windows 7 Multiboot - Two HDD's"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by Jadephyre on 2010-04-30
Alright guys, I'm out of ideas...
I have a system here with three harddiscs, the first is a 500GB disc which is supposed to contain Windows 7, the second is a 250GB disc for Ubuntu 10.04 and the third is a 1TB drive which contains all my music, movies and stuff like that.

Now I installed Windows 7 first, then Ubuntu 10.04 onto the other disc.
The thing is that the Ubuntu-Installer gave me the option of installing them side by side by shrinking the Windows Disc, which I don't want it to because I hate to clutter up ONE drive with more than one OS.
So, after installing and rebooting into Ubuntu, I went to see if I could still start Windows 7, which I now can't.

Is there a way to have Windows 7 and Ubuntu 10.04 playing nicely together WITHOUT swapping the SATA ports or something like that ?
And please don't ask why i'm giving Ubuntu the smaller drive... I'm still a gamer, and my games need a lot of space.
I just want to make a switch to Ubuntu for the times where I'm not playing any kind of Games.

By the way: Both Operating Systems where installed in 64-bit flavour.

---

### Post by mourngrym1969 on 2010-04-30
Without more detail from you, I will have to make a couple of assumptions: chief among them is that during the Ubuntu install, the last step has an 'advanced options' button (right after the partitioning, during the 'confirm everything we are going to do' screen). Clicking that button would have asked what drive you wanted the boot loader to install to. By default, the boot loader will install to the primary boot drive set in the computer BIOS.

Since you mentioned Windows was installed first, I have to assume that device was the first physical drive in BIOS. That is where the boat loader installed and thus installed over the Windows boot loader. That is normally ok because historically Ubuntu does a good job of detecting additional operating systems and adding them to the boot menu.

However, one of the bugs mentioned here was that Ubuntu 10.04 and the new version of GRUB were not detecting dual boot systems correctly. Now, you can do one of two things:

1) Manually add your windows partition to the boot menu, a quick google search for an example grub.cfg for a dual boot system will give you examples
2) Put the windows CD in the drive, go to recovery mode and do the famous 'fixmbr' and 'fixboot' commands to restore the windows boot loader. Unfortunately that will blow away GRUB and you won't be able to boot linux.

If you need more details behind either solution, let me know and I can post detailed instructions, I have had to do both before (although not because of this specific issue).

Mourn

---

### Post by spydeyrch on 2010-04-30
Actually, I have the answer. On the final day before ubuntu was released, a bug was discovered. It doesn't allow booting in to alternate OSs in grub for some people. Not everyone is affected but a large majority are. It erases the boot option from your grub boot menu. There is an update that should fix it or if you want to wait, the ubuntu dev team is re-spinning the .iso files and should have them out soon, if they are out by now.

If you don't believe me, you can google it and read about it. Your win 7 partition is still there. It is just a bug with 10.04 for the moment. sorry man.  :(

Hope that at least takes away any worries about your win 7 partition. You could always hit your boot interupt key during POST. This allows you to chose what drive to boot from instead of going off of the default via the BIOS. Then just choose your windows drive. I have a tri-boot system: Windows 7 Pro x64, Ubuntu 9.10 x64, and Mint 8 x64. It works for me so it should work for you. Let us know if it helps.

-Spydey :lolflag:

---

### Post by Jadephyre on 2010-04-30
Would it help if I let Ubuntu install GRUB on it's own partition, so that it can add Windows when I re-install Ubuntu ?

Or let's ask: Is that possible ?

---

### Post by spydeyrch on 2010-04-30
> **Jadephyre said:**
> Would it help if I let Ubuntu install GRUB on it's own partition, so that it can add Windows when I re-install Ubuntu ?

Or let's ask: Is that possible ?

This is what I can tell you, how I got it to work on my machine. Now granted, I am not running 10.04 yet and from what I understand, the standard apt grub-update won't add your win7 line to your grub menu. So I don't know if my way will work or not with your setup. Actually, I have an idea that will work for you, I am positive.

Ready?

---

### Post by spydeyrch on 2010-04-30
> **Jadephyre said:**
> Would it help if I let Ubuntu install GRUB on it's own partition, so that it can add Windows when I re-install Ubuntu ?

Or let's ask: Is that possible ?

Hey Jadephyre, can you still boot into your Windows partition, via it being the only drive connected?

---

### Post by Jadephyre on 2010-04-30
no, the bootloader is, as it seems, completely shot

---

### Post by spydeyrch on 2010-04-30
Ok, so this is the idea that I had to get it to work to some degree. I will also post the way that I did it on my machine and it works for me. Two seperate ways to do it. The first one will work for you (like 98% sure). The second one I am not sure because you are using 9.10 but you can try it if you want.

Part 1 coming in just a moment.

-Spydey :lolflag:

---

### Post by spydeyrch on 2010-04-30
> **Jadephyre said:**
> no, the bootloader is, as it seems, completely shot

Ok, so first things first, we need to get your boot loader up and running. It is very important that you are able to boot into your windows drive.

Do you still have your Win7 installer DVD?

---

### Post by Jadephyre on 2010-04-30
Of course, right here on the table.
I was going to do a fixmbr & fixboot in a minute.

---

### Post by bcbc on 2010-04-30
See here [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

---

### Post by spydeyrch on 2010-04-30
> **Jadephyre said:**
> Of course, right here on the table.
I was going to do a fixmbr & fixboot in a minute.

Awesome, that is what I was going to tell you to do.

But make sure that all other HDD are NOT (not "screaming", just adding emphasis. :)) connected. We just want your Win7 HDD connected. Then go ahead and fix the MBR and the boot loader. Let me know when you are done with that. In the meantime, I m going to write up my first idea that should allow you to boot into either OS. Granted, it might get a little annoying after a while. I don't find it annoying but everyone is different, right.

Should have that write up in just a little bit.

-Spydey :lolflag:

---

### Post by Jadephyre on 2010-04-30
alright, I'll do that and follow instructions again when I'm back in windows.

---

### Post by spydeyrch on 2010-04-30
_**Option 1**_

After you get your win7 boot loader fixed and you are sure that you can boot into win7 do the following (read it at least once prior to doing it so that you know the desired out come):

Disconnect your win7 HDD.
Connect the HDD that you want to use for Ubuntu. Make sure that your "media" drive is not connected yet.
Install Ubuntu just like normal. 
Once ubuntu is installed, with mchine off, re-connect your win7 hdd.
Turn on your PC, during POST, you should see a message similar to "Press FX" (i.e. F8 is my button, for some it might be F12) to choose boot device. If you don't do this, it will boot from the primary boot device configured in your BIOS.
When the menu comes up, chose the corresponding HDD to boot from and viola!
Reconnect your "media" hdd.

What this means though is that you will have to do this every time or it will boot from your primary boot device.

Also, you could use vista boot pro or a similar program (don't remember the name right now) and add your ubuntu boot drive to the windows boot loader. This will then give you an option, via the windows boot loader, to boot from windows or ubuntu. It works, I have don't it many a times.

So this is option 1. I will write up option 2 in just a moment.

-Spydey :lolflag:

---

### Post by spydeyrch on 2010-04-30
> **spydeyrch said:**
> 
Also, you could use vista boot pro or a similar program (don't remember the name right now) 

The other program is called EasyBCD and it is the one I use. I actually have both Vistaboot Pro 3.x and EasyBCD installed as I need both of the to do things. EasyBCD will fix your MBR and Boot loader with a quick push of a button. :-)

-Spydey :lolflag:

---

### Post by Jadephyre on 2010-04-30
Fixing Windows didn't work, I have to start all over again.
But the first Solution sounds good, i'll try that... later...

---

### Post by spydeyrch on 2010-04-30
> **Jadephyre said:**
> Fixing Windows didn't work, I have to start all over again.
But the first Solution sounds good, i'll try that... later...

I have a way that you can fix the MBR. Don't start over yet!!!!

Please don't start over until you have at least tried my way to fix the MBR. It really isn't "my" way but a way that I know of to fix it.

Respond back once if you read this before you start over. 

-Spydey :lolflag:

---

### Post by spydeyrch on 2010-04-30
> **spydeyrch said:**
> I have a way that you can fix the MBR. Don't start over yet!!!!

Please don't start over until you have at least tried my way to fix the MBR. It really isn't "my" way but a way that I know of to fix it.

Respond back once if you read this before you start over. 

-Spydey :lolflag:
Starting over will take a long time. At elast give this fix a try first.

-Spydey :lolflag:

---

### Post by spydeyrch on 2010-04-30
To repair the  damage, open a Command Prompt window from your booted windows 7 DVD and  run the following command, substituting the  letter of your DVD drive for d here:  

[B]d:\boot\  bootsect.exe /nt60 all

[/B]That should repair it but you can only have your windows 7 hdd connected while doing it.

-Spydey :lolflag:

---

### Post by spydeyrch on 2010-04-30
Also, check out these webistes for possible bcd fixes.

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

-Spydey :guitar:

---

### Post by spydeyrch on 2010-04-30
Let me know if you would like me to post option 2.

Heading off to bowling with my office colleagues. I will check back later.

Good luck.

-Spydey :lolflag:

---

### Post by Jadephyre on 2010-04-30
post option 2 if you like, but I don't see any other option anymore than to reinstall Windows and stick to it... I'm close to believing that this hassle isn't worth it...

Or I could install Ubuntu thru Wubi... though that would be the option with the most "suckage"...




15 years i'm working with computers now and I feel like a goddamn newbie... I hate this crap...

---

### Post by Jadephyre on 2010-04-30
Alright, I've installed Windows to the 500GB Drive again (yes, a complete re-install) and installed Ubuntu to the 250GB Drive, telling it to also put GRUB on the same drive as Ubuntu.

I've tried to add Ubuntu to the Windows 7 Bootloader by using EasyBCD, but I've done something wrong as it seems because it stil isn't working.
Now it's the other way around, Windows is working, but Ubuntu isn't...

---

### Post by spydeyrch on 2010-05-03
Sorry about the delay in responding. I went bowling with my office co-workers and then after that I headed off to do some weekend camping and hiking. Just got back into the office this morning.

> **Jadephyre said:**
> Alright, I've installed Windows to the 500GB  Drive again (yes, a complete re-install) and installed Ubuntu to the  250GB Drive, telling it to also put GRUB on the same drive as Ubuntu.

I've tried to add Ubuntu to the Windows 7 Bootloader by using EasyBCD,  but I've done something wrong as it seems because it stil isn't working.
Now it's the other way around, Windows is working, but Ubuntu  isn't...

So it sounds like it isn't playing nice with EasyBCD. :( Sorry to hear that.
My recommendation would be that you install windows on one drive, with no other drives attached, then install ubuntu with no other drives attached. Then connect all drives and during your POST hit your boot selection key. Mine is F8, some people's is F12. Yours may be different.

You will have to do this every time if you don't want to boot into the default boot drive/OS.

Another thing you could do is use the Chameleon Bootloader. It is pretty sweet!! Google it and if you need some help, let me know. :D

-Spydey :popcorn:

---

### Post by oldfred on 2010-05-03
IF you have grub2 installed on the MBR of a second drive it can be set to boot first in BIOS. You leave the windows boot loader in the MBR of the first drive and can go back to it at any time.

Grub2 will find your windows install and give you a choice to boot either windows or grub.

---

