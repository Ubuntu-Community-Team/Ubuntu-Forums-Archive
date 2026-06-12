---
title: "plymouth news"
date: 2010-02-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sgage on 2010-02-23
Well, as of today's updates, hitting "enter" no longer causes a system freeze - instead, I'm getting the login screen. I guess that's progress :(

Resuming from sleep is still broken, but now after doing the C-A-F1...C-A-F2 dance, I'm getting... the login screen. Is there a pattern here?

I removed plymouth, so I'm back to an ugly boot but no problems with the "enter" key.

---

### Post by jppr on 2010-02-23
i made fresh istallation and updates, so haven´t anymore problem with plymouth and enter key, system works fine. system run now nouveau-driver  and it also works just fine = )

---

### Post by sgage on 2010-02-23
Hmmm... maybe it's time for a fresh install. I'm using the nvidia drivers - couldn't get nouveau to work. Maybe I'll do a fresh install after A3 is officially released.

Other than the plymouth business and the resume problem, I am really liking Lucid. I just have to keep reminding myself... this is only an alpha!

---

### Post by Didius Falco on 2010-02-23
I reinstalled plymouth with the new updates and it works just fine so long as I leave it on the default theme.

I changed it to solar, with the required rebuild of initrd and it boots to a black screen. Pressing enter at this point brings me to the log-in screen with no problem.

I'll experiment with other themes and see how it goes.

It does seem a bit faster with plymouth than without it, but extra key-presses are the last thing I need. 

Still, there IS progress...

---

### Post by VMC on 2010-02-23
The problem with plymouth is you never know for sure. It took several re-boots for it to raise its ugly head.

Even when it froze my system, on the next re-boot it went through. Usually though, when it starts freezing, it then only works 25% of the time. 75% of re-boots, I have to power-cycle the computer.

 I'll keep a careful eye on the latest version.

---

### Post by frustphil on 2010-02-23
wait does this mean lucid is using playmouth instead of grub2?

---

### Post by xtoudi on 2010-02-23
> **frustphil said:**
> wait does this mean lucid is using playmouth instead of grub2?

Rather plymouth instead of xsplash - one of these two is a step after grub2.

---

### Post by Didius Falco on 2010-02-23
> **frustphil said:**
> wait does this mean lucid is using playmouth instead of grub2?

Plymouth and Grub2 are two different things.

Grub2 boots your whole PC - you can boot into various versions of Linux and/or Windows with it.

Plymouth is a graphical loader for Ubuntu 10.04 (well, it will be when they get it to work properly, but that's the whole idea behind Alpha/Beta software <G>).

So, for example, you start your PC and the Grub2 menu comes up. You choose the Ubuntu 10.04 option. Plymouth would then start and load Ubuntu 10.04 and take you to the log-in screen.

---

### Post by SevenMachines on 2010-02-23
> **Didius Falco said:**
> 
I changed it to solar, with the required rebuild of initrd and it boots to a black screen. Pressing enter at this point brings me to the log-in screen with no problem.

you might want to try changing your resolution in /etc/default/grub if you havent already. i think solar worked for me in 1024x768 but black screened in 640x480

---

### Post by xtoudi on 2010-02-23
> **SevenMachines said:**
> you might want to try changing your resolution in /etc/default/grub if you havent already. i think solar worked for me in 1024x768 but black screened in 640x480

Changing res in /etc/default/grub has impact ONLY for grub. Plymouth uses KMS (which is at kernel level) and it uses proper drivers with proper resolution.

---

### Post by Didius Falco on 2010-02-23
It worked fine the first time - subsequents boots were the ones that gave the black screen. I'm running at 1920x1080 (tks Santa!!).

I was going to uninstall it again, for now since splash screens, etc. are not important to me. The latest updates seems to have tied more dependencies into Plymouth. It wants to remove remastersys and ubiquity, which are tools I use frequently.

Looks like my fate is tied to plymouth now...

---

### Post by jppr on 2010-02-23
> **VMC said:**
> The problem with plymouth is you never know for sure. It took several re-boots for it to raise its ugly head.

Even when it froze my system, on the next re-boot it went through. Usually though, when it starts freezing, it then only works 25% of the time. 75% of re-boots, I have to power-cycle the computer.

 I'll keep a careful eye on the latest version.

as i said, i haven´t now any problem. = ) no problem wiht plymouth, no problem with enter key, no problem with boot or boot windows 7 (i have /dev/sda1 ubuntu 10.04 and /dev/sdb1 windows 7), no freezes. system works just fine now = )

---

### Post by NightwishFan on 2010-02-23
Plymouth "works" for me when I use the Nouveau driver. When I use Nvidia it sometimes causes a lockup and usually is full of graphical glitches. It also uses the stock "loading bar", which is expected.

Can someone tell me how I can send my usage data or perhaps logs from Plymouth to Canonical?

---

### Post by frustphil on 2010-02-23
> **xtoudi said:**
> Rather plymouth instead of xsplash - one of these two is a step after grub2.

Yes this is what I had in mind. :-)

---

### Post by ranch hand on 2010-02-23
I have no change in plymouth behavior.  I wish I would.  This is getting boring.

For those of us still getting the same old black screen deal.  If you update the initramfs before shutting down or rebooting it usually works.  This is updated when you run an update which is why, I think, a lot of people think it works for them.

If they rebooted a couple times it would probably fail.

The thing that really bugs me is that all my 10.04 installs are on the same drive and plymouth works on one of them perfectly.  I wonder what is wrong with that install.

---

### Post by NightwishFan on 2010-02-23
I am sure it will work better as time goes on. When I used Nouveau it worked perfectly on my Nvidia 6150SE.

---

