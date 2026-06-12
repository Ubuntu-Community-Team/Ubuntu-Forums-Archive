---
title: "kernel panic: not syncing: unable to mount root fs"
date: 2007-10-15
forum: Installation &amp; Upgrades
---

### Post by jimbo99 on 2007-10-15
Luckily I didn't do this om my main machine.  If I had I'd be in deep **** as I use it for everything.

We should be praising that as any time we can do all our work on Linux the better.

Anyway, I choose to test out the new soon to be released Ubuntu 7.10.  I had done an upgrade on this from 6.10 when Feisty came out.  Before doing the update via "update-manager -d" I had to do some updates just to get the update manager to give me the option to do the upgrade.

This machine had been my main machine for a long time and I had it customized.  I had been using it as a file server for the most part but the role is not all that important to me currently.  So, I didn't feel too bad about doing the update even if it bricked my install--which it did.

After doing the update-manager -d it did the processing, gave me the estimated amount of time, and then proceeded.  During this it told me it would take at times 6 hours, somtimes 7, sometimes more.

I found that periodically it would stop, telling me the cups system or the other couldn't be updated.  Since that is the printing subsystem and I wasn't alarmed.  But it kept stopping the update instead of  just continuing.  So, that 6 or 7 hours turned into MANY more.

I'd say the stopping was the only thing that pisses me off.  This should not stop like that and certainly not repeatedly on the same issue.

After it finally finished and I rebooted the computer when it came back I got the message (roughly written out):

kernel panic: not synching VFS: Unable to mount root fs on unknown...."

That's the end of my ability to use that workstation for the time being until this is resolved for someone can give me a hint on how to resolve it.  Otherwise I guess I'll mount the hdd in another computer, back up the files, and then wipe and reinstall.  I didn't want to do that because the ubuntu default desktop configuration and virtually everything else is sort of cheap looking.  It just means many additional hours to recustomize the whole desktop.

Maybe it'll be worth it. 

Frankly, though these guys should have been double checking the set up and stopped the installer and reverted back if there was going to be this kind of issue.  No one likes to have their machine bricked.

Anyway, for the time being, any hints on how to resolve this quickly and simply would be appreciated.

---

### Post by chrism66 on 2007-10-18
Did you try booting from an older kernel? I am getting the same message and I have too boot from 2.6.20-16-generic, none of the 2.6.22-^^ kernels will work for me.

---

### Post by hackmeister on 2007-10-18
Ditto on the new kernel. Old one works fine.

---

### Post by Fraoch on 2007-10-18
I've had the same exact experience:

[http://ubuntuforums.org/showthread.php?t=579608](http://ubuntuforums.org/showthread.php?t=579608)

I can only boot into the recovery mode on an older kernel.  I can't get a GUI anymore on any kernel and I can't get into even recovery mode with the new kernel, with that "unable to mount root fs" error you noted.

Like you - good thing I did this on a spare machine first!  I won't be touching my main 7.04 machine for some time now.  I'll give it a month or two.

---

### Post by erjohan on 2007-10-19
I a similar problem and I found out that I was missing an initrd line in /etc/grub/menu.lst.. 
I also had problems with getting lvm to start, which was fixed with a custom boot script doing lvchange -a y MY-LOGICALVOLUME-NAME, running before S30checkfs.

Not sure how that happened, but I gues I ****** up the end of my install where all the kernel config is..

---

### Post by VSpike on 2007-10-19
I have the same problem. I can boot into 2.6.20 but but 2.6.22 gives me the VFS root partition errors, both for normal and recovery mode.  I also ended up with a mysterious extra 2.6.20 kernel in my grub menu that didn't actually exist, but running an update-grub got rid of it.

I also have the problem that I can't start X with the nVidia drivers... may have to fall back to nv driver to get things working.

I wish I had tried this on a spare machine, but I don't have one!  I should have dual booted I guess.  Oh well, sometimes you have to learn by (bad) experience.

---

### Post by VSpike on 2007-10-19
I actually found a fix for this.  You need to add **ide1=noprobe ide2=noprobe** to the grub boot line for the affected kernels.

The way I did this was to add a new line in /boot/grub/menu.lst copying my existing kopt but adding the new options for the 2.6.22 series kernels.

```
# kopt=root=UUID=e0e888e9-3e87-4382-ad3a-5aa9331cb228 ro nosplash
# kopt_2_6_22=root=UUID=e0e888e9-3e87-4382-ad3a-5aa9331cb228 ro ide1=noprobe ide2=noprobe nosplash
```

This at least makes the system boot - hopefully it's not causing FS corruption behind the scenes!  Now I just have to fix all the other problems.

---

### Post by chrism66 on 2007-10-20
setting[COLOR="Green"] **ide1=noprobe ide2=noprobe **[/COLOR] did not work for me still getting the Kerenel panic

---

### Post by VSpike on 2007-10-20
I forgot to add that you need to run "sudo update-grub" after this, to rebuild the menu.  The other option of course is to add the parameters directly to the kernel boot entries, but then they will get deleted next time the kernel is updated.

Also, if you don't use UUID's to mount your hard drives, this will cause you problems as device names will change.

---

### Post by zveroboy on 2007-10-25
I've also experienced the same error after doing the network upgrade from 7.04 to 7.10.  As we most of you I could only boot to the older kernel (2.6.20-16-386).  

To make the story short I'll get right to the point and provide any details upon request.

In menu.lst file I noticed that the only menu option that has initrd entry in it is the one for the older kernel.  So I added corresponding initrd entry to the 2.6.22-14-386 and 2.6.22-14-generic kernels.  Then rebooted the system and was able to boot with the newer kernel.

I also had to re-add a menu entry for Windows XP ( for dual booting), as this entry was removed by the upgrade procedure.  

I hope this helps and let me know if you need any more details. :)

Good luck.

---

### Post by kyspaceranger on 2007-10-28
zveroboy, I realize it's a lot to ask, but could you post more details?  This seems to be a very common issue with 7.10 and a lot of people could really use the step-by-step version of how to fix the problem.  I know I could.  Right now I can't do anything with my laptop.  Won't boot to live cd's, won't boot to the hard drive, can't wipe the hard drive b/c I can't boot to live cd's . . . it's a mess!

Frankly, I'd like to try your method, but I need help.  Basic beginner kind of help.  I've been running Ubuntu for a year and this is the first real problem I've ever had.

Thanks

---

### Post by chrism66 on 2007-10-29
I think my problem has been found it has to do with update-initramfs producing unbootable images.
[URL="https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/151132"]
Here is a link to the bug report:[/URL] I think I will just have to wait and see. I have to say Gutsy is a real dud but I am stuck with it until the end of the quarter in December. I hate to admit it but I have been using my windows mainly as Gutsy is just plain unstable on my machine.

---

### Post by zveroboy on 2007-11-06
Chrism66, I guess I'll attach my menu.lst file.  Keep in mind that in my case both Ubuntu 7.10 and WindowsXP share RAID0 set, so initially (when I had installed 7.04) I followed instructions on this page: [https://help.ubuntu.com/community/FakeRaidHowto#head-b927d0f65cd0bda00341578088b2c605f71b421a](https://help.ubuntu.com/community/FakeRaidHowto#head-b927d0f65cd0bda00341578088b2c605f71b421a)
Take a look at the page, for explainations of various entries in the menu.lst file.

I was able to boot from live CD as well as to an older kernel, so your problem is more fundemental and it has to be dealt with first.  I am quite confused on why you can't boot from live cd.  What kind of errors are you getting?

I hope it helps.  And I appologize for not replying earlier.  Let me know if have any other specific questions.

---

### Post by chrism66 on 2007-11-06
Zveroboy,

 Thanks for the reply. I am going to go over the info.

As for the live CD I get no messages period, I get too the boot menu and it locks up. Oh well...

Chris

---

### Post by zveroboy on 2007-11-07
Chris,

In the effort to see what is going wrong with the live cd, try (If you even can get this far) pressing F6 (I believe), which brings up an actual command.  At the end of this command there are two options 'quiet' and 'splash'.  Remove them, so that you can possibly/hopefuly determine where the boot process gets stuck.  Leave the two '--' at the end.  I am not quite sure what they are for, so I just leave them there.  
I also have reading that adding *noapic* option worked for may to get live cds to boot.

As a side note, recently I was messing around with an older PC trying to install Ubuntu on it, and when I enable USB legacy support in BIOS, it, too, was getting stuck on trying to boot live CD.

By the way, don't give up - the solution will present itself :).  Computers suck (but that's another topic) :lolflag:

---

