---
title: "white screen at login after upgrade"
date: 2008-11-08
forum: Installation &amp; Upgrades
---

### Post by submition on 2008-11-08
Hi there,

I upgraded my Ubuntu server edition from 8.04 to the new 8.10 edition and I'm getting a problem upon loading up the login screen.

During the upgrade process I didn't run into any problems what so ever. After the update I restarted the computer and then right before the login screen pops up it goes all white and locks up. Nothing I've tried seems to be able to get around this so far (loading up with a earlier version, loading up in recovery mode etc...) I never used Compiz or any other effect types other than the default standards that come with ubuntu on that computer. 

Anyone have any ideas that might help out?

---

### Post by jerrylamos on 2008-11-08
Would help if we knew what hardware you have, processor, memory, graphics chip.  Problems vary with what it is running on.

For many with Intel graphics chip boot hangs with a black or tan screen just after login.  This is because compiz which is on by default (!) uses a video code path not used by any other software.  Compiz is "eye candy" and "animation",  Removing compiz affects no actual function.  The workaround is:

boot in rescue mode which is the second line on the initial grub screen
root shell prompt
sudo apt-get remove compiz compiz-core
exit 
resume normal boot

Another thing to try is to boot in rescue mode and try the X windows fix selection, I think the bottom selection on the menu.  There are various other Xwindows fixes on the posts which you may find by doing a search, example for:
xfix

Jerry

---

### Post by submition on 2008-11-08
Thx for the reply! 

Current hardware:
AMD Sempron 1800+
2gb DDR400 RAM
IGP VIA UniChrome Pro Graphics Engine
chipset: VIA K8M800 + VT8237

I'll give your suggestion a try and we'll see what happens :P

---

### Post by submition on 2008-11-08
Nope, using "sudo apt-get remove compiz compiz-core" or xFix did not work :(

---

### Post by charliedelong on 2008-11-09
I have the same thing (while it's a tan screen) and if I press CTRL-ALT-Backspace it loads the login screen.  Then I just have to choose failsafe and it will load fine.

Is there an easy way to see what the error is?  I turned off the splash screen so i could see what's going on, but it's right after GUI kicks in...

Anyone have any suggestions?

PS - I also have already removed Compiz.

---

### Post by submition on 2008-11-09
CTRL-ALT-Backspace doesn't load up the login for me :( 

Still looking for some advice.

---

### Post by dickohead on 2008-11-09
Does your computer have an ATI based graphics card?

Try this: [http://ubuntuforums.org/showpost.php?p=6129000&postcount=12](http://ubuntuforums.org/showpost.php?p=6129000&postcount=12)

---

### Post by submition on 2008-11-09
unfortunately I do not. On that computer it's only a VIA UniChrome IGP.

---

### Post by nerfdooker on 2008-11-09
well i seem to be having the same problem too, except that my screen is black(i changed the color from tan to black because it looked better:)) I don't think its an issue with compiz fusion since that isn't started until after you log in. To me it seems like gdm is not starting. It just sits there with the little spinny cursor and doesn't load. Any body know how i can log in from command line and then start x without having to go though gdm? 

PS my video card is a nvidia 9800gt:guitar: (envy me)

---

### Post by submition on 2008-11-10
Anyone have any ideas? I'd like to not format the HD because I'd lose all of the stuff I've worked on :(

---

### Post by dickohead on 2008-11-10
You could try using the vesa driver instead of the ati, via or nvidia driver. Then if it does boot in - it might be compiz, or a video driver issue.

I'd also suggest that you update your graphics drivers from the command line, I know that Nvidia has a nice command line tool for compiling new drivers, and ati drivers are in the repos, but as for via... mmmm good luck with that.

---

### Post by se.srikanth on 2008-11-17
Hi,

I too had the same problem, mine is a fresh install. i have MSI-7142 board with integrated grpahics (S3 Unichrome 2D/3D.) Like your's case, system freezes after launching graphics ending with a white screen and unresponsive mouse.

I tried getting to "recovery mode; drop down to root console" and issued "sudo X -configure" copied the newly generated xorg.conf to /etx/X11; restarted. Still no improvement. Searched for matching driver, but no use.:mad:

Finally, slapped in a supported graphics card. now the system is up!:)

If anyone had success with MSI-7142 board and Ubuntu 8.10, please post if they had success.

-srikanth

---

### Post by speedy67 on 2008-11-17
> **jerrylamos said:**
> For many with Intel graphics chip boot hangs with a black or tan screen just after login.  This is because compiz which is on by default (!) 

...

sudo apt-get remove compiz compiz-core

...

Thanks! This fixed my problem with a tan screen on a freshly installed Ubuntu 8.10. Used hardware: Compaq Evo D310 desktop with Intel 82845G/GL/GE chipset integrated graphics.

Speedy67

---

### Post by submition on 2008-12-08
Sooo, from what I've read I either need to uninstall 8.10 and go back to 8.04 OR buy a new video card... 

Anyone tell me how I can uninstall 8.10 and reinstall 8.04 while keeping my data on that harddrive?

---

