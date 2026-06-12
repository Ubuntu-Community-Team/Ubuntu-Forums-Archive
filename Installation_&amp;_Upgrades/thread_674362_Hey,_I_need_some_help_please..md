---
title: "Hey, I need some help please."
date: 2008-01-21
forum: Installation &amp; Upgrades
---

### Post by bmanstyles on 2008-01-21
I had a dual boot going beforehand with windows xp and ubuntu on my main computer.  Windows xp is not booting because it is missing a file. I want to reinstall windows xp. I cannot enter bios mode to delete the os repositories. I just want to start from scratch and go back to windows xp, I know linux is more safe and more fun, but my stepdad wants me to go back to xp, so he can put a parental control thing onto my internet. It reads the xp disk initially and tells me to press enter to begin the setup and than afterwards says it cannot read the disk, please insert the proper cd disk and press enter to continue. I am stuck please help. 

1. Can I get a parental control added onto ubuntu and onto my asus eee pc as well without having to go back to xp?

2. How can I get rid of all operating systems and get windows xp installed?

Thank you all very much.

---

### Post by bmanstyles on 2008-01-21
By the way, he only needs to put a parental control onto the internet, with a password so I won't be able to fumble around with the settings, and so naughty sites are unaccessable.

---

### Post by c0met on 2008-01-21
Hi,

If you are planning on deleting everything that you have and going for a fresh install, I'd do the following.
[LIST]
[*]Boot up from the Ubuntu Live CD and run the partition editor (under System >> Administration).
[*]Using this, I'd delete all the partitions that you have and then "apply"; if the partition editor (GParted) shuts down during this process, it's ok, just restart it.
[*]create new partitions (or a single one, whichever suits) and choose the format to be NTFS. Apply the changes.
[*]Shutdown the Ubuntu CD and reboot from the Windows XP installation CD.
[*]You should now be able to install.
[/LIST]

---

