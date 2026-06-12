---
title: "Stripping down/building up ubuntu 11.04"
date: 2011-08-25
forum: Installation &amp; Upgrades
---

### Post by en_vort3x on 2011-08-25
I would like to build a custom ubuntu by starting from a minimal iso and building it to a unity/gnome desktop with only the packages I need, as I am booting from usb and default iso releases are far too large. 

I am mostly using it for coding and development.
Features I would like:
Ethernet
Python 3 and 2.7, c++/c
Basic mp3/audio player
Firefox
Unity/Gnome 2

The alternative is stripping down from the default iso's, but I think building up from the minimal will produce a cleaner os.

Eventually I hope to convert this to a full-blown how-to.

I will do some more research the coming few days too see what I can find, but if anyone can help so long with some hints, links and experience, please post.

Thanks

---

### Post by jerrrys on 2011-08-25
mini.iso hint:

do the terminal install (second choice)

after reboot do:

sudo apt-get update

sudo apt-get upgrade

sudo apt-get install gdm gnome-control-center gnome-terminal

that will give you the basic building blocks you need

good luck

---

### Post by en_vort3x on 2011-08-26
After installing the minimal command-line 11.04 (In virtual box) I can't get the system to boot. It seems as if the system is in fact running but the display is not working, as I am only getting a black screen.

I have googled around and can't seem to find any definitive answer as to the solution.

I have an ATI gfx card, which might be relevant as I know the drivers to give issues. I have however run the 11.04 full perfectly on this system.

After looking at the Grub options I see
"set gfxpayload=$linux_gfx_mode" in there.

Could this be something I could change to force the Xvesa driver or something to get into a working terminal to solve the issue?
I have no idea where to look or what to do?

UPDATE: found out ctrl+alt+f5 gives me a tty5 (terminal?) to log in to.

---

### Post by sanderd17 on 2011-08-26
If you want to start from something minimal, better start from Arch.

Once you set it up, you never have to do that effort again (it's rolling) and Arch has a great wiki full of information on how you can tweak your system.

Nothing against Ubuntu, but it isn't made for what you want. If you want to do-it-yourself, you should pick a do-it-yourself distro.

It would be different if you would want to repackage that OS as a new live CD (so that users of the live CD don't have to redo the process).

---

### Post by en_vort3x on 2011-08-26
> **jerrrys said:**
> mini.iso hint:

sudo apt-get upgrade

sudo apt-get install gdm gnome-control-center gnome-terminal

that will give you the basic building blocks you need

good luck

**What does the upgrade command do?**
 It upgrades the current linux kernel. Old kernels are kept in GRUB to boot from in case of kernel failure. (Is this statement correct?)
I would like the system to be as stable as possible, so I wouldn't want to upgrade the the absolute newest terminal, in case the new one borks out on me.

What does the gnome-control-center do?

---

### Post by sanderd17 on 2011-08-26
> **en_vort3x said:**
> What does the upgrade option do?

upgrade all packages to the most recent version
> 

what does the gnome-control-center give me? Does this install gnome 2 or gnome 3 desktop environment? If so, how would I go about changing it to a unity environment?

11.04 will give gnome2. If you want unity, you can just install the unity package (the same way). You can switch between the two at login time.

---

### Post by en_vort3x on 2011-08-26
> **sanderd17 said:**
> If you want to start from something minimal, better start from Arch.

Once you set it up, you never have to do that effort again (it's rolling) and Arch has a great wiki full of information on how you can tweak your system.

Nothing against Ubuntu, but it isn't made for what you want. If you want to do-it-yourself, you should pick a do-it-yourself distro.

It would be different if you would want to repackage that OS as a new live CD (so that users of the live CD don't have to redo the process).

I would in fact like to repackage this when done, and although you might be correct on Arch, I would like to try it in Ubuntu.

I am sure many beginners/intermediates would find this exploration useful once I have completed and documented it.

---

### Post by jerrrys on 2011-08-26
in vBox; once you boot you will only see a blank screen with a blinking cursor.  to get to terminal:

Host (right Ctrl key) + F2

edit:  after the install do a:

sudo reboot

---

### Post by jerrrys on 2011-08-26
[gnome control center]("http://packages.ubuntu.com/natty/gnome-control-center")

---

### Post by MAFoElffen on 2011-08-26
> **en_vort3x said:**
> After installing the minimal command-line 11.04 (In virtual box) I can't get the system to boot. It seems as if the system is in fact running but the display is not working, as I am only getting a black screen.

I have googled around and can't seem to find any definitive answer as to the solution.

I have an ATI gfx card, which might be relevant as I know the drivers to give issues. I have however run the 11.04 full perfectly on this system.

After looking at the Grub options I see
"set gfxpayload=$linux_gfx_mode" in there.

Could this be something I could change to force the Xvesa driver or something to get into a working terminal to solve the issue?
I have no idea where to look or what to do?

UPDATE: found out ctrl+alt+f5 gives me a tty5 (terminal?) to log in to.
In some ways... You are making this much harder than it really is...  I mod LiveCD's for users that are having problems, to automate steps they can't seem to grasp for their hardware.  I also tweak distro's.  

I do it manaully.  There is 2-3 good guides/tutorials that explain the in's and outs of that.  
```

[LiveCDCustomization - Community Ubuntu Documentation]("https://help.ubuntu.com/community/LiveCDCustomization")
[InstallCDCustomization - Community *Ubuntu* Documentation]("http://www.google.com/url?sa=t&source=web&cd=3&sqi=2&ved=0CCcQFjAC&url=https%3A%2F%2Fhelp.ubuntu.com%2Fcommunity%2FInstallCDCustomization&rct=j&q=ubuntu%20modifying%20live%20cd&ei=AfNXToyzIuvZiAL_oMWxCQ&usg=AFQjCNHGdkBWyLThi2o3MuxzLd6s1aw2Ig&cad=rja")
[How-To: Customize your *Ubuntu Live CD* | Debian/*Ubuntu* Tips ]("http://www.google.com/url?sa=t&source=web&cd=9&sqi=2&ved=0CHEQFjAI&url=http%3A%2F%2Fwww.debuntu.org%2Fhow-to-customize-your-ubuntu-live-cd&rct=j&q=ubuntu%20modifying%20live%20cd&ei=AfNXToyzIuvZiAL_oMWxCQ&usg=AFQjCNGZAAv6uNh6u2Yl3ZjkVO3BoEr0UQ&cad=rja")

```There are also a few good tools that make this easier for people just starting out with these kinds of things.  They both have a user inerface with check boxes to automate things for the user.
```

[Creating Custom *Ubuntu Live*-*CD* With Remastersys | *Ubuntu* Geek]("http://www.google.com/url?sa=t&source=web&cd=5&sqi=2&ved=0CEIQFjAE&url=http%3A%2F%2Fwww.ubuntugeek.com%2Fcreating-custom-ubuntu-live-cd-with-remastersys.html&rct=j&q=ubuntu%20modifying%20live%20cd&ei=AfNXToyzIuvZiAL_oMWxCQ&usg=AFQjCNGxEvFjKl9LqjkrjOkU2vcLInIlbg&cad=rja")

```Then there is another method that you setup the way you want your distro to be, with the app's you want--> then create an iso from it...
```

[LiveCDCustomizationFromScratch - Community *Ubuntu*]("http://www.google.com/url?sa=t&source=web&cd=3&sqi=2&ved=0CCcQFjAC&url=https%3A%2F%2Fhelp.ubuntu.com%2Fcommunity%2FLiveCDCustomizationFromScratch&rct=j&q=Creating%20Custom%20Ubuntu%20Live-CD&ei=ePVXTu6YH8bXiAK8wLG3CQ&usg=AFQjCNG7yeyL_qWCkQTBynKPkEfj4pV2kw&cad=rja")

```Outside of that... the problem you are having in Virtual Box and your X-Session... Remember that VirtualBox creates a virtual machine.  The hardware is virtual.  Most of the time a virtual machine is defined with an Intel Video GPU (even though you have different) unless the user defines it deferentially to use the hosts graphics GPU.  

If it is or if you need help diagnosing and fixing X, refer to this stcky:
**[B]Sticky:**[/B]                                      [COLOR=#008C00]**[all variants]**[/COLOR]                          [Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535")             

There is an Ubuntu Forum for LiveCD's and Disro's... but my experience with that forum is that I'm not sure how many people really keep an eye on it.  It's not really that active.  All my questions there have gone unanswered.  I had better luck asking here or in General Help.

If you do have any questions, just ask in this thread.  If I can help, I'll try to watch this thread and share what I can/when I can.

---

### Post by en_vort3x on 2011-08-26
Thanks for awesome information. It is really helpful, will keep me away from here, reading, for a while :D.

I know there are much easier ways, but I would still like to try this as both an experiment and  a learning experience for me.

I would really like to get involved with the Ubuntu community, and the linux community in general I guess. Anyway, thanks for the help. I will clean up this thread as I go along and eventually, if people are interested turn it into a how-to for building your own from scratch. 

So far it seems that you are right though, it would be much easier just working from a live cd and removing/adding packages, as there are many little packages and things that are nice to have, but hard to find and how to install them.

---

### Post by en_vort3x on 2011-08-26
I am having some trouble using the synaptic package manager.
Opening it with 
**$sudo synaptic**
works perfectly after typing in my password, but
launching synaptic from the gnome/ubuntu menu under administrative
also asks for administrator password, but it won't accept the one I use for sudo? This has to be an error as I have used Synaptic often in all my normal ubuntu installations?

I am having the same problem with all adminstrative applications like software sources,synaptic etc.

---

### Post by MAFoElffen on 2011-08-26
> **en_vort3x said:**
> I am having some trouble using the synaptic package manager.
Opening it with 
**$sudo synaptic**
works perfectly after typing in my password, but
launching synaptic from the gnome/ubuntu menu under administrative
also asks for administrator password, but it won't accept the one I use for sudo? This has to be an error as I have used Synaptic often in all my normal ubuntu installations?
Using "gksudo" instead of "sudo" will carry the previlegdes over through gnome... i.e.:
```

~$ gksudo synaptic

```

---

### Post by en_vort3x on 2011-08-26
```
$gksudo synaptic
```
Opens synaptic, then there is a window that says "granting rights", which goes away and I can use synaptic as normal. This however seems to have no effect different from 
```
$sudo synaptic
```
The same problem still persists: it says password invalid when openening from administrative in main menu. Same for all other admin tools.

---

### Post by MAFoElffen on 2011-08-26
> **en_vort3x said:**
> ```
$gksudo synaptic
```Opens synaptic, then there is a window that says "granting rights", which goes away and I can use synaptic as normal. This however seems to have no effect different from 
```
$sudo synaptic
```The same problem still persists: it says password invalid when openening from administrative in main menu. Same for all other admin tools.
Is this in your virtual install of Ubuntu?  On the admin previledged user that you set up during the install?

(Sorry for the wait-- doing server maintenance.)

---

### Post by mörgæs on 2011-08-27
[http://andyduffell.com/techblog/?p=689](http://andyduffell.com/techblog/?p=689)

---

### Post by en_vort3x on 2011-08-28
> **MAFoElffen said:**
> Is this in your virtual install of Ubuntu?  On the admin previledged user that you set up during the install?

(Sorry for the wait-- doing server maintenance.)

Sorry for the delay in answer. Yes to both questions.

---

### Post by en_vort3x on 2011-08-28
> **mörgæs said:**
> [http://andyduffell.com/techblog/?p=689](http://andyduffell.com/techblog/?p=689)

Thanks this has proven to be very helpful. Im currently editing the script to produce my own version. This is exactly the type of thing I am looking for. I think what I'd like to do is Remastersys an iso with ubuntu minimal, and then include the packages in the script, and then have the script automatically execute after installation, or something similar.

---

### Post by cbowman57 on 2011-08-28
First, I'd recommend that you don't try to do this in a virtual machine.
Second, much easier to start with a live iso and modify it with UCK.
Third, unless you are extremely familiar with Ubuntu, building from a minimal iso is going to take a lot of trial & error.

Good luck.

---

### Post by jerrrys on 2011-08-28
> **cbowman57 said:**
> 
Third, unless you are extremely familiar with Ubuntu, building from a minimal iso is going to take a lot of trial & error.

Good luck.

the way l like to put it:

reinventing the wheel is not so easy :)

if you would like to post your script for review, i bet a lot of people would take a look

---

### Post by cbowman57 on 2011-08-28
> **jerrrys said:**
> the way l like to put it:

reinventing the wheel is not so easy :)

if you would like to post your script for review, i bet a lot of people would take a look

Exactly, I've done it with Ubuntu, Debian & Arch but I've been using Ubuntu for a couple days and have become intimately familiar with what packages are required for a graphical DE.   That being said, every time I do it is a learning experience. :)

---

### Post by jerrrys on 2011-08-28
[http://ubuntuforums.org/showthread.php?p=11196239#post11196239](http://ubuntuforums.org/showthread.php?p=11196239#post11196239)

---

### Post by mörgæs on 2011-08-29
> **en_vort3x said:**
> Thanks this has proven to be very helpful. Im currently editing the script to produce my own version. This is exactly the type of thing I am looking for. I think what I'd like to do is Remastersys an iso with ubuntu minimal, and then include the packages in the script, and then have the script automatically execute after installation, or something similar.

You are welcome. I guess Andy D would be happy, if you share your findings with him. 


Here is some more reading:
[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)
The oldest part of the thread is for obsolete Ubuntu releases, but in the newer part you might find some inspiration.

---

### Post by cbowman57 on 2011-08-29
One method I tried included installing a minimal base, copying in a sources.list list & a script from another installation and building a system with dpkg, worked pretty well if I remember right.  Not sure if I tried it with Ubuntu, but it worked well with Debian so it should work with Ubuntu.

When you get a system customized just the way you want it look at the export options in synaptic.

---

### Post by en_vort3x on 2011-08-29
Just looking at the amount of people willing to help is why I would like getting more involved with Ubuntu community.

That aside, I am still having trouble with the following issue.

> **en_vort3x said:**
> ```
$gksudo synaptic
```
Opens synaptic, then there is a window that says "granting rights", which goes away and I can use synaptic as normal. This however seems to have no effect different from 
```
$sudo synaptic
```
The same problem still persists: it says password invalid when openening from administrative in main menu. Same for all other admin tools.

Can anyone help with the above?

It is nearly University vacation for me and then I will really give all the suggestions a go. For now I am progressing quite slowly. I have been trying various installs and customizing live CDs and tweaking on the minimal build. I am also considering lubuntu, and revisiting my previous attempt at Slitaz, now that I have access to more stable internet.

---

### Post by jerrrys on 2011-08-30
i don't know if its loaded or not, so open a terminal and enter:

sudo apt-get install gconf-editor

then (still in terminal) enter:

gconf-editor

and navigate to

Apps>gksu>sudo mode

and check that box

---

### Post by en_vort3x on 2011-08-30
> **jerrrys said:**
> i don't know if its loaded or not, so open a terminal and enter:

sudo apt-get install gconf-editor

then (still in terminal) enter:

gconf-editor

and navigate to

Apps>gksu>sudo mode

and check that box

Thanks Jerry, this worked!

(random question, I know it's rather trivial)
Is it general practice to respond to any successful answers posted by members on these forums? It makes the thread much longer, but as there is no credit system like Stackoverflow, should I just take the advice and not thank.

---

### Post by mörgæs on 2011-08-30
It is good practice to respond to the answers indicating what worked and what did not. This will help other people reading the thread.

---

### Post by jerrrys on 2011-08-30
congratulations and don't forget to to install "ubuntu-restricted-extras"

---

### Post by en_vort3x on 2011-08-31
Thanks Jerrys.
I have yet another question:
I am trying to edit files, I use vim and/or gedit, but neither will allow me to create or edit files, only if I open it with sudo.
Clearly I did something wrong with the permission and account setup on install, but I don't know what it is or how to fix it.

I am planning on a re-install once I have trial-and-errored by way into a satisfactory setup, but for the moment this permission issue is turning out a bit of a hassle. Any idea as to the root :P of my problem?

---

### Post by mörgæs on 2011-08-31
It seems that the system is behaving like it should. No need to reinstall.

If you are editing a system file, no matter which tool you use, Ubuntu wants a confirmation (=the sudo command) that you really want to do so. 

You should be able to edit user files without sudo.

You can read more about permissions in the manual in my signature.

---

### Post by jerrrys on 2011-08-31
> **en_vort3x said:**
> I am trying to edit files, I use vim and/or gedit, but neither will allow me to create or edit files, only if I open it with sudo.
Clearly I did something wrong with the permission and account setup on install, but I don't know what it is or how to fix it.

you are the owner of home and can create and edit your home files.  all other files are owned by "root" and will require sudo.

---

