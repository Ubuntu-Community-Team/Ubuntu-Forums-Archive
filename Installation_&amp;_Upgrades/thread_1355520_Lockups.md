---
title: "Lockups"
date: 2009-12-15
forum: Installation &amp; Upgrades
---

### Post by johnsd on 2009-12-15
Ubuntu 9.04 was rock solid for me.

I recently did a clean install on my desktop of 9.10. All is good except I get total lockups about once an evening. The mouse is still functional but not the keyboard (I have enabled <CRTL><ALT><BACKSPACE> but it or an attempt to go to a command shell does not work).

After a bit of research I figure that the  Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01) might be causing the problem??

A quick test of Fedora 12 from the live CD also caused a lockup.

I am using 2.6.31-16-generic.

It appears that something in 9.10 must have changed to cause this problem as the system was totally rock solid before the new install.

Does anyone have a fix or a work around for this problem? I have tired viewing the logs but have not found anything that is of note to me.

---

### Post by andrewc6l on 2009-12-15
I'm seeing the same thing (I'll have to check what video chipset I'm using.) An additional data point: once it locks up, you can still ssh in and do things, including trying to kill X. The regular kill doesn't work, but kill -9 takes it down... things just don't start up again afterwards.

---

### Post by johnsd on 2009-12-15
> **andrewc6l said:**
> ... once it locks up, you can still ssh in and do things,..

I can understand that since on my PC if you leave it sitting there, the HDD light still comes on randomly as if things are still working behind he scenes!

---

### Post by andrewc6l on 2009-12-18
I just checked my machine - I also have the 82845:
```
$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

```

Some of my reading points to this being a problem with UXA acceleration - which means setting it not to do acceleration in xorg.conf might help it. That would be:
```
Option "NoAccel" "true"
``` according to [http://alcor.concordia.ca/manpages/sys4/intel.4.html](http://alcor.concordia.ca/manpages/sys4/intel.4.html) and might increase stability at the expense of performance. It might also be possible to use instead: ```
Option "AccelMethod" "EXA"
``` (which I believe was the default in 9.04).

I've also read that it might be power management related - so adding noapic apci=off to the kernel boot options might help too.

---

### Post by johnsd on 2009-12-18
Many thanks for that - I have generated a xorg.conf file with the 9.04 option in it for starters to see what happens.

The lockups seem to be further apart as time goes on - but they still happen.

---

### Post by johnsd on 2009-12-18
> **andrewc6l said:**
> 
I've also read that it might be power management related - so adding noapic apci=off to the kernel boot options might help too.

I am suspecting not in my case since all lockups have happened while I have been using the system.

---

### Post by johnsd on 2009-12-19
Progress report - a lock up has occurred with the option below. Will try the other one and see how it goes.

Option "AccelMethod" "EXA"

---

### Post by johnsd on 2009-12-21
... and now it has locked with the other otion.

I presume that once you supply a /etc/X11/xorg.conf file it will be automatically read when X is started. This is the first time I have encountered the default of no xorg.conf file.

Any other ideas. As I pointed out, things worked fine in 9.04 (and I ahve made no hardware changes to the system).

---

### Post by johnsd on 2009-12-22
A lock up happened within 3 minutes of starting this evening. Anyone with any ideas would be appreciated!  Otherwise since this is my main PC I will need to find a distro that works properly on my PC!

---

### Post by iponeverything on 2009-12-22
Do you have an early kernel to boot from?

Also -- try installing "linux-backport-module"

---

### Post by johnsd on 2009-12-22
> **iponeverything said:**
> Do you have an early kernel to boot from?

Also -- try installing "linux-backport-module"

Just had the second lockup for the evening :<(

No old kernels unfortunately since I did a clean install.

Defn of backport :"Backporting is the action of taking a certain software modification (patch) and applying it to an older version of the software than it was initially created for. It is part of the maintenance step in a software development process".

I am not clear as to what this would do in this situation?

---

### Post by johnsd on 2009-12-22
> **andrewc6l said:**
> 

I've also read that it might be power management related - so adding noapic apci=off to the kernel boot options might help too.

OK - I will give this a go - but not clear about where you set this if you are using GRUB2?

---

### Post by iponeverything on 2009-12-22
> **johnsd said:**
> Just had the second lockup for the evening :<(

No old kernels unfortunately since I did a clean install.

Defn of backport :"Backporting is the action of taking a certain software modification (patch) and applying it to an older version of the software than it was initially created for. It is part of the maintenance step in a software development process".

I am not clear as to what this would do in this situation?

The problem didn't exist with last release.. So, it just stands to reason that your probably dealing with a software regression.

---

### Post by johnsd on 2009-12-22
Have not had anything  to do with backports before. Is installing that package the only thing I have to do? -- or is there more to it?

---

### Post by iponeverything on 2009-12-22
> **johnsd said:**
> Have not had anything  to do with backports before. Is installing that package the only thing I have to do? -- or is there more to it?

Nothing except reboot.

If it does not solve the problem you can remove the package and the system will be back to the way it was.

---

### Post by johnsd on 2009-12-22
Have installed it - will see what happens

---

### Post by johnsd on 2009-12-23
> **iponeverything said:**
>   -- try installing "linux-backport-module"

A whole evening with no lockup - so this may have solved it. Will see how it goes over the next few sessions.

---

### Post by iponeverything on 2009-12-23
knock on wood..

---

### Post by johnsd on 2009-12-26
Hope you have had a good Christmas!

... just when it has gone for a couple of evenings with no problems - a lock up again.

So back to my question - how do you turn APIC off with GRUB2?

______________________________________________
Found it - add the command to the end of the line below in /etc/default/grub


GRUB_CMDLINE_LINUX=" splash vga=771 acpi=off"

So giving this a go now

---

### Post by johnsd on 2009-12-27
This was a no go - the above line and 

GRUB_CMDLINE_LINUX="acpi=off"

stopped my PC from completing the boot process so obviously this is not correct!

If I don;t get this sorted shortly I will need to try another distro.

How close to Ubuntu is Mint - is it likely to have the same problem?

---

### Post by Lyleb on 2009-12-27
Solution that works:

Format and install 9.04. 
9.10 was not and is not ready for release.

---

### Post by johnsd on 2009-12-27
> **Lyleb said:**
> Solution that works:

Format and install 9.04. 
9.10 was not and is not ready for release.


I am beginning to think that this suggestion may be the best. Downside is that I like to have the latest software.

Just giving Mint8  a try from the live CD.

---

### Post by johnsd on 2009-12-28
Tonight I was copying some files to a USB HDD when the screen went black except for a cursor at the top left and the mouse pointer. This is not good. Other people may be having a good run out of 9.10 but for me the release is not not up to scratch.

I am waiting for a rainy day to set things back to 9.04.  If the next release behaves like this I will need to find myself another distro I think.

---

### Post by johnsd on 2009-12-28
Found what looked to be a very useful site at:

[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

Unfortunately for my system, the 2.4 driver stopped X from working at all and had to revert to the newer driver.

---

### Post by iponeverything on 2009-12-28
> **johnsd said:**
> Tonight I was copying some files to a USB HDD when the screen went black except for a cursor at the top left and the mouse pointer. This is not good. Other people may be having a good run out of 9.10 but for me the release is not not up to scratch.

I am waiting for a rainy day to set things back to 9.04.  If the next release behaves like this I will need to find myself another distro I think.

Luckily there are a lot to choose from. I have held back at 9.04 just because I really didn't have any compelling reason to go to 9.10. People seem to think that latest distro is newest software, this is not true, in most cases the only thing user will be missing are a few of the latest drivers, some UI changes and other fun bleeding edge stuff. My wife does not care what filesystem she is using or new pretty default background.. she just want her machine to work when she needs it..

---

### Post by johnsd on 2009-12-29
OK - back to 9.04 now and hopefully to normality!!

Thank you people for your attempted help on a release that didn't do the job for me.

---

