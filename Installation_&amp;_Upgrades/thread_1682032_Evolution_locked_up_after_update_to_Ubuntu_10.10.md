---
title: "Evolution locked up after update to Ubuntu 10.10"
date: 2011-02-05
forum: Installation &amp; Upgrades
---

### Post by pieemme on 2011-02-05
Evolution displays all my messages, but doesn't open them. After clicking on a message, the screem greyes out and I can oly get out from Evolution by forcing the exit.  I have tried launching  Evolution from the terminal window:all I can learn is from this rather cryptic message:
EI: MAIL PREFSThere is an existing lock 137 seconds old
I have searched a number of forums without finding any suggestion.  I suppose I should delete some folder in the file system, but have no idea as to which one.  I have made backup copies, so I hope I am safe with this.

Furthermore, Evolution seems to be drying out most of the available memory.

Any suggestion is greatly appreciated,

Pieemme

---

### Post by mörgæs on 2011-02-06
Hi, welcome to the fora.

Since you have a backup, I guess the fastest solution is a complete removal of Evolution (meaning purge) and a reinstall after that.

---

### Post by pieemme on 2011-02-06
I hadn't thought of this radical possibility, but, in fact, there seems to be little harm in trying. I have already tried removing evolution without purging, but nothing changed.

---

### Post by pieemme on 2011-02-06
Thanks,I applied both purge and remove, as well autoremove, to get rid of dependencies, but when I reinstalled Evo, I could find all my mailboxes back there, just as stuck as they were before this excercise.  A very stubborn programme I must say.

I guess all of the problem is with the mailboxes. I wish I could understand where they are all scattered to rename them. I noticed that, if I launch Evo with sudo, I get a brand new Evo, with no customised settings. but this would likely be a parallell installation.

Any idea how to delete/rename the mailboxes?

---

### Post by mörgæs on 2011-02-07
Googling your error message yields a lot of posts like
[http://www.mail-archive.com/evolution-list@gnome.org/msg03869.html](http://www.mail-archive.com/evolution-list@gnome.org/msg03869.html)

Does it help?

---

### Post by pieemme on 2011-03-20
Thanks a lot [mörgæs]("http://ubuntuforums.org/member.php?u=939075") for yr kind reply.  I've tried Juergend's recipe, but it didn't unfortunately work for me. Launching evolution causes this blessed error message to appear in terminal, as soon as I click on any message from Evo's window:

there is an existing lock... XXX seconds old

I tried deleting whatever I had in the path 
~/.evolution/mail/local/.#

but it didn't change this situation. I also find that oponing and force shutting Evo seems to eat up a lot of resources and my computer's performance has got as bad as with any lousy Windows installation.  I used to be an Ubuntu fan...

---

