---
title: "Upgraded 16.04 two days ago: Now no graphical interface after user login"
date: 2018-08-12
forum: Installation &amp; Upgrades
---

### Post by richgil2 on 2018-08-12
I was offered an auto upgrade by the software manager and accepted it. It ran without producing obvious error messages. After reboot I get the graphical login prompt. The login does not complete but halts.

I can obtain a virtual terminal with Ctrl-Alt-F1 and login there without error. I saw a similar query on the forum which suggested that the ~/.Xauthority owner/group might need to be altered from root/root. The owner/group was root/root and I have altered it.

Unfortunately that has not fixed the problem.

I would be grateful for any suggestions to investigate and fix the problem

---

### Post by mörgæs on 2018-08-14
Hi, welcome to the fora.

How does 18.04 work in a live boot?

---

### Post by richgil2 on 2018-08-14
Thank you very much for your reply. I will try that version. Since posting I have found that 'Ubuntu advanced options' on the boot menu contains about a dozen boot versions, each of which has sub-options generic, upstart and recovery. At least two of the recovery sub-options give me a graphical log in and then give me a working GUI. I don't know why ubuntu provides all these options or how they differ but as I can now run a GUI when logged in, I'm happy. Could anyone point me towards any documentation about this? Thanks

---

### Post by mörgæs on 2018-08-14
It's a list of old kernels and they are kept for troubleshooting a situation like this.

You can of course use an old kernel but be aware that new kernels are released for a reason, often for fixing a security bug. General rule: The further from the latest you go the higher the risk. 

Is using recovery mode for the latest kernel enough?

---

### Post by richgil2 on 2018-08-15
The latest kernel I have is initrd.img-4.15.0-32 and in recovery mode that gives me a user graphical interface. In future I will not use the software manager update/upgrade option but will try testing live DVDs as they become available. Many thanks.

---

### Post by mörgæs on 2018-08-15
Good, you can delete the old unneeded kernels with the command ```
sudo apt autoremove
```If you have a dozen of them you will free at least 3 GiB of space.

---

### Post by richgil2 on 2018-08-15
Many thanks.

I've just run apt --dry-run autoremove and it's proposing to remove a few other files too, so I should recover a bit more space.

---

### Post by mörgæs on 2018-08-16
> **richgil2 said:**
> In future I will not use the software manager update/upgrade option but will try testing live DVDs as they become available.

I guess that I understand but just to be sure: I recommend that you update (within release number) every day but when you eventually want to upgrade to a new release I suggest that you do a fresh install.

---

