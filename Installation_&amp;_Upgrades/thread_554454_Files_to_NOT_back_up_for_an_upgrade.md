---
title: "Files to NOT back up for an upgrade?"
date: 2007-09-19
forum: Installation &amp; Upgrades
---

### Post by mdebusk on 2007-09-19
There are plenty of articles and how-tos describing what to back up before an upgrade, but I've found nothing about what to AVOID backing up.

When I installed 6.06, it was my first serious attempt at Linux, and I haven't looked back at OS/2. But when I went to uprade to 6.10, I realized I'd made a small sort-of-mistake: /home was on the same partition as everything else. So I backed up /home, repartitioned to give /home its own place, and restored my backup.

(I realize it isn't truly an error. It's just that I have always installed 32-bit operating systems with a separate data partition, so TO ME it was an error.)

I had also backed up /etc from 6.10 and restored it to 7.04, but to the best of my recollection I did not overwrite anything.

When I installed 7.04, I was impressed at how nearly everything I'd changed about my desktop was still there from the very first boot. I was happy with my /home partition.

I'm having some troubles with sound and video, though, and can't seem to track them down. I'm wondering if there are configuration files somewhere in my home directory or the /etc directory that are causing, or at least contributing to, these problems.

What files should one NOT transfer from an existing install to a new one? What do you think?

---

### Post by ryno519 on 2007-09-19
> **mdebusk said:**
> There are plenty of articles and how-tos describing what to back up before an upgrade, but I've found nothing about what to AVOID backing up.

When I installed 6.06, it was my first serious attempt at Linux, and I haven't looked back at OS/2. But when I went to uprade to 6.10, I realized I'd made a small sort-of-mistake: /home was on the same partition as everything else. So I backed up /home, repartitioned to give /home its own place, and restored my backup.

(I realize it isn't truly an error. It's just that I have always installed 32-bit operating systems with a separate data partition, so TO ME it was an error.)

I had also backed up /etc from 6.10 and restored it to 7.04, but to the best of my recollection I did not overwrite anything.

When I installed 7.04, I was impressed at how nearly everything I'd changed about my desktop was still there from the very first boot. I was happy with my /home partition.

I'm having some troubles with sound and video, though, and can't seem to track them down. I'm wondering if there are configuration files somewhere in my home directory or the /etc directory that are causing, or at least contributing to, these problems.

What files should one NOT transfer from an existing install to a new one? What do you think?

I typically just tar.gz my entire home directory minus the music and movies and then extract it in the new install. That way I still have all of my settings.

---

