---
title: "unable to boot Ubuntu 18.04 Couldn't get UEFI db list"
date: 2019-02-20
forum: Installation &amp; Upgrades
---

### Post by mzh01 on 2019-02-20
[COLOR=#242729][FONT=Arial]I migrated from Windows to Ubuntu few months back, today I was working with my project and due to wrong PHP code it stuck my machine 2 to 3 times, I restarted directly and then it showed some inode cleaning message, now my ubuntu doesn't load and show me this error. [Image of My Screen Ubuntu]("https://i.stack.imgur.com/4ttCm.jpg")[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Partitions are ext4 and not a dual boot machine, only ubuntu, I can login with the recovery mode, after [/FONT][/COLOR]flush journal to persistent storage[COLOR=#242729][FONT=Arial] but direct boot always show above message.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]By following the command. [the same message appear]("https://i.stack.imgur.com/e6DJG.jpg")[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]This [screen appear when loading]("https://i.stack.imgur.com/hMTYo.png"), after it emergency mode appear in console, someone know how to resolve this, I can access the console, help please!

sudo fsck -nf /dev/sda3

[/FONT][/COLOR]https://imgur.com/swhvtS4

---

