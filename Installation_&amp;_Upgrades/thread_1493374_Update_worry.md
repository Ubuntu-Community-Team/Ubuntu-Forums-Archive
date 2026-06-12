---
title: "Update worry"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by rob45 on 2010-05-25
Hi well ive just had a bit of a problem with updates in 10.04.
Everything downloaded fine but during the grub update things went a bit wacky.

A window pops up saying that i had chosen not to install grub on any part of my system and was informed that by choosing to do this my 10.04 installation was doomed.:confused:
There didn't seem to be away of closing the message window so i was forced to re boot....in the middle of the update.

On going back to update manager i was informed that partial update was the way forward so i let it carry on...same thing happened...only this time the message came in form of the installtion console......like what you see in dos.....with a yes/no option on wether or not i wanted the grub update to carry on.

Selecting either of them made no difference......so again i was forced to re boot ...again in the middle of installing updates.

A bug report thing did pop up which i have filled in.

My concern is even though the update thing did finally manage to complete  what states my grub in.

When i re boot i now have 4 options for linux.......2 for normal start and 2 for recovery........and i think my XP  is still there.....cant say i noticed during all the confusion.

Do i need to do anything?

---

### Post by Ozymandias_117 on 2010-05-25
It should all be fixed by running ```
sudo update-grub
```

---

### Post by rob45 on 2010-05-26
> **Ozymandias_117 said:**
> It should all be fixed by running ```
sudo update-grub
```

Cheers....that seems to have fixed it..:)

---

