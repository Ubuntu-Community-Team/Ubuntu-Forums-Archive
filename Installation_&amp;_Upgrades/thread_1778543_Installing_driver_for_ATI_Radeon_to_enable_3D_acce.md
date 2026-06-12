---
title: "Installing driver for ATI Radeon to enable 3D acceleration"
date: 2011-06-09
forum: Installation &amp; Upgrades
---

### Post by psydex on 2011-06-09
I'm trying to install driver for ATI Radeon x550 to enable 3D acceleration so i can run Unity.
I'm currently using Ubuntu 11.04 (classic view)
A looked at this article [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) but i didn't understand what exactly should i do to install it.

PS: I tryed the driver downloaded from the ATI's website but i get this error:


```
peppo@ubuntu:~/&#1055;&#1083;&#1086;&#1090;$ ./ati-driver-installer-9-3-x86.x86_64.run
Created directory fglrx-install.EadNMC
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.593...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:x86_64:lib32::none:2.6.38-8-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.EadNMC
```

What should i do? Any help? Command?

---

### Post by coffeecat on 2011-06-09
Hi, and welcome to the forum.

You won't be able to get the proprietary fglrx/catalyst driver working with your card which ATI now consider a legacy one. They dropped support in the proprietary driver in 2009. See:

[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.7&product=2.7.4.3.3.3.1&lang=English)

The link you posted is interesting. It doesn't list your X550 specifically in the good 3d support category, but it does list the X300 which has the same RV370 code as yours, according to this:

[http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units#PCIe_.28X3xx.2C_X5xx.2C_X6xx.2C_X10xx.29](http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units#PCIe_.28X3xx.2C_X5xx.2C_X6xx.2C_X10xx.29)

Which suggests that you should be able to get 3d acceleration with the default open source driver. However, Unity is more demanding and your card may simply not be capable of running Unity even if you can get some compiz effects in the classic gnome desktop.

Open a terminal and run this command and post the output:

```

/usr/lib/nux/unity_support_test -p
```

---

### Post by ajgreeny on 2011-06-09
> **coffeecat said:**
> The link you posted is interesting. It doesn't list your X550 specifically in the good 3d support category, but it does list the X300 which has the same RV370 code as yours, according to this:

[http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units#PCIe_.28X3xx.2C_X5xx.2C_X6xx.2C_X10xx.29](http://en.wikipedia.org/wiki/Comparison_of_ATI_Graphics_Processing_Units#PCIe_.28X3xx.2C_X5xx.2C_X6xx.2C_X10xx.29)

Which suggests that you should be able to get 3d acceleration with the default open source driver. However, Unity is more demanding and your card may simply not be capable of running Unity even if you can get some compiz effects in the classic gnome desktop.
This is, I believe the important point of the problem.

I have an old radeon card (9200SE) which runs compiz wonderfully in 10.04 and 10.10 using the open source driver, but there is no way I can get unity running, so I still have no way to properly test how good, bad, (or even hateful, as some seem to think) it is, and can only go by what many people are saying on these forums and other places.

I realise that gnome2 with its old fashioned panels is going very soon so something else had to take its place, but after the debacle of KDE3.5 to KDE4 why did they try to make such a quantum leap and upset so many users.

You may have gathered from this that I'm an old fashioned guy, who still likes the panel setup.  I know its been around since the year dot, but so what?  It still works for the great majority of people, and we do not all live by social networking sites and "the cloud"; in fact I mistrust cloud computing and still do not even use Ubuntu-one. preferring to keep all my files here with me, rather than somewhere out "there" in the ether.

---

### Post by coffeecat on 2011-06-09
> **ajgreeny said:**
> This is, I believe the important point of the problem.

I have an old radeon card (9200SE) which runs compiz wonderfully in 10.04 and 10.10 using the open source driver, but there is no way I can get unity running, so I still have no way to properly test how good, bad, (or even hateful, as some seem to think) it is, and can only go by what many people are saying on these forums and other places.


That's a useful observation. I was involved in a thread the other day where the OP, (using an onboard ATI graphics chipset which is never as satisfactory as a dedicated card anyway) was able to get good compiz 3d acceleration in the Natty classic desktop using the proprietary fglrx driver, but Unity struggled. It worked, sort of, but lagged badly. From what that OP said, from what you say and from what the OP of this thread has told us so far, I believe the extra demands of Unity are just too much for some of the older cards. Unity is a compiz plugin, so you have that running as well as any compiz effects already enabled.

It's a sad fact but true that legacy hardware gets left behind with newer versions of operating systems. It's true of Windows; it's true of Apple MacOS and it's true of other Linux distros, not just Ubuntu. I'm sorry that you haven't been able to try Unity out, because it is worth trying out. I've noticed an interesting phenomenon. There are an increasing number of posts where the poster says that at first they did not like Unity, but that it has grown on them and now they prefer it. That was my experience.

---

### Post by psydex on 2011-06-10
> **coffeecat said:**
> Open a terminal and run this command and post the output:

```

/usr/lib/nux/unity_support_test -p
```

This is the result:
```
peppo@ubuntu:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   X.Org R300 Project
OpenGL renderer string: Gallium 0.4 on ATI RV370
OpenGL version string:  2.1 Mesa 7.10.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes

```

I'm currently using Ubuntu as a classic view but also without effects. Both (Unity and Ubuntu classic with effects) can't load the dektop and i'm asuming this is caused by the lack of drivers.

---

### Post by coffeecat on 2011-06-10
According to the output from unity_support_test your card can run Unity (and compiz) with the default driver. At least in theory. What happens when you try to log in to Unity ("Ubuntu" at the login screen)? Do you get an error message or does it just dump you into gnome classic? Also - you say you can run classic gnome but without effects. What have you tried? The old effects tab from the Appearance settings utility has been deprecated. You need to install compizconfig-settings-manager to adjust any compiz settings.

However, try this. In the classic desktop open a terminal. Move it so that it is over a desktop icon or another open application. Is it semi-transparent, or just solid purple so that you can see nothing through it?

**EDIT**: sorry, I should have been clearer. When you say:

> I'm currently using Ubuntu as a classic view but also without effects.  Both (Unity and Ubuntu classic with effects) can't load the dektop and  i'm asuming this is caused by the lack of drivers.

... does that mean that at the login screen when you have the choice of "Ubuntu", "Ubuntu Classic" and "Ubuntu Classic (No effects) that you can only log in to the last of those?

---

### Post by psydex on 2011-06-10
> **coffeecat said:**
> **EDIT**: sorry, I should have been clearer. When you say:

... does that mean that at the login screen when you have the choice of "Ubuntu", "Ubuntu Classic" and "Ubuntu Classic (No effects) that you can only log in to the last of those?

**Exactly! **
And yes , the background is solid (terminal isn't semi-transparent).

Also i don't get any error messages on the other two choices (Unity & Ubuntu Classic) but **no** desktop icons / buttons / toolbars or whatever it is appear - just the wallpaper and that's all

---

### Post by coffeecat on 2011-06-10
> **psydex said:**
> **Exactly! **
And yes , the background is solid (terminal isn't semi-transparent).

Also i don't get any error messages on the other two choices (Unity & Ubuntu Classic) but **no** desktop icons / buttons / toolbars or whatever it is appear - just the wallpaper and that's all

OK, thanks for the clarification.

Going by the output of unity_support_test your card *should* be OK for Unity but this isn't your experience. We need to see if the unity_support_test output is misleading or if something has happened to the configuration of your installation. Do you still have a live CD or live USB of Ubuntu 11.04? Try booting up with it and choose "try Ubuntu" in order to get to a desktop. Does it load Unity or does it fall back to a classic gnome desktop, and if it does the latter, with or without effects?

---

### Post by psydex on 2011-06-10
> **coffeecat said:**
> OK, thanks for the clarification.

Going by the output of unity_support_test your card *should* be OK for Unity but this isn't your experience. We need to see if the unity_support_test output is misleading or if something has happened to the configuration of your installation. Do you still have a live CD or live USB of Ubuntu 11.04? Try booting up with it and choose "try Ubuntu" in order to get to a desktop

Actualy i'm using Wubi to Dual-Boot with Windows XP SP3.
Could that be the reason?

> **coffeecat said:**
> Does it load Unity or does it fall back  to a classic gnome desktop, and if it does the latter, with or without  effects?
As i said - it just shows the wallpaper without loading or doing/loading absolutely anything.

---

### Post by coffeecat on 2011-06-10
> **psydex said:**
> Actualy i'm using Wubi to Dual-Boot with Windows XP SP3.
Could that be the reason?

I don't believe so, but I'm not 100% sure.

> **psydex said:**
> As i said - it just shows the wallpaper without loading or doing/loading absolutely anything.

No - that's with your permanent Wubi installation. My question was trying to find out what you see by running the live CD live. Let me explain. When confronted with a puzzling situation like this when something doesn't behave as it *should*, it is always a useful exercise to run the Ubuntu CD live to see how a default installation behaves with your particular hardware combination. Configuration changes since you installed, possibly through updates, or even your unsuccessful attempt to install the catalyst driver, could have made changes affecting the ability of your system to run compiz/Unity. If you run the CD live and can't get Unity or effects in the classic desktop, then the conclusion is that your graphics card isn't able to, whatever unity_support_test says about it. If the live CD does give you Unity/effects then we can concentrate on whatever may have gone wrong in your permanent installation.

If you have fast broadband and don't mind using about 700MB of your download allowance, dl the Natty ISO from here:

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

Burn it to CD as described here:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Change the boot order in your BIOS (if necessary) so that it boots from CD/DVD before hard drive, and boot up with the CD. It is much slower than from hard drive, but after a couple of minutes or so you are presented with the choice of try Ubuntu or install Ubuntu. Choose try Ubuntu and you will be taken to the live desktop. Tell us what you see - Unity or classic gnome, with or without effects?

---

### Post by psydex on 2011-06-10
> **coffeecat said:**
> When confronted with a puzzling situation like this when something doesn't behave as it *should*, it is always a useful exercise to run the Ubuntu CD live to see how a default installation behaves with your particular hardware combination. Configuration changes since you installed, possibly through updates, or even your unsuccessful attempt to install the catalyst driver, could have made changes affecting the ability of your system to run compiz/Unity. If you run the CD live and can't get Unity or effects in the classic desktop, then the conclusion is that your graphics card isn't able to, whatever unity_support_test says about it. If the live CD does give you Unity/effects then we can concentrate on whatever may have gone wrong in your permanent installation.

If you have fast broadband and don't mind using about 700MB of your download allowance, dl the Natty ISO from here:

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

Tell us what you see - Unity or classic gnome, with or without effects?

Actualy non of them! So i did exactly what you told me to do.
I burned a CD with the distribution and i booted from it. When i pressed the "Try Ubuntu" button it started to load files (i hear the CD working). Then appeared top toolbar with couple of icons on the right (ONLY) like shutdown / wi-fi etc. Then screen went black with the mouse on it (ONLY) - i heard the welcome Ubuntu sound but still black screen. I waited 10-15 more minutes to eventualy load something but all i get was the black screen with a mouse on it. Tryed that twice - same effect.

*I can attach video of what i said above if you want me to.*

---

### Post by coffeecat on 2011-06-10
It sounds as though it's trying but failing to load the Unity desktop. First thing, how much RAM do you have?

Anyway, boot up the CD again and when you hear the Ubuntu welcome sound and you have only a black screen with a mouse pointer, press AltGr-Print-k. Hopefully you will be taken to a log in screen. Start the login with "ubuntu" for username but before you try a password, choose the classic desktop with effects. The password is blank for the live session, so just press enter. Do you get taken to a live desktop with effects?

If not, press AltGr-Print-k again. Do the same but choose classic desktop without effects.

I think this will test what your graphics card is capable of with 11.04. That is, so long as you have adequate RAM.

---

### Post by psydex on 2011-06-10
> **coffeecat said:**
> It sounds as though it's trying but failing to load the Unity desktop. First thing, how much RAM do you have?
I got 512MB of RAM (i know it's not much) , Pentium 4 3.2 GHz
I'll do what you told me but can you clarify **AltGr-Print-k**?

---

### Post by coffeecat on 2011-06-10
> **psydex said:**
> I got 512MB of RAM (i know it's not much) , Pentium 4 3.2 GHz
I'll do what you told me but can you clarify **AltGr-Print-k**?

512MB used to be enough to run gnome in previous versions, but I really don't know whether it's enough for 11.04. It should be if you have swap enabled, but I'm not sure.

AltGr is the alt key to the right of the spacebar. Print is the key labelled Print, PrtScn or SysReq and the k key is the k key in the main part of the keyboard. If you press them together, it kills the xserver and all running applications and takes you to the login screen. What I do is to press the AltGr key first and hold it down and then press Print and k together with whatever fingers can reach.

---

### Post by psydex on 2011-06-10
> **coffeecat said:**
> 512MB used to be enough to run gnome in previous versions, but I really don't know whether it's enough for 11.04. It should be if you have swap enabled, but I'm not sure.
Yeah , i runned Ubuntu 9.04 before and it runs perfect. I also got SWAP enabled - i hope it will work (somehow).


> **coffeecat said:**
> AltGr is the alt key to the right...Print is the key  labelled Print and the k ...
Yeah i thought so but i wanted to be sure (ALT+PrtScr+K) . Thanks

---

### Post by psydex on 2011-06-10
You should tell me to use "ubuntu" as a username - i didn't knew that but i figured it out.

Anyways , now for the results:
I get absolutely _the same behavior_ from the Live CD as the alredy installed distribution!

**Ubuntu** - only wallpaper without anything else
**Ubuntu (classic)** - only wallpaper with "loading cursor"
**Ubuntu (classic without effects)** - loads perfectly normal

---

### Post by coffeecat on 2011-06-10
> **coffeecat said:**
> IAnyway, boot up the CD again and when you hear the Ubuntu welcome sound and you have only a black screen with a mouse pointer, press AltGr-Print-k. Hopefully you will be taken to a log in screen. Start the login with [SIZE=3]**"ubuntu"**[/SIZE] for username but before you try a password, choose the classic desktop with effects. The password is blank for the live session, so just press enter

> **psydex said:**
> You should tell me to use "ubuntu" as a username - i didn't knew that but i figured it out.

:wink:

> **psydex said:**
>  Anyways , now for the results:
I get absolutely _the same behavior_ from the Live CD as the alredy installed distribution!

**Ubuntu** - only wallpaper without anything else
**Ubuntu (classic)** - only wallpaper with "loading cursor"
**Ubuntu (classic without effects)** - loads perfectly normal

Well - disappointing result, but at least you've established that your system definitely won't run Unity or classic gnome with effects in a default install. As I mentioned before you needed to go through that rigmarole to be sure that some configuration on your installed system was not at fault.

We are left with that slightly perplexing unity_support_test result of "Unity supported:          yes". I don't believe it is misleading - it means that the graphics card/driver combination passed the parameters needed to run compiz. There must be some other factor in your hardware preventing this. The only things I can think of are insufficient RAM (possible but unlikely) or some problem with the BIOS.

If it's the latter I think we've nearly reached the end of the line. Except I've one last thing to suggest but I'm not sure how you do this with a wubi install so let's try with the live CD. Sorry about that - I know it's tedious.

Start the live CD but as soon as you see the purple screen with two small icons at the bottom of the screen, tap the spacebar. Choose your language and you will be taken to a text menu. Now press F6 ("Other Options"), move the highlight with the arrow key and select "nomodeset" with the enter key. Press ESC to close the F6 menu and now select the first option, "Try Ubuntu without installing". What happens now? Can you get Unity or desktop effects with classic gnome?

---

### Post by psydex on 2011-06-10
> **coffeecat said:**
> If it's the latter I think we've nearly reached the end of the line. Except I've one last thing to suggest but I'm not sure how you do this with a wubi install so let's try with the live CD. Sorry about that - I know it's tedious.

Start the live CD but as soon as you see the purple screen with two small icons at the bottom of the screen, tap the spacebar. Choose your language and you will be taken to a text menu. Now press F6 ("Other Options"), move the highlight with the arrow key and select "nomodeset" with the enter key. Press ESC to close the F6 menu and now select the first option, "Try Ubuntu without installing". What happens now? Can you get Unity or desktop effects with classic gnome?

Yeah it runs all 3 of them:
**Ubuntu** - looks just like classic without the launcher tho.. (i still haven't seen the launcher for real)
**Ubuntu** (classic) with and without effects

PS: Sorry for that "ubuntu" username ..thing ... Looks like i missed out that part

---

### Post by coffeecat on 2011-06-10
> **psydex said:**
> Yeah it runs all 3 of them:
**Ubuntu** - looks just like classic without the launcher tho.. (i still haven't seen the launcher for real)
**Ubuntu** (classic) with and without effects

PS: Sorry for that "ubuntu" username ..thing ... Looks like i missed out that part

Don't worry about the "ubuntu". :) When you see me using the winking smiley it means I'm teasing - or at least not being serious - and am in a good mood!

Anyway... We have semi-progress. You have the classic desktop with effects but you aren't getting the proper Unity. I think it would be safe to add "nomodeset" to your boot options permanently but I'm hesitant to suggest this until you've tried booting with nomodeset as a temporary boot option in your Wubi system, just in case there is a complication I haven't thought of.

It's been some time since I tried wubi, so I have a question. After the inital boot menu (which is the Windows boot.ini or equivalent one), do you get a grub menu to choose either to boot normally or recovery mode or memtest? If you do, try this:

Select the first entry to boot normally but don't press enter. Press the 'e' key to edit that entry. Move the cursor to the end of the line that starts "linux". It will end with either "quiet splash" or "quiet splash vt.handoff=7". Type in a space after the last option and then "nomodeset" (no quotes though). Now press ctrl-X to boot. See if you can get Unity. I'm hoping you might because the live CD session is more RAM hungry and you will have more memory available in your wubi install.

Post back with what you find and if that works, or half works, I'll explain how to add that as a permanent boot option.

---

### Post by psydex on 2011-06-11
> **coffeecat said:**
> After the inital boot menu (which is the Windows boot.ini or equivalent one), do you get a grub menu to choose either to boot normally or recovery mode or memtest? If you do, try this:

Select the first entry to boot normally but don't press enter. Press the 'e' key to edit that entry. Move the cursor to the end of the line that starts "linux". It will end with either "quiet splash" or "quiet splash vt.handoff=7". Type in a space after the last option and then "nomodeset" (no quotes though). Now press ctrl-X to boot. See if you can get Unity. I'm hoping you might because the live CD session is more RAM hungry and you will have more memory available in your wubi install.

Post back with what you find and if that works, or half works, I'll explain how to add that as a permanent boot option.

So we made 2 pages discussing and trying to solve the problem to finaly get this message appeared...#-o
[[IMG]http://i.imgur.com/F1GJo.jpg[/IMG]]("http://imgur.com/F1GJo")

---

### Post by coffeecat on 2011-06-11
Yes, that's very disappointing. Is that with your wubi install and do you at least get ubuntu classic with effects? If so, I can tell you how to make the nomodeset option permanent.

I came across another thread where someone was using nomodeset with an ATI card with some other options. But this was for a different issue. It might be worth searching the forum for your particular card. Someone may have got this working with a particular mix of boot options.

---

### Post by psydex on 2011-06-11
> **coffeecat said:**
> Yes, that's very disappointing. do you at least get ubuntu classic with effects?


Unfortunately - no!
Looks like i'll stick with Ubuntu 9.04 at least until i upgrade my machine :-k

PS: Kubuntu works a bit choppy but it runned on first try on my PC tho.

---

### Post by coffeecat on 2011-06-11
I hope you mean 10.04, not 9.04! 9.04 has passed-end-of-life and has been unsupported for some months now.

Good luck with whatever you decide. I'm sorry we weren't able to get Unity working on that machine. Perhaps when you upgrade the machine 11.10 will be out and there are expectations that Unity will be much improved in 11.10, good though it already is.

---

### Post by psydex on 2011-06-11
> **coffeecat said:**
> I hope you mean 10.04, not 9.04! 9.04 has passed-end-of-life and has been unsupported for some months now.

Good luck with whatever you decide. I'm sorry we weren't able to get Unity working on that machine. Perhaps when you upgrade the machine 11.10 will be out and there are expectations that Unity will be much improved in 11.10, good though it already is.

I actualy ment 9.04 because i got it on CD - i didn't knew it's unsupported.
Will 10.04/10.10 be running smooth on my machine (like 9.04 used to)?

Also , thank you for being so helpful! I appreciate that - a lot!

---

### Post by coffeecat on 2011-06-11
I hope that 10.04 and 10.10 will work smoothly. One thing to be aware of is that the open source ATI driver was less capable back in 9.04 days and may not give you 3d/compiz- or it might with your card, but certainly the ATI driver in the later versions of Ubuntu is better. I know compiz is a bit of a sore point at the moment but the version of the ATI driver in 10.04/10.10 will hopefully give you that, which is always nice to have.

I'm afraid the only way of finding out if it runs smoothly is to download it and try it from the live CD. It's always a bit of a gamble if you do a wubi install without knowing whether the version you're installing will work with your hardware - as you've found out the painful way.

And - you're welcome. :)

---

### Post by psydex on 2011-06-11
I'm about to find out right now if 10.10 will work. Wish me luck :)

---

### Post by coffeecat on 2011-06-11
Good luck! :wink:

---

### Post by psydex on 2011-06-11
Ok , so i got quite the same problem with 10.10 but it **works** pretty good with the "nomodeset" command! YAAAAAAY !!:KS Could you tell me how to make it permanent?

---

### Post by coffeecat on 2011-06-11
OK.  Open a terminal, and :

```
gksudo gedit /etc/default/grub
```You'll see that the first few lines of the file are:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```Change the GRUB_CMDLINE_LINUX_DEFAULT line so that it shows:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```Save the file and close gedit. Now, from the terminal:

```
sudo update-grub
```And the nomodeset option should stick. Let us know if that works OK.

---

### Post by psydex on 2011-06-11
> **coffeecat said:**
>  Let us know if that works OK.
Yes it's all okay now! Thank you

---

### Post by DougieFresh4U on 2011-06-11
> **psydex said:**
> You should tell me to use "ubuntu" as a username - i didn't knew that but i figured it out.


He/She did :p:p

> **coffeecat said:**
> It sounds as though it's trying but failing to load the Unity desktop. First thing, how much RAM do you have?

Anyway, boot up the CD again and when you hear the Ubuntu welcome sound and you have only a black screen with a mouse pointer, press AltGr-Print-k. Hopefully you will be taken to a log in screen. **[B]Start the login with "ubuntu" for username but before you try a password**[/B], 

Just being a 'smarty pants'

---

### Post by coffeecat on 2011-06-11
> **psydex said:**
> Yes it's all okay now! Thank you

Excellent. Good luck! :)

---

