---
title: "Upgrading Xubuntu to Fiesty 7.04 failed and killed my system"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by ZephyrXero on 2007-05-03
**This post could be related to an Ubuntu bug filed at**: [https://launchpad.net/ubuntu/+source/update-manager/+bug/68027](https://launchpad.net/ubuntu/+source/update-manager/+bug/68027) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Ok, so I've just made a major mistake. I was not aware of the bug with Xubuntu + update-manager when you try to do a dist-upgrade....*someone should really make this more publicly aware to those who don't frequent the forums that often.* My problem seems to be worst than most that I've heard of too. :(

Sometime right after all the packages finished downloading and the actual installs began my machine seemed to freeze up. I switched to another console and ran top to find that Xorg was eating up way more CPU than it should have. I knew this would kill out all the child processes, including the update-manager, but I didn't seem to have a choice. After killing and restarting X, seemed to come back up fine. The update manager informed me there was an error and to try Synaptic. Upon opening Synaptic it told me to run "dpkg --configure -a" to restart and finish my interupted installations. I ran the command and it completed without errors....however, my system was still at 6.10. I attempted to start up update-manager again, but it once again directed me to Synaptic. Synaptic allowed me to upgrade all my remaining packages since it appeared my repos had already been updated to feisty I figured this should be fine....I guess I was wrong. Somewhere halfway though this process the system hard locked and video went all distorted. Once again, I had no choice but to do something drastic, this time a full system reboot. Now when my machine comes up Grub can't find my root partition, and I'm betting my kernels either.

As annoying as this all is, I'd probably be fine with just doing a reinstall if I hadn't, also stupidly, forgotten to recently backup my Postgres database that resided on this machine. Please please please tell me there's someway to type in some magic command in grub to get my machine back up, or mayber perhaps chroot off a liveCD and run a postgres dump???

Any ideas will be more than welcome ;)

---

### Post by follier on 2007-05-20
*sigh*... I didn't want to upgrade, adept just kept bugging me so, I figured what the heck?  

After a successful install, I am now left only with a cursor.  No Grub, No Partitions, No nothing.  So I have to now go through with a fixdisk CD or whatever else I can find to get my more important data back.

All because I was weak... and said ok when the it asked me to upgrade the 100th time.  Unless you really know what you're doing, and willing to redo everything, I wouldn't recommend trusting the easy button.

[-X

Enuff complaining, back to work... I need to get my research off of there.

---

### Post by eapache on 2007-05-20
Try booting from the livecd, then mounting the root partition. I'm not familiar with postgres, so:

- if all it needs to backup are a few files, just copy them to a usb stick then reinstall and copy them back.
- if there is an option inside the program that puts all the required files from various locations into one backup file, install postgres on the livecd, and point it to the mounted directory, then backup from there and copy to a usb stick.

I hope this helps.

---

