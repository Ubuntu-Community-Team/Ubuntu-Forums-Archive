---
title: "GRUB2 - Help! I don't speak computer..."
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by juliarain on 2009-12-11
I'm re-posting this from the Absolute Beginner's Forum, after a guy told me what program the issue was with. As a quick recap, I installed some updates onto Ubuntu/Wubi and now I can't access my desktop. The guy who commented told me to input "update-grub" and that didn't work (though I might have been doing it wrong because I don't speak computer).  At this point, I just want to access my desktop. 

Here is the post: 

[INDENT] 				[[IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG] 				**Absolute Noob Installs Updates, Can No Longer Access Desktop**]("http://ubuntuforums.org/showthread.php?t=1351724") 			
So I installed Ubuntu using the [Wubi]("http://wubi-installer.org/") installer for Windows (not because I want to keep Windows, but because I don't have a CD driver on my laptop anymore and didn't want to attempt [these complicated instructions for installing Linux from a USB drive]("http://wiki.archlinux.org/index.php/Install_from_a_USB_flash_drive")). 

I should mention that the whole goal of this was to get a working wireless card again, since I accidentally deleted the Windows software that allows me to use it. I know nothing about C++. I just thought Linux would be a good option since I didn't want to repurchase the software that would allow me to access the internet again. Dell did not send me any installation disks with the laptop - and even if I had them, I couldn't use them due to my nonexistent CD drive - and the laptop is literally held together with packing tape at this point, so it's really not worth spending any money on. It would just be nice to have a working internet connection on it again. Anyway... 

I had Ubuntu installed (via Wubi) and it was working fine for several days. Then I installed a bunch of updates, and restarted my computer. Now, when I start the computer and tell it to run Ubuntu, it gives me this: 


[CENTER]GNU GRUB  version 1.97~beta4
[/CENTER]

 [ Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device/file completions. ] 

sh:grub>_


// So I press tab, and it says: 


Possible commands are: 
 . [ baldram boot cat chainloader configfile cpuid dump echo exit export halt help initrd insmod linux list_env load_env loopback ls lsmod parser.rescue parser.sh reader.normal reader.rescue reboot rmmod root sav_env search set sleep source terminal_input.console terminal_output.console test unset
sh:grub>_


Obviously I don't understand what any of this means (with the exception of "exit"), so my question to you is, what do I do now to access my desktop? 

Thanks so much for your help, 

- Julia


[INDENT]Reply from Merk42: 

 				 				**Re: Absolute Noob Installs Updates, Can No Longer Access Desktop** 			
The USB instructions were probably complicated because it was Arch Linux.  USB instructions for Ubuntu can be found [here]("https://help.ubuntu.com/community/Installation/FromUSBStick")

As for your current issue, not too familiar with GRUB2 or WUBI, possibly there was kernel update and it needs to be added as an entry?

So try update-grub at that terminal you get.
More information on GRUB2 [here]("http://ubuntuforums.org/showthread.php?t=1195275")


[/INDENT][/INDENT]Thanks so much for your help, 

- Julia

---

### Post by adaucourt on 2009-12-11
> **juliarain said:**
> I'm re-posting this from the Absolute Beginner's Forum, after a guy told me what program the issue was with. As a quick recap, I installed some updates onto Ubuntu/Wubi and now I can't access my desktop. The guy who commented told me to input "update-grub" and that didn't work (though I might have been doing it wrong because I don't speak computer).  At this point, I just want to access my desktop. 

Here is the post: 
[INDENT]                 [[IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG]                 **Absolute Noob Installs Updates, Can No Longer Access Desktop**]("http://ubuntuforums.org/showthread.php?t=1351724")             
So I installed Ubuntu using the [Wubi]("http://wubi-installer.org/") installer for Windows (not because I want to keep Windows, but because I don't have a CD driver on my laptop anymore and didn't want to attempt [these complicated instructions for installing Linux from a USB drive]("http://wiki.archlinux.org/index.php/Install_from_a_USB_flash_drive")). 

I should mention that the whole goal of this was to get a working wireless card again, since I accidentally deleted the Windows software that allows me to use it. I know nothing about C++. I just thought Linux would be a good option since I didn't want to repurchase the software that would allow me to access the internet again. Dell did not send me any installation disks with the laptop - and even if I had them, I couldn't use them due to my nonexistent CD drive - and the laptop is literally held together with packing tape at this point, so it's really not worth spending any money on. It would just be nice to have a working internet connection on it again. Anyway... 

I had Ubuntu installed (via Wubi) and it was working fine for several days. Then I installed a bunch of updates, and restarted my computer. Now, when I start the computer and tell it to run Ubuntu, it gives me this: 


[CENTER]GNU GRUB  version 1.97~beta4
[/CENTER]

 [ Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device/file completions. ] 

sh:grub>_


// So I press tab, and it says: 


Possible commands are: 
 . [ baldram boot cat chainloader configfile cpuid dump echo exit export halt help initrd insmod linux list_env load_env loopback ls lsmod parser.rescue parser.sh reader.normal reader.rescue reboot rmmod root sav_env search set sleep source terminal_input.console terminal_output.console test unset
sh:grub>_


Obviously I don't understand what any of this means (with the exception of "exit"), so my question to you is, what do I do now to access my desktop? 

Thanks so much for your help, 

- Julia

[INDENT]Reply from Merk42: 

                                  **Re: Absolute Noob Installs Updates, Can No Longer Access Desktop**             
The USB instructions were probably complicated because it was Arch Linux.  USB instructions for Ubuntu can be found [here]("https://help.ubuntu.com/community/Installation/FromUSBStick")

As for your current issue, not too familiar with GRUB2 or WUBI, possibly there was kernel update and it needs to be added as an entry?

So try update-grub at that terminal you get.
More information on GRUB2 [here]("http://ubuntuforums.org/showthread.php?t=1195275")


[/INDENT][/INDENT]Thanks so much for your help, 

- Julia

so why didnt you just download the drivers from manufacturers website instead of trying your hand at a whole new OS?

You could try the following 2 commands at the grub prompt: 
 
root (hd0,1) 
chainloader +1

---

### Post by juliarain on 2009-12-11
> **adaucourt said:**
> so why didnt you just download the drivers from manufacturers website instead of trying your hand at a whole new OS?

That... did not occur to me. *sigh* 

I tried those commands; it just gives me this: 

(hd0,1): Filesystem is ntfs.

---

### Post by adaucourt on 2009-12-11
> **juliarain said:**
> That... did not occur to me. *sigh* 

I tried those commands; it just gives me this: 

(hd0,1): Filesystem is ntfs.

paste the output of this command from the grub prompt:
```
ls
```

---

### Post by juliarain on 2009-12-11
```
(loop0) (hd0) (hd0,1)
```

---

### Post by darkod on 2009-12-11
From the prompt you are getting, to get wubi up and running again try the following commands one by one:

sh:grub>set root=(loop0)
sh:grub>linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro
sh:grub>initrd /boot/initrd.img-2.6.31-14-generic
sh:grub>boot

If that helps wubi to start, open terminal and execute:

sudo update-grub2

That should sort out the sh:grub problem.

---

### Post by juliarain on 2009-12-11
It worked! Thank you so so much!!! :KS

---

### Post by standarshy on 2010-01-05
My friend was having this problem and your solution worked.  Thanks for contributing!


> **darkod said:**
> From the prompt you are getting, to get wubi up and running again try the following commands one by one:

sh:grub>set root=(loop0)
sh:grub>linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro
sh:grub>initrd /boot/initrd.img-2.6.31-14-generic
sh:grub>boot

If that helps wubi to start, open terminal and execute:

sudo update-grub2

That should sort out the sh:grub problem.

---

### Post by PuterTrouble on 2010-01-07
> **darkod said:**
> From the prompt you are getting, to get wubi up and running again try the following commands one by one:

sh:grub>set root=(loop0)
sh:grub>linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro
sh:grub>initrd /boot/initrd.img-2.6.31-14-generic
sh:grub>boot

If that helps wubi to start, open terminal and execute:

sudo update-grub2

That should sort out the sh:grub problem.

Will this command work with a regular Ubuntu installation? Not wubi.

---

### Post by Newbie6 on 2010-01-08
I have this problem with wubi too. I have tried to run the command ls and get this:

(loop0) (hd0) (hd0,6)  (hd0,5)  (hd0,4)  (hd0,2)  (hd0,1) 

When I run ls /boot I get this:

2.6.31-17-generic-pae

I have tried to run the commands mentioned in this thread and have changed the kernel name with 2.6.31-17-generic-pae instead of 2.6.31-14-generic and the partition name with sda1 and sda2 etc. 

and everything goes well until I run the command boot.....

then it writes a lot of things..... I have noticed these 2 sentences:

unable to mount root fs on unknown-block (8,5)

2.6.31-17-generic-pau swapper not tainted #54 Ubuntu

Can anyone please help me please? Thanks.

---

### Post by drs305 on 2010-01-08
> **PuterTrouble said:**
> Will this command work with a regular Ubuntu installation? Not wubi.

No, the command is different for a normal Ubuntu install.
Change the two bold two lines from:
> 
**set root=(loop0)**
...
**linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro**
To this:
> 
set root=(hd0,1)
...
linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 ro
Of course, change the version and root to whatever apply in your situation.

---

### Post by presence1960 on 2010-01-08
> I should mention that the whole goal of this was to get a working wireless card again, since I accidentally deleted the Windows software that allows me to use it. I know nothing about C++. I just thought Linux would be a good option since I didn't want to repurchase the software that would allow me to access the internet again. Dell did not send me any installation disks with the laptop - and even if I had them, I couldn't use them due to my nonexistent CD drive - and the laptop is literally held together with packing tape at this point, so it's really not worth spending any money on. It would just be nice to have a working internet connection on it again. Anyway...

You didn't get any disks because you have a hidden recovery partition which can restore your hard disk to the factory image (the way it came on day one). 

You should not have to repurchase the drivers/software for your wireless. You should be able to go to the manufacturer's web site & download them.

Installing an OS that you know very little about IMHO is the lazy way out of solving your problem and not too bright either. Even if Ubuntu fixed the wireless issue you still will not be able to run it in Windows as windows can not use the drivers in Ubuntu. Not to be a wise *** but you have to do some legwork on your own. That would be the easiest and most sensible way to fix your wireless. Use google to search for your wireless device and you most likely will find the info on where to download the drivers for it. The other option is to back up all your data and use the recovery partition to restore your hard disk to the way it was day one. This will restore your wireless drivers in the process. Then if you want Ubuntu install it again. Refer to your documentation to see how to start the recovery process for your model Dell lappie. Or go to dells web site and get the manual for your model lappie.

If the lappie is held together with tape get it repaired or junk it.

---

### Post by xairoy on 2010-01-08
> **darkod said:**
> From the prompt you are getting, to get wubi up and running again try the following commands one by one:

sh:grub>set root=(loop0)
sh:grub>linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro
sh:grub>initrd /boot/initrd.img-2.6.31-14-generic
sh:grub>boot

If that helps wubi to start, open terminal and execute:

sudo update-grub2

That should sort out the sh:grub problem.
Hi,
I am having the same problem with Grub2. I also got the same Prompt as the other user. So I started following your intruction. But After I type the first line  i.e. set root=(loop0) i get the following error :
**error: not an assignment.**
then I thought when it does not work, i type directly your seocnd line. I typed it but now comes the foolowing error:
**unknown command linux/boot/vmlinuz-2**
 
**Please help.**

---

### Post by meierfra. on 2010-01-10
xairoy: If you are using Wubi, boot into Windows and try this solution from Agostino Russo  (the man in charge of wubi)

[https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210]("https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210")

---

### Post by thehallofshields on 2010-05-14
> **adaucourt said:**
> paste the output of this command from the grub prompt:
```
ls
```

Alright, so I've got the same problem, but when I type ls I just get:

(hd0) (hd0,1) (hd1) (hd1,1)

but I was just getting:

(hd0) (hd0,1) a few minutes ago.

I'm very green and I need to get my computer back and running tonight!

Could anyone give me some commands?

Running Grub 1.97beta4 and an up-to-date Wubi, not sure which version.

---

### Post by thehallofshields on 2010-05-14
Alright, so I really really want to use this fix rather than the wubildr file replacement since my Windows install is also corrupt and my laptop is not taking a boot disc.

but,
[B]
I don't seem to have a /boot

sh:grub>ls /boot
error:file not found

and I don't seem to have a loop

sh:grub> ls
(hd0) (hd0,1)[/B]

I hate to be a sad story; but I have 2 term papers for my college major that were due yesterday, and I don't have time to order an adapter to pull the documents off my hard drive. Please HELP!

---

