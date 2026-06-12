---
title: "New install hangs at 96%."
date: 2005-04-12
forum: Installation &amp; Upgrades
---

### Post by nuke on 2005-04-12
Hi!

I am installing HH 5.04.  The installer gets all the way to 96%, then asks me to remove the CD, which I do, then it hangs.  I also get the message that the installer will reboot to complete the install.

I am installing on a brand new Compaq nc6120 laptop.

GRUB has been installed OK, Windows XP is still OK.  I can boot into the command prompt.

Could someone suggest some things that I can do to fix or complete the install?

Thanks
Nuke

---

### Post by sethmahoney on 2005-04-12
[QUOTE=nuke]Hi!

I am installing HH 5.04.  The installer gets all the way to 96%, then asks me to remove the CD, which I do, then it hangs.  I also get the message that the installer will reboot to complete the install.

I am installing on a brand new Compaq nc6120 laptop.

GRUB has been installed OK, Windows XP is still OK.  I can boot into the command prompt.

Could someone suggest some things that I can do to fix or complete the install?

Thanks
Nuke[/QUOTE]
 I'm guessing that when you manually reboot GRUB doesn't come up, and it doesn't try to boot into linux?

---

### Post by vnbuddy2002 on 2005-04-12
As I know, once you reach that point, the installation is completed.

---

### Post by Ptero-4 on 2005-04-12
[QUOTE=nuke]Hi!

I am installing HH 5.04.  The installer gets all the way to 96%, then asks me to remove the CD, which I do, then it hangs.  I also get the message that the installer will reboot to complete the install.

I am installing on a brand new Compaq nc6120 laptop.

GRUB has been installed OK, Windows XP is still OK.  I can boot into the command prompt.

Could someone suggest some things that I can do to fix or complete the install?

Thanks
Nuke[/QUOTE]
 How recent is your laptop. I have heard that the latest DELLs, Compaqs and HPs come with a hardware-based DRM system which will prevent installation of non-Microsoft OS's and/or software (read Linux). If your PC is very recent then chances are that your problems installing Ubuntu are caused by that DRM mechanism.

If that is the cause of your installation problems then the only solution is to replace the PC either with an older (pre-2002) PC or with a Mac (recommended).

P.D: I tell you this because I have had nasty experineces with lots of those new "Windows-only" PC's.

Thanks , and hope this helps.

---

### Post by nuke on 2005-04-13
Thank you everyone for your suggestions.

Just to follow-up to some of these suggestions ...

I didn't realize that there are some Windows only laptops, but I did ask specifically if there was any issue running Linux on the various laptops that I looked at.  We have an office rule that any new equipment must be able to run Linux.  I would be mighty ticked off if I find out that this laptop won't run anything other than Windows.

GRUB is OK and I can get to Ubuntu that is installed on a separate partition.  X doesn't start.  All I get is the command prompt.  I have used apt-get update and apparantly I have everything current.  But as I mentioned, X won't start at boot.  The command startx doesn't work either.

I have read that after you do the base install, the system is to eject the installer cd and reboot to allow the final portions of the install and check for any updates.  I can't get to this.  Since the installer hangs at 96%, it never gets to the reboot command.  I have to force the shutdown.

Is there a script that I can launch that does this final check for updates, final configuration issues etc..

If at 96% complete, I am finished the install, why doesn't Ubuntu reboot into x?

Thanks again
Nuke

---

### Post by almarag on 2005-04-13
If the X doesn't start, is probably because it not finished the configuration script. You can configure by hand with the xconfigurator utility bundled with xfree (in case you are using a Warty, in Hoary I ignore if this work, since it uses x.org, but maybe will or you can search if the install creates the xorg.conf file, and edit by hand)

If the install was correct, this can save you fron reinstall again.

almarag.

---

### Post by nuke on 2005-04-24
thanks for the suggestions, Almarag.

I finally had a chance to look at the install and from what I can see, it doesn't have a /X11 folder in /etc/.  The live-cd works though.  That is how I was able to determine that the X11 folder and its content is missing.

I have tried to install Ubuntu Hoary a number of times and each time it stops at 96%.  I suspect that you are correct that the X11 configurator doesn't finish.

Could someone suggest what to try next?

I would be curious if I can somehow install the Live-CD files to the existing partition on the laptop since the Live-CD works OK.

Thanks again
Nuke

---

### Post by gingermark on 2005-04-24
[QUOTE=nuke]Could someone suggest what to try next?[/QUOTE]

Maybe not something to try **next**, but you could always try installing 4.10 and then upgrading to 5.04... Not ideal, I know, but an option that may be worth considering if all else fails.

Good luck.

---

