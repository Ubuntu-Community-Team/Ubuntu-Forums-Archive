---
title: "Samsung r700 installation problems."
date: 2008-07-09
forum: Installation &amp; Upgrades
---

### Post by myprip on 2008-07-09
So, I have this shiny new Samsung r700 aa01.
Sadly, good old ubuntu fails to even boot. It just hangs at 1/3 of the boot process. I tried to boot with the "nosplash" option, to see if I could read something useful about the error, but I see nothing interesting.

It seems from a quick search that people have installed ubuntu successfully on this laptop, without problems of this sort.

I tried both the 64bit and the 32 bit version, just for completeness. The behaviour is the same. I also tried to install it "on windows", as the autostart menu says. And, again, it hangs during the boot.

I hope someone gives me some indication. Thanks.
Could this be a problem of the last version? (8.04.1)

---

### Post by myprip on 2008-07-09
I must add that I correctly checked the md5sum of both the iso images.

---

### Post by avtolle on 2008-07-09
Did you also do the CD verification after burning (option 4 from the menu when you first boot) to be sure the burn was good? I've found that burning the image at a slow speed (4x) works for me every time, using a CD-R (I've some older hardware).

---

### Post by myprip on 2008-07-09
Yes, I did that on the 64 bit version, and I got no errors.
I burned the cd at 20x. Should I try to burn it at a lower speed, or from another computer? Or would that be a waste of time.

---

### Post by avtolle on 2008-07-09
I'd try it at a slower speed. Sometimes CD drives can be a bit finicky. If that doesn't seem to solve the problem, you might want to look again at the threads you have found about installing on the type of computer you have to see whether any boot parameters were needed to get the job done, making sure, of course, that the poster had (as nearly as you can tell) the same hardware that you have.

---

### Post by myprip on 2008-07-09
Well. Now I can definitely say that it's a software problem.
The failure behaviour is the same.
Here are the last four printed lines when booting without "quiet" and with "nosplash".

input: sleep button (cm) as /devices/virtual/input/input8
ACPI: sleep button (cm) [SLPB]
ACPI: battery slot [bat1] (battery present)
ACPI: AC adapter [adp1] (on-line)

As I said, not very insightful. But maybe we can say that it hangs because of ACPI problems, or the thing that would come right after.

I just can't find information on someone that installed ubuntu on this laptop, if not for some function button problems.

Should I report a bug or a feature request?
I'm afraid I don't have sufficiently detailed information.

---

### Post by myprip on 2008-07-09
In a desperate attempt to install a useful operating system on that laptop, I tried debian testing. And I found that (after having installed it) it also hangs at boot. With the exact same lines as before as the last one printed. So, it must be some kind of awful acpi problem.

---

### Post by myprip on 2008-07-09
Those lovely developers have resolved this issue on the .26 kernel (it appeared after .22):
[http://bugzilla.kernel.org/show_bug.cgi?id=10448](http://bugzilla.kernel.org/show_bug.cgi?id=10448)

So, I can only install Gutsy, or wait for the .26 kernel to arrive on Hardy.

Sorry for the storm of posts.



____
EDIT

Ok, so the trick is to boot from grub (hardy is ok) with options "acpi=off noapic"
Then, on the live, install ubuntu, and add "blacklist video" in /etc/modprobe.d/blacklist

Next reboot and it should work. (got some problems with gnome, but hey!)

---

### Post by deadreaper on 2008-11-26
OK I had the same Promlem described here, solved it using acpi=off while setup and adding it to /boot/grub/menue.lst but after that i had no posibility to get the energy funktions working, especially i could not see the battery charge. Everything else worked just fine.

So I tryed to use APM instead of ACPI but I haven't got it to run.
Havn't found the Module and couldn't buld it because missing kernel sources.

So I have blacklisted the Video module as described in the last post, this works so I can see the battery charge, but now the display is continualy changing its brightness, and I can't use fn + UP/DOWN to regulate the brightness.

So this is not the best solution for me.

---

### Post by ingie on 2008-12-22
hi,

has anyone come up with a good* workaround for this, as i'm going to be installing [or was planning to do so] hardy onto a new shiny samsung r700 next week [once it arrives]

i.e. is there a tested way via the described above disabling of the acpi during boot to then apply the rc3 kernel which supposedly addresses the issue. and then re-enabling acpi?

or would i be better off waiting for the rc3 kernel to be released fully and then disable acpi, update the kernel normally, and re-enable acpi afterwards?


* and by "good" i mean - a workaround a layman can understand [i'm not a layman but i never see the purpose in making the obscure more obscure as the next person finding this thread may not be as technical as i]

---

### Post by titato on 2008-12-24
i have the same problem with a samsung r610as02. Booting only with acpi=off.
Then when using Fn+whatever functionkey reboots the laptop..i was not very amused since i deleted all the existing partitions including the recovery partition...

After trying a lot of "solutions" i found out ubuntu is not ready yet for my shiny new samsung. So i tried to reinstall with WindowsXP, well then i found out that WinXp too is not ready for my laptop. And im sure not going back to vista.

Not sure what to do.. anyone?

---

### Post by titato on 2008-12-30
I found a kernel parameter which works better for me.
instead of acpi=off i now use mem=4096M.
Battery indicator works, no reboots on functionkeys, there are even functionkeys which are working like they suposed to.

Downside is that not all of my 4GB RAM is found.

---

### Post by deadreaper on 2009-01-16
OK I'll try to post a little workaround, but beware after that you can't change the brightness of your screen. But that is OK for me.

[LIST]
[*]On Setup use the Option ACPI=off to boot the Live Disk

[*]Normally Install your System

[*]On FIRST boot use the Boot Setting ACPI=off again
[LIST]
[*]To do so run grub and press 'e' to edit your boot entry.
[*]Select the boot parameters and press 'e' again.
[*]Now append "acpi=off" to the line. (Without the ")
[*]Boot the temporary modified entry by Pressing 'b'. 
[/LIST]

[*]While you have access to your System blacklist the Video module
[LIST]
[*]To do so append the line "blacklist video" to your "/etc/modprobe.d/blacklist". 
[*]I recommend to add a comment line that describes why you are Blacklisting the video module. 
For instance "# Workaround for ACPI problems".
[*] Comment lines have to begin with a #.
[/LIST]

[*] The next time you'll reboot your system you schould have ACPI working
[/LIST]

:guitar:

---

