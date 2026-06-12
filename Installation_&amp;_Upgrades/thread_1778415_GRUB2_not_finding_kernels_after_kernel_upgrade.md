---
title: "GRUB2 not finding kernels after kernel upgrade"
date: 2011-06-09
forum: Installation &amp; Upgrades
---

### Post by JedMeister on 2011-06-09
I have been using Ubuntu for some time now and obviously I've been a bit blase.

I have recently installed the Maverick backport kernel (2.6.35 - from the lucid-updates/main repo) and while I was at it I also manually (through synaptic) got rid of some old kernels. I made sure that I kept the current Lucid kernel though (that was working fine). All seemed well (although I didn't actually check - just no errors) so I rebooted.

On reboot I have lost all my Ubuntu kernel options!

I rebooted with a live cd, mounted, etc and ran ```
sudo update-grub
``` but it doesn't seem to find any kernels!

I have searched and tried everything I can think of and finding no answers.
Things I've tried
[LIST]
[*]Reinstalling GRUB: ```
grub-install --recheck --root-directory=/media/mnt /dev/sda
```
[*]Checked /boot to see if the kernels are there:
```
jed@lightning:/boot$ ls
abi-2.6.32-31-generic         memtest86+.bin
abi-2.6.32-32-generic         System.map-2.6.32-31-generic
abi-2.6.35-25-generic         System.map-2.6.32-32-generic
burg                          System.map-2.6.35-25-generic
config-2.6.32-31-generic      vmcoreinfo-2.6.32-31-generic
config-2.6.32-32-generic      vmcoreinfo-2.6.32-32-generic
config-2.6.35-25-generic      vmcoreinfo-2.6.35-25-generic
grub                          vmlinuz-2.6.32-31-generic
initrd.img-2.6.32-31-generic  vmlinuz-2.6.32-32-generic
initrd.img-2.6.32-32-generic  vmlinuz-2.6.35-25-generic
initrd.img-2.6.35-25-generic
```
[*]Even reinstalled burg (used to use it but it got broken by a kernel update long ago and never bothered to fix it as I only use Linux these days anyway)
[/LIST]
Funny thing is that BURG finds the kernels and reports no problem, but then drops to the grub-error prompt on boot.

Can somebody please help out??

---

### Post by Rubi1200 on 2011-06-09
Hi,
use a LiveCD to download and run the boot info script. There is a link at the bottom of my post with instructions.

Hopefully, the results will shed some light on what is going on with the system.

Thanks.

---

### Post by JedMeister on 2011-06-09
Hi Rubi1200,

Thanks heaps for your quick & helpful reply. I'm at work at the moment and probably won't get a chance to do this until a bit later but I'll post back when I have the required info.

Cheers!

---

### Post by Rubi1200 on 2011-06-09
No problem, I will keep an eye on the thread and return once you have posted the information.

Thanks.

---

### Post by TBABill on 2011-06-09
For future reference, I would NEVER remove older kernels at the same time I install new ones. You could, as you have found, find yourself completely without a machine until you figure out the fix. New kernels do not always perform properly on all machines so it's imperative that you always have a known working kernel available to boot back into in the event something goes awry. I'm sure you know this now, but for anyone who searches and finds this thread in the future, perhaps it will save future heartache.
 
Sorry for the bad luck you encountered. I did the same thing in the past and found out the hard way how important my current and older kernels can be during the addition of a new kernel. It takes me a few extra minutes when I do it, but I install, verify, delete, verify. Pain in the rear, but worth it in the end.

---

### Post by JedMeister on 2011-06-09
@Rubi1200 - Thanks again - Please find attached my RESULTS.txt file from the boot info script. I was going to just post it but it's pretty long so thought it better to upload, hope that's ok. Very handy script! But on my brief perusal of it everything seems in order (although not sure about the code bits - quite possible missed something there). The only thing that did seem a little odd was that the new kernel (2.6.35) doesn't seem to get a mention!? Setrange...

Also for the record the only Ubuntu live CD I have (9.10) decided it didn't want to load anymore (I think my CD drive is on it's way out too which I'm sure wasn't helping). So I used a copy of [SystemRescueCD]("http://www.sysresccd.org/Main_Page") which I had laying around and booted into my existing install (I think it loads the kernel off the CD and auto mounts the rest of the system off the HDD). The video drivers aren't loaded but otherwise looks and acts like my system. For completeness I quickly went through the actions I had already taken to see if that changed anything, it didn't...

@TBABill - Yep, must say that's crossed my mind too! :) Like I said in my first post, I think I was a bit blase - obviously too comfortable with Linux and not careful enough! I thought leaving the last 2 working kernels would be sufficient, but perhaps not... TBH though I'm inclined to think that this may be a result of the new kernel install rather than the removal of the old ones.

Actually that reminds me (something I didn't put in my intial post) I have also tried a reinstall of the kernel that was working previous to all this and it said it was already at the latest version... I then forced it to reinstall, made no difference...

Anyway I'm off to bed now (just home from night shift).

Thanks again.

---

### Post by oldfred on 2011-06-09
I do not know much about burg other than it adds a level of complication. Do you get a burg menu or a grub menu when you boot?

Can you boot with the version that grub is showing?
Linux 2.6.35-25-generic

Sometimes with the updates to a new kernel the old version are not compatible enough to still work.

If not I would follow the procedure to uninstall and reinstall grub2 from drs305.
chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Because of burg these standard reinstalls may not work:
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
Grub2 info & full chroot version - see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by JedMeister on 2011-06-09
Hey oldfred, thanks for the input. 

Let me clarify. I can boot with either.

If I get in with the rescue CD (effectively a live CD chroot of my system) and update burg (update-burg blah blah - what used to make it boot with burg) it finds all the kernels and reports no error, but when I try to boot it crashes to a grub prompt (but with no listed error). 

If I do the same with grub (update-grub blah blah - what used to make it boot with grub2) it doesn't find any kernels (just memtest and my old XP partition) but still reports no error. When I boot, grub loads fine but gives me no option to boot into Linux (just memtest or XP).

If I reinstall grub then it again reports no errors but still doesn't pick up any of the kernels.

Thanks for your links. I will try removing grub with apt-get and reinstalling. I think thats certainly worth a try. But I've got stuff I need to go do at the mo. When I get back I will try it and report back. Thanks again.

---

### Post by JedMeister on 2011-06-10
Excellent work people. Problem solved! Yay!

Purging and reinstalling Grub2 did the trick. Obviously there was something corrupt in the settings somewhere. To tidy up I got rid of Burg too. Thinking back I think it may have been a combination of something I did a long time ago and installing the new backported kernel. I can't remember how I did it but I recall changing something so only the latest kernel showed up in the Grub menu and I think that may have caused the problem when I installed a completely new kernel.

As it turned out that wasn't quite the end of my problems. So for completeness I will add further info in case someone else does a similar thing and is looking for an answer to that. 

The old kernel worked ok, but the new kernel was having troubles loading the nVidia drivers and errorred when I tried to reinstall them. To resolve this I added the updated X.org and video driver update PPA and updated all my nVidia drivers (which included a new driver v270.x from memory). ```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates && sudo apt-get update && sudo apt-get upgrade && apt-get dist-upgrade
``` That was almost it but when setting monitor config it couldn't save the settings. Normally nVidia-settings will ask for the password when changing settings but for some reason it wasn't. Starting from the terminal with gksudo nvivia-settings solved this issue too.

So long story short: All fixed. Thanks everyone for your input and ideas.

---

### Post by Rubi1200 on 2011-06-10
Great news :-)

Glad you got it sorted out.

---

