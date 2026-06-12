---
title: "upgrade ubuntu studio lucid directly to ubuntu studio maverick?"
date: 2011-01-09
forum: Installation &amp; Upgrades
---

### Post by youWho on 2011-01-09
Hi all,

I'm currently using Ubuntu Studio Lucid and would like to use Ubuntu Studio Maverick, but I'm unsure how to go about the upgrade. Should I upgrade to generic ubuntu maverick then upgrade to ubuntu studio? Or install ubuntu studio maverick from a DVD?? Or something else??

I should say that I have a separate /home partition.

[Edited because what I first wrote was confusing:]  when I started the process of upgrading with Update Manager it said that quite a lot of things would be removed (it would be upgrading only to generic Ubuntu for one thing)---I aborted that by the way. I was wondering if anybody knew of a way to avoid having to first sort of note everything that I have installed, then do the upgrade to generic Ubuntu, then do an upgrade to Ubuntu Studio, then reinstall all of the apps in their newer versions. Might there be a way to upgrade the OS itself first and then just directly update the apps without having to reinstall them, figuring out what to install all over again too?

I'd also like to keep all of my settings and configurations and such, though I'm guessing that there's no problem with that thanks to /home remaining the same.

Thanks for any tips.

---

### Post by youWho on 2011-01-12
Well, this is not a reply of course, just further thoughts in case anybody else might be trying to figure out how to go about this.

I decided to install from an Ubuntu Studio DVD to a new partition. Frankly I'm very glad I did that because I'm still very new to GNU/Linux and learning as I go. By keeping the old system for the moment I can still for example post this ;-).

I found a couple of probably useful posts re integrating the /home partition, which I kept during the fresh install of Maverick (if you have a separate /home and want to keep that you have to choose to do things "manually" during the partitioning stage of the installation---sorry I didn't write down exactly what it said but it's quite clear---and to use BUT NOT REFORMAT the /home partition). Now I'm about to try getting Maverick set up and to get it to use the user accounts I have. These are the postings I found on that:
[http://ubuntuforums.org/showthread.php?t=1344132](http://ubuntuforums.org/showthread.php?t=1344132)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1308767](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1308767)

---

### Post by Frogs Hair on 2011-01-12
If you choose to install Ubuntu Studio backup your data and do a clean installation. It would be much easier to install the packages you want from US on your current installation.

---

### Post by youWho on 2011-01-12
> **Frogs Hair said:**
> If you choose to install Ubuntu Studio backup your data and do a clean installation. It would be much easier to install the packages you want from US on your current installation.

You know, I very much appreciate your reply, just because it could save some people a lot  of trouble; that is, to anybody who reads this: please be careful and read on to see how it's going for me at the moment:

*Fortunately* even before Frogs Hair's post I had decided to install Ubuntu Studio Maverick onto a separate  partition, so as to be able to keep the (working) Ubuntu Studio Lucid install I have. I say "fortunately" because after installing Maverick I had quite some difficulty getting to the internet i n the new OS. It would seem that Ubuntu Studio doesn't include network-manager by default and for those of us who are new to Ubuntu Studio getting that installed can be a hack (I'm not a total noob, though I'm new to GNU/Linux and not a programmer). For those who have this problem, I'll post elsewhere how I solved it but briefly it entailed adding the DVD to the repositories used by Synaptic, inserting the DVD, installing the network-manager (to which was automatically added network-manager-gnome plus others), getting that configured, reset and workiing... Anyway al fin iinternet.

Next I ran System->Administration->Update Manager to bring the OS up to date. All went well.

After a restart I tried System->Administration->Hardware Drivers to "activate" the proprietary nvidia driver for my Sony Vaio VPCF116FX---this is what had eventually gotten the display working properly in the Lucid case. *But* after running that and restarting I now have a totally dead display, and am at the moment stumped. *Any help would be appreciated.* The symptom is that the computer boots but in the last stages of the boot instead of getting to the gui I get a blank light purple screen, and that's all. Alt-F1, 2, etc. don't get me to a console; the only way I can even get to a terminal-like situation (sorry for my lack of proper terminology here) is to select in the grub menu at startup to go to a recovery mode, then to choose a "failsafe" (display) mode. From there I could finally run "sudo nvidia-xconfig", in the hope that that might fix it, but no go.

Like I say, if any of you kind folks has any tips I'd love to read them (thanks in advance). I've ben searching high and low but haven't found any solutions, I think at least partly because I don't know what the problem is exactly ("blank purple screen"???)

---

