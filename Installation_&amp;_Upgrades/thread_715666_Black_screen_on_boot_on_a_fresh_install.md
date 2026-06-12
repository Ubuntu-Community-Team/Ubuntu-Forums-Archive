---
title: "Black screen on boot on a fresh install"
date: 2008-03-05
forum: Installation &amp; Upgrades
---

### Post by yezu on 2008-03-05
I just installed Ubuntu on a Toshiba Laptop.
The thing is that after grub starts to boot the system, only one line is shown on the screen and after that everything goes black.
After I press ctrl-alt-f6 everything returns to normal. The system continues to boot.
What is wrong? How can I make the laptop boot normally?
It has a ATI graphics card....

thanks...

---

### Post by HyRax on 2008-03-05
Are you sure that the system is "pausing" on the black screen? It may be a case that you cannot see the splash screen, but the system is still actually booting up in the background.

When you're in Ubuntu, I suggest you go to System->Administration->Synaptic Package Manager and install "StartupManager 1.0.9-0ubuntu1". This will add a "StartUp-Manager" option under System->Administration which you can use to specify the screen resolution used by the Ubuntu splash screen. By default Ubuntu sets it to be 1280x1024, which not every laptop can do. You might want to specify 640x480 or 800x600 instead (note that this specifies the screenmode for _just_ the splash screen, not the desktop itself).

I'm using Ubuntu on a Toshiba Satellite A210 with a native resolution of 1280x800, and it didn't show the splash screen at 1280x1024 after a fresh install of Gutsy. I've switched it to 800x600 and it works fine now while my desktop does a native 1280x800.

---

