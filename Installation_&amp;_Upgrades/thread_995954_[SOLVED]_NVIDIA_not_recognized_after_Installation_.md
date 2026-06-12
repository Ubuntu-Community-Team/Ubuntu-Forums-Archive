---
title: "[SOLVED] NVIDIA not recognized after Installation of Security Update"
date: 2008-11-28
forum: Installation &amp; Upgrades
---

### Post by KentonS on 2008-11-28
I'm running Ubuntu 7.10 on a laptop. I just downloaded and installed the Security Update *du jour*. Here's the Update log from Synaptic Package Manager:

======
Commit Log for Fri Nov 28 09:06:52 2008

Upgraded the following packages:
linux-generic (2.6.22.15.22) to 2.6.22.16.23
linux-headers-generic (2.6.22.15.22) to 2.6.22.16.23
linux-image-generic (2.6.22.15.22) to 2.6.22.16.23
linux-restricted-modules-generic (2.6.22.15.22) to 2.6.22.16.23

Installed the following packages:
linux-headers-2.6.22-16 (2.6.22-16.60)
linux-headers-2.6.22-16-generic (2.6.22-16.60)
linux-image-2.6.22-16-generic (2.6.22-16.60)
linux-restricted-modules-2.6.22-16-generic (2.6.22.4-16.12)
linux-ubuntu-modules-2.6.22-16-generic (2.6.22-16.41)
======

(A security update yesterday upgraded nvidia-glx-new from 100.14.19+2.6.22.4-15.11) to 100.14.19+2.6.22.4-16.12. Everything worked fine after the upgrade.)

Now, the system will only come up in low-graphics mode. A screen comes up during the boot process saying that the screen and graphics card could not be detected correctly.

I went  into System -> Administration -> Restricted Drivers Manager, and it shows the NVIDIA accelerated graphics driver (latest cards) enabled but not in use. I tried disabling it and re-enabling it to no avail.

I then went into System -> Administration -> Screens and Graphics and tried to set the configuration manually. Nothing changed. Wen I went back into Screens and Graphics, everything was set back to what it was before I made my changes.

Now what? ;-)

Thanks very much for any assistance anyone can provide.

---

### Post by Tanker Bob on 2008-11-28
If you haven't already, enable the universe repository. Then install EnvyNG with your package manager. After EnvyNG installs, run the script from the menu, select NVidia and ensure that it is set to install the NVidia driver with automatic detection. Click Apply and let the script run. When it completes, let it restart the system. That should get you back running the proper NVidia drivers.

---

### Post by RedRat on 2008-11-28
KentonS
Yes this is probably THE MOST ANNOYING part of Ubuntu. I just did the security upgrade in 8.04 today and got exactly the same thing happening to me--exactly same symptoms.

The only way around this, at least for me, was to use envyng. What I did was to go into Terminal and type the following:

```
envyng -g
```

this brings up Envy, you select the graphics card (in my case it is Nvidia) and then click the radio button to manually install the new driver, second button down. Then tell it to go.

Envy will open a terminal window showing all that it is doing and when it finally finishes, takes several minutes so be patient, it tells you reboot. Usually this comes up in the correct resolution and monitor choice. If it does not, then you have to run your settings program as root. In my case it is nvidia-settings:
```
gksudo nvidia-settings
```
You must run it as root otherwise if you click the "Save Settings" button, it does not save it and you begin the whole damn process over again. 

Hope that this helps.

I really wish the developers of Ubuntu would get this problem with graphics drivers under control, it really seems silly to me that you can't just upgrade and get back to where you were prior to that upgrade. This is about the third or fourth time I have had to do this and it is really GETTING ANNOYING!!!

---

### Post by KentonS on 2008-11-28
Tanker Bob and RedRat:

Thanks for the replies. I'm confused though.

I went into Software Sources and enabled main and universe repositories. I then went into Synaptic Package Manager and looked for EnvyNG. I couldn't find it.

I then went to install nvidia-settings in Synaptic Package Manager. It wants to uninstall nvidia-glx-new. Is this a Good Thing?

What did I do wrong?

Right before I saw your posts I was going to restore my previous, backed-up etc/X11/xorg.conf. I'm now beginning to wonder if this is a good idea.

Your thoughts?

---

### Post by RedRat on 2008-11-28
> **KentonS said:**
> Tanker Bob and RedRat:

Thanks for the replies. I'm confused though.

I went into Software Sources and enabled main and universe repositories. I then went into Synaptic Package Manager and looked for EnvyNG. I couldn't find it.

I then went to install nvidia-settings in Synaptic Package Manager. It wants to uninstall nvidia-glx-new. Is this a Good Thing?

What did I do wrong?

Right before I saw your posts I was going to restore my previous, backed-up etc/X11/xorg.conf. I'm now beginning to wonder if this is a good idea.

Your thoughts?

I believe you have to enable the mediabuntu.org or add this to software sources: 
"http://packages.mediabuntu.org free non-free"
You may have to add that to your software list. Once you have that added, you can start Synaptic and after it has loaded, make sure that you hit the "RELOAD" button in the upper left corner. Then search for "envyng" and install it. You can also get it from the terminal by using:
```
sudo apt-get envyng install
```

---

### Post by KentonS on 2008-11-28
Well, I restored my backed-up xorg.conf. No luck.

I installed nvidia-settings (which caused nvidia-glx-new to be removed. No luck.

I added "http://packages.medibuntu.org gutsy free non-free" to my software sources. No EnvyNG. I haven't (yet) done the apt-get thing. I'll try that later.

I can set the screen Model="LCD Panel 1280x1024", Resolution=1024x800, and Graphics Card Driver="nv - nvidia RIVA 128, RIVA TNT, GeForce...", and everything looks fine. But as soon as I reboot, it's back to low-graphics mode.

It shouldn't be this difficult!

---

### Post by Tanker Bob on 2008-11-28
No, it shouldn't be that hard. Unfortunately, it is. Try starting your terminal and typing:

```
sudo apt-get update
sudo apt-get install envyng
```

After it installs, you can run it from the same terminal as KentonS indicated above:

```
sudo envyng -g
```

Then proceed as stated in the earlier posts.

---

### Post by KentonS on 2008-11-28
OK.

I did a sudo apt-get update. It went OK.

I did a sudo apt-get install envyng. I got the following:
======
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package envyng
======

What am I not getting here?

---

### Post by Zimmer on 2008-11-28
if you use synaptic you would see the package you need is probably envyng-gtk if you are running a Gnome desktop ..  simple name error on the command line....

---

### Post by KentonS on 2008-11-28
Zimmer:

I searched in Synaptic Package Manager just for "envy". All it brought up was alsa-tools-gui, which contains the string "envy24control" in its description.

In fact, I tried "sudo apt-get install envyng-gtk" in a terminal session as well. It didn't work either - "E: Couldn't find package envyng-gtk".

---

### Post by RedRat on 2008-11-28
KentonS
I am sorry I just noticed that you are still running 7.10. You need to add the medibuntu repo to your list of software. You need to go to the toolbar at the top of your screen:
System>Administration>Software Sources 

Been awhile since I last looked upon Gutsy's menu but there should be something like that there. Click on Software Sources and it should open a box with tabs. Click on the tab that says Third Party Software. There you should see a list of repositories. This is where all the third party software is housed. You will need to add the medibuntu source. Click the Add button a box will appear and then Type in the following where it says APT line:

```
deb http://packages.medibuntu.org Gutsy free non-free
```
Then click the Add Source button. That should do it.

Now try the apt-get update and the install envyng.

---

### Post by KentonS on 2008-11-28
RedRat:

I'd already added that line to Software Sources before I wrote Post #6.

Here's where I am now:
[LIST]
[*]I removed nvidia-settings.
[*]I reinstalled nvidia-glx-new.
[*]I restored xorg.conf from backup. The current xorg.conf is the one that was working before this whole mess started.
[*]I removed all the xorg.conf-failsafe.n files.
[*]I've enabled the universe repository.
[*]I've added [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy free non-free to my Software Sources and reloaded the repository in Synaptic Package Manager. EnvyNG is not there. Neither is EnvyNG-gtk (or anything else with envy in its name).
[*]I've run apt-get update (successfully).
[/LIST]
... and after rebooting, I'm still stuck in low-graphics mode with a brand new /etc/X11/xorg.conf.failsafe file.

---

### Post by RedRat on 2008-11-28
> **KentonS said:**
> RedRat:

I'd already added that line to Software Sources before I wrote Post #6.

Here's where I am now:
[LIST]
[*]I removed nvidia-settings.
[*]I reinstalled nvidia-glx-new.
[*]I restored xorg.conf from backup. The current xorg.conf is the one that was working before this whole mess started.
[*]I removed all the xorg.conf-failsafe.n files.
[*]I've enabled the universe repository.
[*]I've added [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy free non-free to my Software Sources and reloaded the repository in Synaptic Package Manager. EnvyNG is not there. Neither is EnvyNG-gtk (or anything else with envy in its name).
[*]I've run apt-get update (successfully).
[/LIST]
... and after rebooting, I'm still stuck in low-graphics mode with a brand new /etc/X11/xorg.conf.failsafe file.

First get nvidia-settings back, I think you can get it from Synaptic or use apt-get:
```
sudo apt-get nvidia-settings install
```

Envyng should be available for 7.10, I believe. Perhaps one of the more experienced users out there has info about that. I am coming at this from the point of view of an 8.04 LTS user, been awhile since I ran 7.10 so I might be rusty on it, but it should be similar to 8.04.

Other than that, I guess this has to be bumped up.

---

### Post by KentonS on 2008-11-29
Yup. I definitely think we're at the "has to be bumped up" point. This problem goes way beyond a messed-up video driver issue.

Once the system boots (in low-graphics mode) I'm able to log on, set the screen Model="LCD Panel 1280x1024", Resolution=1280x1024, and Graphics Card Driver="nv - nvidia RIVA 128, RIVA TNT, GeForce..." (using the Open Source driver), log out, log back in, and everything looks fine. However:
[list]
[*]When I run Stellarium, I get a message that says "This system does not support OpenGL".
[*]When I run VirtualBox to bring up my WinXP VM, I get a message that says "VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason."
[/list]
So basically, that so-called "Security Update" didn't *merely* hose my setup; it *most sincerely* hosed it.

I don't know how one "bumps up" an issue, but I think this one definitely needs to be bumped up!

---

### Post by Tanker Bob on 2008-11-29
KentonS,

The open source nv video driver does not support any advanced video functions, including OpenGL. That's endemic with the lack of proprietary driver. The VirtualBox problem is because VB has to compile a new driver for the updated kernel. I don't use VB so can't advise on specifics, but suggest that you reinstall or reconfigure the program. If VB has a configuration script, I suggest rerunning that as a first step.

I did some research and found that Envy Legacy is not listed in Medibuntu for Gutsy. You need to download it directly from [Alberto's website](http://albertomilone.com/nvidia_scripts1.html) and then install the .deb package. Once you install Envy Legacy, restart your system. When the GRUB menu appears, choose the recovery mode for the new kernel. When you get to the terminal prompt, run:

```
envy -t
```

Envy will do the heavy lifting from that point. When it is finished, reboot the system and start normally. That should get your video up and running. You'll probably have to either reconfigure or reinstall VirtualBox to get it running again.

Let me know how this works out.

---

### Post by Tanker Bob on 2008-11-29
BTW, I wrote a [blog post here](http://reformedmusings.wordpress.com/2008/11/29/upgradingupdating-kubuntus-kernel-with-nvidia-drivers/) running through the whole NVidia update process. I hope that it helps.

---

### Post by RedRat on 2008-11-29
KentonS
What you may want to do, if you are up to it and I can't blame you for all that you have gone through here, is to update to 8.04 LTS. I would not update to 8.10 because it clear here from the blogs that there seem to be real issues with video drivers. I believe that Envy is part of the Hardy update. 

Now 8.04 is not perfect either, but with Envy on board, it makes recovery a tad bit easier. I have had about 4 kernel updates for 8.04 and had to go through this Nvidia mess that many times too. From what I have read here and elsewhere, it seems to be wise to stick with these LTS releases until their support time runs out, which I guess is 2-3 years.

---

### Post by KentonS on 2008-11-29
RedRat and Tanker Bob:
First, I can't thank you enough for sticking with me through this whole thing.

Second, you're both going to think me a bit of an idiot when I tell you what I discovered - quite by accident, and a byproduct of following the instructions in Tanker Bob's blog: After I had downloaded and installed Envy Legacy, I rebooted. When I went into GRUB, I noticed that the .15 kernel was highlighted, rather than the .16 kernel. Nonetheless, I went into the .16 recovery mode, which was unable to connect with the mirror site where apparenty the NVidia drivers, etc. reside. After it had retried several times, I cycled power and went back into GRUB. Figuring that the problem the whole time was that it was attempting to load the *old* kernel that had probably had been renedered unusable, I just selected the .16 kernel. Guess what? Everything came up perfectly. OpenGL works, The screen and graphics card work, in fact pretty much everything works. (OK, VirtualBox still isn't working but that's a separate issue.)

In my Linux newbiness I was unable to appreciate all the implications of the fact that a new kernel had been installed. In fact, I didn't even recognize that a new kernel had been installed. Once I saw the GRUB menu, things finally made sense. If only the screen that said I needed to reboot had also said that 1) a new kernel had been installed, and 2) I needed to select it. Oh well... Guess I'll know next time, assuming there *is* a next time.

So once again I thank you very much for all your help.

---

### Post by KentonS on 2008-11-29
> **RedRat said:**
> KentonS
What you may want to do, if you are up to it and I can't blame you for all that you have gone through here, is to update to 8.04 LTS.

RedRat:
I want very much to upgrade to 8.04. The only reason I didn't do it right away when I got my laptop with 7.10 is that a tech guy who worked at R-Cubed Technologies ([http://shoprcubed.com](http://shoprcubed.com)) - the company I bought the Linux laptop from - raised some yellow flags that had to do mostly with their proprietary mechanism to install/update multimedia stuff. He told me the process that does that may not work under 8.04. Of course, he doesn't work there any more. I haven't gotten back in touch with them yet to learn the particulars, but, given their lack of response to all the support requests I sent them, I don't expect that I'd get much help anyway. (I have support requests with them that are over a month old to which I've received virtually *no* response, despite almost-weekly requests for them to respond.)

So I need to investigate any ramifications of upgrading before I go for it.

---

### Post by Tanker Bob on 2008-11-29
Glad that it worked out for you. We've all been there at some point. I, too, would recommend 8.04.1 if the issues with R-Cubed will allow.

---

