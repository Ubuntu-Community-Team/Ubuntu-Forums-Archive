---
title: "Ubuntu repair"
date: 2006-09-02
forum: Installation &amp; Upgrades
---

### Post by gflores on 2006-09-02
I first want to say, I love Ubuntu. But I've got a problem...

Here's the situation. I installed Ubuntu 6.06 for my brother, who lives 4 hours away. Well, when this Aug. 22 update fiasco occurred, he couldn't boot up. I told him to follow the steps listed in the wiki, but he says he's not getting that blue screen. Plus, he's not too comfortable using the command line.

What I would like for him to do is use the Ubuntu cd to repair his current installation. How can he do this? Also, will his programs and personal files disappear? I don't remember if his home directory is in a separate partition or not, I used the 'guided installation'.

What are the steps towards repairing Ubuntu?

---

### Post by meng on 2006-09-02
Are you sure he couldn't boot at all, or he just couldn't get the Xserver started? There's a big difference: if he can't boot, perhaps he has an unrelated problem.
The X-server problem can be solved with a single command in console mode. It seems silly to me to attempt a reinstall/repair, which would risk losing his personal data with a simple mistake.

---

### Post by zxee on 2006-09-02
Go to this thread: [http://www.ubuntuforums.org/showthread.php?t=241254](http://www.ubuntuforums.org/showthread.php?t=241254)
Read "Howto fix the problem with the Alternate Installer CD of Ubuntu (not the live installer)" Perhaps you can talk your brother through some of it-he will need to use the terminal for some of that. Hope that helps.

---

### Post by gflores on 2006-09-03
> **meng said:**
> Are you sure he couldn't boot at all, or he just couldn't get the Xserver started? There's a big difference: if he can't boot, perhaps he has an unrelated problem.
The X-server problem can be solved with a single command in console mode. It seems silly to me to attempt a reinstall/repair, which would risk losing his personal data with a simple mistake.
My mistake. Ubuntu booted but xserver did not start. He's already backed up his files, so that's not an issue. 

I'll check out the Alternate Installer CD.

---

