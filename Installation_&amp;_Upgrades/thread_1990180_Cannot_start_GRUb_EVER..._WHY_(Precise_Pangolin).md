---
title: "Cannot start GRUb EVER... WHY? (Precise Pangolin)"
date: 2012-05-29
forum: Installation &amp; Upgrades
---

### Post by r_avital on 2012-05-29
Hello all,

Here's the situation:
One PC was happily running Lucid (10.04 LTS) AMD64 for years.  The only  video connection is the good-old plain-vanilla VGA.  On this PC under  Lucid, I was always able to start grub by holding down the left Shift  key during boot.  Never a problem.

Upgraded straight from Lucid to Precise (12.04 LTS) AMD64, from DVD I  burned from official Desktop ISO.  Installed all updates immediately  after installation.  All flawless.  Ubuntu runs happily, I installed the  gnome-fallback stuff so I'm in gnome classic (irrelevant to the grub  problem, just giving full details).  Also installed and ran the  boot-repair utility successfully, just in case.

Booting up normally, I first get message from my monitor, "dsub - no  connection" or words to that effect.  Then after a few seconds, I get the  pretty login page, everything is cool.

Trying to boot into grub.  Hold down left Shift key,** I see the message  "GRUB Starting"** - and the screen goes blank again.  And eventually I get  the login page, and can log in.

But I can NEVER run Grub???? What on Earth did the developers do here in  the name of fancy innovation?  Why was this working flawlessly with the  SAME hardware before the upgrade to Precise?

**NOTE:  _This is not a dual boot. _ There is absolutely nothing on this PC other than Precise Pangolin amd64.**  Lucid was completely removed with installation of Precise.

Please, please help with this.

Thanks in advance

---

### Post by dino99 on 2012-05-29
boot up on your dvd and chroot the faulty Precise. There be sure that old grub (legacy) and its menu.lst are gone. The best is to use synaptic (not installed by default) to purge everything related to grub, 

then install grub-pc on /dev/sda (or sdb or ....)

sudo update-grub

---

### Post by r_avital on 2012-05-29
Thanks, Dino, 

I confess i did not follow your procedure exactly.  I already had Synaptic installed, and even though I understand the benefit of safety in booting from the DVD, I simply went to Synaptic and uninstalled everything related to grub, including config files.  Then I tried to reinstall, and got error messages about dependencies not satisfied by my repositories.

Reinstalled the boot-repair utility from Synaptic, and ran it.  When it finally showed a screen with options, I looked at the "grub options" tab, and found an option to "uncomment" a line referring to GRUB_GFXMODE, and a comment that it resolves the "no-signal" issue.

So I used that, and followed the rest of the instructions to the letter.  It recommended installing grub to both sda and sda1 (redundant, I thought, but I did anyway).  Once I rebooted, held down the left Shift key, and grub showed up in all its glory.

So thanks for setting me on the right path.  It's not that I didn't trust your instructions, I'm sure you've tested and verified your procedure thoroughly.  It's just that, you see, I am a programmer by profession, I'm not deterred from following procedures like you described (chroot and so forth), but I don't have the time or patience for this, it's a 3rd backup computer anyway, and I just want cr@p to work.  I'm just testing Precise Pangolin on this test machine before I commit to upgrading my reliable Lucid LTS (which is becoming less and less likely by the minute).

Thanks again and all the best :)

---

