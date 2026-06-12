---
title: "Undo update"
date: 2006-10-05
forum: Installation &amp; Upgrades
---

### Post by sheine on 2006-10-05
I allowed the latest system update about a day ago. Now my system that worked well is messed up. When I start, I get a message about gnome settings that can't be found. Then Big Buddy comes on and wont go away. Finally, the computer wont shut down. I have to disconnect power to turn it off.

I just want to go back to where I was three days ago in an easy way.

---

### Post by confused57 on 2006-10-05
I don't know if this will help or not:

[http://www.ubuntuforums.org/showthread.php?t=271523](http://www.ubuntuforums.org/showthread.php?t=271523)

---

### Post by sheine on 2006-10-05
The problem is that the last update package had so many updates that I do not know the source of the problem. I will try the update that came afterwards but that is another two and a half hour download even with DSL. While I realize that the people who run Ubuntu are constantly trying to improve Ubuntu, there is also the maxim "If it aint broke, dont fix it". After all Dapper Drake is the stable distribution not the developmental Edgy EFT.

---

### Post by sheine on 2006-10-05
Congratulations, guys. I went through the second set of updates and Ubuntu is unusable. Now, I cannot even get into the graphic mode.

I am using Puppy to send this message. How do I get a working Ubuntu system?

---

### Post by sheine on 2006-10-06
Thanks to advice on another thread, I got gnome back. The solution was: sudo apt-get update and then sudo apt-get install xserver-xorg.

However, there are still troubles resulting from the updates. I shall wait until the stable version comes out.

---

### Post by caveden on 2008-01-18
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/bugs/184046](https://bugs.launchpad.net/bugs/184046) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Have you found out how to make a "block" downgrade? I made a big update today and some of my applications crashed. I'd like to undo it all at once. Going packet by packet is tiring and error prone...

Thanks,
Tiago.

---

