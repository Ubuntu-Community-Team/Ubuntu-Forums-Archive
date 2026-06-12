---
title: "Xubuntu 15.04 to 15.10 upgrade froze/crashed"
date: 2016-02-11
forum: Installation &amp; Upgrades
---

### Post by russkyca on 2016-02-11
I run Ubuntu on two partitions, one is Ubuntu with Gnome.   The other is Xubuntu.   The Xubuntu one is a bit behind so I decided to upgrade 15.04 to 15.10.   Everything went well until it got to the upgrade of grub-pc.    It froze...I left it for a long time and concluded nothing was going to happen so I restarted the computer by pressing the computer's reset/restart button.

It booted up and when I chose the Xubuntu one in the grub menu, it did load.   But, it **didn't** finish so what surprises am I into?

The last steps was 'clean up' and to restart the machine.

I decided to run the 'Software Updater' now but what else should/can I do?   I know that the latest grub 2.02 is beta and maybe there are problems when you upgrade the Ubuntu version to a newer one - when the step of grub (upgrade) package comes up?   

I don't recall a problem when I upgraded my other Ubuntu OS (on the other partition).   

Will I need to 'clean' things up or how can I check if I need to fix anything?   The upgrade sure wasn't clean or smooth so I am anticipating problems.   

Does anyone need me to run any commands to provide further info or?

---

### Post by furtom on 2016-02-11
Believe it or not, I think you are ok.

You can just run:

```
apt-get autoremove
```

to do the clean-up. Check the output to make sure apt isn't removing anything crucial, but it shouldn't. If you have any question, select no and post the output here first.

As long as GRUB was successfully installed, as it appears it has been, you are pretty much OK.

---

