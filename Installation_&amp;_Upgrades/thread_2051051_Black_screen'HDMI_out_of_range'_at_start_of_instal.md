---
title: "Black screen/'HDMI out of range' at start of installation Ubuntu 12.04"
date: 2012-09-01
forum: Installation &amp; Upgrades
---

### Post by mazinho on 2012-09-01
Hi Guys,

I'm trying a fresh installation of 12.04 from a USB stick on a system with an nvidia card using hdmi out. As soon as I select an installation option (try ubuntu, install on a HD) I will see a stream of code across the screen for a couple of seconds, followed by the HDMI going out of range. The installation appears to continue but I have no idea what's going on as I have no picture. :)

Hoping someone can help with this.

I'm completely new to Ubuntu so possibly have missed something obvious.

I've been reading through a lot of potential solutions on these forums which seem to rely on pressing F6 and using 'nomodeset' or typing commands in grub.

My problem is that no keyboard shortcuts seem to work, I have the installation options but don't get to the keyboard symbol or to the language select, and none of the short cuts I've seen mentioned work for me. I don't even get to grub.

So far I've not seen any solution that works for me, but as I said above, I'm possibly missing something very simple.

Any ideas on a possible solution?

Thanks,

mazinho

---

### Post by mazinho on 2012-09-02
I did finally manage to solve this.

For anyone who has the same problem and is similarly uninitiated in Ubuntu/Linux, this is what I did:

On the initial installation screen I highlighted the option to install to a hard disk. Then pressed 'Tab'. I then edited the text which appeared at the bottom of the screen, changing 'splash' to 'nosplash' and then typing 'nomodeset' immediately after. Click enter, and bam, installation begins and HDMI works fine.

Success.

---

