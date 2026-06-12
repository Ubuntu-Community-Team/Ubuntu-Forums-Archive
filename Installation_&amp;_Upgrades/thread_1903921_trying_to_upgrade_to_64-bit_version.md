---
title: "trying to upgrade to 64-bit version"
date: 2012-01-03
forum: Installation &amp; Upgrades
---

### Post by ProntoAnthony on 2012-01-03
I've been on the 32-bit version of 11.10 for over 2 months now with 1G of memory. Was having a problem with running Unity. Unity 2D worked great but development using Eclipse was running really slow. With memory cheap these days I decided it would be much less expensive to add memory as opposed to upgrading my entire PC.

The system has an AMD Athlon 64 X2 dual-core processor, and with the added memory I have to upgrade to 64-bit addressing in order to access the full 4Gig of RAM.

Installed the memory last night. Now the system runs Unity 3D and Eclipse runs much faster. Still, I could only access 3.6Gig of the memory using the 32-bit version of Ubuntu 11.10, so I decided to bite the bullet and do the upgrade. I was not looking forward to reinstalling all applications, but in the long-run I knew it will be worthwhile.

I downloaded the ubuntu-11.10-desktop-amd64.iso image to my hard drive and then used a new 8G USB stick that I bought along with the memory to create a 64-bit usb boot image. When I booted off the USB stick the monitor went all snowy and the system halted. All I could do was reboot of the hard drive since I couldn't read the screen. 

Is there a step I missed in the upgrade process?

---

### Post by fantab on 2012-01-04
First of all double check the integrity of the USB .iso you have created... if needed download the .iso again and if possible use a torrent download and follow the instructions to the dot with creating the USB disk.

---

### Post by ottosykora on 2012-01-04
well, to install the x64 over the 32 is just a new install. This is no upgrade as such, so all has to be then done from scratch.
Look also where you have your data (home folder) and backup all to some other media best as you can. If you have separate /home partition, then ok, it can be used with the new install, but still backup it first.

But: do your installed kernels bear the 'extension' pae ?
If yes, you do not need to change to x64.

Tried an update after installing the new RAM? 

I am not sure if an update does it, but when I installed 32bit on a machine with 4g ram, it automatically detected the ram and picked the pae kernel version so the ram could be handled properly.

---

### Post by ProntoAnthony on 2012-01-04
fantab,

Good suggestion.

Downloaded the 64-bit iso file via torrent. Created a new start-up usb image. 

Same result. Didn't work.

Thought perhaps my new usb stick was bad, so I went through and created a 64-bit image on my old usb stick that worked for the 32-bit image.

Same result. Didn't work.

Switch usb ports on my PC, thinking perhaps the port was bad. Created a start-up usb stick on a different port made no change, except the resulting image on the monitor was a little different. Still unreadable.

So I'm back on the 32-bit version.

Now I'm going to see if perhaps going through a network upgrade as if I were still on 11.04 and seeing if ottosykora's idea that the system would automatically be upgraded to the 64-bit version because of the amount of installed memory will be a solution.

That didn't work. I couldn't find an option for doing a network upgrade like I intended. 

Any ideas would be appreciated.

---

### Post by ottosykora on 2012-01-05
no network upgrade, just when you have more memory, the pae kernel should be installed then. 
You can do that from synaptic too by hand probably, but update should do it too.

You can try also to pick same number of kernel in synaptic which has the pae at the end. Install it and start next time with this kernel. This can manage then your ram. This is not a x64 kernel , it just has drivers for more ram on board, but the rest is still normal 32 kernel.

---

### Post by ProntoAnthony on 2012-01-05
Success!! Thanks!

Adding the -pae version increase system memory from 3.4G to 3.966G. Nice trick, but I'm confused about the ramifications. Yes, all my 32-bit apps are still here and appear to be functioning. That's a real good thing.

What is missing? Am I taking a performance hit by not using 64-bit processing? 

BTW, what does "pae" stand for?

---

### Post by ProntoAnthony on 2012-01-05
And another thing: From the size of the launcher icons being so large and not changing even after going into CCSM, Unity does not appear to be running. Only Unity 2D.

I'm going to try using Synaptic and reinstalling Unity.

no, this had no affect, even after rebooting.

How do I get Unity back? How do I get Gnome 3 back? It is going to Gnome Classic when I login.

---

### Post by ottosykora on 2012-01-05
> **ProntoAnthony said:**
> Success!! Thanks!

Adding the -pae version increase system memory from 3.4G to 3.966G. Nice trick, but I'm confused about the ramifications. Yes, all my 32-bit apps are still here and appear to be functioning. That's a real good thing.

What is missing? Am I taking a performance hit by not using 64-bit processing? 

BTW, what does "pae" stand for?

no, you are not missing anything and you do miss any performance etc. If your 32bit environment runs fine, leave it so! Apparently the speed difference is not really measurable, I have heard also about some x64 programs running worse then the 32bit versions.

I have myself changed to x64 some time ago, but then it was due to some incompatibility of some items with probably my hardware. So in this direction I had definitely a gain in performance, as in my particular case certain important things did crash permanently.



The only difference with the pae kernel is, that it contains a module driver for the larger ram space handling.
The processor has to support this in fact, but most current onces do support it fine.

If installed on a hardware with more ram, then the pae kernel is picked right at the install time, otherwise if the ram is added later, it can be installed later from repository.

---

### Post by ottosykora on 2012-01-05
pae =

[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

---

### Post by ProntoAnthony on 2012-01-05
Thanks. That makes sense. So easy to implement.

By why doesn't Unity work? Why only Unity 2D?

---

### Post by ottosykora on 2012-01-05
>How do I get Unity back? How do I get Gnome 3 back? It is going to Gnome Classic when I login.
<

well me being from the unity opposition party, surprise that someone needs that back, but in general the reset to default helps.

Check search in the forums for reseting unitity or something like that, in general it does soleve all problems with it in one single go.


----
for example here is one:
[http://ubuntuforums.org/showthread.php?t=1870876&highlight=reset+unity](http://ubuntuforums.org/showthread.php?t=1870876&highlight=reset+unity)

---

### Post by ProntoAnthony on 2012-01-05
Well I can understand about Unity, but I'm having trouble getting into Gnome 3 as well. How do I reset Gnome?

---

### Post by ottosykora on 2012-01-05
> **ProntoAnthony said:**
> Well I can understand about Unity, but I'm having trouble getting into Gnome 3 as well. How do I reset Gnome?

well gnome3 is the base on which all that compiz and unity and what ever runs. Or did you install some gnome shell or what?

I am not an expert on those things actually, but gnome3 is installed as basic of your whole GUI.
How do you try to get into what ever front end? In general at login, one does select the right gui. If the hardware or drivers for example for graphic adapter are not sufficient for the 3d unity  , it will default back to 2d unity.

Did you have all running before and now it is lost or did you do some adjustments or modification to settings or how did it happen that things do not work properly?

---

### Post by ProntoAnthony on 2012-01-06
Still trying to get it working....

I had to completely re-install VirtualBox so that I could do some web testing on Safari under Windows XP, but I'm coming back to this problem with running Gnome Classic and/or Unity 2D.

I had to run Unity 2D because (I thought) this PC didn't have enough memory. That was the problem with running VirtualBox before. It was so slow! Now that I've configured my Windows XP session tyo have 1Gig of memory I can get some work done without being bored to tears waiting for the system to respond.

I'm going to try re-installing Unity and Gnome to see if it will clear up my problem.

---

### Post by ProntoAnthony on 2012-01-06
Used Synaptic to un-install the Gnome shell.

Re-installed using: sudo apt-get install gnome-shell

Rebooted.

Now I'm able to log into Gnome as well as Gnome Classic.

---

### Post by ProntoAnthony on 2012-01-06
Getting Unity back was somewhat more difficult but I did it. The steps I took:

from terminal:
[LIST]
[*]sudo apt-get remove unity
[*]sudo apt-get install unity
[/LIST]

Next:


[LIST]
[*]restarted system
[*]boot process did not get to the auto-login process, so I key alt-F2 to get a non-gui login prompt.
[*]Enter my username and password at prompts
[*]keyed in command: start x
[*]Gui starts, with Unity coming up. I noticed because the launcher icons are smaller.
[*]logged out and the GUI ends, dropping me back t the command prompt.
[*]Keyed in: SysReq button with ctl-alt held down, then hit the B key to reboot.
[*]Boot process gets to auto-login process and logs me into Gnome 3.
[*]Then logged out
[*]The login screen apears and I choose Unity from the gear icom login menu.

[*]Logs me in to Unity 3D and I'm done!
[/LIST]

---

