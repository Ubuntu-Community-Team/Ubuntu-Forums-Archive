---
title: "no grub screen visible on boot"
date: 2014-06-16
forum: Installation &amp; Upgrades
---

### Post by Pedroski55 on 2014-06-16
It's me again!
I installed Ubu 14.04. It works. Originally the timeout on grub was set to 0. I changed that to 40 and rebooted.

Where I expect to see the grub choices, I see nothing but a black screen with a purple frame around it. By accident I pressed esc, and then the usual grub boot choices screen appeared, Windows is still not one of the choices, but memtest, recovery mode etc are there.

Anyone had this particular problem?

---

### Post by yancek on 2014-06-16
> Originally the timeout on grub was set to 0. I changed that to 40 and rebooted.

Did you change it in the /etc/default/grub file and then run sudo update-grub?  The change you made should not have resulted in the boot screen you see but there are several other settings.  You might have accidentally changed something like the HIDDEN_TIMEOUT.  Other than that, I don't have any idea.

---

### Post by oldfred on 2014-06-17
Did you previously have grub-customizer installed? It adds and changes grub's scripts.

Post this:

 sudo ls -l /etc/grub.d

---

### Post by Pedroski55 on 2014-06-17
Sorry, this is my home computer, no probs here. My friend's computer is not here. As far as I know, we did not install anything special. His was a new install. Unless grub customizer is put in by default, I don't think we had it.He's off to the Philipines, I don't think I'll see him now until September. But he is happy, he can boot Ubuntu and access his Windows partition, even if the start up is a bit strange. He is even learning to enter the bios and change things!

Get back to you on this one in September. Maybe we can get dual boot working for him!

---

