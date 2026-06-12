---
title: "Problems installing/seting up unbuntu please help!"
date: 2008-08-26
forum: Installation &amp; Upgrades
---

### Post by spartan73 on 2008-08-26
hi all! First post and I'm I need of help! 

I've installed ubuntu... Well I say install but I have went through
 the set up process and click finish when the computer then
restarts but the action goes onto standby, I then have to hold the 
power button for 5 seconds to turn the computer completely off
I then started it back up and after the normal bios start it comes 
up with the normal unbuntu loading screen but then only progresses
to a scree. Which he wot looks like a command scren prompt
asking me to enter something I guess of type help for a list of
commands.  Now I cannot get past this screen and this is the
ferthst I've been in ubuntu so far! Can anyone help? 

I've already resorted to reinstalling ubuntu but the same thing 
always happens? I've always had a issue wiu this computer 
and itputti g the monitor on stnd by and not letting it turn on when 
the computer restets so I think this is what has caused the problem
just cnt seem to find a way around it! 


Sorry about the long post! Cheers arron I

---

### Post by Pumalite on 2008-08-26
Post your specs:
Memory? Graphics?

---

### Post by damis648 on 2008-08-26
As I understand it, you are getting to a Busybox prompt. Try the following:
at the GRUB menu, press "e" on the Ubuntu boot option. Go down to the second line, and press "e" again. From the end of the line that appears, remove the words "quiet" and "splash". Now press enter, followed by "b". When you get this busybox prompt again, please tell us the error message that preceded right before it.

---

