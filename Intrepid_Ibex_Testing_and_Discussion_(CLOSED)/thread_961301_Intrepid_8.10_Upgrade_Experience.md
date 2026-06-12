---
title: "Intrepid 8.10 Upgrade Experience"
date: 2008-10-28
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by denham2010 on 2008-10-28
Hi,

I thought for once I would go ahead of the pack, and update to Intrepid RC before the official release.

I only upgraded tonight, just 2 nights before the official release, so there should just be a handful of updates once the final version is done.

I just wanted to post my experience of the upgrade so hopefully it may help others about to embark on Canonical's latest.

Feel free to post your own upgrade experiences, as these will no doubt assist others.

This is what I have experienced so far - I will update this post as I discover more (it's late here and nearly time to get some sleep).

Firstly, as I have always experienced difficulty upgrading with anything but the default repositories in your sources.list, I removed all non-official repositories, including partner and medibuntu.

The upgrade ran perfectly. Not one error (this bodes well as I have XFCE, GNOME and KDE installed as I use a wide mix of applications from all desktop environments - running XFCE as my desktop)

1. Make a note of your compiz settings. If you are running the Hardy repository version, your settings are lost on upgrade (dare I say due to incompatible differences in the new version).

2. Back up your LIRC configuration (in /etc/lirc) if you are using an infrared remote. The default config replaces your own.

3. If you are using any version of AWN besides the repository version, back up your settings. Non repository versions are removed.

4. Others have experienced problems with the nvidia drivers and X. Obviously it will completely depend on your video card. I am using a GFORCE 8500 GT. The upgrade to the new drivers worked flawlessly. I believe most of the nvidia issues will arise with legacy cards.

That's it for now....as I check everything on my system (habit with an upgrade as I have always had some annoying issues in the past), I will update this post, but in general, this appears to be the most painless upgrade I have done!

Cheers!

Denham2010.

---

### Post by denham2010 on 2008-10-29
Back again.....

Well, what can I say?

I am so impressed with the Intrepid release.

As per my previous post, I now have my compiz settings back, along with the wonders of cube deformation, I have re-installed awn-trunk (I no longer have a panel and some of the awn applets - eg pynot and slickswithcer - I require to remain 'panel-less' are not available in the repository version), and I have copied my lirc config back to where it belongs.

The result, my system is running more than 100% to what it was previously (some previous niggles in Hardy have since disappeared).

Absolutely everything I have set up on my system, from Samba to MythTV and all inbetween, are working flawlessly!

Canonical, kudos on the fastest and most painless upgrade I have ever experienced!

Cheers.

---

### Post by peterthewolf on 2008-10-29
I agree totally a completely error free upgrade on 29th October. After the upgrade mythtv would not show TV, I had noticed at boot that module apparmor was giving an error

Oct 29 10:50:39 tv-pc AppArmor(init): Skipping profile /etc/apparmor.d/gdm-guest-session.dpkg-new
Oct 29 10:50:39 tv-pc kernel: [ 4299.042752] audit(1225277439.563:3): type=1505 operation="profile_replace" info="unsupported interface version" pid=2288
Oct 29 10:50:39 tv-pc kernel: [ 4299.132711] audit(1225277439.651:4): type=1505 operation="profile_replace" info="unsupported interface version" pid=2292

So I removed apparmor via synaptic and the reinstalled apparmor, rebooted and TV via mythtv worked.
The apparmor error still occured at boot.

---

### Post by Musashi on 2008-10-29
I made the upgrade too, so far no problem with compiz, nautilus or the system.

---

### Post by stormtrooprdave on 2008-10-29
I upgraded on Monday gone and had no problems what so ever.  A couple of settings had to be changed (eg changing conky script from eth1 to wlan0 for wireless info).

The biggest changes I've noticed are boot times are sped up greatly and I had a regular issue with a kernel panic linked to wireless but it has yet to occur in Intrepid.

---

### Post by Saneless on 2008-10-29
Upgrade went mostly fine.  Biggest issue is that Compiz doesn't work with custom key functions involving Super.  So if I set Rotate Cube to Super+Mouse Button it doesn't work.  Ctrl+Alt+Mouse Button does though.

Super works at least for some things, like Zoom, but not for others, like Super+L For lock workstation. No idea what broke.

---

