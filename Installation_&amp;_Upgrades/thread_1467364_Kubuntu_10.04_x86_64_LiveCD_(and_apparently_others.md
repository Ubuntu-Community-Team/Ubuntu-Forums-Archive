---
title: "Kubuntu 10.04 x86_64 LiveCD (and apparently others) won't boot on Dell XPS 630i"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by Chronon on 2010-04-30
I torrented the Kubuntu 10.04 LiveCD for 64-bit yesterday and seeded all last night.  I planned to use this afternoon to install the new version.  However, I have found that it won't boot on my hardware.  (Yes, I verified MD5sums, verified the burned data, etc.)

Another person with the same hardware as me (Dell XPS 630i) [also cannot boot this (or the Ubuntu/Xubuntu 64-bit for that matter) LiveCD](http://kubuntuforums.net/forums/index.php?topic=3109872.0) after similarly checking MD5sums and verifying burned data.  I did have this problem with the Karmic disks as well for both Ubuntu and Kubuntu.  I ended up getting around this by installing Zenix, an Ubuntu remix.  I would upgrade, except that the person in the thread I linked has reported breakage on this hardware when upgrading from 9.10 to 10.04.

====================
I guess I will wait for Zenix's next release in May and try to install from that.  First, I might try installing from the Alternate CD, though.  I'll report my findings with that. *No, this gets stuck at the same spot (after language selection and choosing to install).*

Update: I guess I will try the upgrade for myself.  I still have the Karmic CD for Zenix to use to reinstall if it goes south.
====================

I just want to post this so that other people with the same hardware won't be surprised if they run into snags with installing from the LiveCD.  Has anyone had success with the LiveCDs with this hardware?

---

### Post by Chronon on 2010-04-30
I am replying because I think the updates are getting a bit messy.

I had success with updating to 10.04.  I did get the "error: the symbol 'grub_puts_' not found" message after rebooting, but I was able to follow this guide to get it working again:
[http://grub.enbug.org/Grub2LiveCdInstallGuide](http://grub.enbug.org/Grub2LiveCdInstallGuide)

I won't mark this as solved because I consider this merely a workaround that worked for me.  The LiveCDs still do not work for me and this is not a viable method for first-time installers to use.

---

### Post by Shigoki-linux on 2010-04-30
i have a compaq, and also get what i think is the same problem as you. my monitor just says no signal. i tried both my monitor and tv. same. i am thinking its a hardware problem, but it shouldnt have any problem.

i aparently solved it with the F6-> nomodset. just fyi.

---

### Post by Chronon on 2010-05-01
Thanks for the input.  That might be useful to know.

It sounds a little different from my situation, however, since my screen isn't blank (with no signal), it's black with a flashing white cursor in the upper left corner of the screen.  I should say "was", since I am now typing this from my running Lucid installation.

---

### Post by jakeman66 on 2010-05-02
> **Chronon said:**
> Thanks for the input.  That might be useful to know.

It sounds a little different from my situation, however, since my screen isn't blank (with no signal), it's black with a flashing white cursor in the upper left corner of the screen.  I should say "was", since I am now typing this from my running Lucid installation.

Could you share how you got 64 bit running?  Thanks.

---

### Post by Chronon on 2012-06-07
Sorry to leave you hanging.  I sincerely hope you were able to find a solution elsewhere.  While I am here I will mention what I did to work around this issue (which hasn't been present for a couple of releases now).  

In order to install Ubuntu, I installed a derivative distro (Zenix), which did not cause this problem to appear (different boot parameters?).  From there I was able to achieve a normal (K)ubuntu setup.

---

