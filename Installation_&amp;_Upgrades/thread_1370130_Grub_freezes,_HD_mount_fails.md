---
title: "Grub freezes, HD mount fails"
date: 2010-01-01
forum: Installation &amp; Upgrades
---

### Post by mistersleep on 2010-01-01
Hi.

I've got an old IBM Thinkpad 2611-452 (366mhz, 128Mb, 6Gb HD). Before this, it was running Win98, just fine.  Don't ask why I'm still using this old thing, it's a long story.

I installed the Alternative Installation of Ubuntu HH LTS, as many mondern Ubuntu Live CD will not work on this hardware.  The machine is a single boot system, so it should be a straight forward install... but it's not.  

After the install, which seemed to go smoothly, I re-booted the computer and grub comes up and freezes before it detects anything.  It just says, "Grub is loading, please wait..." and no errors are given.

I put the CD back in and ran the Repair Grub utility, and it runs without an issue, but it still wont boot.  Then I started the machine with my Knoppix live cd, and when that comes up I can't mount the HD to see what's going on in there.  In the GUI it gives me, "Error org.freedesktop.Hal.Device.volume.UnknownFailure. In the terminal, I'm just as unsuccessful.  Any ideas, anyone?  Thank you very much.

---

### Post by solar george on 2010-01-02
How about simply re-running the installation.

---

### Post by mistersleep on 2010-01-02
I ran the install 6 times all with the exact same results.  I even tried different file systems, fully automatic installs, manual installs, etc.  

Maybe Grub doesn't like something, is there a way to try an Ubuntu install with Lilo? Or to replace Grub with Lilo somehow?

Thanks though.  I'm open to any ideas.

---

### Post by mistersleep on 2010-01-03
Well during yet another try at installing Ubuntu an error occurred during an installation process and it asked me where I wanted to continue in the list of things to install. It listed many things including both 'install Grub' and 'install lilo'.  Not knowing if I could ever get to that menu again, I chose to install lilo, then followed some prompts.

Long story short, it works now.  I don't know why, or if I could ever get it right again.  Plus I'm not 100% sure everything that did install, actually installed properly.  Only time will tell.

---

### Post by solar george on 2010-01-03
Using the alternate installer you can get that option by choosing to do an "Expert Install" at the alternate disk boot screen (I can't remember how to do this to Hardy Heron).

---

