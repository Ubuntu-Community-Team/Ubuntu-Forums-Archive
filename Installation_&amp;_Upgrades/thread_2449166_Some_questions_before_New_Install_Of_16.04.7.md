---
title: "Some questions before New Install Of 16.04.7"
date: 2020-08-21
forum: Installation &amp; Upgrades
---

### Post by O)9(yo&amp;# on 2020-08-21
I recently installed the new 16.04.7 on a HDD. It is performing flawlessly, using the Nvidia 304 driver this computer needs. I would now like to install it on a SSD.  Some questions:

First, how can I install it in such a way that it does not upgrade to kernel 4.1x? I need to keep it on 4.4, for the already mentioned reason; namely, that I need the 304 driver. Currently, I have to select Advanced Options in Grub, and choose the 4,4 kernel. I know you can delete kernels, but I have only done it for old ones, not new ones, and I'm afraid I may damage things severely. Also, editing Grub is a bit frightening to me. Again, I would like to avoid that.

Second, is there a trimmed-down version, so I don't have to install things I will later have to delete, namely the browser and office suite? I prefer different ones.

Third, what is the best way to disable or uninstall the amazon lens?

Thanks as always, the help is much appreciated.

---

### Post by mikewhatever on 2020-08-21
1. To keep the kernel 4.4, you need to start with Ubuntu 16.04.1 installation image, and make sure not to install the HWA stack. 
    All the later ones have later kernels.
    Get it here: [http://old-releases.ubuntu.com/releases/16.04.1/](http://old-releases.ubuntu.com/releases/16.04.1/)

2. No.

---

### Post by oldfred on 2020-08-21
You can install the server version and then not install anything additional other than specifically what you want.
If you have to have the old 304 nVidia, you probably have to stay with older versions of Ubuntu. I found my older nVidia card worked just as well for normal use with nouveau as proprietary driver. And then found the Intel haswell chip's video was just as good or slightly better than my GT 620 card.

If you install the full desktop, you also get all the applications. But you can from server just install apps you want.
Server uses this to let you choose what apps to default install. You can choose nothing.
[https://help.ubuntu.com/community/Tasksel](https://help.ubuntu.com/community/Tasksel)

---

### Post by TheFu on 2020-08-21
Support for 16.04 will be ending next April, so now is the time to start planning what you will do then.  I had an nVidia 7200 GS card that lost proprietary  support from nVidia for the 16.04 release.  There is the nouveau driver available in the newer versions, but I couldn't get it to run at the resolution desired.  $70 and a new GPU solved that issue.  If solving a problem will take over 4 hrs or $70 solves it, I'll pay the $70 every time.

I'll be upgrading our 16.04 systems this fall sometime. Timing depends on support for each application with newer releases.  I really want to skip 18.04 completely, but a few of the applications usually take 12 months before they support the current LTS, so timing could be too tight.

As for using lighter Ubuntu - any of the other flavors will be lighter than the normal, default, Ubuntu Desktop running Gnome3.  Xubuntu, Lubuntu, Ubuntu-Mate are all choices.  Some have a "minimal" desktop option - but that does the normal install, then removes the other packages.  I complained that the minimal install included a browser - the team decided that a browser wasn't optional.  I suggested lynx, since obviously, anyone desiring a minimal install would happily accept a minimal browser.  Overruled again. ;)

If you don't load Gnome3, you won't get any 'lense' stuff.

There is also the "alternate installer", but that is more hassle than just removing the packages, IMHO.  If you need to do this often, make a list and keep that list in a file that is part of your backups. Every time you find another package to remove, just add that to the list.  I use ansible and have config modifications, new packages to be installed and other packages to be removed from all my systems.  It is always becoming more complete, more automatic, and more consistent that way.

If you install the server version, then you won't care about the proprietary GPU driver. Server doesn't have a GUI. It is certainly lighter than any desktop.  The CPU isn't wasting time with GUI processing. That's a good thing.

---

### Post by O)9(yo&amp;# on 2020-08-21
> **mikewhatever said:**
> 1. To keep the kernel 4.4, you need to start with Ubuntu 16.04.1 installation image, and make sure not to install the HWA stack. 
    All the later ones have later kernels.
    Get it here: [http://old-releases.ubuntu.com/releases/16.04.1/](http://old-releases.ubuntu.com/releases/16.04.1/)

2. No.

Thanks, but I want to stay with the 16.04.7 for security reasons. I still have Ubuntu 14.04, believe it or not, with extended security, good until 4.21. so when I saw 16.04.7 was out, it rekindled my interest in trying to get it up and running. Previous attempts had failed, as i couldn't get the 304 driver going. for whatever reason, I was successful this time.

I guess I'll have to figure out how to edit Grub. I can use the current HDD install and if successful, then apply it to the SSD one.

---

### Post by O)9(yo&amp;# on 2020-08-21
> **oldfred said:**
> You can install the server version and then not install anything additional other than specifically what you want.
If you have to have the old 304 nVidia, you probably have to stay with older versions of Ubuntu. I found my older nVidia card worked just as well for normal use with nouveau as proprietary driver. And then found the Intel haswell chip's video was just as good or slightly better than my GT 620 card.

If you install the full desktop, you also get all the applications. But you can from server just install apps you want.
Server uses this to let you choose what apps to default install. You can choose nothing.
[https://help.ubuntu.com/community/Tasksel](https://help.ubuntu.com/community/Tasksel)

Thanks for all that great info. I have never installed a server version, as this is just for home use. A desktop is a must.

---

### Post by O)9(yo&amp;# on 2020-08-21
> **TheFu said:**
> Support for 16.04 will be ending next April, so now is the time to start planning what you will do then.  I had an nVidia 7200 GS card that lost proprietary  support from nVidia for the 16.04 release.  There is the nouveau driver available in the newer versions, but I couldn't get it to run at the resolution desired.  $70 and a new GPU solved that issue.  If solving a problem will take over 4 hrs or $70 solves it, I'll pay the $70 every time.

I'll be upgrading our 16.04 systems this fall sometime. Timing depends on support for each application with newer releases.  I really want to skip 18.04 completely, but a few of the applications usually take 12 months before they support the current LTS, so timing could be too tight.

As for using lighter Ubuntu - any of the other flavors will be lighter than the normal, default, Ubuntu Desktop running Gnome3.  Xubuntu, Lubuntu, Ubuntu-Mate are all choices.  Some have a "minimal" desktop option - but that does the normal install, then removes the other packages.  I complained that the minimal install included a browser - the team decided that a browser wasn't optional.  I suggested lynx, since obviously, anyone desiring a minimal install would happily accept a minimal browser.  Overruled again. ;)

If you don't load Gnome3, you won't get any 'lense' stuff.








There is also the "alternate installer", but that is more hassle than just removing the packages, IMHO.  If you need to do this often, make a list and keep that list in a file that is part of your backups. Every time you find another package to remove, just add that to the list.  I use ansible and have config modifications, new packages to be installed and other packages to be removed from all my systems.  It is always becoming more complete, more automatic, and more consistent that way.

If you install the server version, then you won't care about the proprietary GPU driver. Server doesn't have a GUI. It is certainly lighter than any desktop.  The CPU isn't wasting time with GUI processing. That's a good thing.


More great info, thanks I appreciate it. As for the lens issue, my searches brought up a number of threads, many from here, but there seemed to be much conflicting info on the subject, and the possibility of damaging Unity if not careful. Which is why I haven't done anything yet. Other than put the icon in the trash. Which I know doesn't really do anything, Of well, it could be worse. Much worse. Windows 10 worse.

As for support running out in 4/21, I plan to sign up for extended security maintenance, which I have on 14.04. Just installed that for nostalgia's sake, really. I was mainly using Linux Lite 3.8, but that also runs out in 4/21. Which is why I wanted 16.04.7. Yeah, I could buy a new card, but since the machine is 12 years old, I'm reluctant to do that, if I can get things working as is. 

The nouveau drivers won't even run Xubuntu, or Ubuntu Mate. Really have to have the Nvidia drivers (apologies to Nvidia haters, but hey the stock is soaring).

---

### Post by oldfred on 2020-08-21
My 2006 Laptop with 1.5GB of RAM was essentially retired when I got my new UEFI system in 2014. And it then had 12.04. When 16.04 came out, I installed it to laptop. I typically installed full Ubuntu, but changed to fallback/flashback as Full Ubuntu was so slow. And 16.04 was almost functional with standard Ubuntu.

But I recently, just as a test, tried to install 20.04. Desktop would not install at all. But I was able to install server version and then add fallback/flashback. Expected that to pull in all the gnome pieces it needed but it did not. So I had to add more gnome. But ended with with functional desktop. But spoiled with fast SSD systems, so laptop still retired.

---

### Post by mikewhatever on 2020-08-21
> **michael_diemer said:**
> Thanks, but I want to stay with the 16.04.7 for security reasons. I still have Ubuntu 14.04, believe it or not, with extended security, good until 4.21. so when I saw 16.04.7 was out, it rekindled my interest in trying to get it up and running. Previous attempts had failed, as i couldn't get the 304 driver going. for whatever reason, I was successful this time.

I guess I'll have to figure out how to edit Grub. I can use the current HDD install and if successful, then apply it to the SSD one.

You'll get from 16.04.1 to 16.04.7 after installing updates. There is probably quite a lot, so remove all unneeded packages first. Starting with that old image is the key to get nvidia-304 to work, because it has the right kernel and xserver versions, which may be old, but still supported.

...Not sure what you mean by "edit grub". Why bother?

---

### Post by TheFu on 2020-08-21
Unity?  Unity is dead, dead, dead. Move on. Get over it.  Try fvwm. ;)

Nouveau drivers work on all Ubuntu releases. There's nothing tied to any DE.

If you buy a current PCIe GPU, it can be moved to the next system you get/built.

Nvidia stock price has no impact on Linux ease of use, sadly.  On the cheap GPUs, there's little reason to prefer nvidia.

---

### Post by O)9(yo&amp;# on 2020-08-21
> **mikewhatever said:**
> You'll get from 16.04.1 to 16.04.7 after installing updates. There is probably quite a lot, so remove all unneeded packages first. Starting with that old image is the key to get nvidia-304 to work, because it has the right kernel and xserver versions, which may be old, but still supported.

...Not sure what you mean by "edit grub". Why bother?

I did get 304 working in a fresh 16.04.7 install. It had nouveau going by default. I knew from previous experience with 16.04 that switching to Nvidia 304 was going to be dicey, as pulling up the Additional Drivers dialogue would crash the display. So I used the terminal to get there. that worked, the dialogue came up and I was able to run it and make the switch to 304. It's been running flawlessly. Only problem is it updates to the newer kernel.

so it seems I can either keep 16.04.7, and use Advanced Options in Grub, to boot the 4,4 kernel; or remove the newer kernels; or edit grub to boot the 4.4 kernel. Or, install 16.04, and stay on the 4.4 kernel, and eventually get t0 16.04.7 that way.

when I figure it all out, I'll put it on the SSD. Meanwhile, I'm continuing to test 16.04.7. so far it works as well as Linux Lite 3.8, which has been working flawlessly for several months now.

---

### Post by O)9(yo&amp;# on 2020-08-21
> **TheFu said:**
> Unity?  Unity is dead, dead, dead. Move on. Get over it.  Try fvwm. ;)

Nouveau drivers work on all Ubuntu releases. There's nothing tied to any DE.

If you buy a current PCIe GPU, it can be moved to the next system you get/built.

Nvidia stock price has no impact on Linux ease of use, sadly.  On the cheap GPUs, there's little reason to prefer nvidia.

Interesting. Never heard of FVWM, but I just checked it out, maybe that's something to look into it. As for Unity, I must confess I'm a bit of a Luddite, given to living in the past to some extent. Maybe because the world is getting so crazy and confusing. Like Will Smith in "I, Robot." 

If Unity still works, and Ubuntu 16.04.7 works, I'll run it happily, until it no longer works or is no longer supported.

---

### Post by O)9(yo&amp;# on 2020-09-04
> **mikewhatever said:**
> You'll get from 16.04.1 to 16.04.7 after installing updates. There is probably quite a lot, so remove all unneeded packages first. Starting with that old image is the key to get nvidia-304 to work, because it has the right kernel and xserver versions, which may be old, but still supported.

...Not sure what you mean by "edit grub". Why bother?

Well I decided against getting another SSD, due to the fact that this computer is so old, and the video card and 450 Watt PSU both stopped working. I had to put the original 300W PSU back in. In addition to needing the 304 driver, I guess I have to be careful about adding too many peripherals. Yes, I could solve all this with a new PSU and video card, but I stopped putting money into my 20 year-old Accent recently, and the same logic applies here. Keep it simple and see how long it lasts. Then probably buy a new desktop, which I will be able to put anything on. Although I seem to prefer older systems anyway...

Anyway, I installed 16.04.1 yesterday. I dual-booted it with Linux Lite 3.8, which like U16 is supported until April (I plan to sign up for extended support at that time). I just did a round of updates, and true to your word, I still have only the 4.4 kernel, only now it's 4.4.189. I'm assuming at some point it will get to 16.04.7, but it's not there yet.

Thanks for the help. So far everything is working fine. If it doesn't update to 16.04.7 eventually I'll let you know.

---

### Post by TheFu on 2020-09-04
> **michael_diemer said:**
> Interesting. Never heard of FVWM, but I just checked it out, maybe that's something to look into it. As for Unity, I must confess I'm a bit of a Luddite, given to living in the past to some extent. Maybe because the world is getting so crazy and confusing. Like Will Smith in "I, Robot." 

If Unity still works, and Ubuntu 16.04.7 works, I'll run it happily, until it no longer works or is no longer supported.

I completely understand choosing to use older stuff.  fvwm is from 1995-ish, but has been maintained and upgrades over the decades with more "features."  It is basically the same now as it was then, just with lots more pre-made themes, which I really couldn't care about. It is the minimal memory use and total control for window styles and placement and the virtual desktops that got me initially and brought me back after screwing around with DEs for about a decade.

Unity is a failed experiment. There is never a good time to change desktops, so a migration when you have control seems to be a prudent method.  fvwm won't conflict with Unity. You can have both on the same system, using the same HOME directory safely. That's different than with other DEs. Sometimes their config data getting mixed breaks things, badly. Not with fvwm.  Try it. Learn the POWER of the fvwm. ;)  And you may never switch to any of the new-fangled DEs again that all the kids have been running since the mid-2000s.

After all, the DE is just another program that runs on top of a WM that runs on top of X11 that runs on top of Linux.

---

### Post by O)9(yo&amp;# on 2020-09-04
> **TheFu said:**
> I completely understand choosing to use older stuff.  fvwm is from 1995-ish, but has been maintained and upgrades over the decades with more "features."  It is basically the same now as it was then, just with lots more pre-made themes, which I really couldn't care about. It is the minimal memory use and total control for window styles and placement and the virtual desktops that got me initially and brought me back after screwing around with DEs for about a decade.

Unity is a failed experiment. There is never a good time to change desktops, so a migration when you have control seems to be a prudent method.  fvwm won't conflict with Unity. You can have both on the same system, using the same HOME directory safely. That's different than with other DEs. Sometimes their config data getting mixed breaks things, badly. Not with fvwm.  Try it. Learn the POWER of the fvwm. ;)  And you may never switch to any of the new-fangled DEs again that all the kids have been running since the mid-2000s.

After all, the DE is just another program that runs on top of a WM that runs on top of X11 that runs on top of Linux.

I'll have to give it a try. I know what you mean about putting alternative desktops on a system. I have indeed had issues, which ultimately forced me to reinstall, so I've decided against trying say, XFCE (my favorite). Unity works well enough, but  never feels entirely intuitive. Like, I would like to configure it so that as soon as I click on the Start button, all my apps are there. But I have to first click on the right symbol, then "show 75 more items" or whatever it says. Maybe that's configurable, but I'd rather not get into it. I do prefer Unity to Gnome 3, however, but that's a moot point as this computer can't go beyond 16.04 and still have the Nvidia driver. So. I'll look into fvvm. Unity is about the heaviest DE that will work for this rig. I'm always waiting for a display failure, but I had been using it with no problems for a couple months on a HDD,so I went ahead and put it on the SSD, where of course it's much faster., so it probably will continue to work. But having something lighter as a fallback is a great idea.

---

### Post by mikewhatever on 2020-09-04
> **michael_diemer said:**
> Well I decided against getting another SSD, due to the fact that this computer is so old, and the video card and 450 Watt PSU both stopped working. I had to put the original 300W PSU back in. In addition to needing the 304 driver, I guess I have to be careful about adding too many peripherals. Yes, I could solve all this with a new PSU and video card, but I stopped putting money into my 20 year-old Accent recently, and the same logic applies here. Keep it simple and see how long it lasts. Then probably buy a new desktop, which I will be able to put anything on. Although I seem to prefer older systems anyway...

Anyway, I installed 16.04.1 yesterday. I dual-booted it with Linux Lite 3.8, which like U16 is supported until April (I plan to sign up for extended support at that time). I just did a round of updates, and true to your word, I still have only the 4.4 kernel, only now it's 4.4.189. I'm assuming at some point it will get to 16.04.7, but it's not there yet.

Thanks for the help. So far everything is working fine. If it doesn't update to 16.04.7 eventually I'll let you know.

I am glad it worked for you. With all available updates, it should be at 16.04.7, unless that was just the new ISO identifier.
Check what you have with <lsb_release -d>.
PS: For all applicators, try <nautilus /usr/share/applications>. You can create a launcher or a shortcut for it.

---

### Post by O)9(yo&amp;# on 2020-09-05
> **mikewhatever said:**
> I am glad it worked for you. With all available updates, it should be at 16.04.7, unless that was just the new ISO identifier.
Check what you have with <lsb_release -d>.
PS: For all applicators, try <nautilus /usr/share/applications>. You can create a launcher or a shortcut for it.

You're right, I do have 16.04.7. I saw on the Grub menu that I now have two versions of 16.04.7, one on an old HDD, and the new one on the SSD.

Which brings me to another problem. I can't boot Linux Lite 3.8 from the grub of Ubuntu 16.04.7. It is  listed, but I get the "hit any key" thing if I try to boot it. I can boot it from the Super Grub 2 rescue disc. I tried repairing LL3.8 with gparted, while on Ubuntu. Also tried a boot repair disc, but it wanted me to do some terminal commands, which I'm reluctant to do as they involved changing root. Which makes me a little nervous (guess I don't trust that repair disc completely. you never know).

Thanks for the tip on the Launcher.

I need to get this working, so I can image the SSD as a backup. Does it have something to do with which OS is root (that is, has the slash mark on gparted)?

---

### Post by TheFu on 2020-09-05
> **michael_diemer said:**
> I tried repairing LL3.8 with gparted, while on Ubuntu. Also tried a boot repair disc, but it wanted me to do some terminal commands, which I'm reluctant to do as they involved changing root. Which makes me a little nervous (guess I don't trust that repair disc completely. you never know).

"changing root" is just a way to use the correct installation binaries to accomplish a specific task.  This would be important to fix a non-booting system.

I haven't dual booted in a very long time.  I use virtualization all the time, constantly, right now. Usually have 10-15 VMs running all the time. You probably already know all the reasons why virtualization is handy, less risky, and easier, so I won't bore you.

---

### Post by O)9(yo&amp;# on 2020-09-05
> **TheFu said:**
> "changing root" is just a way to use the correct installation binaries to accomplish a specific task.  This would be important to fix a non-booting system.

I haven't dual booted in a very long time.  I use virtualization all the time, constantly, right now. Usually have 10-15 VMs running all the time. You probably already know all the reasons why virtualization is handy, less risky, and easier, so I won't bore you.
Thanks, guess I'm being overly cautious. I'm currently downloading Resactux to try and solve this. I tried using those terminal commands in the past with the boot repair disc, but got nowhere, so I'll give this a shot. 

Virtualization does seem to be getting more and more popular. I'd need a more powerful machine for it, though. I do have an i7, but that is solely for my music creation. I only have windows 7 Pro on it, which I need because of the programs I run. No good alternatives in Linux for what I do. If my Linux machine finally bites the dust, I may put a Linux-only drive in the music rig. Or just get a new Linux-only desktop. But virtualization is fun, I've played around some with it.

---

### Post by TheFu on 2020-09-05
boot-repair was fine for non-UEFI systems with 1-2 OSes.  After that, really just use it for the "Gather Information" button so all the boot information gets posted where some smart people can check it out and make recommendations based on facts.

Virtualization has been popular since the 1990s. In 2004-ish, the company where I worked mandated that all new server deployments be virtual. That company had over 20K Windows servers and 40K Unix servers. Most were using less than 20% of the CPU, so it was a business imperative to get more business value/work from the systems. The new CPU goal was 80% utilization.

These days, many companies have move onto Linux Containers rather than virtualization.  Those aren't all that useful for desktops, however.

---

### Post by O)9(yo&amp;# on 2020-09-05
> **TheFu said:**
> boot-repair was fine for non-UEFI systems with 1-2 OSes.  After that, really just use it for the "Gather Information" button so all the boot information gets posted where some smart people can check it out and make recommendations based on facts.

Virtualization has been popular since the 1990s. In 2004-ish, the company where I worked mandated that all new server deployments be virtual. That company had over 20K Windows servers and 40K Unix servers. Most were using less than 20% of the CPU, so it was a business imperative to get more business value/work from the systems. The new CPU goal was 80% utilization.

These days, many companies have move onto Linux Containers rather than virtualization.  Those aren't all that useful for desktops, however.

If Resactux doesn't solve it, I'll use the boot repair disc to do what you suggested - post the info so smart people can figure it out (like you).[IMG]https://ubuntuforums.org/images/icons/icon7.png[/IMG]

---

### Post by CelticWarrior on 2020-09-05
Do not use the Boot Repair disk (ISO). It hasn't been updated for years. Use a live session and install it from the PPA, i.e., the 2nd option: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by O)9(yo&amp;# on 2020-09-05
> **CelticWarrior said:**
> Do not use the Boot Repair disk (ISO). It hasn't been updated for years. Use a live session and install it from the PPA, i.e., the 2nd option: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Thanks, I was not aware of that. It has helped me out many times, but now I'll use the live session version. 

the reason I got nervous about using it: the only time I was hacked (at least to my knowledge), I was on a composers forum, which uses the Flash player (I won't use it myself and have been telling them for years to get rid of it). I stepped away from my computer for a bit, and when I returned, someone had got in somehow. They had a terminal up and running, and before my very eyes somebody was typing "chroot." Of course I shut down immediately, overwrote the OS (it was BSD system). I used a heavy duty app, something like "dban" as I recall. So, when I remembered that incident, and an app was wanting me to mess with the chroot command, I got cold feet. I don't know if they got in because of Flash, or because it was a BSD system, or something else. but I have become really paranoid now about the web.

---

### Post by monkeybrain20122 on 2020-09-05
> **TheFu said:**
> Unity?  Unity is dead, dead, dead. Move on. Get over it.  Try fvwm. ;)




No, it is maintained by the community, it can be easily installed with sudo apt install ubuntu-unity-desktop, switch to lightdm when prompted.
Reboot, log into unity, that's it (optionally one can remove gnome-shell)
I am using unity in 20.04. Works flawlessly, much better than the clunky mess that is gnome shell.
[https://discourse.ubuntu.com/c/desktop/ubuntu-unity-dev](https://discourse.ubuntu.com/c/desktop/ubuntu-unity-dev)

---

### Post by O)9(yo&amp;# on 2020-09-05
> **monkeybrain20122 said:**
> No, it is maintained by the community, it can be easily installed with sudo apt install ubuntu-unity-desktop, switch to lightdm when prompted.
Reboot, log into unity, that's it (optionally one can remove gnome-shell)
I am using unity in 20.04. Works flawlessly, much better than the clunky mess that is gnome shell.
[https://discourse.ubuntu.com/c/desktop/ubuntu-unity-dev](https://discourse.ubuntu.com/c/desktop/ubuntu-unity-dev)

I'm glad to hear that it is still maintained. I too vastly prefer it to Gnome. Wasn't sure how well it worked in >Ubuntu 16 systems. I wish Xubuntu, Lubuntu and Mubuntu had 5 year support. If so I'd probably be using one of them.

---

### Post by monkeybrain20122 on 2020-09-05
> **michael_diemer said:**
> I'm glad to hear that it is still maintained. I too vastly prefer it to Gnome. Wasn't sure how well it worked in >Ubuntu 16 systems. I wish Xubuntu, Lubuntu and Mubuntu had 5 year support. If so I'd probably be using one of them.

Unity works flawlessly on 20.04.

---

### Post by O)9(yo&amp;# on 2020-09-05
The only way I can get both U-16 and Lite 3.8 to boot is to have Lite be the Grub 0wner. If I have Ubuntu be the owner, Lite won't boot. not a big deal, except the Ubuntu grub is a lot prettier, with that purple color. Gotta have that purple...Oh well...

---

### Post by TheFu on 2020-09-06
> **michael_diemer said:**
> The only way I can get both U-16 and Lite 3.8 to boot is to have Lite be the Grub 0wner. If I have Ubuntu be the owner, Lite won't boot. not a big deal, except the Ubuntu grub is a lot prettier, with that purple color. Gotta have that purple...Oh well...

There are other boot managers, I hear.  Guys in my Linux group use one, but since I don't dual boot, I've never paid attention. In the OS/2 days, I used some thing called OS-BS, but that was to get passed the boot sector limitation that lilo had all those years ago. I think grub is still used, just to each different system, they don't know about each other.

---

### Post by mIk3_08 on 2020-09-06
> **TheFu said:**
> Unity?  Unity is dead, dead, dead. .

Are sure, Why I'm still using it until now? If its dead I'm sure it won't run to my system right now but it did with no hassle running on 64 bit OS Kernel: 5.4.0

---

### Post by TheFu on 2020-09-06
Correction: Unity _should_ be dead, dead, dead.  It is an abomination. Has been since the beginning.  Better?  

But this is a matter of opinion.  ;)

---

### Post by O)9(yo&amp;# on 2020-09-06
Last night I downloaded Grub Customizer, in an effort to spruce up Linux Lite's bland looking grub (most of them are). but it didn't seem to work. The picture I chose was not there when I booted up. Must be doing something wrong, or maybe Lite doesn't want me messing with its grub? I consider Ub. 16 to be my primary system now, since, with extended support, it's good until 2024 (as is kernel 4.4). Where Lite 3.8 support ends next year. So I would like it own Grub. I could put Lite on its own hard drive, but then it would be slow. Still, it would be there as a backup in case Ubu stops working. Decisions, decisions...

---

### Post by TheFu on 2020-09-07
Pre-boot images have to be in very specific formats with very specific resolutions AND the BIOS has to support them.

---

