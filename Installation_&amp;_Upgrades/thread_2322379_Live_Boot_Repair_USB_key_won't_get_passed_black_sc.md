---
title: "Live Boot Repair USB key won't get passed black screen"
date: 2016-04-27
forum: Installation &amp; Upgrades
---

### Post by javierdl on 2016-04-27
The USB key does show the read light showing it's being read, but eventually it stops and there's nothing on the screen :(
I just created this USB key for the second time.

Any ideas?

Specs: Acer Predator G3-710, Win10. Ubuntu Studio installed, but not showing when using F12 key to choose available OSs. This is why I need to run Boot Repair.

---

### Post by oldfred on 2016-04-27
Do not know about your specific model, but all Acer have required you to set a UEFI supervisory password and enable "trust" on the grub/Ubuntu efi boot files.
Also some older threads say to downgrade to older UEFI, but newer ones say to make sure you have newest UEFI from Acer.

 Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)
Acer E5-573G, downgrade UEFI, supervisor password & trust on Ubuntu efi boot files.
[http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912](http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912)
Acer Aspire E15 will not dual boot, many details
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)
Acer Aspire E 15 Downgrade to older UEFI, password & trust (ACPI issues?)
[http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062](http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062)
Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
One of several with more details:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)

If you can boot Ubuntu installer (in UEFI mode) then just add Boot-Repair to that. 
And Boot-Repair cannot fix the "trust" issue that Acer uses.

---

### Post by javierdl on 2016-04-27
I'll set up that password.
To "enable trust" on the grub/Ubuntu efi boot files I have to figure out where they are first. Wish me luck with that.
About  flashing the Bios, I have been leaving that as a VERY last resort,  because from what I have been reading one can ruin the whole computer if  done wrong, no coming back from that :(

Thanks a bunch oldfred :)

---

### Post by javierdl on 2016-04-27
Ok, thanks to your second link, I found a [list of steps to install Ubuntu]("http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot").
Unfortunately I get stuck at step # 35:
[COLOR=#111111][FONT=Ubuntu]"Use the right cursor key to highlight "Security" and use the down cursor key to highlight "**Select an UEFI file as trusted for executing**" and press Enter."
I do have a tab called Security (that's where I set the Supervisor password), but I do not have the above bolded text option.
Would this be a sign that I need to update or downgrade the BIOS?
If so, should I start with "updating" it?

Thanks oldfred :)[/FONT][/COLOR]

---

### Post by oldfred on 2016-04-27
I do not know Acer as I do not have one.
But what I could read in various threads, seemed to be slight differences on where or how deep under a menu item it is. You should look around. One screen was to open hidden settings which only appeared after setting password.

I regularly update UEFI/BIOS on my systems and never have had an issue. But it never should be interrupted and a power failure in the middle could be a huge problem.  That may be why with most systems they suggest not updating unless you need it. And some of my motherboards have dual BIOS so they have a way to recover if needed.

---

### Post by javierdl on 2016-04-28
Thanks for sharing your experience installing Bios, it gave me the reassurance I needed. I've got the latest Bios installed now.
Unfortunately I still don't see that option to choose the trusted files.
I found something else though, it might be related : When switching Secure Boot Mode to Custom, it shows "Default Key Provisioning", it can be enabled or not. It says it's to manage all factory keys (PK, KEK, db, dbx). Install Factory default Secure Boot Keys when System is in Setup Mode.
Below there is one last choice : "Install Default Secure Boot Keys". It's description says : Force System to User Mode - Install default Secure Boot Variables (PK, KEK, db, dbx).
What do you think?

---

### Post by javierdl on 2016-04-28
Should I be contemplating to downgrade the BIOS?

---

### Post by oldfred on 2016-04-28
I would not change any keys for Secure boot.
That is very advanced, and everyone currently is using the default Microsoft key if using UEFI Secure Boot. 
I have Secure Boot turned off, currently.

I do not remember any of the Acer threads, posting screen shots, but several had details of commands.
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)

This one says he had to have secure boot on to find setting:
[http://ubuntuforums.org/showthread.php?t=2290594&p=13338364#post13338364](http://ubuntuforums.org/showthread.php?t=2290594&p=13338364#post13338364)

---

### Post by javierdl on 2016-04-28
I hear you. I won't touch those Keys then.

I read in some of the links you sent, that it's important not just to have these settings certain way, but to do it BEFORE installing Ubuntu. Hence, I'm reinstalling it now. 
Something I had not given any importance before is that there's an option to "Turn Off Secure Boot" in the installer (see attached image).

Based on what it explains I chose to turn it off with a password (see attached image).

Unfortunately while installing it found a couple errors (see attached image).

You can read all details about the error [here]("https://bugs.launchpad.net/ubuntu/+source/bbswitch/+bug/1576285")
The short version is this:
[B] "package  bbswitch-dkms 0.8-3ubuntu1 failed to install/upgrade: subprocess  installed post-installation script returned error exit status 10"

[/B]I also had this other error related to the [Nvidia card.]("https://bugs.launchpad.net/bugs/1575726")

So far the installer continues though... But I have to run, I may not be able to see it done :(

---

### Post by oldfred on 2016-04-28
Please attach screen shots, not everyone has High Speed Internet.
You can easily attach with forum's advanced editor and the paperclip icon.

My desktop has an older nVidia card and the open source driver works. So I have not installed the nVidia driver yet.
Do not know bbswitch but that also is related to switching Intel & nVidia video.

---

### Post by javierdl on 2016-04-28
Oops! Sorry, you're right. I'll keep that in mind.
I just arrived from work. And now that I could restart the computer and hold F12 to access the menu, I was able to confirm that this work is still not done: I only found Windows Boot Manager available :( Just when it looked so promising.
It's a real drag that one has to go through all this and more just to setup a dual boot. Doing them before UEFI was WAY easier!
I'll have to continue checking more into the links you shared before. I must say though, I'm pretty discouraged and tired of reading, and trying this, trying that... Anyway, sorry about the rambling...

---

### Post by javierdl on 2016-04-29
whett, from community.acer.com suceeded:
> Hurray! I finally have a working dual-boot box. I have used boot-repair from a USB flash drive (I don't remember whether booted with or without CSM BIO option). And then I did exactly what this program told me to do. After typing the given bcdedit command in a Windows administrator command shell, it miraculously worked. I can now boot with CSM = "Never" and I get a selection screen with the first option being UBUNTU and then some Windows boot loaders.  Let's hope it will stay like that!
Facit: boot-repair is a fine program.

[Source]("http://community.acer.com/t5/Predator-Desktops/Ubuntu-Linux-on-a-Acer-Predator-G3-605/m-p/431410#M863")

I'm going to have to try that...
It seems he enabled CSM to use Boot Repair. Then he disabled it.

---

### Post by oldfred on 2016-04-29
Glad you got it working.
If you still have video related issues best to start another thread.

---

### Post by javierdl on 2016-04-29
Lol, thanks for congratulating oldfred :)
But that wasn't me :(
That was someone else from the Acer forums.
Unfortunately that didn't work for me :(
I was able to boot the Live Boot Repair Disk USB key. By disabling TPM. basically I was in BIOS mode. But b4 BRD was able to completely load, it encountered an error, and showed nothing but a black screen.
I'm at work now, so I'll have to wait until next chance.

---

### Post by oldfred on 2016-04-29
Sorry, mis read it.

I retired my 10 year old laptop & built a new SFF desktop with similar specs, but only use Intel graphics. 

Do you also have nVidia then?
And can you control which video is used by settings in UEFI, or is it only automatic?
And when you boot is Intel video or nVidia in charge?

With nVidia you often need nomodeset. But my older desktop with nVidia 620GT just works well with open source driver.
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) 

But some Intel needed a different boot parameter, but with 16.04, I did not need it.
Skylake needs this boot parameter:  i915.preliminary_hw_support=1
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support](http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support) 
16.04 Intel Skylake (6th gen) CPU and an NVIDIA GPU bug & work around
[https://bugs.launchpad.net/ubuntu/+source/llvm-toolchain-3.8/+bug/1564156](https://bugs.launchpad.net/ubuntu/+source/llvm-toolchain-3.8/+bug/1564156)

---

### Post by javierdl on 2016-04-29
Thanks for the links oldfred :)
This makes me wonder: would it be easier to just remove the NVidia card before I install Ubuntu?

---

### Post by oldfred on 2016-04-29
That might be one way, but then when you re-install it, Ubuntu may still have issues?
Sounds like you are the one that gets to experiment. :)

---

### Post by javierdl on 2016-04-30
I found this very [complete tutorial]("http://askubuntu.com/questions/666631/how-can-i-dual-boot-windows-10-and-ubuntu-on-a-uefi-hp-notebook") on how to make this dual boot.
What I didn't see coming though, is that it advises to install Ubuntu FIRST, and Windows 10 SECOND!!!
No wonder this was not working for me!

---

### Post by oldfred on 2016-04-30
That is most unusual. 
Normal recommendation is to install Windows first. And that has HP which is not particularly friendly to dual booting. HP violates UEFI spec that says not to use Description as part of boot. So work arounds are required.

---

