---
title: "&quot;Your CPU is lacking expected security protection&quot; ??"
date: 2010-02-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by emarkay on 2010-02-22
I just updated this morning and happened to reboot in the non-GUI boot and was told to go to  "usr/lib/update-notifier check-bios-nx --verbose", but that seems to be a program of some sort. 

How do I ruin this and what does this mean?

---

### Post by seeker5528 on 2010-02-22
> **emarkay said:**
> I just updated this morning and happened to reboot in the non-GUI boot and was told to go to  "usr/lib/update-notifier check-bios-nx --verbose", but that seems to be a program of some sort.

That should be:

```
/usr/lib/update-notifier/check-bios-nx --verbose
```

: You have to open a terminal window and run it from there.

Either you have NX support or you don't, it may be an option that can be enabled or disabled in the bios.

[http://www.google.com/search?q=%2Blinux+%2Bbios+%2BNX&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox](http://www.google.com/search?q=%2Blinux+%2Bbios+%2BNX&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox)

Later, Seeker

---

### Post by emarkay on 2010-02-22
Anyone?

---

### Post by Joel B on 2010-02-22
I'm guessing it means that your processor doesn't support the NX bit, which is the "No Execute" bit. This allows the OS to prevent execution from a block of memory. This greatly reduces the attack surface for buffer overflow attacks, which are a common cause of security problems.

So, you are less secure, but unless you've specifically disabled this option in your BIOS, there isn't much you can do about it.

-Joel

---

### Post by Didius Falco on 2010-02-22
It's simply telling you that your BIOS isn't set up to use this setting, but it reads it as a CPU that should be able to. Check your BIOS settings at the next boot to see if you can enable it.

NX stands for "No Execute" and is a setting used in newer AMD CPUs that prevents code from running in data-only memory pages, which is a common technique used in buffer-overflow attacks.

The Intel equivalent is XD which stands for "eXecute Disable".

It's a friendly warning to help you make your PC more secure.

---

### Post by emarkay on 2010-02-23
Never saw this before - is this something changed in Lucid; the detection or warning during boot?

---

### Post by Didius Falco on 2010-02-23
Have a look at this wiki page, it has a lot of information about security features in Ubuntu, including this one.

[https://wiki.ubuntu.com/Security/Features](https://wiki.ubuntu.com/Security/Features)

---

### Post by emarkay on 2010-02-23
> **Didius Falco said:**
> Have a look at this wiki page, it has a lot of information about security features in Ubuntu, including this one.
[https://wiki.ubuntu.com/Security/Features](https://wiki.ubuntu.com/Security/Features)

Um, OK, but it says nothing about my question and/or anything about Lucid (10.04).

---

### Post by kurros on 2010-02-24
Yes, the detection is new in 10.04. An unfortunate number of users reporting bugs to launchpad have logs that indicate their processors support NX but appeared to be disabled.

More information:
[https://wiki.ubuntu.com/Security/CPUFeatures](https://wiki.ubuntu.com/Security/CPUFeatures)
[http://www.outflux.net/blog/archives/2010/02/18/data-mining-for-nx-bit/](http://www.outflux.net/blog/archives/2010/02/18/data-mining-for-nx-bit/)

---

### Post by emarkay on 2010-02-24
> **kurros said:**
> Yes, the detection is new in 10.04. An unfortunate number of users reporting bugs to launchpad have logs that indicate their processors support NX but appeared to be disabled.
More information:
[https://wiki.ubuntu.com/Security/CPUFeatures](https://wiki.ubuntu.com/Security/CPUFeatures)
[http://www.outflux.net/blog/archives/2010/02/18/data-mining-for-nx-bit/](http://www.outflux.net/blog/archives/2010/02/18/data-mining-for-nx-bit/)

Get me the LP Bug# and I'll subscribe to it.  Thanks!

---

### Post by bregnernice on 2010-02-25
Hi. I have also just upgraded to lucid and get the same message after boot. I am at a loss what to do, the option to enable/disable security protection as described in the links above don't show in my bios.

When i power on my cpu grub loads but doesn't give me a choice to boot into the usual modes and memtest, just goes straight ahead and shows me 'you cpu is lacking expected security protection' notice.

Is there any way to proceed from here?

---

### Post by bregnernice on 2010-02-25
I'm trying to dig into this to be able to boot into my ubuntu desktop. 

When i run: /usr/lib/update-notifier/check-bios-nx --verbose , i get this:
 'This CPU is family 6, model 15, and has NX capabilities but is unable to use these protective features because the BIOS is configured to disable the capability. Please enable this in your BIOS. For more details, see: [https://wiki.ubuntu.com/Security/CPUFeatures](https://wiki.ubuntu.com/Security/CPUFeatures) 

Which tells me:
 'In a Dell laptop BIOS, look under "Security" / "CPU XD Support": it should be set to "enabled". In an American Megatrends BIOS, look under "CPU Features" / "Execute Disable Bit": it should be set to "enabled".' 

It seems to be a simple problem but i can't identify this feature in my BIOS, and alas, i am completely stuck, unable to boot into my desktop.

---

### Post by bregnernice on 2010-02-25
My cpu has NX capabilities but i can't find out how to enable them in BIOS. There is no such thing as 'CPU XD Support' or 'Execute Disable Bit' in Bios menu.

Does anyone know of any way to enable NX capabilities so i can boot into desktop? Is it possible to enable this feature from the command line?

If everything fails, is there any way i can recover my data? 

Sorry for the multiple posts. im just worried i really messed up my system this time.

---

### Post by emarkay on 2010-02-26
So no one has filed a Launchpad Bug on this?

---

### Post by Koterpillar on 2010-02-28
This is not a bug - in Ubuntu. It is your BIOS (and, sadly, mine) that does not allow to switch the mode on, so complain to your vendor.

---

### Post by Didius Falco on 2010-02-28
I'd look for a BIOS update first - if there isn't one, _then_ complain.

---

### Post by emarkay on 2010-03-06
> **Koterpillar said:**
> This is not a bug - in Ubuntu. It is your BIOS (and, sadly, mine) that does not allow to switch the mode on, so complain to your vendor.


OK, so that's a bummer for anyone with an older PC - I bet this is going to be a hot topic on RC and Final Release time....

---

### Post by cookiecruncher on 2010-03-06
I get that message when I log in via ssh.

---

### Post by lswb on 2010-03-06
> **bregnernice said:**
> 
...
Does anyone know of any way to enable NX capabilities so i can boot into desktop? Is it possible to enable this feature from the command line?
...


Lack of NX/XD capability will not keep a system from starting. There is likely some other problem and this just happens to be the last warning message posted before the real problem hits.

---

### Post by emarkay on 2010-03-07
Just confirmed the AWARD Bios here, Phoenix V6.00 is from 3/2005 and there is nothing newer, for the MSI mainboard I have...

Still it's a silly thing to have this warning if most who get it can't do anything about it.

Will monitor this and see what others think.

---

### Post by recluce on 2010-03-08
> **emarkay said:**
> Just confirmed the AWARD Bios here, Phoenix V6.00 is from 3/2005 and there is nothing newer, for the MSI mainboard I have...

Still it's a silly thing to have this warning if most who get it can't do anything about it.

Will monitor this and see what others think.

Actually, this warning makes perfect sense - I would venture that many people today have a system with a BIOS that has the option to enable/disable the execute disable bit.

If your BIOS allows you to select the XD bit, the warning makes sense as you should change the setting. If your BIOS does NOT allow you to change the XD bit setting, the warning still makes sense - at least you know now that you are more vulnerable to a number of attacks out there.

---

### Post by ssam on 2010-03-08
maybe this should be displayed as a notification, like the 'your disk is failing' one. that way it could link to some instructions on how to fix it.

also there should be a way to turn the warning off. i have install ubuntu for people on machines where they don't know the BIOS password.

---

### Post by recluce on 2010-03-08
> **ssam said:**
> maybe this should be displayed as a notification, like the 'your disk is failing' one. that way it could link to some instructions on how to fix it.

also there should be a way to turn the warning off. i have install ubuntu for people on machines where they don't know the BIOS password.

That would be even better. But it should at least require the root password to turn the warning off.

---

### Post by stone1343 on 2010-03-14
Just to clarify, I got this message for the first time this morning, on an up-to-date Lucid system. I don't have the BIOS option mentioned and the system just boots to a terminal, no graphical desktop at all. So to me, a non-expert, that installation is hosed, I have to re-install. Fortunately, I use an external hard drive, and actually have two of them, but at one point today neither of them booted. Because of this extremely rare h/w setup, I didn't lose any data but I ended up spending the day reinstalling etc. I view this as a catastrophic problem. Interestingly, I could boot from that drive on 2 other computers, just not from the system it was originally installed on. I almost went out and bought a new computer, I actually thought some component had been fried...

However, my gut feel agrees with a previous poster, that this is just the last message and doesn't really have anything to do with the problem. Something in the latest bunch of updates breaks the system. I'm running now fine, but I'm sure if I apply the updates, it'll die again. If anyone wants me to a guinea pig, and can help get valuable info, no problem, let me know how I can help, but this is a huge problem for those of us who get it.

Jeff

---

### Post by stone1343 on 2010-03-14
cpu-checker provides /usr/bin/check-bios-nx, so if I remove cpu-checker and install updates that would confirm that's it's a problem with the updates, not the NX thing, right? I'm think I'll try that on my other drive.

---

### Post by stone1343 on 2010-03-14
ok so a few important pkgs require cpu-checker, such as network-manager, so didn't remove it. As it turns out, it's not the updates, it's the reboot. Second time I reboot after the install, it gets the message. I think I'm using the March 13 daily build.

But now that I think of it, that's the same one I used to install the system I'm currently on, don't know what the difference is... Very confused.

---

### Post by Didius Falco on 2010-03-14
> **stone1343 said:**
> Just to clarify, I got this message for the first time this morning, on an up-to-date Lucid system. I don't have the BIOS option mentioned and the system just boots to a terminal, no graphical desktop at all. So to me, a non-expert, that installation is hosed, I have to re-install. Fortunately, I use an external hard drive, and actually have two of them, but at one point today neither of them booted. Because of this extremely rare h/w setup, I didn't lose any data but I ended up spending the day reinstalling etc. I view this as a catastrophic problem. Interestingly, I could boot from that drive on 2 other computers, just not from the system it was originally installed on. I almost went out and bought a new computer, I actually thought some component had been fried...

However, my gut feel agrees with a previous poster, that this is just the last message and doesn't really have anything to do with the problem. Something in the latest bunch of updates breaks the system. I'm running now fine, but I'm sure if I apply the updates, it'll die again. If anyone wants me to a guinea pig, and can help get valuable info, no problem, let me know how I can help, but this is a huge problem for those of us who get it.

Jeff

It sounds like you are experiencing a plymouth (the new splash screen provider) problem. When you get to the terminal, hit Ctrl-Alt-F7 - that should take you to the graphical desktop.

There are several Plymouth threads going, where you can keep up with what is going on with it, and workarounds for it.

Some folks are just uninstalling it, but that pretty much defeats the whole purpose of Alpha/Beta testing...

---

### Post by emarkay on 2010-03-14
I have killed Plymouth with much success - just remove it and it's threads and all will be well.

But still, this warning needs to be addressed and at least modified to say that "Older BIOS may not have the ability to correct this issue.  Ignore it."

---

