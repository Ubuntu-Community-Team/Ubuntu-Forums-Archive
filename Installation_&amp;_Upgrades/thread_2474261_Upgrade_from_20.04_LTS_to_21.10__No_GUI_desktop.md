---
title: "Upgrade from 20.04 LTS to 21.10 : No GUI desktop"
date: 2022-04-25
forum: Installation &amp; Upgrades
---

### Post by scubascooby on 2022-04-25
Last night I realised that my LTS installation was never going to update with apt get update and upgrade so I did a release update to get to 22.10  It took a few hours but went well and restarted.

The blue Lubunu screen appearred with the circular hummingbird logo but after that all I got was a black screen, the sign in screen did not appear.

I was able to open the vconsole with ctr-alt-f2 and from there I could startx and the desktop opened.


How do I get Lubuntu to open the gui automatically ?


(I've been an occasional ubuntu user since about 2004 but don't dig into it's internals too much.)

---

### Post by Rex Bouwense on 2022-04-26
I am assuming that you are taIking about 22.04.  22.10 is scheduled for release next October.  It is generally not advisable to do a release upgrade from on LTS to the next LTS until the first point release.  22.04.1 is expected to be release around August.  At that time you would  receive a notification that it was available.  Bad things tend to happen if you attempt it before.  I have always conducted a fresh install of the LTS release.  (It generally only takes about 12-15 minutes.)  Is the only thing you have discovered wrong was the failure to open the desktop?  I would suspect that other things might not behave properly as well.

---

### Post by scubascooby on 2022-04-26
I did a release upgrade, I'm not sure how I could control which version it upgrades to.

Pretty sure it says 22.10 but I will check again.


MY MISTAKE. It's 21.10.  I was sure I saw 22.
10 somewhere.

---

### Post by scubascooby on 2022-04-26
Everything else seems to be ok but I've not tried a great deal, I've been focusing on fixing the desktop and Grub (menu doesn't appear).

Firefox and Skype look ok.

---

### Post by scubascooby on 2022-04-26
On console f7 where I would expect the desktop there is just a flashing cursor.

Also, until I start the f2 console the monitor behaves as though the gfx is being restarted. It keeps saying there is no input and then detects the input a few seconds later, looping.

---

### Post by ActionParsnip on 2022-04-26
It won't be 22.10. 22.10 is released in 20**22 **in the **10**th month (October). Unless you are a time traveller :lolflag:

---

### Post by guiverc on 2022-04-26
Lubuntu 20.04 LTS, if you'd *release-upgraded* as per the [Lubuntu manual]("https://manual.lubuntu.me/lts/D/upgrading.html") without the `-d` option would have upgraded you to the next *supported* release which currently is Lubuntu 21.10

If you'd used the `-d` option you would have upgraded to Lubuntu 22.04 LTS.  **After** the release of Lubuntu 22.04.1 this will be the release you upgrade to without `-d` option [from 20.04 LTS].

I would expect the following for Lubuntu 21.10 & 22.04 

- Ctrl+Alt+F7 should show a disabled text terminal; ie. a flashing cursor but no GUI.  It can be used to see kernel messages if left there (*and messages occur*).

- Ctrl+Alt+F1 is the GUI on modern kernels and is what is expected 

Lubuntu uses the Ubuntu defaults, and modern Linux kernels now default Ctrl+Alt+F1 to the GUI session (*what used to be Ctrl+Alt+F7*).

I wonder what you meant by "*Last night I realised that my LTS installation was never going to update  with apt get update and upgrade*" as upgraded packages are still occurring for Lubuntu 20.04 LTS which still has a year of *full-support* to run, and longer for the base Ubuntu packages.  That detail may provide some clues.

I also wonder if you're actually starting 2x GUI's, as if you ignore the main GUI accessible on F1, and use `startx` on a text terminal, you'll get  two Xorg sessions.

---

### Post by scubascooby on 2022-04-26
F1 is just a black screen, no cursor.

What I meant by the lack of upgrades is that it was still on 20.04.  I was expecting upgrade to at least offer a newer version but I realised that the config was set  LTS and I changed it to release.

I've been caught out before and been stuck on a version I couldn't upgrade from.

The release upgrade has now bumped it to 21.10.  I don't know they were year. Month numbers.


Why is the gui desktop not starting as expected ? Are there any diagnostics that may give a clue ?

I'm wondering if I should bump it to 22.04 to see if that fixes it.

---

### Post by scubascooby on 2022-04-26
Before startx:
xorg is running on tty1


After startx:
Xorg is running on tty1

Xorg and lxqt are running on tty2

---

### Post by scubascooby on 2022-04-29
I just applied the 22.04 LTS upgrade and the result is much the same. Blue boot screen and then a black screen and still cannot access the grub menu.

I added nomodeset to the /etc/default/grub config file and removed quiet but this made no difference.

When logging in to the F2 console there is now a "nouveau" error.

---

### Post by scubascooby on 2022-05-01
Thinking this is a grub issue I edited the /etc/default/grub file to add:

GRUB_DISABLE_OS_PROBER=false

and restarted grub.

Rebooting was worse, nothing, just black screens and no consoles.  However the caps lock and numlock lights suggested that it
wasn't completely dead.

So I plugged in a vga cable and rebooted and it actually got to the login screen and I can login at 1024x768.

So is this a gfx problem ?

---

### Post by tea for one on 2022-05-02
After a week without a concrete result:-

Why not download an ISO of Lubuntu 22.04
Prepare a USB boot device
Run a live session for evaluation
Back up data
Install Lubuntu 22.04 if all OK
Restore data

---

### Post by guiverc on 2022-05-02
I'll give some thoughts here.

If it was me; I'd likely write Lubuntu 21.10 to thumb-drive & boot it on your actual hardware in *live* mode (ie. Start Lubuntu and just use it). Lubuntu 21.10 uses the 5.13 kernel, and maybe your machine doesn't like that?  You now highlight a *potential graphics* issue; thus why I'm thinking kernel.


However, Lubuntu 20.04 LTS was using either the GA kernel (5.4) **or **the HWE kernel which currently is 5.13 anyway; meaning your kernel may have been very different (*if you were using the GA kernel stack; were you?*) or no change at all (*ie. 5.13 if fully-upgraded to 20.04.4 with HWE**; were you?).   *Do you remember what you were using? or what media you installed Lubuntu 20.04 LTS with?  With Lubuntu 20.04 LTS, the default kernel stack you were using is dictated by the media you installed your system with (*as it is for all flavors of Ubuntu*).

I've had boxes in QA that were fine with Lubuntu 18.04.3 & earlier; but had an issue with the HWE kernel when it hit 18.04.4, and other boxes that didn't like 18.04.5.. but by switching those boxes back to using the GA kernel stack those old boxes were great. Here I'm talking about **old **hardware, ie. boxes from 2003-2005, and I've found the older boxes tend to perform better on older kernels.  FYI:  Those boxes weren't reacting to anything done by Lubuntu; it was the newer kernels they didn't like; so they reacted the same if it was Ubuntu, Xubuntu or any other OS using the same kernel.

I'd test your system using *live* media; ie. I'm meaning the "*Try or Install Lubuntu*" in the manual [here]("https://manual.lubuntu.me/stable/1/1.3/installation.html") or [here]("https://manual.lubuntu.me/lts/1/1.3/installation.html") (*I've provided links for different Lubuntu manuals; they are the same page but what you see will be represented by one of these pages; with the Try or Install or Start Lubuntu - where you're just going to Try/Start it but not install; ie. to see if it boots up & visually works.. you can use it normally to browser internet briefly etc*).

I'd try Lubuntu 21.10 first (5.13 kernel); as it's what you upgraded to, then try Lubuntu 22.04 LTS (5.15 kernel), as if you were going to re-install; I'd recommend Lubuntu 22.04 LTS too if you had to go that way.

FYI:  What I'm suggesting is what @tea for one mentions in the prior reply anyway (ie. *run a live session for evaluation*). 

Knowing how the *live* tests go (5.13 & maybe 5.15 kernel), plus hopefully what kernel stack you were using back when you were on 20.04 (GA? HWE? you didn't specify), I'd hope to have possible clues; as I'm suspicious your issue relates to kernel change -- **but**  I have no idea which kernel stack you were using back when using Lubuntu 20.04 LTS.

---

### Post by scubascooby on 2022-05-03
You have used abbreviations and terminology I'm not familiar with.

Although I've used Ubuntu for may years, I'm an occasional user and avoid playing with the installation because of too many bad experiences with updates leaving me with broken installations and lost data.

I think this build was originally  ~18.04 installed from the boot cd, and using the internet method.

What is odd if that the gfx worked fine when running startx manually.

---

### Post by scubascooby on 2022-05-03
Yesterday in an attempt to get the grub menu to appear I added this to the end of the config file:

GRUB_DISABLE_OS_PROBER=false


and ran

> sudo update-grub

It made no difference to grub but afterwards it would only boot with VGA and I couldn't get it to boot with DVI like before.

Reverting the change and I am able to get to the F2 console and startx in DVI

---

### Post by scubascooby on 2022-10-02
Last night I downloaded the latest [SIZE=2]Lubuntu 22.04.1 LTS [/SIZE]and put it on a USB stick.  Booting from the stick produced no desktop but if I moved the dvi cable to the other output there is a desktop.

Great, so I installed it on a fresh HD and rebooted.  Once again no desktop.  So I switched to console F2 and ran startx like I did above.  This produced a desktop with no icons and no folder icons in the lower menu either so it's not very usable.

I liked Lubuntu but I think it's time to abandon it.

---

