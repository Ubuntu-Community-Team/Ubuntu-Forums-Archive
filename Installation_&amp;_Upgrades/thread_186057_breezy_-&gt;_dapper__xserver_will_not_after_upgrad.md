---
title: "breezy -&gt; dapper:  xserver will not after upgrade"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by beforewisdom on 2006-06-01
Hi;

I just upgraded from breezy -> dapper.

All went well until I rebooted.  The system told me that the xserver wouldn't start and this was most likely due to a poor configuration.  I know nothing about xservers :).

I tried
dpkg --configure xserver-org
but it told me that it was already configured and did nothing.  There was no "--reconfigure" option.

Any help getting through this would be appreciated.

Thanks

Steve

---

### Post by johnc4510 on 2006-06-01
The command is:
sudo dpkg -reconfigure xserver-xorg

---

### Post by metoo on 2006-06-01
What graphic card do you have?

Happend to me on SuSE 10.1 with kernel 2.6.16 - no 3D driver for an old Geforce2 Pro.

You have a new kernel now - 2.6.15 .

---

### Post by beforewisdom on 2006-06-01
Okay, the command is dkpg-reconfigure, one word.

Once there I had a strong sense of deja vu when I tried playing with raw debian years ago.  I still have the same monitor ( one of the early thin ones ).  I remembered that whatever software that configures the monitor always picked screen resolutions, and refresh rates that were too high.

dpkg-reconfigure also tells everyone that choosing "frame buffer" is the safe bet and it is not for my monitor.   I picked the other choice, went with 1024 x 768, picked "advanced" on the monitor config choices and chose 24 ( or 16 ).  That fixed it.

I am posting this here in case it might help someone else.......or me in the future when I do this again and forget what I did .

---

### Post by th3gh05t on 2006-06-01
[QUOTE=johnc4510]The command is:
sudo dpkg -reconfigure xserver-xorg[/QUOTE]

Hi, 

I have tried this command, and it doesn't work. dpkg says that there isn't a 
"-reconfigure"

Are there any other solutions?

---

### Post by Ragazzo on 2006-06-01
I'm having the same problem. I used "sudo dpkg-reconfigure xserver-xorg" and tried selecting vesa driver instead of ati and disabling frame buffer but those didn't help. I have Radeon 9600 Series.

---

### Post by nicky75 on 2006-06-01
I have the same problem too, in the grub list there isn't the new kernel 2.6.15 of Dapper but the old 2.6.12, but in consol appears Dapper 6.06 :-k

---

### Post by Ragazzo on 2006-06-01
Finally it works :) . I had to write "sudo apt-get dist-upgrade" again in the terminal.

Some problems I encountered:
-At some point during the upgrade I got the login screen. When I entered my name, it looked like it crashed and all I saw was orange background. The upgrade was still going on in tty1. After it finished, I rebooted and it worked perfectly.
-It removed Windows XP from GRUB list

---

### Post by th3gh05t on 2006-06-01
[QUOTE=Ragazzo]Finally it works :) . I had to write "sudo apt-get dist-upgrade" again in the terminal.

Some problems I encountered:
-At some point during the upgrade I got the login screen. When I entered my name, it looked like it crashed and all I saw was orange background. The upgrade was still going on in tty1. After it finished, I rebooted and it worked perfectly.
-It removed Windows XP from GRUB list[/QUOTE]

Hi, 

Does this go through the entire installation again? How long did it take?

Were you experiencing the same inbound and outbound connections flying across the screen?

---

### Post by Ragazzo on 2006-06-01
[QUOTE=th3gh05t]Hi, 

Does this go through the entire installation again? How long did it take?

Were you experiencing the same inbound and outbound connections flying across the screen?[/QUOTE]

Hmm. It didn't download the files again, only installed them. It took about 15-30 mins.

---

