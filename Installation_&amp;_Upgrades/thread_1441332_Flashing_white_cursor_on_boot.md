---
title: "Flashing white cursor on boot"
date: 2010-03-28
forum: Installation &amp; Upgrades
---

### Post by rayjchris on 2010-03-28
Hello, I have recently installed Ubuntu 9.10 Desktop x64 on my storage server. With just the boot swap and a 50GB root partition the server will boot up fine and you can log in as normal.

The server itself has 10 x 1TB hard drives in raid 6. The boot swap and root partitions are all contained on this raid volume. When assigning the remainder of the volume to a separate data partition (about 7.2TB, EXT4) using gparted it takes about 40 minutes to create and format. It does this without showing any error messages.

Upon restarting the server all you are presented with after the bios and raid controller screen is a white flashing cursor. Does anyone have any suggestions as to why this might be happening?

The only thing that has changed from the initial install is the addition of the large data partition. I have tried this twice now and got the same results both times. I'm tempted to update the bios on the raid controller but if this was the root of the problem I would have expected to have issues installing Ubuntu on the raid in the first place!

Hope to hear from someone soon!

---

