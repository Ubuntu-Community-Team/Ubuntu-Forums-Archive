---
title: "Installation warning on Dual boot Windows systewms."
date: 2007-08-06
forum: Installation &amp; Upgrades
---

### Post by tuksi on 2007-08-06
Ubuntu overwrites the MBR on the hard drive when it installs itself by assuming that it will control the boot partition from that point on. The problem is that if one needs to remove Ubuntu the MBR is corrupted for proper booting for Windows.

If the programmers want to convince Windows users to use Ubuntu as well ( all will want to ) then :
1 - the option of a dual boot Grub should be provided at installation time.
2 - there has to be a clean Ubuntu REMOVAL tool to restore the MBR.

Ubuntu r:popcorn:eminds one of the first versions of Windows. A very good beginning. HOWEVER ! The folks who assembled Ubuntu made a few bad assumptions similar to that of Microsoft : "doing it our way is the best. You will not want to remove ANYTHING once you try it." Heaven help the novice user if they try to REMOVE Ubuntu from a dual Windows boot system !

Folks, lets get this thing better field tested : we all need a better alternative to Windows !!!!

---

### Post by merlinus on 2007-08-06
Did you even try to find simple instructions for this situation:

[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

And frankly, ubuntu is not for people who are uninterested in learning new things.

-merlin

---

### Post by dabl on 2007-08-06
Ummmmmmm, Ubuntu has a perfectly WONDERFUL method for enabling folks to try it as long as they wish, before they make any long-term commitment -- it's called LIVE CD!


Sheesh .....

---

### Post by Pumalite on 2007-08-06
Ditto. ( Go and look at the dictionary )

---

### Post by rillip on 2007-08-06
Let's review the facts:

1. If you install Ubuntu after Windows, you get the Ubuntu boot loader (Grub).
2. If you instal  Windows , you get the Windows boot loader (... whatever MS calls it)
3. Grub lets you boot Windows
4. MS's boot loader... doesn't.

So in review of these facts, Grub is in fact already trying to play nice and not just screw you out of your other OS like Windows does.  Now you want it to be able to go back and reconfigure the Windows boot loader when you decide you don't want it anymore? edit: Also, most installations detect the Windows install and automatically add it to grub for booting, so your first point is moot.  

You have Grub, that plays nicer than Window's boot loader.  You have the LiveCD.  You can even set it up to leave grub and just use it to boot Windows after you uninstall. Windows does none of this for you.

While I can understand your opinion, and it is yours to have, Ubuntu is already trying hard to work well with others.  It's not fair to put the onus on it to go back and set your configuration back to the pre-installed state.  If you're not willing to pop in a Windows CD and run "fixmbr," or to install grub to a partition you can leave, then don't bother to install.

---

### Post by SeanHodges on 2007-08-06
Windows overwrites the MBR on the hard drive when it installs itself by assuming that it will control the boot partition from that point on. The problem is that if one needs to remove Windows, the MBR does not allow you to boot Ubuntu properly.

If Microsoft want to convince Linux users to use Windows as well (some might want to) then:
1 - the option of a dual-boot Windows boot should be provided at installation time.
2 - there has to be a clean Windows removal tool to restore the MBR.
3 - [http://badvista.fsf.org/what-s-wrong-with-microsoft-windows-vista](http://badvista.fsf.org/what-s-wrong-with-microsoft-windows-vista)

Windows reminds one of the first versions of Linux. A very good beginning. They constantly make the assumption that "doing it our way is best, you must have these things to use your computer and some of this you will need to pay additional costs for." they also insist that you must put up with bugs and security issues until the demand is high enough, and they get time to fix them.

Both Windows and Ubuntu have been field tested, a lot; and after looking up both options, trying both for a good number of years, as a user and as a developer, I have come to my own conclusion that Ubuntu far exceeds Windows.

---

### Post by tuksi on 2007-08-07
How quickly we forget how awkward Windows was in the beginning and why we dislike it to this day. Repeating errors of the past is not progress.

---

### Post by Pumalite on 2007-08-07
Windblows ia awkward today.

---

