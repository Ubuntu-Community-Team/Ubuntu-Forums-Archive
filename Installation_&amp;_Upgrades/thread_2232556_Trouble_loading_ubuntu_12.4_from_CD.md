---
title: "Trouble loading ubuntu 12.4 from CD"
date: 2014-07-02
forum: Installation &amp; Upgrades
---

### Post by Frank_Callo on 2014-07-02
Hi all

I am trying to load ubuntu 12.4 onto my old dell desk top (optiplex 520).

I put the disk in which tells me I can run it as a demo with an instalation option once the demo is running.  So I get the thing running, looks good.  I try to use the installation application which installs all the files and then tells me to restart the computer.  This is where the trouble starts.

I boot up, choose ubuntu and hit enter.  I get the ubuntu screen with the five dots beneath the ubuntu logo.  The dots scan orange and white for a good while and then I get the following message.

BusyBox v.1.18.5 (ubuntu 1:1.18.5-1ubuntu4)built-in shell
(initramfs) unable to find a medium containing a live file system).

If you guys can help I'd thank you.  I could use the old windows XP operating system but it doesn't let me download a lot of the free ware.  Beside, I fear that this OS will become unstable.  Want to get away from microsoft anyway.

Tannks
Frank

---

### Post by ubfan1 on 2014-07-02
Do you have more than one disk in the desktop?   Take a look at the grub boot commands -- type "e" on the grub menu screen, and look at the disk references.  There are several types, but a single disk machine will probably look like (hd0,..., or /dev/sda...., or UUID=.   The UUID references should be OK.  If you see things like (hd1 (instead of hd0), edit the number back to 0.  If you see things like sdb, edit the b to a.  and try to boot (F10 or Crtl X).  If you succeed, immediately fix things up by running
sudo update-grub

---

### Post by Frank_Callo on 2014-07-02
How do I get to this "grub boot commands"?  Is this something that I would already have to have ubuntu running to access?  Sorry, I am really ignorant about a lot of this behind the scenes stuff

I have two hard drives in this machine.

---

### Post by ibjsb4 on 2014-07-02
A couple of observations ..

I think that ubuntu is too resource demaning for your box.  I would suggest [Lubuntu.]("http://lubuntu.net/")

Second, I think that you need to use nomodeset.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

I could be all wrong about this, but this is the path I would pursue.

Want to discuss this this? Post back.

---

### Post by yancek on 2014-07-03
> How do I get to this "grub boot commands"?  Is this something that I would already have to have ubuntu running to access?

If you are referring to the suggestion to edit the boot line suggested by ubfan1, when you see the Grub boot menu, if Ubuntu is highlighted just hit the e key on your keyboard.  It's possible that you just need to add nomodeset to the end of the line which begins with linux.  After you hit the e key, you should see your Ubuntu menuentry.  Use the keyboard arrow keys to move down to the line which begins with linux, then right arrow to the end, leave a space at the end of the line and type:  nomodeset and select the key indicated to continue booting.  This is a one time thing but should get you into Ubuntu and you can then install drivers.

---

### Post by mörgæs on 2014-07-03
Installing from USB is a better way than CD/ DVD.

If you have an old BIOS you could make it Windows' last job to install a new one.

---

### Post by ubfan1 on 2014-07-03
I see a previous post gave you the edit instructions (they appear at the bottom of the grub screen too).
Since you have two disks, you may be restricted by your BIOS so that boot only occurs from one of them.
The CD install is slower, more prone to media problems, but does have the advantage that the CD does NOT (usually) get inserted in the hard disk enumeration, like USBs do.  Since the USB usually gets sda, all the other disks are bumped up a letter, and the created grub.cfg configuration file refers to these device names (which change when the install media is removed) (longstanding bug).

---

