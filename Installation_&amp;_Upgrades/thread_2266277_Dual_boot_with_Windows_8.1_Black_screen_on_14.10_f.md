---
title: "Dual boot with Windows 8.1: Black screen on 14.10 first time installation"
date: 2015-02-21
forum: Installation &amp; Upgrades
---

### Post by lewis-kimber7 on 2015-02-21
My acer laptop has only Windows 8.1 installed and I've just ran through the ubuntu 14.10 installation on the laptop via USB stick. After being prompted to restart after installation, I did so and was met with a black screen, and no sign of anything happening after leaving my laptop for about an hour. I looked up the problem on the web of others experiencing similar situations with replies saying "press ctrl + alt + f2 and type this command", however, typing these combinations of keys on my laptop had no sign of doing anything. The only way I could go out of the black box was to shut down my laptop via the power button, however my laptop goes straight to Windows. Even when I look in my boot menu there is no sign of ubuntu being installed on my laptop at all.

Any help would be greatly appreciated :)

---

### Post by headmower on 2015-02-21
I have the same problem on my acer 5741 with windows 7 installed, when I try to install ubuntu 11.10 and other higher versions the screen goes black and I have to use power button to turn off pc then boots back to windows 7 as nothing was installed. Ready to give up on LINUX--- please help](*,) p.s. I kind of remember a thread about a hardware issue on acer 5741.

---

### Post by headmower on 2015-02-21
I can install ubuntu 9.04, 9.10, 10.4 with no problems, also was able to installed Ultimate Edition 2.6 with no problems. When it comes to new releases the black screen comes up or I,ll get error messages as my acer trys to install the iso image on the disk. The disks are good.

---

### Post by hierstehtnormaleinname on 2015-02-23
Well you guys need to stop thinking about giving up linux just because of a regular black screen problem. I am absolutely sure that there are many howtos online for this problem. I am very sure because I wrote a similar one for nearly the same bug related to a UEFI install of Ubuntu!

However when your computer works fine with another OS, when you can install Ubuntu without problems and when you can start your computer and the hdd or sdd seams to work and the only problem is a black screen?! Guys, guess what the problem might be in most cases? To give a broad hint "Dark screen" ?! Right, your graphic settings! So now you&#8217;re may thinking something like "Wow, you're such a wisenheimer hierstehtnormaleinname if you are so intelligent why did old Ubuntu versions work fine than and why did all the help solutions of other users don't work, hugh?". Because with every new version of Ubuntu some older graphic cards (chips) get moved from proprietary to standard drivers or something like that and because many other guys are just trying to be important and therefore they give ****** help posts.

So easiest way would be to load the "failSaveX" you can reach it by holding [shift] at start up and enter the additional start options of ubuntu and than the recovery mode. Just select failsafeX wait until it has finished and select reboot. If you are able to start Ubuntu now you should correct your graphic driver first and may adjust the display modes. There also some extra PPAs available like xorg edgers that offer a bigger range of g.card drivers.

If this won't help you you need to log in via text mode and change your group start option for example with nomodeset &#8211; but first try failsaveX and come back if it won't work for you!

Bye

---

### Post by lewis-kimber7 on 2015-03-01
> **hierstehtnormaleinname said:**
> Well you guys need to stop thinking about giving up linux just because of a regular black screen problem. I am absolutely sure that there are many howtos online for this problem. I am very sure because I wrote a similar one for nearly the same bug related to a UEFI install of Ubuntu!

However when your computer works fine with another OS, when you can install Ubuntu without problems and when you can start your computer and the hdd or sdd seams to work and the only problem is a black screen?! Guys, guess what the problem might be in most cases? To give a broad hint "Dark screen" ?! Right, your graphic settings! So now you’re may thinking something like "Wow, you're such a wisenheimer hierstehtnormaleinname if you are so intelligent why did old Ubuntu versions work fine than and why did all the help solutions of other users don't work, hugh?". Because with every new version of Ubuntu some older graphic cards (chips) get moved from proprietary to standard drivers or something like that and because many other guys are just trying to be important and therefore they give ****** help posts.

So easiest way would be to load the "failSaveX" you can reach it by holding [shift] at start up and enter the additional start options of ubuntu and than the recovery mode. Just select failsafeX wait until it has finished and select reboot. If you are able to start Ubuntu now you should correct your graphic driver first and may adjust the display modes. There also some extra PPAs available like xorg edgers that offer a bigger range of g.card drivers.

If this won't help you you need to log in via text mode and change your group start option for example with nomodeset – but first try failsaveX and come back if it won't work for you!

Bye

Sorry for the late response, I've been away from my pc.

You're aware that the black screen doesn't occur on startup, but once as I was completing the ubuntu installation? I can't find ubuntu installed anywhere on my laptop. Holding shift while my computer boots doesn't do anything it all, on the motherboard screen or with the usb plugged in.

---

### Post by lewis-kimber7 on 2015-03-03
This is still an ongoing issue if anyone is able to offer a possible solution.

---

### Post by oldfred on 2015-03-03
While installer defaults to some minimal video actual install tries to be better. But that often causes issues.

And if UEFI you have to press escape key at UEFI boot before system starts, or if installed in BIOS boot mode you must hold shift key from BIOS until grub menu appears.

What video card/chip does your system have?
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by lewis-kimber7 on 2015-03-04
> **oldfred said:**
> While installer defaults to some minimal video actual install tries to be better. But that often causes issues.

And if UEFI you have to press escape key at UEFI boot before system starts, or if installed in BIOS boot mode you must hold shift key from BIOS until grub menu appears.

What video card/chip does your system have?

My laptop uses onboard graphics (CPU Intel Celeron).
Pressing either esc or holding shift before system boot doesn't do anything.

---

### Post by oldfred on 2015-03-04
Lets see boot configuration, run Summary report and post link it gives.

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by lewis-kimber7 on 2015-03-04
> **oldfred said:**
> Lets see boot configuration, run Summary report and post link it gives.

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[http://paste.ubuntu.com/10534348](http://paste.ubuntu.com/10534348)
Still no grub/sign of ubuntu on boot.

---

### Post by oldfred on 2015-03-04
What model Acer?

If you are not getting grub at all you may need one of the work arounds for those systems that only boot Windows. UEFI specifies you can boot anything, but vendors are modifying UEFI to only boot an entry with Windows in it.

       Video on getting into UEFI - 1 Min Acer but similar to all Windows 8
[http://www.youtube.com/watch?v=QGiG1oljjZI](http://www.youtube.com/watch?v=QGiG1oljjZI)


 Acer Aspire ES1-512-C39M Details on password and settings to enable trust on ubuntu entries
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)

Other work arounds like renaming bootx64.efi are in the link in my signature. Many have to use that rename.

---

### Post by lewis-kimber7 on 2015-03-05
My laptop is a Acer Aspire ES1-311.
Thank you!! I followed the instructions on the second link you provided and it's worked for me!
Quick question, 2 new boot options: "EFI File Boot 0: yes" and "EFI File Boot 1: Yesf" appeared in my boot priority order, I moved them to the top and the grub appears, but what are those 2 boot options? Do I need both?
My computer also won't shut down once I'm in ubuntu but I'll look around for a fix on that as thats another question, thanks a lot again for your help! I've been trying to get this working for so long with no luck previously.

---

### Post by oldfred on 2015-03-05
What model Acer?

Did you enable trust or password (never lose that)? At least some models of Acer have  UEFI passwords.
Also Boot-Repair says you have Windows fast boot or always on hibernation enabled. Best to turn that off.

 Acer Aspire ES1-512-C39M Details on password and settings to enable trust on ubuntu entries
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)


 Acer E3 requires UEFI password to allow added settings Post #8
[http://ubuntuforums.org/showthread.php?t=2253311](http://ubuntuforums.org/showthread.php?t=2253311)
Aspire E1-522 InsydeH20 Bios unlock -  7 min video
[https://www.youtube.com/watch?v=7SkBFkzOW0A](https://www.youtube.com/watch?v=7SkBFkzOW0A)

---

### Post by lewis-kimber7 on 2015-03-07
I had to set a pastword to enable ubuntu, and okay I'll turn fast boot off, thanks again for the help!

---

