---
title: "Moving home folder from another gnome2 distro"
date: 2011-07-25
forum: Installation &amp; Upgrades
---

### Post by Alistair George on 2011-07-25
Desired option - to be able to take my other Linux gnome2 home folder and replace my ubuntu so that effectively works as a backup restore.

I had read elsewhere, and also been told, that you can do this without any ado. Unfortunately, does not seem to be wholly correct:
Ubuntu set up a new user (as backup) called guest. My original Linux Mint folder was 'alistair' as is my new ubuntu home folder.
After setting up (backup) guest account, I logged out and in as root. Deleted folder alistair and replaced it with folder alistair from Mint: includes all hidden files and directories.
I get two errors the first 'could not update ICE authorityfile /home/alistair/.iceauthority (which I tried manually replacing with the ubuntu one stored in trash still no joy. Sorry, second error I cant recall.
any ideas?

Easy enough to revert back to installation defaults from trash, but that is not the object of the exercise.
thanks,
Alistair

---

### Post by Perfect Storm on 2011-07-25
If you have separated /home partitions.
Under a new installation you go to manually edit partitions, choose /home to keep, then use the same name and password. You can now automatically log in under your 'old' username and the kept settings.

---

### Post by Alistair George on 2011-07-26
> **Artificial Intelligence said:**
> If you have separated /home partitions.
Under a new installation you go to manually edit partitions, choose /home to keep, then use the same name and password. You can now automatically log in under your 'old' username and the kept settings.
Ideally, I could have copied my Linux Mint user over to Linux Ubuntu user, and it would have all been spot on.
Here is what I did with limited success:
Already my alistair account on ubuntu was valid. As root, I deleted all under home/alistair and copied from my Mint to ubuntu alistair.
Next
sudo chown -R alistair alistair /home/alistair
(above to enable permissions in ubuntu on the copied Mint data)
It booted but there were enough problems to show the installation was broken (eg not recommended).
Since my goal was to do away with the Mint logical drive and stay with ubuntu if it were better, the idea of simply copying all the data over from Mint to Ubuntu has proven invalid.
Even though both systems use the same gnome2, to use another systems files appears to me to be an invalid process. Pity about that.
I am happy to be corrected. What is of concern to me is if under Linux of any guise, if you have a major crash, and have backup of your home/user directory, this backup might not be valid? From this experience it would seem possibly not.
Best wishes,
Alistair

---

