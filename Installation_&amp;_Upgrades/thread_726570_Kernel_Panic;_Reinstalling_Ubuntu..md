---
title: "Kernel Panic; Reinstalling Ubuntu."
date: 2008-03-16
forum: Installation &amp; Upgrades
---

### Post by rolandixor on 2008-03-16
I have had the kernel panic issue on Ubuntu 7.10. I have tried to get help, but no one seems to want to answer the question directly. Is there some way to fix it without reinstalling?

I am cautious about reinstalling because of the fact that it might mean losing files, and not to mention the programs. BTW, I cannot!!! risk losing the files on the drive. I can possibly transfer them by memory key, but that will take forever.

So, please, tell me, clearly (please) :-), what can I do?

---

### Post by Pumalite on 2008-03-16
Give details and exact error messages for people to be able to help you.

---

### Post by rolandixor on 2008-03-16
sorry, I can't be precise right now, since I can't get onto the laptop drive right now. But basically it's the regular Not syncing madness (with something about VFS)

I've asked for help before, but it always ends up being a waste of my time since everyone gives a merry-go round relpy and then gives up. HAS NO ONE EVER SOLVED IT?

And if not, is there a way to recover the installation without losing files???:popcorn:

thanks for caring...

---

### Post by Pumalite on 2008-03-16
Without knowing more, all I can tell you is that you can save your data with Ubuntu Live CD.

---

### Post by rolandixor on 2008-03-16
Qouting the output:

VFS: Cannot open root device "UUID=4dc4da78-2a14-4886-b567-3cbdb89ca7e0" or unknown-block(0,0)

Please append a correct "root=" boot option; here are the available partitions:

Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

This is the output I got, any ideas?

---

### Post by AdNZL on 2008-03-18
I have a very very similar issue. I have been using 7.10 for a few months now and after freezing up on me I rebooted and the computer got stuck on startup screen (the one with the progress bar) I tried starting up in recovery mode and got that **VFS** error, so I thought " no problem I'll just use the live CD, but that is just as bad. Ubuntu did run a disk check today booted up fine then died about 5 minutes later, but even running of the cd with that HD disconnected and my XP one plugged in leads to identical results.** Windoze seems to be working fine**, which is kinda annoying, but at least it means I can write this.

Here's the last few lines that come up, the last one seems to be where things start going horribly wrong :(

```
[     52.966062] VFS: Cannot open root device "<NULL>" or unknown-block(104,1)
[     52.966113] Please append a correct "root=" boot option; here are the available partitions:
[     52.966178] Kernel panic-not syncing:VFS: Unable to mount root fs on unknown-block(104,1)
```

I copied this down by hand so there might be an error or two, but I checked it pretty carefully. [COLOR="DarkOrange"]Any Help would be much appreciated as I don't want to go back to window's just because Ubuntu won't run on my machine, especially as it had been running for months without any issues.[/COLOR]

---

### Post by AdNZL on 2008-03-18
Well Just as randomly as the problem started it dissapeared. After leaving my comp alone (but still on with xp) I tried booting ubuntu from the HD again and it worked fine. I think for me, at least, the problem lies with old slowly dying hardware. Although I'd still love to know what exactly was happening and why the live CD wouldn't even work. Windoze xp was even behaving a little weird, but hey its windoze and weird is just normal.:rolleyes:

---

### Post by Pumalite on 2008-03-18
Glad you got your computer back.

---

### Post by AdNZL on 2008-03-19
Thanks, it's a pretty horrible feeling when ya rely so much on your comp for everyday stuff and it dies on ya. Especially when a replacement is financially out of reach.

It would be interesting to know what caused it though :-k

---

