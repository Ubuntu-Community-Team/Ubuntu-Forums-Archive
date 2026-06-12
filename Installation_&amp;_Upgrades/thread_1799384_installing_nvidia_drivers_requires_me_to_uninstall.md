---
title: "installing nvidia drivers requires me to uninstall 40 of my programs?"
date: 2011-07-07
forum: Installation &amp; Upgrades
---

### Post by xsk3l3t0rx on 2011-07-07
so i woke up this morning to find synaptic telling me to install a bunch of updates, so i did. computer restarts after so i let it, except now it wont make it to the login screen. there is just a horizontal white line and the screen looks like ****. so i reboot and hold shift to enter grub and boot in recovery low-gfx mode. i find out that in this *update* i uninstalled my nvidia graphics.. my setup was awesome for like 2 months solid, and i was loving ubuntu. 

heres the problem: ok, fine, so my nvidia drivers are gone. i can live with that, so i go into synaptic to reinstall the newest 275.xx.xx drivers, and synaptic informs me that i need to uninstall 40 packages to install my nvidia drivers! and of the 40, they were all my important programs, like my game emulators, ubuntu-desktop, gnome, compiz, boxee, vlc, XORG!!!, etc.. why the hell do i have to uninstall all this crap just for nvidia drivers? i've never in like 5 years using ubuntu had to do that... someone plz help i have to go to work but i'll check the replies via email.. btw im in recovery mode now as i type this.. id rather not start from scratch again... oh btw my computer is an asus eeepc 1015pn

---

### Post by ninfalara on 2011-07-07
[FONT=Trebuchet MS][SIZE=2]I have the EXACT same problem here!  I'm using Kubuntu 11.04 64 bit and when I try to install the nvidia driver it's telling me to uninstall pretty much everything related to kubuntu-desktop (amarok, dolphin, kate, kmail, konsole, kubuntu-desktop... you name it)  [/SIZE]


[SIZE=1][COLOR=DimGray]Kubuntu 11.04 64 bit 
Kernel Linux 2.6.38-8-generic  

CPU AMD Phenom II X2 550
RAM 3.9 GB 
GPU Nvidia Geforce 9800 GT[/COLOR][/SIZE][/FONT]

---

### Post by coffeecat on 2011-07-07
> **xsk3l3t0rx said:**
> i go into synaptic to reinstall the newest 275.xx.xx drivers,

nvidia-current in 11.04 is 270.41.06. Where did you get 275 from? Backports repository, a PPA repository or from the nvidia site?

---

### Post by ninfalara on 2011-07-07
[coffeecat]("http://ubuntuforums.org/member.php?u=129087")'s reply made me realize I missed pointing out that I didn't try to install that package but nvidia-current.

---

### Post by coffeecat on 2011-07-07
> **ninfalara said:**
> [coffeecat]("http://ubuntuforums.org/member.php?u=129087")'s reply made me realize I missed pointing out that I didn't try to install that package but nvidia-current.

This doesn't help you much, but I have an Ubuntu 11.04 (not Kubuntu) system fully-updated as of a few minutes ago, with the nvidia-current package installed. It didn't want to uninstall anything. The other difference from yours is that I installed nvidia-current about a month ago and have had many updates since then, but without problems.

Do you have any 3rd-party repositories enabled, or Backports or Proposed?

---

### Post by xsk3l3t0rx on 2011-07-07
I added a swat ppa or somethi g like that to allow me to install 275. Nvidias site offers a 275 driver as the latest driver, however ubuntu only shows 270, so i added that repository so i could install it via synaptic.. Should i just remove the repository and just try reinstallig 270? 275 was running fine on my computer before todays uPdates, but for some reason during the updates it said thr nvidia drivers had to be uninstalled, and i didnt see any options to keep it. So here i am running in recovery mode. Ubuntu is stupid sometimes. Any help?

---

### Post by coffeecat on 2011-07-08
> **xsk3l3t0rx said:**
> Ubuntu is stupid sometimes.

No, Ubuntu is not stupid. It is an operating system. 

The reason I asked about PPAs and 3rd-party repositories is that if you experience strange dependency or package conflicts such as you are experiencing then that is the first place to look. If you confine yourself to the "official" repositories then you are very unlikely to get this sort of thing, since considerable QA is done before updates are released. That is not necessarily the case with PPAs. My guess - and it's only a guess - is that the 275 driver is incompatible with the version of xserver that is current with Natty/11.04 and that trying to install it has a domino effect on several other packages.

Yes, I would suggest disabling the PPA and installing the 270 driver. Was there anything that the 275 driver offered that the 270 could not do?

---

### Post by ninfalara on 2011-07-08
I disabled all PPAs, tried to install nvidia-current and it's still doing the same thing, nothing changed. So this doesn't look like a dependency conflict.

I haven't tried downloading the driver from the website and installing it "manually" because I'm guessing it's not gonna make any difference, right?

I mean, the last time I actually installed it was before discovering what was going on... I went to settings -> additional drivers and activated the nvidia driver. When I did that, it didn't warn me that all of that was going to be uninstalled and I ended up with no desktop to boot. I just re-installed the OS from scratch.

One more thing, maybe this might make a difference in the dx... I only made changes in the root folder (/) since I have my home dir in a separate partition so it's the same it was before re-installing. Could that be a problem? (I don't think so, but... you never know...)

BTW, Thanks for your help so far! :)

---

### Post by MAFoElffen on 2011-07-08
> **coffeecat said:**
> nvidia-current in 11.04 is 270.41.06. Where did you get 275 from? Backports repository, a PPA repository or from the nvidia site?
@coffeecat- 

NVidia 275.09.07 is current from the 270 "series" NVidia drivers on their website...

You saw this post with me:
> **Harry33 said:**
> Alberto Milone has uploaded a new version of NVidia proprietary drivers in Oneiric repos.
This is, however, not the latest stable.
We can see from Nvidia's web site that the latest stable is [COLOR=Red]275.09.07[/COLOR] from today 14th June 2011.
The[COLOR=Red] 270.41.19 driver[/COLOR] is from 20th May 2011.

Here:
[https://launchpad.net/ubuntu/oneiric/+source/nvidia-settings/270.41.19-0ubuntu1](https://launchpad.net/ubuntu/oneiric/+source/nvidia-settings/270.41.19-0ubuntu1)
There is a date difference, but may be a just a proposed / stable / numbering differences(?) as pointed out here:
> **Harry33 said:**
> The same newest beta nvidia-current_275.09.07 is also in the Xorg-edgers PPA.

But that is systematics.  If installed from a PPA (such as Xorg-edgers) , it's asked that you do a PPA purge before updating a driver.  If on the standard nvidia-current package, I would be suspect on an upgrade that says it has to unistall so many packages to upgrade one... Know what I mean?  If it was NVidia's Nvidia driver (nvidia-installer package from NVidia), then you should do 
```

nvidia-installer --upgrade

```The nvidia installer has it's own dependency resolution for it's own package during updates.  This is not 100% working with Natty but worth a try...  Note on NVidia's own drivers- Ubuntu doesn't update it's package directly --> nvidia-installer does.

The way it's been going with drivers problems lately, I see a lot of work-arounds by purging the current driver, ensure the tools, headers and library files are present and up-to-date... then reinstall the driver.  Seems to resolve conflict and dependency problems.

On special note what I just said, whether you have Ubuntu's nvidia drivers or Nvidia's--  if you uninstall (nvidia)
```

nvidia-installer --uninstall

```or Ubuntu's nvidia drivers
```

sudo apt-get remove --purge nvidia*

```Before reinstalling your driver, please run these 2 commands...
```

[COLOR=Red]sudo apt-get install linux-headers-'uname -r'[/COLOR]
sudo apt-get install build-essential gcc-4.4 g++-4.4 libxi-dev libxmu-dev freeglut3-dev 

```The number one current NVidia work-around right now is just the command highlighted in [COLOR=Red]red[/COLOR].  The second ensures that dependencies are updated.

---

### Post by ninfalara on 2011-07-08
MAFoElffen, thanks for your reply. I tried with:


sudo apt-get remove --purge nvidia*
since I don't have nvidia installer, and it comes back telling me that it's gonna delete:

kubuntu-desktop* nvidia-common* nvidia-current*

That's as far as I went, I just canceled and left it there. So it's still telling me to uninstall kubuntu-desktop (and probably everything that comes with it)... :(

---

### Post by xsk3l3t0rx on 2011-07-08
i got the same exact issues as ninfalara except for the fact that i run gnome and she runs kde... i've removed all the repositories i've recently acquired like the swat ppa one, but even after reloading synaptic, if i type in nvidia-current the 275 driver is the only one offered... i really hate running in crappy low-gfx option since my netbook is my htpc pretty much... i dont want to, but i have a feeling im going to have to reinstall ubuntu to save myself a headache, good thing my /home folder is on a separate partition.... thanks all the same for any help you may have given!

---

### Post by ninfalara on 2011-07-08
> **xsk3l3t0rx said:**
> i got the same exact issues as ninfalara except for the fact that i run gnome and she runs kde... i've removed all the repositories i've recently acquired like the swat ppa one, but even after reloading synaptic, if i type in nvidia-current the 275 driver is the only one offered... i really hate running in crappy low-gfx option since my netbook is my htpc pretty much... i dont want to, but i have a feeling im going to have to reinstall ubuntu to save myself a headache, good thing my /home folder is on a separate partition.... thanks all the same for any help you may have given!

[COLOR=Red]**CAREFUL**[/COLOR]! Let me tell you my whole story first. 

About two weeks ago I was running my kubuntu desktop with fully functional nvidia drivers (last time I had installed the OS was a year ago or so). I (apparently) updated the nvidia driver along with other normal updates and kept using the computer. When I powered it back on the next day, it didn't boot to the desktop b/c it was gone. 

That's when I re-installed the OS (keeping my home folder in another partition). 

When I tried to activate the nvidia driver the whole desktop was uninstalled (again) with no warning and I re-installed *manually* (sudo apt-get install...) one by one all programs I used to have and kubuntu-desktop.

Then I tried to install the nvidia-current package, this time from synaptic, and that's when I discovered the actual issue we're having... that's when I found that in order to install it I was supposed to uninstall everything else.

Bottom line... **re-installing ubuntu from scratch is not gonna do anything for you**, you're still gonna have the same issue.

Hope this saves you some time you'll end up wasting!

---

### Post by coffeecat on 2011-07-09
> **MAFoElffen said:**
> @coffeecat- 

NVidia 275.09.07 is current from the 270 "series" NVidia drivers on their website...

@MAFoElffen, 275 may certainly be the current (latest) driver from nvidia, but the "nvidia-current" package in the Natty restricted repository gives you the 270 driver. That's what I was referring to; let's be clear what we mean by "current". You get the 275 driver in Oneiric with the nvidia-current package and older versions of the driver with older releases. As here:

[http://packages.ubuntu.com/search?keywords=nvidia-current&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=nvidia-current&searchon=names&suite=all&section=all)

The point I was trying to pursue is that the "current" nvidia driver for any particular Ubuntu release is built to be compatible with the version of the xserver used in that release. Using a package from a ppa or from nvidia's site might be the cause of dependency problems, although I am quite perplexed by the issues experienced by the xsk3l3t0rx and ninfalara.

I beg to differ from ninfalara's comment:

[quote="ninfalara"]Bottom line... re-installing ubuntu from scratch is not gonna do anything for you, you're still gonna have the same issue.[/quote]

Do a fresh install of Ubuntu and install the recommended nvidia driver from the repository (using Jockey) and you will not get dependency problems. If you did, there would have been a blizzard of threads about this. There hasn't been. Whether something has gone wrong with Kubuntu's (Natty) packaging though, I don't know.

---

### Post by MAFoElffen on 2011-07-09
> **ninfalara said:**
> MAFoElffen, thanks for your reply. I tried with:


sudo apt-get remove --purge nvidia*
since I don't have nvidia installer, and it comes back telling me that it's gonna delete:

kubuntu-desktop* nvidia-common* nvidia-current*

That's as far as I went, I just canceled and left it there. So it's still telling me to uninstall kubuntu-desktop (and probably everything that comes with it)... :(
then how about getting specific such as
```

sudo apt-get linux-headers-'unamae -r'
sudo apt-get remove --purge nviidia-common
sudo apt-get remove --purge nviidia-current
sudo apt-get remove --purge nviidia-settings
sudo apt-get install nvidia-common
sudo apt-get install nviidia-current
sudo apt-get install nviidia-settings
sudo nvidia-xconfig
sudo service kdm restart

```I do whole-heartedly agree with coffecat.- On the first part, that is is just semantics / naming conventions (on a driver kernel core)... the drivers in the main repositories are stable (themselves).  I also agree... If people can, a fresh install is always a good thing and a fresh start.  If it did recreate after a fresh install, then its either a skills/user training issue or a possible Launchpad issue.

The KDM factor doesn't seem to push it into a corner... I don't see this issue on 2 of the test boxes I have kubuntu-desktop installed on here.

I still really think if its asking to "remove" the complete desktop, that something is seriously wrong with that... There is nothing that I know or heard of in ubuntu-desktop, kubuntu-desktop, xubuntu-desktop or lubuntu-dektop that "should" ask for this in recent changes or updates...I can see maybe being reinstalled or reconfigured, but not removed. And by asking to remove or update a video driver usually doesn't ask to remove a desktop either... Curious.

What personally concerns me with this is that I have some "driver installation tutorials" and a sticky for resolving graihics issues... that I should go back through them all to see if something recently "changed" that may now cause problems with the given command and code examples.  Haven't heard from anyone using them about that, but... Just to be sure.  Trying to help people, not cause them troubles.

The only "new" graphics issues I see from the last few days has been with xserver-core, which this thread doesn't seem to fit into.

---

### Post by ninfalara on 2011-07-11
Tried [MAFoElffen]("http://ubuntuforums.org/member.php?u=1044547")'s suggestion, still doing the same thing... this is quite odd.

And it's funny how we both got the problem the same way: a normal update which ended uninstalling the whole desktop with no warning.

If this was windows, I would say it's a virus!

I have already re-installed the OS from scratch so I'm not gonna do it again. Meanwhile, I'll use nouveau. Too bad dual screen is no longer an option for me.

If any of you can solve this puzzle, I'm willing to test all (harmless) suggestions!

And I appreciate all the help you've given so far :)

---

### Post by MAFoElffen on 2011-07-11
> **coffeecat said:**
> 
I beg to differ from ninfalara's comment:

Do a fresh install of Ubuntu and install the recommended nvidia driver from the repository (using Jockey) and you will not get dependency problems. If you did, there would have been a blizzard of threads about this. There hasn't been. Whether something has gone wrong with Kubuntu's (Natty) packaging though, I don't know.
@coffecat--
++1

@ninfalara
> 
[COLOR=Red]**CAREFUL**[/COLOR]! Let me tell you my whole story first. 
I respect coffecat, his skill and experience.  I am familiar with him from testing and his expereince has got me out of trouble more than once!

I do updates on 4 machines out of 7 a day.  Every week I do about 8 fresh installs on usually 5 of those machines.  These systems are various in archetecture and their multiple desktops- Desktop, Server, ubuntu, kubuntu, xubuntu, lubuntu... XDM, GDM, KDM, LXDM... 

Fresh installs (over reinstall) "will" make a difference.  Allot of interim updates that had problems will be passed over during updates of a fresh install.  Especially if the problem occurred during an update or partial update where packages were held back,  

If you have a separate Home partition,  "sometimes" it won't fix things.  If the problem lies in a corrupt profile/config file.  In that case, do a fresh install, with the default created home directory--  will point that out.  You can always add your other home partition back in later.

@xsk3l3t0rx
> 
i've removed all the repositories i've  recently acquired like [COLOR=Red]the swat ppa one[/COLOR]
Well... Ah... You said you removed this... but how?  (Via software sources)  If you did remove this, was it via a PPA purge, like the instructions for that PPA syas. right?

@All
I have 10 other threads to help out with and some more testing to do.  "coffecat" is very well versed with this...

---

