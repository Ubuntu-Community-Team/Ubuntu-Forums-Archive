---
title: "Lucid - Login twice"
date: 2010-02-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by gibbylinks on 2010-02-06
Hi,

I'm running Lucid Alpha 2 with all current updates. When I login I'm having to enter my password twice before I get to desktop.

Anyone any ideas why ?

Thanks

---

### Post by overdrank on 2010-02-06
Moved to Lucid Lynx Testing and Discussion

---

### Post by Kevbert on 2010-02-06
I had the same problem with Lucid Kubuntu. Even after a re-install the same problem occurred ??? Problem not resolved.

---

### Post by ghostborg on 2010-02-21
I was originally set for auto login and whenever I was required to enter my password I would get logged out and have to enter my password again.
That stinks if your in the middle of something.
I turned off auto login and have to login twice before getting to the Desktop. Better than before.

Lucid Alpha 2 with all current updates.

---

### Post by bladerunner6 on 2010-02-21
getting an issue with latest build and updated,
if i get logged out, it wont login again unless i go into the shell and restart gdm service

---

### Post by ghostborg on 2010-03-01
This happened again after a fresh install of Alpha 3 only after enabling the Nvidia driver in Hardware drivers. This is noted in a bug report that I saw with no solution at this time.
If I enable auto-login then attempt to do something that requires sudo password I am immediately logged out and all programs open at the time are terminated.

If I log in twice at the login screen the Ubuntu seems to operate normally.

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/528830]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/528830")

---

### Post by recluce on 2010-03-01
Check out this thread:

[http://ubuntuforums.org/showthread.php?t=1417140](http://ubuntuforums.org/showthread.php?t=1417140)

Short answer: try to remove plymouth from Synaptic

---

### Post by gibbylinks on 2010-03-04
> **recluce said:**
> Check out this thread:

[http://ubuntuforums.org/showthread.php?t=1417140](http://ubuntuforums.org/showthread.php?t=1417140)

Short answer: try to remove plymouth from Synaptic

Hi yes removing Plymouth solves it, but removing it doesn't help the developers trying to debug. 

I still have this problem with all the latest updates installed.

---

### Post by int on 2010-03-04
this happens also to me, with clean Lucid alpha 3.

I have auto login, and just after I put the gnome-keyring password, the X restarts, and ask to login again..

---

### Post by Uncle Spellbinder on 2010-03-04
> **gibbylinks said:**
> Hi yes removing Plymouth solves it, but removing it doesn't help the developers trying to debug. 

I still have this problem with all the latest updates installed.

Still have the problem here as well. No intention of removing Plymouth. As you say, "removing it doesn't help the developers trying to debug."

---

### Post by Owen.C93 on 2010-03-04
It's not really random. It's as soon as you press enter. I fixed this by updating the latest noveau drivers.

---

### Post by Uncle Spellbinder on 2010-03-04
I'm using nVidia 195 driver.

---

### Post by Easy Lyle on 2010-03-04
Does it to me also.  But I have noticed that if I click the button with my mouse, I log right in.  If I just hit the enter key, then I'm doomed to drop back to the login screen the second time.

---

### Post by philinux on 2010-03-04
> **Uncle Spellbinder said:**
> Still have the problem here as well. No intention of removing Plymouth. As you say, "removing it doesn't help the developers trying to debug."

To be honest uninstalling at this stage wont make much difference to testing. All you have to do is keep an eye on the updates. When a new plymouth version comes out, then test it.

I've got it installed but with the nouveau driver so it's working fine.

---

### Post by Uncle Spellbinder on 2010-03-04
New Plymouth released in updates. No change here on nVidia driver.

---

### Post by philinux on 2010-03-04
> **Uncle Spellbinder said:**
> New Plymouth released in updates. No change here on nVidia driver.

I dont think there will be much change for nvidia-current until this bug gets fixed.

[https://bugs.launchpad.net/ubuntu/lucid/+source/plymouth/+bug/526892](https://bugs.launchpad.net/ubuntu/lucid/+source/plymouth/+bug/526892)

---

### Post by haydoni on 2010-03-04
I don't have to log in twice anymore (nvidia 8200 - with nouveau) after the last set of updates.

The log-in page really doesn't match (design-wise) now...

---

### Post by philinux on 2010-03-04
> **haydoni said:**
> I don't have to log in twice anymore (nvidia 8200 - with nouveau) after the last set of updates.

The log-in page really doesn't match (design-wise) now...

Yes ouch it's horrid. Lets hope gdm gets some love.

---

### Post by exavoid on 2010-03-04
When I press the number 2 of my netbook it also restarts the gdm ;).

Regards

---

### Post by sgage on 2010-03-04
I'm running Alpha 3, all updates, nouveau drivers with an 8500gt.

Post grub, I get a black screen for a few seconds, then a flash of the ubuntu screen (perhaps a second), then the little activity orb, then a black screen again. There it stays until I hit enter, and then the log-in screen comes. But then I only have to log in once ;)

When I log out, I see the ubuntu screen for several seconds, with little traversing balls under the "ubuntu".

Seems like I see something different every time!

---

### Post by recluce on 2010-03-04
> **gibbylinks said:**
> Hi yes removing Plymouth solves it, but removing it doesn't help the developers trying to debug. 

I still have this problem with all the latest updates installed.

The bug is reported on launchpad. As soon as they release a new version of plymouth (or a relevant change like new gdm, kernel etc) I reinstall and give it another test. Just to continue testing a version of plymouth that is already known and reported as broken seems pointless to me.

---

### Post by Kevbert on 2010-03-04
recluce - you mean this [[COLOR="Red"]bug[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/515822")?

---

### Post by Owen.C93 on 2010-03-04
Actually I think you mean[ this bug]("https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/522692"). GDM restarts after enter is pressed.

---

