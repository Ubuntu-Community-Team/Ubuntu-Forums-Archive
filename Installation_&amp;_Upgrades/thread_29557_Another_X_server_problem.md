---
title: "Another X server problem"
date: 2005-04-24
forum: Installation &amp; Upgrades
---

### Post by ronepowell on 2005-04-24
I am trying (for the third time ) to install Ubuntu. Every distro I have used has always at least got me into the X window.  However, at the end of the install I get the notice: "I cannot start the X server .....  Would you llike to view the X server output to diagnose the problem?"  This is what is told me "
X Window System Versioin 6.8.2, release date: 9 Feb 2005. . . . Current operating system: Linux 2.6.10-5-386 #1`Tue Apr 5 12:12:40 UTC 2005 i686.
Module Loader present.  OS Kernel: Linux version 2.6.10-5-386 (buildd@terranova) (gcc version 3.35 (Debian 1:3.3.5-8ubuntu2). . .  Markers: (--) prbed, (**) frm config file, (==) default setting, (++) from command line, (!!) notice, (II) informational.
Okay this means nothing to me.  Can someone help??  I thought this was supposed to be a user friendly distro.

---

### Post by nad on 2005-04-24
This is just the header of the log file, /var/log/Xorg.0.log. At this point in the fail, if you use the down arrow key, you should see the rest of the file. It may show a completed attempt with noted errors or it may be an incomplete log and where it stops is a clue as to what went wrong. If this is the whole file... Have you tried the live cd to see if it works.

Please post your detailed system configuration.

---

### Post by ronepowell on 2005-04-24
Oh my, there is much more.  Here goes:
"/usr/X11R6/lib/modules/extensions/libGlcore.a:m_debus_clip.o":No symbols found.  Skipping.
"/usr/X11R6/lib/mosules/extensions/libGLcore.a:m_debug_norm.o" : No symbons found.  Skipping
"/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o": No symbols found
(EE) No devices detected
Fatal server error: no screens found.

Please also check the log file at "/var/log/Xorg/0.log" for additional information.  (How to I do that since I can't get any further)?

I did not use/ do not have the live CD.  Forgive me for obvious stupidity (well, more like ignorance), but where do I locate detailed system config??

Also, I am really impressed by the speed of your reply.  Whether or not we are successful, thanks a lot.

---

### Post by nad on 2005-04-24
There is nothing to forgive. We were all beginners at one time.

You should be left at a command prompt. No graphical user interface. If you feel like attempting this I can lead you through some early diagnoses. You apparently have a way to transmit this info so here goes:

One command to view the complete log file is: less /var/log/Xorg/0.log

This will give you one screenful at a time with the ability to scroll and page up and down.

Posting the complete log file here (in a code box, <code>...</code>) will be helpful as well as the log of your current session, /var/log/messages

The command:  dmesg | less   will show you this log file as above.

The output of the command: lspci  will suffice for now to let us know your system configuration.

---

### Post by ronepowell on 2005-04-24
The output for lspci is:<000:00:00.0 Host bridge: VIA Technologies, Inc. VT8605 (ProSavage PM133) (rev 8)>
<000:00:01.0 PCI bridge: Via Technologies, Inc. VT8605 (PM133 AGP)>
<000:00:04.0 ISA bridge: VIA Technologies, Inc. VT82C686 (Apollo Super South) (rv 22)>
<000:00:04.1 IDE interface:VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT82x/A/C PIPC bus Master IDE (rev 10)>
<000:00:04.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)>
<000:00:04.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 10)>
<000:00:04.4 Host bridge: VIA technologies, Inc. VT82C686 (Apollo Super ACPI) (rev 30)>
<000:00:0d.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)>
<000:00:0d.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)>
<000.00:0e.0 Ethernet controller: VIA Technologies, Inc. VT86C100A (Rhine) (rev 6)>
<000:00:0f.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 08)>
<000:00:0f.1 Input device controller: Creative Labs SB Live! MIDI/Game Port (rev 08)>
<000:01:00.0 VGA compatible controller: Matrox Graphics, Inc. MGS G400 AGP (rev 04)>

The output for the dmesg | less was huge, so I will not try to post all of it.  Maybe we can narrow some of the output down to a meaningful (to you --- I will remain in a state of paralysis).

---

### Post by nad on 2005-04-24
The posted file notes that you are using a matrox video card which may not be supported yet. I found reference to a MGA G400, but not yours. This in itself shouldn't cause X to not start. X should default to a generic driver, however, there have been many issues with the xorg X server and ubuntu lately.

To post a large file, use a code box. Put the tag: <code> before the file and the </code> tag at the end. This will show up as a scrollable box in your post. The output of the xorg log file is important. The system message log has necessary diagnostic information in it also. If you are hand copying these files, please advise. There are other methods. Your system appears to be up and running. You just do not have a gui.

---

### Post by ronepowell on 2005-04-25
Thanks so much for your patience and help so far.  However, I think I will go back to MEPIS for now --- which works right from the get-go --- and wait until Ubuntu reaches a stage of maturity that avoids all this labor to get it working.

---

### Post by nad on 2005-04-25
Your welcome. I agree.

Personally I use my own home rolled version of debian for every day use and anything important. I'm hoping that ubuntu can get it together because they have the best of many worlds, but, I am afraid that they are biting off more than they can chew with a 6 month release schedule and pushing the limits. Quality is suffering.

---

