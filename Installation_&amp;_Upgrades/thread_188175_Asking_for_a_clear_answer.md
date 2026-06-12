---
title: "Asking for a clear answer"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by rickyjones on 2006-06-03
Hey,

I'm still running Breezy Badger and I have a question that I'm asking a clear answer for.

My system is partitioned in such a way to allow for Windows XP Pro to live here, along with Ubuntu. My /home is a seperate partition. If I do a clean install of Dapper in it's normal partitions, will my user account (assuming I use the same username) use my current home directory the right way, and will all of my applications continue to work (Evolution)? I'd prefer to not lose any data from the home directory, and I'm afraid that a clean install might not be able to use my old data.

Thanks!

-Richard

---

### Post by MetalMusicAddict on 2006-06-03
Yes. As far as I know if you dont format on install, your settings, along with mail, files and such should stay. I *have* heard of problems so I would still back-up things you dont want to lose. Dapper is awesome. You wont regret the move. ;)

---

### Post by aysiu on 2006-06-03
When you go through the installation, choose to manually edit your partition table.

Then make sure you mount your Home partition at /home and choose **not** to reformat it.

---

### Post by rickyjones on 2006-06-03
[QUOTE=aysiu]When you go through the installation, choose to manually edit your partition table.

Then make sure you mount your Home partition at /home and choose **not** to reformat it.[/QUOTE]

That's my plan - to manually partition and mount.

And yes - Dapper DOES seem awesome! Running the desktop live-cd right now to test my hardware. Just trying to see if any of the same bugs from Breezy are still here on my laptop (Toshiba Satellite M265 something).

Can anyone confirm that the new Evolution w/ Gnome will work with the data files from the past version?

Thanks for the help guys!

-Richard

---

### Post by meng on 2006-06-03
Yes all my data was preserved. IIRC it's only an upgrade from v 2.4 to 2.6 for evolution, unlike the v.1 to v.2 upgrade that changed the storage format (I didn't lose any data then either).

---

### Post by rickyjones on 2006-06-03
Thanks for the information guys! I'm poised to upgrade later on tonight, else later on this week :-)

-Richard

---

