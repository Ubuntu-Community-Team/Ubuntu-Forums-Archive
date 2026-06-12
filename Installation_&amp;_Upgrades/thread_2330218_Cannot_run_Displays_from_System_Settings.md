---
title: "Cannot run Displays from System Settings"
date: 2016-07-09
forum: Installation &amp; Upgrades
---

### Post by UserJB on 2016-07-09
I installed Ubuntu 14.04 on an Intel i6700k with an Nvidia GTX 970 video card.  After the install I did 'apt-get update' and 'apt-get upgrade' and 'apt-get dist-upgrade'.  I can boot the machine and login, but when I click 'Displays' from the 'Systems Settings ' window, Ubuntu reports (occasionally) an internal error, and never creates the Displays window. 

I also can't seem t o get Keyboard shortcuts to work.

What should I do?

UPDATE: the Ubuntu error window said this: unity-control-center crashed with SIGABRT in g_assertion_message()

---

### Post by mörgæs on 2016-07-09
You have a Skylake processor and I wouldn't expect 14.04 to work well here. Have you considered a fresh install of 16.04?

---

### Post by grahammechanical on 2016-07-09
If you have a proprietary video driver then you should use the settings utility that was installed with the driver. The Displays utility works best with an open source video driver.

---

### Post by UserJB on 2016-07-09
I have installed 16.04 and it works.  But, I need to have 14.04 installed for other reasons.

---

### Post by ajgreeny on 2016-07-09
You may be able to manage with 14.04.5 point version when it arrives very soon (August 4th 2016?) which should have all the stability of 14.04, but the kernels and graphics system from 16.04 which is what you probably need for that new hardware.

Depending on what it is from 14.04 that you need, that point version may be an answer for you.

---

### Post by MAFoElffen on 2016-07-09
> **UserJB said:**
> I have installed 16.04 and it works.  But, I need to have 14.04 installed for other reasons.
Is the reasons you "hint at" for why you need 14.04 because an application you want to run is not available for 16.04 yet? What is that application?

I have desktops here with NVidia GTX 750ti, GTX 970, 2x GTX 980ti's in SLI... and saving for 2 Founder Editions.

---

### Post by UserJB on 2016-07-11
I don't know of a specific application yet.  However, Ubuntu 16 uses gcc 5.3, and I'm expecting that to cause problems as all the other developers are running Ubuntu 14, which has gvv version 4.x.

---

### Post by UserJB on 2016-07-12
BTW, you seem to think the problem is with the displays.  Maybe because I included that in the title of this thread.  However, ubuntu 14.04 boot fine, and it looks exactly like any other ubuntu after it boots.

I think the problem is with the GNOME settings window, and more specifically: unity-unity-control.  I can't get any setting to work.  Also, when I right-click on the desktop background, I get the usual menu, but there is no option to create a launcher.  So, I can't get a terminal window to type commands.

---

### Post by UserJB on 2016-07-12
BTW, you seem to think the problem is with the displays.  Maybe because I included that in the title of this thread.  However, ubuntu 14.04 boot fine, and it looks exactly like any other ubuntu after it boots.

I think the problem is with the GNOME settings window, and more specifically: unity-unity-control.  I can't get any setting to work.  Also, when I right-click on the desktop background, I get the usual menu, but there is no option to create a launcher.  So, I can't get a terminal window to type commands.

---

### Post by mörgæs on 2016-07-12
Then you could try installing one of the other buntus, say Xubuntu.

---

