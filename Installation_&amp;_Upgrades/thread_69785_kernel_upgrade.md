---
title: "kernel upgrade"
date: 2005-09-27
forum: Installation &amp; Upgrades
---

### Post by raven on 2005-09-27
I have this linux-image 2.6.10-5-386 and linux-image-386 packages
in synaptic look at the attachement
I have 2 other packages linux-image 2.6.10-5-686 and linux-image-686
can somebody explains what the difference between those 2 packages ?
and if it's advisable to upgrade ?
if yes
how can I do it step by step without borking my box
I have a PIII 450
thanx

---

### Post by YourSurrogateGod on 2005-09-27
686 is specifically for the newer intel architecture, imo, it would make sense to upgrade if you over 1 gigabyte of ram (since the 386 kernel does not recognize ram beyond 900 megs.)

---

### Post by raven on 2005-09-27
[QUOTE=YourSurrogateGod]686 is specifically for the newer intel architecture, imo, it would make sense to upgrade if you over 1 gigabyte of ram (since the 386 kernel does not recognize ram beyond 900 megs.)[/QUOTE]

Thanx for the reply
any benefit in speed ?
if you look at the attachement above in the first thread
do I remove first the installed packages 386, than install the 686
or I install the 686 packages reboot than remove the 386 ??
can you tell me the safe way to do it ???

---

### Post by 23meg on 2005-09-27
it's best to install 686, reboot, make sure your system is ok with it, and then remove 386.

---

### Post by YourSurrogateGod on 2005-09-27
[QUOTE=raven]Thanx for the reply
any benefit in speed ?
if you look at the attachement above in the first thread
do I remove first the installed packages 386, than install the 686
or I install the 686 packages reboot than remove the 386 ??
can you tell me the safe way to do it ???[/QUOTE]
I honestly don't know. I'd suggest trying to install 686 first and then uninstalling 386 (if that isn't done automatically.)

Again, not sure about this. You can always wait until someone else gives a more satisfactory response...

---

### Post by Emerzen on 2005-09-27
Hey as the previous thread stated 686 kernel's are for newer architecture and greater RAM.

386< 1GB of RAM
686 for > 1Gb of RAM

x86-smp if you have Hyperthreading (intel) or Hypertransport (AMD) OR a dual core processor

If you have a processor w/ HT, to enable that function you have to add the -SMP part of the kernel as well.  For example, and Intel P IV w/ HT and >1 GB of RAM would function well w/ Linux-686-smp kernel.

You do NOT need to uninstall old kernel's before adding new ones.  Add the kernel of your desire, then when GRUB boots up, there should automatically be an option to boot w/ the new kernel, or the old one depending on your choice.   For example, when I boot and GRUB appears I have several options: 386, 386 recovery mode, 686-smp (old and new versions), and 686 recovery mode (and, sigh, Windows XP).  Boot into whatever kernel your heart desires.  

Finally, if you're running Breezy, you can change GRUB settings w/ a GUI tool under Admin>BOOT.  You can add items to your boot menu, i.e. Windows on another partition, and change which boots automatically, and time to wait for boot.  But if you install kernel's via synaptic, this will be done automatically for you and you do not need to edit GRUB.

---

### Post by YourSurrogateGod on 2005-09-27
[QUOTE=Emerzen]Hey as the previous thread stated 686 kernel's are for newer architecture and greater RAM.

386< 1GB of RAM
686 for > 1Gb of RAM

x86-smp if you have Hyperthreading (intel) or Hypertransport (AMD) OR a dual core processor

If you have a processor w/ HT, to enable that function you have to add the -SMP part of the kernel as well.  For example, and Intel P IV w/ HT and >1 GB of RAM would function well w/ Linux-686-smp kernel.

You do NOT need to uninstall old kernel's before adding new ones.  Add the kernel of your desire, then when GRUB boots up, there should automatically be an option to boot w/ the new kernel, or the old one depending on your choice.   For example, when I boot and GRUB appears I have several options: 386, 386 recovery mode, 686-smp (old and new versions), and 686 recovery mode (and, sigh, Windows XP).  Boot into whatever kernel your heart desires.  

Finally, if you're running Breezy, you can change GRUB settings w/ a GUI tool under Admin>BOOT.  You can add items to your boot menu, i.e. Windows on another partition, and change which boots automatically, and time to wait for boot.  But if you install kernel's via synaptic, this will be done automatically for you and you do not need to edit GRUB.[/QUOTE]
Just curious, but does the newer kernel provide some other improvements? I heard that apps that are made for the later 686 architectures are sometimes faster because they utilize some registers that the 386 kernels doesn't.

---

### Post by Emerzen on 2005-09-27
There is only one place where I notice considerable improvement and that's when I'm doing video work, especially, if I want to multi-task while I've got some video conversion in the background.  I have 2GB of RAM so 686 is a necessity to utilize it.  If I edit video w/ a 386 kernel my CPU is at 100% full time when it's cooking, w/ 686-smp I get considerable CPU breathing room (I have a PIV w/ HT so it's not truly dual core but the kernel looks at it that way).  I guess gaming would benefit as well, but I'm not into that so I don't know directly.

---

### Post by raven on 2005-09-27
[QUOTE=Emerzen]There is only one place where I notice considerable improvement and that's when I'm doing video work, especially, if I want to multi-task while I've got some video conversion in the background.  I have 2GB of RAM so 686 is a necessity to utilize it.  If I edit video w/ a 386 kernel my CPU is at 100% full time when it's cooking, w/ 686-smp I get considerable CPU breathing room (I have a PIV w/ HT so it's not truly dual core but the kernel looks at it that way).  I guess gaming would benefit as well, but I'm not into that so I don't know directly.[/QUOTE]

I have PIII450 512 ram
in your analogy I should not need to upgrade BUT
in a way there is no harm if you upgrade, I mean if it does not benefit you
for sure it will not harm linux installation
am I right ???

---

### Post by Emerzen on 2005-09-28
The best option for you would be the vanilla 386 kernel.  The 386 kernel is very capable of handling a PIII w/ 512MB of RAM.  

I like to think in terms of risks vs. benefits.  There will be virtually no benefit, I know of, in trying a 686 kernel or to add smp support with your hardware.  Their is a risk though that trying a 686 kernel will bork something or simply not work, although I think it's highly unlikely.  Most likely a 686 kernel will install and boot for you no problem, or install and not boot but it's unlikely to do any harm (though possible).  

Keep in mind, if you do upgrade your hardware someday, that you can then use both 686 (optimized) or 386 kernels, and I know that configuration works well.  One more thing, don't think of 686-kernel as an updated 386.  New, updated 386 kernels come out all the time, 386 vs 686 is a hardware difference.  Hope that helps.

---

### Post by raven on 2005-09-28
excellent, it did help
thanx

---

