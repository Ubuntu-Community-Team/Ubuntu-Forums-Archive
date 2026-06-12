---
title: "image of closed program shows on desktop sort of ghost image"
date: 2020-10-09
forum: Installation &amp; Upgrades
---

### Post by keep-tryin on 2020-10-09
Just installed Ubuntu 20.04 LTS on an older computer for my niece
When you close a program, (thunderbird, Files,Firefox, Libre Office) it disappears then the last image from the closed program will partially redraw on the desktop when you move the mouse sort of a ghost image of the last item. If you click on the desk top it disappears but can redraw several times before the image quits showing up in the background like wall paper. This is what the machine has for graphics
display
             description: VGA compatible controller
             product: 82G33/G31 Express Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: msi pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:fdf00000-fdf7ffff ioport:f400(size=8) memory:d0000000-dfffffff memory:fd800000-fd8fffff memory:c0000-dffff
Any ideas on what could be causing this and how I can fix it?

---

### Post by CatKiller on 2020-10-10
> **keep-tryin said:**
> Any ideas on what could be causing this and how I can fix it?

What's causing it is that the framebuffer - the region of memory used for storing the image for that part of the display - isn't being cleared when you exit the application. I couldn't tell you whether it's a bug in the driver, a bug in the window manager, or a bug in the application framework, though.

Trying a different desktop environment or a different version of Mesa (there are various PPAs with newer versions) might help you to narrow it down so you can send a bug report.

---

### Post by keep-tryin on 2020-10-10
I don't understand much about graphic drivers, but I did find some things that suggested turning off hardware acceleration in browsers is this something that might solve the problem and if so is there away to turn if off for everything?

---

### Post by keep-tryin on 2020-10-22
installed xubutu-desktop solved the problem and is working fine. How would I file a bug report? This solution solved it for me but a bug report might help someone else.
                 Thanks 
                  Linda

---

### Post by uRock on 2020-10-22
Hello Linda,

You can find directions on how to report bugs here. [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

Xubuntu is my favorite. The only downside is having to upgrade every three years, instead of five.

---

### Post by CatKiller on 2020-10-22
> **keep-tryin said:**
> installed xubutu-desktop solved the problem and is working fine. How would I file a bug report? This solution solved it for me but a bug report might help someone else.
                 Thanks 
                  Linda

Glad to hear it's working for you now. Of the three things that I thought of as likely culprits that might cause that symptom, you're still using the same driver and the same application framework (Gnome and Xfce both use GTK), so the window manager seems like a likely cause. Gnome's window manager is, I think, [Mutter](https://launchpad.net/mutter).

---

