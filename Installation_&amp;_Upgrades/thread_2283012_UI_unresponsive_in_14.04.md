---
title: "UI unresponsive in 14.04"
date: 2015-06-18
forum: Installation &amp; Upgrades
---

### Post by richard120 on 2015-06-18
Recently I decided to install Ubuntu on my Windows PC which was becoming slower and slower. I figured I'd get a clean start with what I was hoping to be a reliable OS. Sadly, reliable hasn't been my experience so far. I consider myself pretty handy with computers, though I'm probably nowhere near as handy as most on these forums.

First off, the install was incredibly rocky, despite the Live CD working absolutely perfect. I had some partitioning issues, but managed to solve those. Notable was that during the installation the UI seemed to become unresponsive. Not lag, just unresponsive. This only occured during the partition phase of the installation.
 In any case, I managed to circumvent the problems with Gparted, and got a fresh installation. Now here the real trouble starts. The UI often becomes unrespsonsive. I won't be able to move or close windows, yet sometimes I will be able to use the program itself. Sometimes the keyboard won't work, other times it will.
I've tried going into the terminal and updating, but this changed nothing.
compiz --replace seemed to have fixed it at least temporarily but I don't want to have to do this every time I get this issue. 
I've been looking online for a solution and found some similar problems but these were all with older versions of Ubuntu and the threads were years old. I was hoping to hear if there's a permanent fix for this problem.

At the moment I'm considering to install Ubuntu 15.xx to see if that solves the problem, but my gut tells me this won't help, as I had the same UI problem with its installation.

I hope somebody is able to guide me through this problem. I'd very much like to use Ubuntu but if I can't fix this I'll have to revert back to Windows.

EDIT: I wouldn't particularly be against switching to Xubuntu. Would that maybe solve this issue?

---

### Post by Bucky Ball on 2015-06-18
*Thread moved to **Installation & Upgrades**.*

Welcome. Couple of questions:

How much RAM does the machine have and how old?
Does Ubuntu work ok from the install media when you 'Try Ubuntu'?
Can you be more specific about what happened when you got to the partitioning section of the install? Do you let Ubuntu install automatically or choose Something Else and partition manually? 
Did you start with a plan or leap in? The former is, of course, recommended. :)

You need to be specific for us to give specific help. What went wrong during the install exactly? What were the error messages, if any? How exactly did you end up installing Ubuntu? You say you used Gparted. That should not be required and would mean leaving the installer.

---

### Post by richard120 on 2015-06-18
Thanks for the quick response! I was at work when I wrote the post and may have rushed it a bit. I'll try to answer your questions one at a time.

> **Bucky Ball said:**
> 
How much RAM does the machine have and how old?


The machine is probably about 4 years old. Funnily enough I've forgotten how much RAM is in it and haven't yet found out how to find it while inside Linux. I suspect it's about 4gig though.
EDIT: Found it in just a few seconds under Xfce, it is indeed 4gig. I'm using an 8gig swap, of which I have a suspicion is way more than needed. Am I correct in this?

> **Bucky Ball said:**
> 
Does Ubuntu work ok from the install media when you 'Try Ubuntu'?


Ubuntu worked great from the CD! Absolutely no problems except that programs were slow on the first load, which I suspect was because they were loading off the cd. Programs load much faster on the fresh install.

> **Bucky Ball said:**
> 
Can you be more specific about what happened when you got to the  partitioning section of the install? Do you let Ubuntu install  automatically or choose Something Else and partition manually? 
Did you start with a plan or leap in? The former is, of course, recommended. :smile:

You need to be specific for us to give specific help. What went wrong  during the install exactly? What were the error messages, if any? How  exactly did you end up installing Ubuntu? You say you used Gparted. That  should not be required and would mean leaving the installer. 

Okay, so here we go:

The first time I opted for the automatic installation without first going into the Try Ubuntu portion. When I selected continue a message popped up asking if I was sure to let it partition the drive. However, the buttons did not respond to my mouse. By pressing escape I was able to get out of it. I then tried to go back and manually change the partitions. Upon trying to change the properties of partitions the UI was unresponsive in the popup windows. My mouse clicks seemed to be registered by the window below, though, as if the popup wasn't there.
I went out and back into the manual partitioning and was greeted by a completely different partition list (not sure of the right term here, but the partitions were different compared to before). Again, I had problems with the UI. I tried to restart the installation, tried the automatic version first, same problem. Went back into manual, which, again, showed a different list the first time compared to re-entering it. Still a partially unresponsive UI.
At this point I got a little fed up and went back into Try Ubuntu to get to Gparted. I set up my partitions with the help of the Ubuntu official guide, then went to install with the installer in Try Ubuntu. I continued into a manual installation, and now everything worked. I set my mount points and made sure it formatted everything again. The installation went fine, though when told to restart the computer never actually shut down. Just a black screen and no response. I did a hard shutdown then restarted the computer. The UI problems were almost immediate and very much like those I encountered when trying to install.

Right now I'm typing on my fresh install, which seems to work fine if I immediately start off with going into terminal with ctrl+alt+1, typing compiz --replace, then going back with ctrl+alt+7. I'm currently switching to Xfce with the guide found here: [https://sites.google.com/site/easylinuxtipsproject/alternative](https://sites.google.com/site/easylinuxtipsproject/alternative) to see how that works. I'd rather use Unity though, so if there's any fix, I'd still greatly appreciate it.

I hope this is enough information, if any more is needed, I'd be glad to supply.

---

### Post by Bucky Ball on 2015-06-18
You don't need a guide. Install xfce4 and that's it. Log out, choose 'Xfce4 session' from the Sessions menu, login. You are looking at Ubuntu with the xfce4 desktop envrironment. It probably won't fix anything, but why not try it anyway. :)

DON'T install xubuntu-desktop. That will drag in *all* Xubuntu default apps and dependencies and is like having Xubuntu installed on top of Ubuntu. Not nice. But do-able. The machine doesn't care, just messy, some redundant apps and bloaty. You may find conflicts.

Getting back to your actual Unity issue, if it works fine with your workaround, then it appears to be something about compiz not starting at boot? Might be a good place to start.

---

### Post by richard120 on 2015-06-18
The guide talks about this and offers a solution to remove those conflicts. Is the solution offered not a proper fix? Right now I'm mostly just messing around to get a better feel for what I'm doing, I fully intend to do a fresh install once I find what works to make sure I have no unnecessary problems later.

On another note, I've read that a SWAP is about one to two times the size of the RAM. It feels like this is way more than I need though. I'm currently running an 8gig swap, is that too much for 4gig RAM?

---

### Post by Bucky Ball on 2015-06-18
2Gb /swap is all you need. If you open a HEAP of programs and are using a lot of RAM and then hibernate a lot, twice the size of installed RAM is recommended. 2Gb is fine for 95% of desktop users.

If you have nothing on the Ubuntu install you want to keep and really want to know if Xubuntu would fix the issue, install Xubuntu. Who knows? Sounds like it might be graphics related to me. Can you open 'Additional Drivers' and see if there is anything there? Also, open a terminal and:

```
sudo lshw -C video
```

Hit enter and post the output here, please.

I know nothing about Compiz, but again, if you restart it to fix, that might be a place to start. I don't use the Ubuntu Desktop or Unity so don't know how you'd go about fixing Unity things, if compiz is one. Have a look at [this]("http://wiki.compiz.org/Troubleshooting") link then check if compiz is actually starting at boot. You made need to tweak so it does start at boot.

---

### Post by richard120 on 2015-06-18
So I checked additional drivers and switched to a driver that seems to solve a lot of AMD/ATI issues for other people in the reviews. It listed two others that seem to have come pre-installed. The names of these packages are: fglrx, fglrx-updates, xserver-xorg-video-ati. It was using the first one, and now I've switched to the third one.

I'm now running Xubuntu and Ubuntu on the same machine, so some things may be acting up because of that, but as I rebooted into Xubuntu just now, I had similair UI problems until I did another compiz --replace. I feel this is due to both running on my system, but felt I should point it out anyway.

Running the command gives me this:

```

  *-display               
       description: VGA compatible controller
       product: Barts XT [Radeon HD 6870]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:53 memory:e0000000-efffffff memory:f7dc0000-f7ddffff ioport:d000(size=256) memory:f7da0000-f7dbffff
```

I'll definitely take a look at that link and see if I can find anything there. I was starting to give up on this but it seems I'm slowly getting closer to a fully functioning OS. Thanks for all your help so far!

---

### Post by Bucky Ball on 2015-06-18
All good. Ah, I wonder if that output was before you installed fglrx, the third party driver. You say it was already enabled? Disable it and reboot so hopefully it will use the open-source 'radeon' driver. See if that makes any difference. Run that command again and check the part I have put in bold here to make sure it says 'radeon' and not 'fglrx'.

> *-display               
       description: VGA compatible controller
       product: Barts XT [Radeon HD 6870]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: **_driver=fglrx_**_pci latency=0
       resources: irq:53 memory:e0000000-efffffff memory:f7dc0000-f7ddffff ioport:d000(size=256) memory:f7da0000-f7dbffff 

Your card may be one of the Radeon ones that AMD no longer support with their driver. How old is it? In any case, if none of the third-party drivers are working, give that a go.

* Update: Nope, I was wrong. Your card appears to be fully supported. See [here]("https://help.ubuntu.com/community/RadeonDriver#Fully_Supported") and read the rest for more clues. 

My money's still on compiz as I'm imaging fglrx is the correct driver for that card. :-k

PS: If you're enjoying tweaking and learning while trying to fix this, please continue. :) If you just want your machine working and you've got nothing to lose, reinstall and see if it goes away. Did you check your install media for defects prior to installing? That is always a good idea.

---

### Post by richard120 on 2015-06-18
fglrx was pre-installed and selected, the X.org sriver was the one I switched to. I'll switch to the Radeon driver and see if that helps anything, but my eye caught something on the link you gave me:
> If you are using an ATI card, Compiz requires at least a Radeon 7000 (or M6).

And there we have it8-[ Will post here if the driver fixes anything, but I'm leaning towards just going Xubuntu as my card doesn't seem to be supported.

EDIT: a search for Radeon in the software center had the X.Org driver as only open-source driver there, is this the one you mean? Because this is the driver I was using when I issued that command and a reboot did not solve the problem.

EDIT2: Okay, I may have put some misinformation here, seems like all 3 drivers in my additional drivers list come from the same software package. Confusion en masse. Am trying to figure out what exactly is happening here. Take above edit with a grain of salt.

---

### Post by Bucky Ball on 2015-06-18
Well spotted! :) You are looking for xserver-xorg-video-radeon. Try a terminal with:

```
sudo apt-get install xserver-xorg-video-radeon
```

Disable other driver and reboot.

You might want to read the last bit of my last post again. A reinstall might not be a bad idea as it is a fresh install. What is the make/model of the machine?

I use Synaptic Package Manager myself so you get more control, but you could remove fglrx with SCentre and reboot. That would probably kill all three drivers in Add Drivers.

---

### Post by richard120 on 2015-06-18
I did check my install media prior to installing, by having my image burner check if the burn completed successfully, so I guess there is always the slim chance something went wrong during the download itself.

Trying to install the radeon driver gives me this error:
> The following packages have unmet dependencies:

xserver-xorg-video-radeon: Depends: xorg-video-abi-15 but it is a virtual package
                           Depends: xserver-xorg-core (>= 2:1.14.99.902) but 2:1.15.1-0ubuntu2.7 is to be installed



The machine is one I "built" myself. (Selected the components based on recommendations and had it assembled.) The motherboard is ASUS with Intel® Core&#8482; i5 CPU 760 @ 2.80GHz × 4. That's as far as I can get atm, it's been a while since I bought the thing and haven't yet figured out how to get all my specs within linux.

So far compiz does seem the safe bet. Or in this case, the unsafe bet. I'll burn a Xubuntu disc and see what happens on a fresh install of that.

---

### Post by richard120 on 2015-06-18
Did a fresh Xubuntu install. Got kind of nervous when I had the same UI problem during installation, and I got a sneaky suspicion - what if it wasn't restarting compiz that was fixing it? Upon rebooting into my fresh installation I had the exact same unresponsive UI. So, I switched to terminal (ctrl+alt+f1), and did a compiz --replace, just in case. Of course it told me no such command was available. I switch back et voila. UI fixed. Weirdest bug ever. Simply switching to terminal and back solves it.

I guess this is something I can live with, but I'd still like to get to the bottom of this. Any ideas on where to start?

---

### Post by Bucky Ball on 2015-06-19
Seeing as you've installed Xubuntu and have exactly the same issue I can only think this must be hardware related. 

Once again, what is the make/model of the machine? That may shed more light on any known issues with it and Ubuntu.

---

### Post by richard120 on 2015-06-19
Managed to find my motherboard make: ASUS P7H55/USB3 with Intel® Core&#8482; i5 CPU 760 @ 2.80GHz × 4. My graphics card you've seen. 4gig of RAM. That's all I can tell you, as it's a custom built PC.

---

### Post by Bucky Ball on 2015-06-19
PS: I said many posts ago that I'd be looking into what is happening with compiz because it **_*IS*_** restarting it that's fixing it and has been since your first code post ... :-k

Check in Session & Startup> Applications. Is it in there anywhere but unticked?

---

### Post by richard120 on 2015-06-19
On a fresh Xubuntu install after a compelte format I had the same problem, with no compiz to restart. I have since then tested it many times, and switching to full-screen terminal and back is indeed what is fixing it. I just now did a fresh Ubuntu install as I managed to mess up my drivers and figured it wasn't a Compiz/Unity problem, I might as well go for my preffered UI. In this case too, just switching to terminal and back fixes the issue.

Compiz is not in my startup list now that I'm back in Unity Ubuntu.

---

