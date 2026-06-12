---
title: "Just upgraded to Ubuntu 10.04 - now can't log in"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by Captainmetal on 2010-05-01
I've just upgraded my laptop to 10.04.  All seems to have gone well enough except that I've now got to the Log in Screen - When I enter the password I had before nothing happens  (screen goes blank and then returns to the log in screen.  I've tried no password and other combinations of passwords and they come back as authentication failed.  Should I just do a clean install?

---

### Post by tommcd on 2010-05-01
> **Captainmetal said:**
>  Should I just do a clean install?
Well, normally I would not suggest this, since it is not what most people want to hear. However, since you asked, I would say: Just cut your losses and reinstall.
This will likely be the easiest way to get up and running again. 
I always do clean installs; and I never have problems.
Many people seem to needlessly fear doing a reinstall. 

And welcome to the Ubuntu forums! I wish I had a better answer to your question.

---

### Post by JohnVLang on 2010-05-21
Hi,

I've got the same situation... only it's with my mother's laptop - she's in the UK, i'm in Australia btw... makes remote support for her a bit tricky if she can't even log in!?!?!? Had set her up with 8.04 when she had visited Australia a while back... then talked her through the online upgrade to 10.04 being the next LTS release, all seemed well - but after the restart she couldn't log in??? Couldn't get a prompt with ctrl+alt+F1 either... Finally after some hours decided to start from scratch, so burn a Live CD and sent it to her in the post for a re-install... talked her through that - same thing, goes to log on and "authentication failed"!!! Double/tripple check user name/password etc.... Any ideas, anyone?

Chrs, John

---

### Post by stuarthall on 2010-06-02
I also have this problem, but on a desktop rather than a laptop ... there's at least one other person with it (see [http://serverfault.com/questions/144357/ubuntu-10-04-unable-to-login-after-fresh-install](http://serverfault.com/questions/144357/ubuntu-10-04-unable-to-login-after-fresh-install)) and the suggestion there is that it may have something to do with old video graphics, which could apply to me.

[LEFT]
[/LEFT]
I can login using safe mode gnome (and xterm) and that is what I am using now. So, what is different between safe mode gnome and normal gnome that might cause this problem?

This is my lspci output;

00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)

As I understand it, the openchrome driver is used for VIA Unichrome video controllers and there is a suggestion at [http://www.openchrome.org/trac/wiki/SupportedHardware](http://www.openchrome.org/trac/wiki/SupportedHardware) that there may be a problem with the km400/km400A version of this.  But, if true, what can be done about it?

Of course, this problem may have nothing to do with video. Is there anything else that might be relevant?

---

### Post by stuarthall on 2010-06-03
> **stuarthall said:**
> I also have this problem, but on a desktop rather than a laptop ... there's at least one other person with it (see [http://serverfault.com/questions/144357/ubuntu-10-04-unable-to-login-after-fresh-install](http://serverfault.com/questions/144357/ubuntu-10-04-unable-to-login-after-fresh-install)) and the suggestion there is that it may have something to do with old video graphics, which could apply to me.

[LEFT]
[/LEFT]
I can login using safe mode gnome (and xterm) and that is what I am using now. So, what is different between safe mode gnome and normal gnome that might cause this problem?

This is my lspci output;

00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)

As I understand it, the openchrome driver is used for VIA Unichrome video controllers and there is a suggestion at [http://www.openchrome.org/trac/wiki/SupportedHardware](http://www.openchrome.org/trac/wiki/SupportedHardware) that there may be a problem with the km400/km400A version of this.  But, if true, what can be done about it?

Of course, this problem may have nothing to do with video. Is there anything else that might be relevant?

Now I can't use the keyboard when I login to safe mode gnome, but I still can in xterm.  So, a gnome problem? The sequence is; when I hit return to login the login prompts disappear followed by a few seconds of purple screen, then the screen blanks and the purple comes back complete with startup jingle and login prompts ... ? Beats me at the moment.

---

### Post by stuarthall on 2010-06-03
OK, the keyboard was a red herring ... I'd managed to set slow keys somehow; annoying.

But, this is the syslog from two attempts to do a normal login;

[I]Jun  4 13:15:16 saltcreek acpid: client 2027[0:0] has disconnected
Jun  4 13:15:16 saltcreek acpid: client connected from 2262[0:0]
Jun  4 13:15:16 saltcreek acpid: 1 client rule loaded
Jun  4 13:15:16 saltcreek kernel: [ 1370.145968] agpgart-via 0000:00:00.0: AGP 3.5 bridge
Jun  4 13:15:16 saltcreek kernel: [ 1370.145998] agpgart-via 0000:00:00.0: bridge is in legacy mode, falling back to 2.x
Jun  4 13:15:16 saltcreek kernel: [ 1370.146006] agpgart-via 0000:00:00.0: putting AGP V2 device into 4x mode
Jun  4 13:15:16 saltcreek kernel: [ 1370.146063] pci 0000:01:00.0: putting AGP V2 device into 4x mode
Jun  4 13:15:17 saltcreek rtkit-daemon[1152]: Sucessfully made thread 2303 of process 2303 (n/a) owned by '114' high priority at nice level -11.
Jun  4 13:15:17 saltcreek rtkit-daemon[1152]: Supervising 4 threads of 2 processes of 2 users.
Jun  4 13:15:17 saltcreek rtkit-daemon[1152]: Sucessfully made thread 2304 of process 2303 (n/a) owned by '114' RT at priority 5.
Jun  4 13:15:17 saltcreek rtkit-daemon[1152]: Supervising 5 threads of 2 processes of 2 users.
Jun  4 13:15:17 saltcreek rtkit-daemon[1152]: Sucessfully made thread 2305 of process 2303 (n/a) owned by '114' RT at priority 5.
Jun  4 13:15:17 saltcreek rtkit-daemon[1152]: Supervising 6 threads of 2 processes of 2 users.
Jun  4 13:15:18 saltcreek gdm-simple-greeter[2297]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.0/gtk/gtkwidget.c:5636: widget not within a GtkWindow
Jun  4 13:15:21 saltcreek gdm-session-worker[2299]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Jun  4 13:15:33 saltcreek kernel: [ 1387.650633] Xorg[2262]: segfault at 0 ip 080a6712 sp bfcc08ac error 4 in Xorg[8048000+19f000]
Jun  4 13:15:34 saltcreek acpid: client 2262[0:0] has disconnected
Jun  4 13:15:34 saltcreek acpid: client connected from 2495[0:0]
Jun  4 13:15:34 saltcreek acpid: 1 client rule loaded
Jun  4 13:15:34 saltcreek kernel: [ 1388.249939] agpgart-via 0000:00:00.0: AGP 3.5 bridge
Jun  4 13:15:34 saltcreek kernel: [ 1388.249969] agpgart-via 0000:00:00.0: bridge is in legacy mode, falling back to 2.x
Jun  4 13:15:34 saltcreek kernel: [ 1388.249977] agpgart-via 0000:00:00.0: putting AGP V2 device into 4x mode
Jun  4 13:15:34 saltcreek kernel: [ 1388.250033] pci 0000:01:00.0: putting AGP V2 device into 4x mode
Jun  4 13:15:36 saltcreek gdm-simple-greeter[2530]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.0/gtk/gtkwidget.c:5636: widget not within a GtkWindow
Jun  4 13:15:39 saltcreek gdm-session-worker[2532]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Jun  4 13:15:49 saltcreek kernel: [ 1403.715360] Xorg[2495]: segfault at 0 ip 080a6712 sp bf99bd2c error 4 in Xorg[8048000+19f000]
Jun  4 13:15:50 saltcreek acpid: client 2495[0:0] has disconnected
Jun  4 13:15:50 saltcreek acpid: client connected from 2722[0:0]
Jun  4 13:15:50 saltcreek acpid: 1 client rule loaded
Jun  4 13:15:50 saltcreek kernel: [ 1404.320178] agpgart-via 0000:00:00.0: AGP 3.5 bridge
Jun  4 13:15:50 saltcreek kernel: [ 1404.320207] agpgart-via 0000:00:00.0: bridge is in legacy mode, falling back to 2.x
Jun  4 13:15:50 saltcreek kernel: [ 1404.320216] agpgart-via 0000:00:00.0: putting AGP V2 device into 4x mode
Jun  4 13:15:50 saltcreek kernel: [ 1404.320273] pci 0000:01:00.0: putting AGP V2 device into 4x mode
Jun  4 13:15:52 saltcreek gdm-simple-greeter[2757]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.0/gtk/gtkwidget.c:5636: widget not within a GtkWindow
Jun  4 13:15:55 saltcreek gdm-session-worker[2759]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed[/I] 


The three lines reporting Gtk-WARNING, GLib-GObject-CRITICAL and  segfault look like a genuine bug to me so I am going to report that on  the official site.

---

### Post by josef613 on 2010-06-10
I have this problem when i boot on a USB start up disk. I put an account on there for myself (So I could save files) and I try to log in, but every password I use gets me "Authentication Failure" . I Used every password I use. 
I also tried to just go in as a live session user, so I clicked other, and typed ubuntu for the username and left the password feild blank and got the same result. "Authentication Failure"
It was working a week ago....
What Should I Do?

---

### Post by stuarthall on 2010-06-26
I reported this and it became Bug #589520 at [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/589520](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/589520).

As a result it was suggested that I disable AIGLX in /etc/X11/xorg.conf.  In my case (by default in 10.04 I believe) there was no existing xorg.conf, so I created one with the following content;

Section "ServerFlags"
    Option "AIGLX" "off"
EndSection

This worked for me and, after reboot, got me logged in without further problem.

Cheers,

Stuart

---

### Post by stuarthall on 2010-06-26
> **josef613 said:**
> I have this problem when i boot on a USB start up disk. I put an account on there for myself (So I could save files) and I try to log in, but every password I use gets me "Authentication Failure" . I Used every password I use. 
I also tried to just go in as a live session user, so I clicked other, and typed ubuntu for the username and left the password feild blank and got the same result. "Authentication Failure"
It was working a week ago....
What Should I Do?

This is a different problem I think.  I was always able to login using safe mode gnome or xterm and I would only get "Authentication failure" if I actually used the wrong password (including when I tried a normal gnome login). Apart from that I'm afraid I don't have any suggestions.

---

### Post by stevek123 on 2010-07-26
Mr Hall
I've been having the same - repeating login issue - and I also have the same hardware. VIA mobo with the S3 vid chip. I have posted in Beginners Forum and not had any useful replies. I found your thread during another google search. 

My login issue happens after adding the updates for 9.10/fresh install and at any time from a good 10.04 CD (user session OR full install). I'd love to try and get the new LTS functional! May I ask how/when you were able to edit the xserver.conf file??? I assume you ran a fresh install and then did your .conf edit. Is this done from the xterm at login? with what command?

---

### Post by Mwanitete on 2010-08-26
Hii I have the Same plobem , wheb I upgraded from 9.10 to 10.4 i can't Login , authentication Failed, I tried to edit , 

Vi /etc/pam.d/gdm.conf @include common-pam_keyring 

But still I got the the erros authentication Failed 

where should I put "@include common-pam_keyring in pam..??

Need Help. where is ubuntu office..??? i am tired

---

### Post by Mwanitete on 2010-08-27
Hii I have the Same plobem , wheb I upgraded from 9.10 to 10.4 i can't Login , authentication Failed, I tried to edit , 

Vi /etc/pam.d/gdm.conf @include common-pam_keyring 

But still I got the the erros authentication Failed 

where should I put "@include common-pam_keyring in pam..??

Need Help. where is ubuntu office..??? i am tired

---

### Post by Mwanitete on 2010-08-27
Hii brother

I need help ::)

I had Linux ubuntu 9.10 but when I upgraded to linux ubuntu 10.4 I cant login 

it says authentication failed..

what should i do to login normal..?


Have a nice time ::)

---

### Post by cornelis spronk on 2010-08-28
I have the same problem.  I do not understand the workarounds suggested.  I am back to using 9.04, as it is the most trouble free version for me at present.  I am waiting for a solution, and will upgrade then.

---

### Post by AgentWD-40 on 2010-08-29
> **stuarthall said:**
> I reported this and it became Bug #589520 at [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/589520](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/589520).

As a result it was suggested that I disable AIGLX in /etc/X11/xorg.conf.  In my case (by default in 10.04 I believe) there was no existing xorg.conf, so I created one with the following content;

Section "ServerFlags"
    Option "AIGLX" "off"
EndSection

This worked for me and, after reboot, got me logged in without further problem.

Cheers,

Stuart

This worked for the system I'm working on with this problem. Thank you very much! For those of you who don't fully understand I'll list out a few steps:

1. Hold the Shift key during boot until you see the grub menu.
2. Select the option closest to the top that says "(recovery mode)" at the end of the line.
3. Eventually you'll get a text mode recovery menu. Select the netroot option. You'll now see a prompt that says something like root@computer:~#.
4. At the prompt type "nano /etc/X11/xorg.conf" without the double quotes of course.
5. You'll now be in a simple text editor. Type the following exactly as you see below:

Section "ServerFlags"
    Option "AIGLX" "off"
EndSection

6. On your keyboard, press Ctrl+o.
7. Push enter when the filename is displayed.
8. Push Ctrl+x to exit the editor
9. Now you should be back at the shell prompt. Type "reboot now" (without the quotes) and let your system start up again.
10. See if you can sign in normally.

If this didn't seem to work you can undo the changes by following steps 1-3 above and then typing "rm /etc/X11/xorg.conf" (without the quotes) at the shell prompt. Then follow step 9 to reboot your system.

Hopefully this helps! :D

---

### Post by save2 on 2011-08-16
I found that in my case it wasn't authentication problem.
also someone suggested some "AIGLX" on xorg.conf which did nothing.

what solved my logins was:
reboot to root console
goto the relevant user home dir
see if there is .xsession-errors file. 
open it and see if you can fix the errors there.

---

