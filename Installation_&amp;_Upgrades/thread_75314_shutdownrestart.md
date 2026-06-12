---
title: "shutdown/restart"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by withoutclass on 2005-10-13
For some reason with ubuntu there is a problem with being unable to fully shutdown/restart.

when i do restart, everything acts normally till it gets to the restarting phase, where it just locks up.

when i shutdown, everything in the system is turned off as normal, except that my laptop does not power down.

Please help

---

### Post by aysiu on 2005-10-13
Does it act any differently if you shutdown or reboot from console? ```
sudo shutdown -h now
``` ```
sudo reboot
```

---

### Post by withoutclass on 2005-10-13
[QUOTE=aysiu]Does it act any differently if you shutdown or reboot from console? ```
sudo shutdown -h now
``` ```
sudo reboot
```[/QUOTE]

the console reboot works perfectly

and console shutdown kills the system and spits out a power down message without going completely off.  I'm not sure if thats normal to this OS or not, since I'm new to it and have only been using it for a week now

---

### Post by aysiu on 2005-10-13
[QUOTE=withoutclass]the console reboot works perfectly

and console shutdown kills the system and spits out a power down message without going completely off.  I'm not sure if thats normal to this OS or not, since I'm new to it and have only been using it for a week now[/QUOTE] Unfortunately, all this means is that you're able to shutdown and reboot perfectly from console and not through GUI. I don't know how to solve this. Anyone else know what the problem could be?

---

### Post by withoutclass on 2005-10-13
[QUOTE=aysiu]Unfortunately, all this means is that you're able to shutdown and reboot perfectly from console and not through GUI. I don't know how to solve this. Anyone else know what the problem could be?[/QUOTE]


oof, after installing some updates, the console reboot does not work properly either :confused:

---

### Post by withoutclass on 2005-10-16
I'm still having this problem, going to bump the thread so as to avoid multiple posting

---

### Post by abstractone on 2005-10-22
I can confirm the bug. On my laptop Sony Vaio VGN-A115 shutdown and reboot do not complete. All services are shut down, but the computer stays on. However hybernating seems to do a successful shutdown at the end.

I have used earlier Ubuntu 4.10 Warty and it worked perfectly.

---

### Post by withoutclass on 2005-10-22
[QUOTE=abstractone]I can confirm the bug. On my laptop Sony Vaio VGN-A115 shutdown and reboot do not complete. All services are shut down, but the computer stays on. However hybernating seems to do a successful shutdown at the end.

I have used earlier Ubuntu 4.10 Warty and it worked perfectly.[/QUOTE]

yes, this is on my laptop too, i have an asus with a centrino chip set.  Everyone else I know that has tried it has a desktop and they never have issues.  This is what ultimately led me away from ubuntu, everything else worked amazingly.

---

### Post by abstractone on 2005-10-22
[QUOTE=withoutclass]yes, this is on my laptop too, i have an asus with a centrino chip set.  Everyone else I know that has tried it has a desktop and they never have issues.  This is what ultimately led me away from ubuntu, everything else worked amazingly.[/QUOTE]
I will let you know if something has been done to fix the problem. Ubuntu is great distribution with great community and things like that should be possible to be fixed. I found one more person having the same problem on laptop. Seems it appears only on laptops.

---

### Post by withoutclass on 2005-10-22
[QUOTE=abstractone]I will let you know if something has been done to fix the problem. Ubuntu is great distribution with great community and things like that should be possible to be fixed. I found one more person having the same problem on laptop. Seems it appears only on laptops.[/QUOTE]

I just spent the last 3-4 days installing gentoo ;)

---

### Post by ouminan on 2005-10-23
I'm using a Toshiba Satellite M55, also on a Centrino platform.

I'm experiencing the same issues where reboot works fine and shutdown never actually powers down the machine.

---

### Post by Apostata on 2005-10-25
Having the same problem here on my desktop, using Kubuntu 5.10 - I even reinstalled to troubleshoot.

As far as I can tell, everything's fine until I process the updates w/Adept after a fresh install.  After that, whenever I reboot/restart it shuts down cold.

This *has* to be a bug in one of the updated files.

Keep this thread alive...

---

### Post by withoutclass on 2005-10-25
maybe it should be made sticky, so that when a fix is put out it gets updated/people realize that its a somewhat prevalent bug

---

### Post by Apostata on 2005-10-25
in the meantime, we should all try to rate this thread highly (and bump for attention)

---

### Post by santo on 2005-10-27
Having the same problem (hangs on "[4320234.374000] Restarting system.")
with Ubuntu v5.10 (Breezy) running inside a vmware

VMWare is a GSX Server v3.2.0 on a Windows Server 2003 Enterprise host.

Other Linux distributions running on that same host do reboot successfully.

---

### Post by GoldBuggie on 2005-10-27
I have also found this bug to be true. Can't be sure what the problem is, but I did find that my laptop hang on some shutting down service that I didn't start up. So I changed some things in bootupmanager and it seems to work at this moment. Can't be sure if this is the problem since I haven't tested this for longer then a week.

---

### Post by Lameduck on 2005-10-27
Hi I am a newbie in Linux & Ubuntu.
I just installed 5.10 in VMware & can logon successfully.
But how to logoff in GUI?

Thanks!

---

### Post by withoutclass on 2005-10-27
[QUOTE=Lameduck]Hi I am a newbie in Linux & Ubuntu.
I just installed 5.10 in VMware & can logon successfully.
But how to logoff in GUI?

Thanks![/QUOTE]


menu, logout

---

### Post by daahli on 2005-10-28
I just want to add, that I also have a similar problem. 

Rebooting works fine here, but my computer refuses to power down completely. I also can't switch from X to any of the console modes, because doing turns off my screen. Could the problem have to do with my graphics card? I'm running a X700 with fglrx drivers installed.

---

### Post by withoutclass on 2005-10-28
i have an ATI also, could it be that ubuntu has trouble with ATI cards?  and not centrino chipsets?

i urge those with the shutdown/restart problem to post again with the kinds of specs and maybe we can narrow it down better?

---

### Post by daahli on 2005-10-28
can you at least switch from X to console? I don't think it is a centrino problem, I have a custom built AMD64 desktop, nforce4 Ultra chipset.

---

### Post by withoutclass on 2005-10-28
u can use ctrl+alt+backspace to kill X server, but, generally it just restarts X

you can in fact use the normal terminal

---

### Post by steve1401 on 2005-11-01
Not read through the full thread here, so appologies if this has allready been resolved. If not this should do the job;

sudo vi /boot/grub/menu.lst

Change the following section
---
title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot
---

To this 

---
title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro **noapic nolapic** quiet splash
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot
---

Note the addition of the noapic nolapic - this is an option in the initial install, but can be passed at boot in this fashion (exactly the same thing actually)

Reboot and of you go...

Cheers
Steve

---

### Post by Lameduck on 2005-11-02
[QUOTE=withoutclass]menu, logout[/QUOTE]
Thanks a lot!
To make it clear - as it shows on my ubuntu GUI - System (shown on tool bar), logout.

---

### Post by f76 on 2005-11-03
Having the same problem with stationary computer as stated in sig. Wont shutdown/boot from gui. Booting/shutdown from login screen (ctrl+alt+backspace) works fine. As a matter of fact i dont get the shutdown/reboot window when klicking the exit icon. I will try the config/command line tips from this thread...

---

### Post by Limulus on 2005-11-03
[QUOTE=steve1401]Not read through the full thread here, so appologies if this has allready been resolved. If not this should do the job[/QUOTE]

I use a Toshiba Satellite A25 and I've been having problems rebooting in Breezy since (or shortly after) I upgraded (I upgraded to Colony 4 and then used the repositories; I didn't have this problem in Hoary, but I figured it would go away by the time the final release came around).  I don't however have any problem shutting down (that works fine).  When I try to reboot, it gets to the end:

Unmounting local filesystems...
unmount tmpfs busy - remounted read-only

(the same message as for shutdown) but then it just stops there.  I tried the "noapic nolapic" fix, but it didn't work :(  Any further suggestions, or is this like a kernel bug or some such that won't be fixed for a while?

---

### Post by NikoC on 2005-11-03
Same problem over here on Sony Vaio Vgn-s4hp/b notebook and Breezy: System won't shut down completely. Anyone tried compiling the new kernel version?

---

### Post by rolando on 2005-11-03
I too am having shutdown and reboot problems as described previously

I have a IBM A22m laptop with an ATI graphics card, with warty and hoary previously installed.

Maybe update will be here soon..

Shame :(

---

### Post by Apostata on 2005-11-05
bump

---

### Post by aev on 2005-11-06
Has anyone tried to hybernate and then restore work successfully?

I press hybernate button and the comp just falls asleep with no full shutdown. I have to restart with the power button.

---

### Post by souki on 2005-11-07
I'm having the same problem on a sony vaio a517b

shutdown from gnome: OK
reboot from gnome: hang
reboot from console: hang
hibernate from gnome: OK

I've tried the "noapic nolapic" options without success

there is a similar thread [here]("http://ubuntuforums.org/showthread.php?t=85379")

---

### Post by Sebby on 2005-11-13
I've been having these problems too on a clean install of Ubuntu. Searching made me come across this thread. Hopefully they'll be a resolution soon.

---

### Post by ploosh on 2005-11-15
I'm getting the same error. 
>  Unmounting local filesystems...
unmount tmpfs busy - remounted read-only Because this is a dual boot system, I'm wondering if the problem may have something to do with the hda1 (windows partition) or my fat32 partition that acts as shared drive space for both os's?

Permissions for hda1 are: dr-x------
Permissions for hda4 are: drwxr-xr-x

Not sure if the drives are related to the problem or not.
Thanks for any help.

---

### Post by souki on 2005-11-15
[QUOTE=ploosh]I'm getting the same error. 
 Because this is a dual boot system, I'm wondering if the problem may have something to do with the hda1 (windows partition) or my fat32 partition that acts as shared drive space for both os's?

Permissions for hda1 are: dr-x------
Permissions for hda4 are: drwxr-xr-x

Not sure if the drives are related to the problem or not.
Thanks for any help.[/QUOTE]

I don't think so,
I've tried with and without a windows partition, the same problem occurs
I've also tested with xfs instead of the default ext3 for the root partition

---

### Post by ploosh on 2005-11-15
I noticed when I shut down the system hangs after "Deactivating swap". So instead of either the previous partitions mentioned, I wonder if it has to do with the swap space?
Also, I created my partitions manually rather than the auto - not sure if the issue could be with that. :(
But everything seems to work fine, except the restart. Wierd.

---

### Post by depp on 2005-11-18
I have a toshiba lapy with this issue too. I can shutdown normally both from GUI and from console, but i can't reboot even once. When i reboot, sometimes it hangs before the completion of the shutdown, sometimes hangs on activating hotplug subsystem.

---

### Post by mefrancis on 2005-11-22
[QUOTE=steve1401]Not read through the full thread here, so appologies if this has allready been resolved. If not this should do the job;

sudo vi /boot/grub/menu.lst

Change the following section
---
title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot
---

To this 

---
title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro **noapic nolapic** quiet splash
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot
---

Note the addition of the noapic nolapic - this is an option in the initial install, but can be passed at boot in this fashion (exactly the same thing actually)

Reboot and of you go...

Cheers
Steve[/QUOTE]

noapic nolapic didn't work.  Try noacpi nolacpi.  That worked for me.

---

### Post by Sebby on 2005-11-22
I've just compiled a new kernel (2.6.14.2) and I'm pretty sure that shutdown and restart is now working... I'll post back for definite soon!

---

### Post by Sebby on 2005-11-22
[QUOTE=Sebby]I've just compiled a new kernel (2.6.14.2) and I'm pretty sure that shutdown and restart is now working... I'll post back for definite soon![/QUOTE]
Okay, strangely rebooting now works but not shutdown! :rolleyes:

---

### Post by depp on 2005-11-22
After long time testing, i found, the issue with reboot on my toshiba a100 is caused by "ipw2100" module, the wireless module. What i should do before i reboot is, remove it!:D  
So just type:
```
sudo modprobe -r ipw2100
```
It's also necessary to do a hibernate. I'm not sure if it's also the case with ipw2200 toshiba laptops, just have a try!
Hope it helps!;)

---

### Post by Sebby on 2005-11-23
[QUOTE=depp]After long time testing, i found, the issue with reboot on my toshiba a100 is caused by "ipw2100" module, the wireless module. What i should do before i reboot is, remove it!:D  
So just type:
```
sudo modprobe -r ipw2100
```
It's also necessary to do a hibernate. I'm not sure if it's also the case with ipw2200 toshiba laptops, just have a try!
Hope it helps!;)[/QUOTE]
You're absolutely right! I have an ipw2200 and stopping the module makes rebooting and shutdown work perfectly! Further to my comments yesterday after compiling a new kernel, it would seem that the only reason it worked to start with is because ipw2200 was not installed!

So, who else that is experiencing reboot/shutdown problems using an ipw2x00?

The next point is: what do we do about it? Report a bug to the ipw2x00 team?

---

### Post by depp on 2005-11-23
[QUOTE=Sebby]The next point is: what do we do about it? Report a bug to the ipw2x00 team?[/QUOTE]
I think so.
But it's not so annoying anyway, since we figured out what is actually buggy. I now just switch on my wireless card before i use it, then add the module, after i use it, i remove the module and turn it off. ;)

---

### Post by Sebby on 2005-11-23
[QUOTE=depp]I think so.
But it's not so annoying anyway, since we figured out what is actually buggy. I now just switch on my wireless card before i use it, then add the module, after i use it, i remove the module and turn it off. ;)[/QUOTE]
I take your point but it *would* be easier if we didn't have to! ;)

---

### Post by depp on 2005-11-23
I did some tweaks again.
For reboot, i added ```
modprobe -r ipw2100
``` to ```
/etc/init.d/reboot
```
For hibernate, i added ```
ipw2100
``` to the ```
MODULE_WHITELIST
``` in ```
/etc/default/acpi-support
``` The modules in this list are supposed not to be unloaded over suspend/resume.
Anyone can suggest a better manner to work it around?

---

### Post by Sebby on 2005-11-23
[QUOTE=depp]I did some tweaks again.
For reboot, i added ```
modprobe -r ipw2100
``` to ```
/etc/init.d/reboot
```
For hibernate, i added ```
ipw2100
``` to the ```
MODULE_WHITELIST
``` in ```
/etc/default/acpi-support
``` The modules in this list are supposed not to be unloaded over suspend/resume.
Anyone can suggest a better manner to work it around?[/QUOTE]
Great, this is exactly what I need. Where abouts in /etc/init.d/reboot do I add the modprobe -r ipw2200?

---

### Post by depp on 2005-11-23
[QUOTE=Sebby]Great, this is exactly what I need. Where abouts in /etc/init.d/reboot do I add the modprobe -r ipw2200?[/QUOTE]
Well, i put it right before ```
shutdown -d -f -i 
```
do you think it's a decent workaround? anyway, it works, :p

---

### Post by Sebby on 2005-11-23
[QUOTE=depp]Well, i put it right before ```
shutdown -d -f -i 
```
do you think it's a decent workaround? anyway, it works, :p[/QUOTE]
Of course it's a good workaround - it works! :p

---

### Post by depp on 2005-11-24
hibernate is not working everytime, any ideas?
but considering the speed of resume from a hibernation, i'd rather do a shutdown and new boot.

---

### Post by Sebby on 2005-11-24
Further to yesterday, I still seem to be having trouble occasionally with reboots... :confused:

---

### Post by depp on 2005-11-24
[QUOTE=Sebby]Further to yesterday, I still seem to be having trouble occasionally with reboots... :confused:[/QUOTE]
My reboot is flawless now. But as i said, the workaround is not so decent though. Shall we let the ubuntu guys know? I know there is a laptop-test-team.

---

### Post by varunus on 2005-11-25
Hmm...

I have an atheros card running using the madwifi driver on my Toshiba, and I still have the reboot issue.  I'll try unloading the module before I reboot and see what happens...

---

### Post by NikoC on 2005-11-28
Though it's a good work around I have to agree with depp, we should inform the laptop-testing-team!

---

### Post by Sebby on 2005-11-28
I'm still having trouble with *some* shutdowns and restarts. Can anyone help?

---

### Post by Limulus on 2005-11-29
[QUOTE=Sebby]You're absolutely right! I have an ipw2200 and stopping the module makes rebooting and shutdown work perfectly! Further to my comments yesterday after compiling a new kernel, it would seem that the only reason it worked to start with is because ipw2200 was not installed!

So, who else that is experiencing reboot/shutdown problems using an ipw2x00?

The next point is: what do we do about it? Report a bug to the ipw2x00 team?[/QUOTE]

I tried stopping the modules as per these posts, but it didn't work for me (running a Toshiba Satellite A25)...  How do I determine if I even have an 'ipw2x00 module' or what modules are running?

---

### Post by Sebby on 2005-11-29
[QUOTE=Limulus]I tried stopping the modules as per these posts, but it didn't work for me (running a Toshiba Satellite A25)...  How do I determine if I even have an 'ipw2x00 module' or what modules are running?[/QUOTE]
If you have an ipw2100:
```
sudo modprobe -r ipw2100
```

Alternatively, if you have an ipw2200:
```
sudo modprobe -r ipw2200
```

I just wrote ipw2x00 so it applied to both. :rolleyes:

I'm finding that I still have problems rebooting every time. Occasionally shutdown works. There appears to be no pattern; it just has a mind of its own! I'd really like to sort this out because I don't like having to hold down the power button to switch off my laptop every day... It can't be good for the hard drive! :p

---

### Post by softgun on 2005-11-29
There is one reply to this thread where it happened in a desktop too. Thus it could be a more complex issue. I can remember that earlier versions of Knoppix had this same problem which was then solved in the newer versions.

Maybe if the main team see this thread they may sort this out for the next version :p

---

### Post by Apostata on 2005-11-29
I'm not sure if you're referring to me, but I'm a desktop user having this problem. I've previoulsy posted on this thread.

---

### Post by Sebby on 2005-11-29
Being still fairly new to Ubuntu, I'm not really sure what action we should take. Does this warranty reporting? If so, who to?

---

### Post by varunus on 2005-11-29
Guys, I found out the problem!

I posted to a bug report, and Matthew Garett was kind enough to give a fix.  This issue will be fixed in dapper, but until then, follow the following guide:

Open up your /boot/grub/menu.lst file using:

```
sudo gedit /boot/grub/menu.lst
```

Find your kernel lines (mine is 686, yours could be 386 or k7):

```
title           Ubuntu, kernel 2.6.12-10-686
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-10-686 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.12-10-686
savedefault
boot
```


Change it to:
```

title           Ubuntu, kernel 2.6.12-10-686
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-10-686 root=/dev/hda3 ro quiet splash reboot=h
initrd          /boot/initrd.img-2.6.12-10-686
savedefault
boot
```

(Add the reboot=h to the end of the kernel line.)

Reboot once again by turning off and on, and the next time you boot up and reboot, you'll be able to choose reboot from System->Log Off!

---

### Post by depp on 2005-11-29
[QUOTE=varunus]Guys, I found out the problem!
[/QUOTE]
Could you pls say something more about the bug? :smile: Is it caused by buggy ipw2x00 driver? I tried SuSe 10.0 days ago, it's just the same issue, i should remove the module before i reboot.

---

### Post by bigc on 2005-11-29
I've done the changes to the grub menu file and all is working well now.

:)

---

### Post by Limulus on 2005-11-30
[QUOTE=varunus]Guys, I found out the problem!

I posted to a bug report, and Matthew Garett was kind enough to give a fix.  This issue will be fixed in dapper, but until then, follow the following guide:

Open up your /boot/grub/menu.lst file using:

```
sudo gedit /boot/grub/menu.lst
```
Find your kernel lines (mine is 686, yours could be 386 or k7):
[...]
(Add the reboot=h to the end of the kernel line.)

Reboot once again by turning off and on, and the next time you boot up and reboot, you'll be able to choose reboot from System->Log Off![/QUOTE]

It worked! =D

Thanks so much for solving the problem. BTW, what exactly does that line do that it fixes things?

As an aside, it seems that "reboot=h" is mentioned in [bug 17152]("http://bugzilla.ubuntu.com/show_bug.cgi?id=17152") to solve a shutdown problem in the Dell OptiPlex Gx620.  Glad to know this is getting fixed in Dapper.

---

### Post by depp on 2005-11-30
I should confess, "reboot=h" is not working for me...

---

### Post by Sebby on 2005-11-30
This appears to be working for me, but that could change. :p

---

### Post by bigc on 2005-11-30
It worked when i rebooted for the first time, but it stoped working now...

---

### Post by Sebby on 2005-11-30
My reboots are now fine, but shutdown is still a problem. Is there a fix for this (shutdown=h perhaps :p)?

---

### Post by bigc on 2005-11-30
I've fixed the reboot problem, but still remains the shutdown...

---

### Post by Sebby on 2005-11-30
[QUOTE=bigc]I've fixed the reboot problem, but still remains the shutdown...[/QUOTE]
Same here. I have created a new bug after reading all the relevant cases on Bugzilla and not managing to find any suggestions. One of the suggestions I did find is to add *nolapic* to the boot command line, but unfortunately this prevented my system from booting altogether; though it may prove a success for you.

---

### Post by depp on 2005-11-30
Guys, let's wait for Dapper now. Finger crossed.

---

### Post by Sebby on 2005-11-30
[QUOTE=depp]Guys, let's wait for Dapper now. Finger crossed.[/QUOTE]
When's it going to be released?

---

### Post by depp on 2005-11-30
[QUOTE=Sebby]When's it going to be released?[/QUOTE]
April 2006, before worldcup anyway
:cool:

---

### Post by Sebby on 2005-11-30
[QUOTE=depp]April 2006, before worldcup anyway
:cool:[/QUOTE]
Still a while. :rolleyes:

---

### Post by depp on 2005-11-30
[QUOTE=Sebby]Still a while. :rolleyes:[/QUOTE]
Before that, just keep our machines on :D

---

### Post by Sebby on 2005-11-30
[QUOTE=depp]Before that, just keep our machines on :D[/QUOTE]
Or in my case, reboot (which works), then load up Windows, then shutdown. :p

---

### Post by depp on 2005-11-30
[QUOTE=Sebby]Or in my case, reboot (which works), then load up Windows, then shutdown. :p[/QUOTE]
I don't have windows now, besides this reboot issue, i'm hoping also mplayer's plugin play more smoothly just like quicktime and wmplayer do in windows.

---

### Post by varunus on 2005-12-02
Hmm...I'm thinking the shutdown issues may be caused by something else, as I didn't have any shutdown issues (mine is a pre-centrino laptop, so I have an atheros card).  reboot=h solved my reboot problems...I'm not sure exactly what it does, however.  Someone want to try halt=h or shutdown=h and see if that works?  I don't even know if that will actually do anything...

Also, maybe someone should try unloading the ipw2200 module and then shutting down?  If that works, you can modify your initscripts to do it every time...

---

### Post by Liam Yates on 2005-12-03
Just reading through this topic, I'm a tad worried.

I was going to put Ubuntu onto my Toshiba laptop, but after finding out apparently we can't shut down, I'm not comftable taking out the battery each time.  Can I ask - Does holding the power button down turn it off? I'm not **too** fussed about not being able to select Shut Down, I just want to know if I can actually turn off my laptop without dismantelling it.

---

### Post by TwiceOver on 2005-12-03
[QUOTE=Liam Yates]Just reading through this topic, I'm a tad worried.

I was going to put Ubuntu onto my Toshiba laptop, but after finding out apparently we can't shut down, I'm not comftable taking out the battery each time.  Can I ask - Does holding the power button down turn it off? I'm not **too** fussed about not being able to select Shut Down, I just want to know if I can actually turn off my laptop without dismantelling it.[/QUOTE]

I'm using a Toshiba A15.  I can shutdown just fine.  My reboot completes but doesn't restart the computer.  When I choose reboot it brings down the OS then I have to hold the power button to shutdown, then press again to boot.  Basically I just use shutdown now.

Otherwise everything else is working perfectly.

---

### Post by Sebby on 2005-12-03
[QUOTE=TwiceOver]My reboot completes but doesn't restart the computer.  When I choose reboot it brings down the OS then I have to hold the power button to shutdown, then press again to boot.[/QUOTE]
Adding reboot=h to the boot command line in /boot/grub/menu.lst will most probably resolve this. For example, my kernel line looks like this:

```
kernel		/boot/vmlinuz-2.6.12-10-686 root=/dev/hda3 ro quiet reboot=h splash
```

You'll have to reboot once "the old way" before future reboots work (hopefully), i.e. adding reboot=h then trying to reboot won't work the first time because the kernel needs to be reloaded.

---

### Post by trelirodia on 2005-12-03
Sweet! Worked perfect for me on a Vaio FS195XP (with Centrino architecture). My problem was that after an upgrade from Hoary to Breezy reboot would hang. No shutdown problems though.

Thanks a million for the help, I have been looking for a solution to this problem for a while. 

Best of luck, 
M

---

### Post by TwiceOver on 2005-12-03
[QUOTE=Sebby]Adding reboot=h to the boot command line in /boot/grub/menu.lst will most probably resolve this. For example, my kernel line looks like this:

```
kernel		/boot/vmlinuz-2.6.12-10-686 root=/dev/hda3 ro quiet reboot=h splash
```

You'll have to reboot once "the old way" before future reboots work (hopefully), i.e. adding reboot=h then trying to reboot won't work the first time because the kernel needs to be reloaded.[/QUOTE]

Thanks... Works great.  Now if I can get suspend to ram and my lid closing event to work I would be extremely happy.

---

### Post by varunus on 2005-12-05
[QUOTE=Liam Yates]Just reading through this topic, I'm a tad worried.

I was going to put Ubuntu onto my Toshiba laptop, but after finding out apparently we can't shut down, I'm not comftable taking out the battery each time.  Can I ask - Does holding the power button down turn it off? I'm not **too** fussed about not being able to select Shut Down, I just want to know if I can actually turn off my laptop without dismantelling it.[/QUOTE]

If you hold down the power button, it turns off.  I don't have the shutdown issue, and the reboot issue is fixed for me..

Earlier, the problem was that after you turned off the computer, it would go through the shutdown process but stay on.  You had to use the power button to turn it off.

There was never a problem with the power button.

---

### Post by afrifreak on 2005-12-11
I have a similar problem, not on a a laptop but on my good old Athlon 1,2 Ghz desktop system. Previous versions of Ubuntu all worked fine.

Shutdown: works
Reboot: gives shutdown

I hope a solution is on its way. Something tells me I shouldn't complain about a free OS, so I won't do that ;)

Best regards,

Andres

---

### Post by Ana Carolina on 2005-12-12
I have a laptop toshiba satellite A45 series that also doesn't reboot...
Does it have a solution?

thanks

---

### Post by Ana Carolina on 2005-12-12
[QUOTE=TwiceOver]Thanks... Works great.  Now if I can get suspend to ram and my lid closing event to work I would be extremely happy.[/QUOTE]

Thanks...
This worked just fine with me :D

---

### Post by Sebby on 2005-12-13
[QUOTE=Ana Carolina]I have a laptop toshiba satellite A45 series that also doesn't reboot...
Does it have a solution?

thanks[/QUOTE]
Have a look at my post #81 a little further up the page... :)

---

### Post by NikoC on 2005-12-17
Just to let you guys know: reboot=h does not work on sony vaio vgn-s4hp!
Guess i'll wait for dapper ;)

---

### Post by Apostata on 2005-12-17
> Just to let you guys know: reboot=h does not work on sony vaio vgn-s4hp!

Doesn't work on my desktop either.

---

### Post by dejitarob on 2005-12-21
The reboot=h workaround does not work for my Asus Z70v laptop either, still freezing during the shutdown/reboot procedure. I might try a manual kernel upgrade but it did not do this on Gentoo 2005.1 with any of the 2.6.10-14 kernels.

---

### Post by Jzor on 2005-12-24
The 'reboot=h' workaround does not work for me either. It just hangs at the final rebooting message.

I do not have either of the ipw modules loaded, so those aren't the issue.

My computer:
AthlonXP 2500+ (@ 3200+ speed)
Abit KV7 Motherboard
1 GB RAM
ATI AIW 9600XT

---

### Post by twoseids on 2005-12-28
Same problem here with my Dell 4100 laptop. I have been using Ubuntu since June 2005 (first Hoary, then Breezy) and this problem just started happening about a week or two ago.

I tried "reboot -h" but it did not work for me. I am thinking about just doing a Breezy reinstall.

---

### Post by Sebby on 2005-12-28
[QUOTE=twoseids]I tried "reboot -h" but it did not work for me. I am thinking about just doing a Breezy reinstall.[/QUOTE]
Should be reboot=h. :)

---

### Post by o----o on 2005-12-29
reboot=h
works for me wihout ipw2200.(but not at first reboot)
sony vaio VGN-FS395VP

thanks a lot. :razz: 

jm

---

### Post by twoseids on 2005-12-30
[QUOTE=Sebby]Should be reboot=h. :)[/QUOTE]
Thanks - I checked my /boot/grub/menu.lst and I had typed **reboot=h** there - I just did the typo here in the forum. So still no dice here. This sucks.

---

### Post by LaSSarD on 2006-01-03
I guess i'm not very lucky... I tried everything you guys said and nothing worked. "reboot=h" on /boot/grub/menu.lst, reboot on console, reboot on gnome, "reboot -h" on console, NOTHING :(

My problem is only with reboot, the notebook seems to be shutdown but actually it's still turned on with no ubuntu loading :(

The notebook in case is a Toshiba Satellite 1805-S274

---

### Post by Sp@z on 2006-01-06
I am having issues with this on my desktop. I have a sneaking suspicion this is something to do with the video drivers. When restarting or shutting down I cannot see any of the dialog of the restart process the screen will go completly black, then I get very nicely colored blocks all over the screen and the sound hangs as well. It appears that everything DOES shutdown preparing for reboot as I get NO messages or dialog saying that it was shut down incorrectly.
Has anyone with more experiance than I looked into it being a video issue?

---

### Post by Olflo on 2006-01-06
I also have shutdwn/restart problms on a desktopAMD 64 running Hoary Kubuntu 5.04.
The system worked perfectly without any such problem, now this issue has come up after I did several things in one session:

1.perform some updates, including a kernel update
2.put a new hdd in the box, installed win xp on it and reconfigured grub to triple-boot
(before, it was a dual-boot system with another linux distro [64studio] running from the same hdd as kubuntu - and no problems. )

after extensive testing i am sure the problem has to do with the configuration of grub and the various problems associated with this...

as far as I've been able to read on this thread though, my guess would be there are several ways to catch this reboot/shutdown problem, not only one...

---

### Post by kuad on 2006-01-06
I've also got this shutdown and reboot problem with my Asus W3N.

Centrino 1.6Ghz, 512Mb memory, 60Gb harddisk, ATI Mobility Radeon 9700, wireless, bluetooth.

Strangely, sometimes when shutting down or rebooting, everything occurs as "normal" up until the system is supposed to power off but doesn't. However other times, the screen doesn't turn off, and just hangs with the code displaying (ie all the "Stopping xxxxxx    [OK]" is still being shown) even down to the final line which is "Power Down" although the laptop doesn't acutally power down.

I haven't tried the "noacpi nolacpi" method yet. But if I do, doesn't this disable all the power management for the laptop?

---

### Post by NikoC on 2006-01-08
Today I tried the livecd of the current Dapper release and shutdown worked fine but reboot didn't... so it looks like this shutdown/reboot problem is gettin' the necessary attention and will hopefully be solved in the final Dapper release.
ps. still using a sony vaio vgn-s4hp ;)

---

### Post by micjustmic on 2006-01-10
I'm actually having the opposite problem, when I shutdown, it reboots.

Anyone experience this one?

Mic

---

### Post by micjustmic on 2006-01-11
Nevermind, looked in /etc/rc0.d and found a link to the reboot script, I don't think that's supposed to be in there . . .

Moved it and all seems well.

Mic

---

### Post by odysseus.lost on 2006-02-15
Since I reached this page and did not find a solution to this thread but I think the answer lies on the following thread I am just adding this link as well.
[http://www.ubuntuforums.org/showthread.php?t=70520&highlight=apm](http://www.ubuntuforums.org/showthread.php?t=70520&highlight=apm)

---

### Post by withoutclass on 2006-02-15
dapper solves this issue for me

---

### Post by NikoC on 2006-02-16
Dapper does indeed give me a full reboot or shutdown... a big improvement indeed... now let's hope the hibernate/sleep function is working soon... they both give a complete shutdown on my system... for now I'll be waiting till the official Dapper release...

---

### Post by withoutclass on 2006-02-16
hibernate works fine for me as well

---

### Post by porcho on 2006-02-16
**varunus** solution at #59 worked perfectly for me. I have a Toshiba Satellite A10 notebook, and though I've never had the shutdown problem some have reported, I never got it to restart under Breezy. Now it does! :D 
Does anyone know what the 'reboot=h' options stands for? Will this issue be fixed on Dapper?

---

### Post by NikoC on 2006-02-17
Porcho: reboot and shutdown already work fine in Dapper on my portable (Sony Vaio VGN-S4HP).

---

### Post by EPOX123 on 2006-03-05
I just would like to post on here that this is not just a notebook problem im on a desktop and have the problem so if you guys report any bugs dont say that its just a laptop thing :)

Mabe we should try and apply one update at a time and see which one is messing up ubuntu shutdown restart etc.

---

### Post by incremental on 2006-04-09
Another Desktop user with this problem:

Running Ubuntu Dapper, flight 6 on:

-Asus p5gd2 deluxe motherboard
-3.0 GHz P4 630

restarts fine, but shutdown just goes through entire process and says "power down", but the computer does not power off. I've tried noapic and nolapic to no avail.

If I start up from in the "recovery mode", as listed in grub and do not start the gdm, then it shuts down fine, but not from normal startup.

---

### Post by yellowtrolley on 2006-04-21
Have you tried typing shutdown=h in your /boot/grub/menu.lst ?

This one seems to work on my toshiba m70

title		Ubuntu, kernel 2.6.12-10-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/sda2 ro noapic nolapic quiet splash shutdown=h
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

---

### Post by yellowtrolley on 2006-04-30
[QUOTE=yellowtrolley]Have you tried typing shutdown=h in your /boot/grub/menu.lst ?

This one seems to work on my toshiba m70

title		Ubuntu, kernel 2.6.12-10-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/sda2 ro noapic nolapic quiet splash shutdown=h
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot[/QUOTE]
Sorry. That doesn't fix the problem. It has been shutting down alright for a few weeks and now it is playing up again.

---

### Post by Xenix on 2006-10-27
I am still having restart issues with Edgy (final) on my desktop, I had it with Dapper, and I have it with Edgy.  Sometimes it works, but when it doesn't, I go to restart the PC, and it will either hang where the shudown splash is suppose to be, or it will fail to post, and just sit there with a blank screen.

The only way I seem to be able to fix it, is turn off the PC via the power switch, wait, then turn it back on (not healthy).  I have no idea what is causing it.  The last time it happened, was in Edgy final, when i installed the binary ATI fglrx drivers from the repo's, following the "Unofficial Guide".

I run Windows day in, day out, and I have no issues with it, so I don't think it is a hardware issue.  I also don't recall it happening with any other distro I have tried.

Specs:-

CPU: P4 "C Northwood" 3.0GHz
M/B: Asus P4C800-E Deluxe
1GB DDR400 Dual Channel RAM
Radeon 9800 Pro AGP Video card
Onboard LAN & Sound
2x Western Digital 80GB PATA HArd Drives

---

### Post by wgscott on 2006-10-27
I had this problem with Dapper.  I just upgraded to Edgy and the problem has gone away, if I shut down using the GUI.  If I issue for example

sudo shutdown -r now

it hangs in the shutdown sequence.

---

### Post by Xenix on 2006-10-27
> **wgscott said:**
> I had this problem with Dapper.  I just upgraded to Edgy and the problem has gone away, if I shut down using the GUI.  If I issue for example

sudo shutdown -r now

it hangs in the shutdown sequence.

Actually, now that you mention it, even though i usually use GUI to shutdown / restart, i MAY have used terminal to do it last time in Edgy, and that might have been responsible.  Although, in Dapper, i still had the issue, regardless of using GUI or terminal.

---

### Post by haxality on 2006-11-16
Hey, just thought I'd add that I have a Toshiba Tecra M1, I was suffering from the same ipw2100 problem, but if I turn off my wireless hardware with the switch on the front of my laptop, I have no problems rebooting.

---

### Post by Kross on 2006-11-16
This Worked For me,,,

[http://www.ubuntuforums.org/showthre...light=shutdown]("http://www.ubuntuforums.org/showthre...light=shutdown")

4th Post down...
Post there If it worked for you..

Thanks

-Kross
Edit/Delete Message

---

### Post by jordoex on 2006-11-16
I am having this problem with edgy on my Pentium 2 Xubuntu computer.  I still need to check all of the possible solutions.  Shutting down worked fine with dapper. Will post more results.

---

### Post by darkpark on 2007-01-20
I'll mention my dilemma for the sake of posterity.  I have an nforce3 motherboard with an AMD64 3500+ processor.   With Dapper, I had no problems shutting down or rebooting.   With Edgy, I could shutdown w/o any problems either, but restarting always gave me problems in Edgy.  If I selected shutdown either form the terminal or from gnome,  X would close than I'd get the shutdown splash screen, followed by a black screen and the computer would start beeping.  I'd have to manually shutdown it down via the power button.
My problem is fixed now, though.   I edited my menu.lst in my grub directory and added those two magic words: noapci nolapci  to the kernel line.   I'm a happy camper now! :biggrin:

---

### Post by sebgei on 2007-01-21
I can report the same problem on my 2005 Sony Vaio VGN-S4XP. Shutdown, reboot, and hibernate worked like a charm with Dapper. After updating to Edgy, the laptop shutdown sequence hangs at "will halt now". Rebooting though still works. I did a clean new install of Edgy Eft, but without any success.

I tried all sorts of boot options: acpi=force, acpi=off apm=on, acpi=off apm=on apm=power_off, added apm power_off=1 to /etc/modules but without any success -- at most, the splash screen dissapears but still the laptop dows not power down completely. acpi_available ; echo $? returns 0, so acpi should work in theory. Entering shutdown -h from the console does not get me any further than adding the boot options.

From what I read on various forums, that's an issue with the kernel (and/or acpi?) and if the boot options don't help, there is nothing one can do than waiting to wait until it's fixed? Or are there any other solutions I could try?

---

### Post by chrisharris0 on 2008-05-14
Try this, it worked or me on me Asus eee


in /etc/default/halt

add the following line right at the end:

rmmod snd-hda-intel

---

### Post by aonaran on 2008-07-22
Confirming bug. Can easily shutdown/reboot from the console. Cannot shutdown/reboot from the GUI (the Log Off button does not display the option to do so - previously, when it did, had the same problems as previously posted). 

Pentium M 2.00ghz
2.00gb DDR2
ATI Radeon Mobility onboard gfx

Could this be a problem for users who have disabled the Metacity in favor of Compiz?

---

