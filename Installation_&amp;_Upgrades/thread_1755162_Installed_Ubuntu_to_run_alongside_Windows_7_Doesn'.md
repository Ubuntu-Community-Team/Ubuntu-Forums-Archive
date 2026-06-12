---
title: "Installed Ubuntu to run alongside Windows 7: Doesn't work"
date: 2011-05-10
forum: Installation &amp; Upgrades
---

### Post by your_cousin on 2011-05-10
Hi

I downloaded and installed Ubuntu (most recent version) today from the website to run alongside my Windows 7 operating system. I restarted as requested, and chose Ubuntu, and it said, "Finishing installation" (or something to that effect), counted down from 5, reached 0, hovered at 0 for a minute, then the screen went black.

After waiting a very long time, I pressed ctrl+alt+delete twice and it rebooted the computer. This time, after doing everything like before, it went into Ubuntu and everything worked normally (as if installing properly) and performed a mandatory reboot.

Now whenever I try to boot Ubuntu, it gives me a list of things to do on boot (I can't remember them but off the top of my head it is something like:)

-Ubuntu 
-Ubuntu (recovery)
-Windows 7
-Windows 7 Recovery [the ones with windows 7 take me back to the page where I can initially choose which OS to run]

Choosing either of the Ubuntu ones causes a very fast string of words to fly across the screen (too technical to understand and too fast to read, but the word 'failed' jumped out a lot) and then the screen goes black. The computer remains on but the screen remains black until I (regretfully) force off my computer.

Any ideas what's happening?

---

### Post by saegeoff on 2011-05-10
Need some more basic info.  What version of Ubuntu are you using? 10.04, 10.10, 11.04? 32-bit or 64-bit?  Same hard drive or separate drives?

---

### Post by your_cousin on 2011-05-10
I believe it is 11.04 and I put it on the same hard drive.

---

### Post by jerome1232 on 2011-05-10
From a live cd can you download and run this script provided by meierfra, and Gert Hulselmans, members of these forums for troubleshooting these kind of issues.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Please post the resulting results.txt enclosed in [noparse]```

```[/noparse] tags

---

### Post by your_cousin on 2011-05-10
I don't know if I feel comfortable running some arbitrary script on my computer. can't I just attempt a reinstall or something?

---

### Post by saegeoff on 2011-05-10
That script is trusted.  It will give us more information regarding your setup.  However, if you feel more comfortable you can attempt a reinstall.  Boot from the CD or DVD and follow the on-screen instructions.

---

### Post by your_cousin on 2011-05-10
Actually, how about this: I just want to remove it entirely, and then I want to run it in a virtual box instead of... whatever this is that it's doing now. Can that be done easily?

---

### Post by jerome1232 on 2011-05-10
I can respect that, you could always look at the script, if you look around this forum you'll see exactly what it does, it get's used frequently for troubleshooting boot problems. I can assure you there's nothing malicious in it.

Before attempting a reinstall I would at leastconfirm that Windows 7 along with your data is there, can you post the output of fdisk?

```
sudo fdisk -l
```


btw how did you do the install before, with the automatic partitioner or did you manually partition? I would also run the disk integrity check to make sure your disk was a good burn.

---

### Post by your_cousin on 2011-05-10
it was automatically partitioned, and can I run that command you gave me without going into Ubuntu? because it would be hard to tell you what it returns through a black screen. I am in Windows 7 right now.

---

### Post by saegeoff on 2011-05-10
It may not be as easy as you would expect.  If you are dual booting, grub took over as your boot loader.  Just deleting the Linux partitions would prevent you from being able to boot back into Windows.

P.S. back everything up in your Windows partition if you aren't sure what you are doing.  If you incorrectly change your partitions, you could end up losing your data.

---

### Post by jerome1232 on 2011-05-10
Oh I thought you said Win 7 wasn't booting.

Okay, so we are all on the same page here...

As I understand it you want to remove Ubuntu, get Win7's bootloader back on the mbr, and install Ubuntu into a virtual machine to test it out correct?

---

### Post by your_cousin on 2011-05-10
omg. so what am I supposed to do?

---

### Post by your_cousin on 2011-05-10
yes jerome, that is exactly what I want to do!

---

### Post by jerome1232 on 2011-05-10
If you have a Windows 7 installation disk you can follow these instructions to restore your mbr

[http://www.ehow.com/how_4836283_repair-mbr-windows.html](http://www.ehow.com/how_4836283_repair-mbr-windows.html) (untested by me and I only briefly looked it over to ensure it looked about right)

Once the MBR is restored you can simply use the Windows 7 parittion manager (Administration tools - computer managment - .... data managment? I think) and delete the Ubuntu partitions and resize your windows 7 system disk to fill the entire drive.


If you do not have a windows 7 disc I guess you can create a recovery disc using the method found in a comment on this page

[http://superuser.com/questions/156339/restore-win-7-mbr-without-recovery-install-disc](http://superuser.com/questions/156339/restore-win-7-mbr-without-recovery-install-disc)


yes I did alot of googling. :)

Let us know if you have more questions

---

### Post by your_cousin on 2011-05-10
must i restore the mbr? or could I just repartition the drive? (I am very lazy)

---

### Post by jerome1232 on 2011-05-10
You must restore the mbr, part of grub resides in the Ubuntu partition, if you wipe out the Ubuntu partition without restoring the mbr you will lose all ability to boot the computer.

Another option I forgot would be to use easybcd to restore the mbr, I like it. 

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)


As for using a Virtual Machine I recommend Oracles Virtualbox, very easy to setup and works like a thing of beauty.

[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by your_cousin on 2011-05-10
I downloaded and installed the easybcd program. Wanna tell me what button to push? lol

---

### Post by jerome1232 on 2011-05-11
No, but at their website they have documentation on how to do so.

[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+with+EasyBCD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+with+EasyBCD)


This is for Vista but it will still apply.

---

### Post by your_cousin on 2011-05-11
Will this get rid of any of my documents?

---

### Post by saegeoff on 2011-05-11
This may be of help as well.

[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

Yes, you must restore the MBR.  You shouldn't lose any documents, unless they are on the linux partitions you are deleting.

---

### Post by jerome1232 on 2011-05-11
> **your_cousin said:**
> Will this get rid of any of my documents?

No, the MBR is the first sector of your disk, it's dedicated for bootloaders, which have zero impact on the rest of your data.

---

### Post by wilee-nilee on 2011-05-11
I think this is a wubi install guys and gals.

> **I restarted** as requested, and chose Ubuntu, and it said, **"Finishing installation"** (or something to that effect)

Anybody ever see this on a regular dual boot.

---

### Post by your_cousin on 2011-05-11
Okay so by restoring the mbr, the ubuntu will automatically be deleted?

---

### Post by wilee-nilee on 2011-05-11
> **your_cousin said:**
> Okay so by restoring the mbr, the ubuntu will automatically be deleted?

Answer me this, did you boot a ubuntu cd to install it?

Take a screen shot of the disk manager in W7 and post it.

No to your question.

---

### Post by saegeoff on 2011-05-11
Your_cousin, do you see Wubi in Add/Remove programs in the Windows Control Panel?  Or frankly, do you know if this is a Wubi install?

---

### Post by your_cousin on 2011-05-11
I used wubi to install it

---

### Post by wilee-nilee on 2011-05-11
> **your_cousin said:**
> I used wubi to install it

And you get the windows boot menu to boot from correct.

---

### Post by saegeoff on 2011-05-11
Okay, different situation.  I think you can just remove that from your Windows Control Panel.  Once you do that, you should have no more issues.

Wubi is not a real dual boot.  Maybe that is why you were having issues.

Just remove it and you should be back to just Windows 7 only.

---

### Post by jerome1232 on 2011-05-11
](*,) ](*,) ](*,) ](*,) ](*,) ](*,)

Good insight. That line didn't even register in my brain when I read it.

---

### Post by your_cousin on 2011-05-11
dear God in Heaven, could it really be that simple? I'll give it a shot and get back to you.

---

### Post by wilee-nilee on 2011-05-11
> **jerome1232 said:**
> ](*,) ](*,) ](*,) ](*,) ](*,) ](*,)

Good insight. That line didn't even register in my brain when I read it.
If I had a $ for everytime I would not be here.;)

---

### Post by your_cousin on 2011-05-11
Well that did it, people. Haha Thank you for all your help :)

---

### Post by Quackers on 2011-05-11
Well spotted wilee-nilee :-)

---

### Post by saegeoff on 2011-05-11
wilee-nilee is a pro power user!

---

### Post by wilee-nilee on 2011-05-11
> **Quackers said:**
> Well spotted wilee-nilee :-)

I learned all from you, you crazy duck.;)

You know takes one to know one.

---

### Post by wilee-nilee on 2011-05-11
> **saegeoff said:**
> wilee-nilee is a pro power user!

I would put that as a quote in my signature but I would be laughed off the forums, I like a good laugh though thanks.;)

---

### Post by Quackers on 2011-05-11
Crazy duck? This from SuperRabbit :-)

---

### Post by wilee-nilee on 2011-05-11
> **Quackers said:**
> Crazy duck? This from SuperRabbit :-)

Sorry I was a bit giddy I forgot my password for my W7 admin account, and I was back in, in about 6 min, with a hirens disc and unlocking the hidden admin account I had locked so I could change the password, for the regular admin. The longest part was finding the darn app to turn off the login confirm so I could get in, on the hirens booted to the mini xp.

---

### Post by Quackers on 2011-05-11
Aha! A forgetful SuperRabbit? :-)

---

