---
title: "Bounces back to login screen"
date: 2008-10-26
forum: Installation &amp; Upgrades
---

### Post by Yoshis88 on 2008-10-26
I've got an old Compaq Presario SR1817CL desktop with 512 MB (soon to be 4GB) RAM and an Athlon 64 processor.  I am able to boot fully into Knoppix.

I burnt an AMD64 Desktop (live) CD, pop it in, let it select "Try ubuntu".  Much to my surprise, it comes to a login screen.  I don't know the password for 'ubuntu', but more importantly, I know that shouldn't happen.

I try to just go directly to the install on the CD.  I get through the wizard, but in the middle of copying, it fails complaining about a faulty CD or CD drive.  I don't know why this happens, but most alarming to me, it has happened many times before to me (on different computers with reburnt-CDs!).  So, I do my usual thing of preparing a USB install using Unetbootin.

That installation goes cleanly and quickly, with Grub written to the MBR.  I reboot the system, only to find that once I am prompted with the (now appropriate) login screen.  I type in my credentials, flashes a bit making you think it's working, then bounces back to the login screen.  I don't even know where to start.  I'm starting to think my hands kill computers.  Any insight is very appreciated!

---

### Post by taseedorf on 2008-10-26
I would try reconfiguing xorg

When you are in the login window press CTRL-ALT-F3 and then log in and type 

sudo dpkg-reconfigure xserver-xorg 

Then

Press CTRL-ALT-F7 to go back to the Graphic User Interface

note

you MIGHT have to choose vesa drivers if for some reason  it doesn't work.

---

### Post by Yoshis88 on 2008-10-28
Thank you for your response!

What I did to get it in was select the "Failsafe GNOME" session.  It got in just fine.  After that, I set just plain "GNOME" as my default session, and it has no problem automatically signing in (after I set it to do so).

It should be noted, the Usplash screen (with the loading bar before and after the OS loads and unloads) does not show properly.  The monitor complains about the resolution being out of range.  I can change it down to 800x600, but it doesn't make much difference.  Since the splash screen at the beginning is not that much of my concern, I'm pretty happy.

---

