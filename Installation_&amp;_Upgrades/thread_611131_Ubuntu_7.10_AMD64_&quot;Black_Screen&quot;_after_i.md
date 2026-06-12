---
title: "Ubuntu 7.10 AMD64 &quot;Black Screen&quot; after install"
date: 2007-11-12
forum: Installation &amp; Upgrades
---

### Post by Badmagic on 2007-11-12
I had the problem with trying to get past the initial options screen of the boot cd (Install, Memtest etc), I managed to fix that after reading dozens of posted conflicting answers by removing &#8220;splash&#8221; and added &#8220;apci=off&#8221; to the F6 launch options until finally I got to the &#8220;desktop&#8221; view with the install icon, I went through the 7 or so questions it wanted answered then it proceeded to install fine.

Once it had reached 100% I got the &#8220;Continue using live cd or re-boot&#8221;.

I chose to reboot and now I think the last message I see is something like &#8220;Loading up&#8230;Starting please wait&#8230;&#8221; (to fast to really know) before my monitor turns itself off with the no signal problem.

I tried using the ESC menu to see if there was a quick way around this but the only options on it are as follows:

1.  Ubuntu 7.10, kernel 2.6.22-14-generic
2.  Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
3.  Ubuntu 7.10, memtest86+

None of which make any difference, the same error occurs on every option forcing a manual reboot.

Can anyone guide me as to a work around for this; I am using the apparently incompatible ATI AGP X800 card?

Using the generic pre-specified driver rather than setting it to the ATI one during the live cd boot seemed to work fine, it was only when I tried to actually set it to the correct driver that it would not function.

Unfortunately I have been searching for a few hours and have found no real solution to the second problem as at the moment I have no idea how to get past it thus a very expensive paperweight instead of a pc is sitting on my desk.

:confused:

***EDIT***

Sorry I did not specify but when using the recovery option it leaves me at the "root@username:~#" prompt where I have absoloutly no idea what it wants me to input.

*END*EDIT*

***EDIT2***

Another note, I have seen it stated that this can be fixed by:

"add 'Option "LVDSBiosNativeMode" "false"' to the driver section of xorg.conf"

Unfortunately nobody seems to have stated anywhere how exactly we are to add 'Option "LVDSBiosNativeMode" "false"' to the driver section of xorg.conf.

*END*EDIT2*

---

### Post by Badmagic on 2007-11-12
So, I manually managed to change it back to vesa using the command line “sudo dpkg-reconfigure xserver-xorg” and it finally let me into the install.

Now the next set of issues, I had a set of spam information boxes telling me the switch user option could not be started followed by something telling me to configure my video drivers which I was dubious about doing what with the last problem but on clicking the option to enable them I have to guess it tried to use the net as now there is no net connection even though it worked by default on the live cd?

On looking at help documentation I finally found the reference to using the “Network” option, unfortunately it just spasm a box stating I am denied access to the “Network” option.

Has nobody written the steps to getting the full install to work as the live cd does anywhere, I have been looking for tutorials but can’t see anything adequate for a new user.

It also seems quite odd that the live cd version works but the full install does not?

So again, this time I am looking for help in remedying this net connection issue, just adding it to this topic as the original question has not been solved at best it was a work around to avoid the problem.

---

### Post by Badmagic on 2007-11-13
So, the work around didn’t work after all, the monitor has resumed shutting itself off before launch again.

---

### Post by nickbrook on 2007-11-15
Hi. I've been experiencing the same problem with a 7.04 install (x86_64). I think it's something related to the splash screen since if you start up in safe mode and start x using:

init 5

everything starts as expected. 

I'll try a 7.10 install tomorrow and see if there's any improvement

---

