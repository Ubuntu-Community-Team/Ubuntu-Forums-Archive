---
title: "upgading to Gutsy beta from Fiesty Crashes badly and does not complete"
date: 2007-10-01
forum: Installation &amp; Upgrades
---

### Post by suchawato on 2007-10-01
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/146204](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/146204) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				So yeah
I'm amazed this thing functions at all after a crash this bad.
It's a statement to the durability of linux/unix. '_^
Here is what I entered in the related bugfile:

"...This happened to me too.
Some python errors, update manager crashed,
and now, the default boot does not function.
I have to open the grub menu and select the oldest generic line in order to boot.
It calls itself Gutsy (although it did not complete the install) the gnome hal splash screen does not launch, gnome cursors do not function, video player abilities do not work, and bit torrent does not function. any help completing the upgrade would be greatly apprecieated. I used the online upgrade.
I will be happy to provide any attachments needed.
Attempts to run 'dpkg --configure -a' end in a crash-infinite loop in which it does not fix, and continues to want me to run 'dpkg --configure -a' to fix the problem."

As I said, any help completing the upgrade and getting the system out of crippled state would be greatly appreciated.
Thanks so much in advance.
-Stu

---

### Post by cosborn72 on 2007-10-01
have you tried running <dpkg --configure -a> yourself, or does it the system trying to do it for you? If it is running automatically, it might be hitting a user prompt and waiting for input.

My installation stalled mid-way as well, but I ran <dpkg --configure -a>, which seems to have fixed it.

---

### Post by Strannik on 2007-10-01
> **cosborn72 said:**
> have you tried running <dpkg --configure -a> yourself, or does it the system trying to do it for you? If it is running automatically, it might be hitting a user prompt and waiting for input.

My installation stalled mid-way as well, but I ran <dpkg --configure -a>, which seems to have fixed it.

I'm having the same issue. and now  that i know, i will not be rebooting =) . yes i have tried to maunally run dpkg --configure -a, it doesn't do anything, and returns me to the prompt...

---

### Post by Strannik on 2007-10-01
also, if i try to run update manager again, it asks me if i want to do a partial upgrade, i say yes, and it gets stuck on the same part. also, if i try to do a apt-get dist-upgrade, it finishes off with this: E: Couldn't configure pre-depend cupsys for cups-pdf, probably a dependency cycle.

---

### Post by Strannik on 2007-10-01
hm. i just replaced the sources.list file with the feisty default one, and the update seems to be working just fine. this definately needs to be added to the default update instructions: 3-rd party repos will mess up your upgrade!!!

---

### Post by suchawato on 2007-10-01
Yes, 
      'dpkg --configure -a' (manually) does nothing, an infinite loop, it crashes, and prompts to do it again, the next time attempted.

Note: I can reboot if I go into the grub menu during boot, and boot to an old generic kernel line.
The default will not boot. but I can get it to run in a crippled state.
I wouldn't reboot either though..

---

### Post by suchawato on 2007-10-01
How did you replace your sources with the Fiesty ones?

---

### Post by suchawato on 2007-10-01
Strannik, it's interesting that you mention third party sources.
During the upgrade (attempted upgrade) I got a prompt saying third party sources WERE disabled.
and that I could re-enable them after the upgrade.
Did you get this as well?

---

