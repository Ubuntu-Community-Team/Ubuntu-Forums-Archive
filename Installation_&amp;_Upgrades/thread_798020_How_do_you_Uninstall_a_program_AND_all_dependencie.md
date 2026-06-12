---
title: "How do you Uninstall a program AND all dependencies."
date: 2008-05-17
forum: Installation &amp; Upgrades
---

### Post by VMC on 2008-05-17
I recently installled [acetoneiso]("http://www.acetoneiso.netsons.org/forum/viewthread.php?forum_id=3&thread_id=20&pid=78#post_78"), thinking it would work similar to Windows UltraISO. It didn't and hard to figure out. So I uninstalled it. 

  When I installed it there were a slew of dependencies that were required to run this program. When I uninstalled Acetoneiso, that was all that got uninstalled. I didn't think to write down the other files. How do I get rid of them?

 I don't know where to look. Is their a directory where they were kept. In the future how do I avoid this mistake?

---

### Post by OskarS on 2008-05-17
Assuming you already uninstalled the program (e.g. with "sudo apt-get remove [whatever]"), just type this in the terminal:

```

sudo apt-get autoremove

```

That will remove packages that were installed to satisfy a dependecy that's no longer needed. apt-get makes these sorts of issues easy to deal with :)

---

### Post by cdtech on 2008-05-17
I use this from a command line:

apt-get remove --purge <program>

---

### Post by VMC on 2008-05-17
Thank both of you!

I executed the command:
sudo apt-get autoremove
A bunch of programs no longer needed were removed, 51+mb

This command, I'm assuming if I executed it first using "acetoneiso" for the program name, then all those unneeded dependencies would have been uninstalled also, correct?
apt-get remove --purge <program>

---

### Post by cdtech on 2008-05-18
Correct....

---

