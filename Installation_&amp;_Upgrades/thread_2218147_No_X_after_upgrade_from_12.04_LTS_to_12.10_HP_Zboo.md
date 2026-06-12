---
title: "No X after upgrade from 12.04 LTS to 12.10 HP Zbook with Nvidia Quadro K3100M"
date: 2014-04-19
forum: Installation &amp; Upgrades
---

### Post by The Dragon Master on 2014-04-19
I have a new HP Zbook. It has an Nvidia Quadro K3100M card.

I had 12.04LTS installed, unity worked fine. I installed nvidia-common. All was OK.

I tried an upgrade to 12.10 and now cannot boot into X (black screen with non-flashing cursor in top left). I can ctrl-alt-f1, ctrl-alt-f2, etc to swap between shells.

startx gives the black screen (with cursor)

I have tried installing nvidia-common.
I have tried purging nvidia-common.
I have also tried 
sudo apt-get remove --purge xserver-xorg
sudo apt-get install xserver-xorg
dpkg-reconfigure xserver-xorg

Curiously,  
lsb_release - a tells me I have quantal, 
but uname -a says
Linux soledad-HP-ZBook-17 3.11.0-15-generic #25~precise1-Ubuntu SMP Thu Jan 30 17:39:31 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

I wonder if the reference to precise is a clue or a red-herring?

When I try startx I get
Fatal server error: no screens found

any thhoughts? :confused:

---

### Post by david98 on 2014-04-19
Why are you upgrading to 12.10 it is no longer supported. Have you tried using  nomodeset ?

---

### Post by The Dragon Master on 2014-04-19
I have also run into the following message a few times today

Starting AppArmor profiles [fail]

e.g I got that just now when I tried an alternative to startx

sudo service lightdm start

---

### Post by The Dragon Master on 2014-04-19
Thanks david98

My real aim is to have CUDA 4.1, the 12.04 repositories only had CUDA 4.0. 

12.10 was the default choice given by the GUI updater / upgrader - so I just went with it. 

Currently downloading 14.04, but on a very slow connection so it will take hours. I'd like to have a solution before then. I'd also like to find a smarter way through this problem than just re-installing.

Thanks for the nomodeset hint, I'd not tried it, but looks promising, I'll read this and see where it get's me.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by The Dragon Master on 2014-04-19
So I followed the steps under "How to temporarily set kernel boot options on an installed OS (not wubi)" here [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

i.e. I edited the line
linux /boot/vmlinuz-3.11.0-15-generic root=UUID=a8906578-8944-4f96-95f5-441877f7d366 ro quiet splash $vt_handoff 
so it says
linux /boot/vmlinuz-3.11.0-15-generic root=UUID=a8906578-8944-4f96-95f5-441877f7d366 ro quiet splash $vt_handoff nomodeset

the result... I get to the graphical ubuntu start-up screen with a little ubuntu logo and five red progress dots, but it freezes there - power-off the only way out :confused:

---

### Post by The Dragon Master on 2014-04-19
Thread closed. I now have 14.10 installed.

---

