---
title: "Lost Unity and titlebar on windows after upgrading from 14.04 LTS to 16.04 LTS"
date: 2016-05-13
forum: Installation &amp; Upgrades
---

### Post by Jonathan_Goodwin on 2016-05-13
Yesterday, I upgraded from 14.04 LTS to 16.04 LTS in hopes of better OpenGL support for my Haswell based laptop (oops).

Ubuntu boots. The background screen with icons on top right appear. I can successfully login as myself or guest. Once logged in, the screen blinks, and clears to the Ubuntu background screen, and nothing else appears (no launchpad, no top icons, etc.). I can do Ctl-Alt-F1 to use the console. I can also right click and open up a console window. All windows that I open (e.g., the console window and Gedit) have no title bar (and therefore no close,minimize, maximize buttons).

After hours of research and experimentation, none of the various proposed apt-get options fixed anything: -f install, update, dist-upgrade, install --reinstall ubuntu-desktop unity.

Also unhelpful was: dconf reset -f /org/compiz/

One command that does make the title bars appear (until re-loading Unity or re-booting) was: "rm -rf ~/.config". However, it does not re-engage Unity.

Experiments running various programs yielded error messages that might be related to this problem. For example, running "update-manager" from the console window spit out three PyGIWarnings related to Gtk, Dbusmenu and Unity, which look like this:

[INDENT]PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.[/INDENT]

Similarly, running another program generates an import error related to Python GI trying to load the _gtk shared object and failing to find Undefined symbol FT_Reference_Face.

It makes me wonder if multiple versions of Python, Python Gobject Introspection and/or Gtk, some from 14.04 or earlier and a different set for 16.04, are confusing each other. Perhaps such shared object loading problems could also cause Unity to fail to launch properly, since it too depends on Gtk. I know too little about how they play together to risk un-installing packages willy-nilly.

I would appreciate any suggestions. Thank you

---

### Post by ubfan1 on 2016-05-13
Did you try the guest session login -- it might work, indicating a further problem with your "dot" files.  What video hardware do you have and what driver for them is in use (lshw -C video).  Any errors in the /var/log/Xorg.0.log (or older ones)?

---

### Post by Jonathan_Goodwin on 2016-05-13
Thank you, ubfan1, for your prompt reply. Here are answers to your questions:

1. Yes. The problem also occurs in the guest session.

2. The output for: lshw -C video
> 
  *-display
       description: 3D controller
       product: GM107M [GeForce GTX 850M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:29 memory:f6000000-f6ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f7000000-f707ffff
  *-display
       description: VGA compatible controller
       product: 4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:30 memory:f7400000-f77fffff memory:d0000000-dfffffff ioport:f000(size=64)


3. I took a long look at /var/log/Xorg.0.log. Mostly everything looks in order. 

In the 5.99x section, it attempts to load 8 video drivers: intel, nvidia, nouveau, intel, modesetting, fbdev and vesa. The nvidia driver is not found, and therefore does not load.

In the 6.000 section, Nouveau interface version 1.3.1 says: "unknown chipset NV117. Falling back to old probe method for modesetting, fbdev, vesa". As it runs the fbdev probe (fbdevhw) it points to "Integrated Graphics Chipset Intel(R) HD Graphics 4600".


One more thing: another set of message complaining about gobject's, this time from running "nautilus" from the terminal session (however it does work): 

> 
(nautilus:2188): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed
(nautilus:2188): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed
(nautilus:2188): Gtk-CRITICAL **: gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed
(nautilus:2188): GLib-GObject-WARNING **: invalid (NULL) pointer instance
(nautilus:2188): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed


I hope this is helpful diagnostic information. If you need more, please let me know.  Again, thank you!

---

### Post by ubfan1 on 2016-05-14
Looks like both Nvidia and Intel graphics, a hybrid system, of which I know nothing.  Maybe search for bumblebee will help.

---

### Post by Jonathan_Goodwin on 2016-05-14
Thank you for giving it a shot. Already you have helped me learn a lot more. I will look into Bumblebee. All the best to you!

---

### Post by g1g133 on 2016-05-29
I've just had the same issue (although I upgraded from 15.10) and resetting Unity fixed it.

unity --reset

---

### Post by B._Bishop on 2016-06-02
I've just had the same issue, but I can log in as guest and have use of my system but no sudo possibilities.

I can open a terminal, but as my knowledge is level n00b I can not do a lot. From the terminal I can open firefox and come here :)

I tried updates under guest because he kept telling me about updates but of course didnt work, when I did unity --reset just now i got the error to run untiy without option, it simply makes the screen sort of flicker once and thats it. It did however let the update screen pop up, funny enough it did work but without me asking to confirm my password.

Did not resolve my problem though. And honestly that's how far my knowledge goes, as far as you guys give suggestions :)

All I can say is, I have upgraded to 16.04 from 15.10, because this is a difficult system to install (Acer Switch) and I still had some issues which I hoped would be resolved by upgrading. It worked for a few days. Now I was on youtube following an instruction video how to change the screen on an iphone, I got as far as disassembling the thing, then my laptop froze. I had a disassembled iphone and no guidance to reassemble it.

Don't know why I'm telling you this, but I felt like sharing.

I hope anyone has any suggestions or finds out what is going on. To the Ubuntu problem that is, I got the phone back together, only had one screw left at the end but it works lol

---

