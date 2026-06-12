---
title: "[resolved] Ubuntu &amp; Lilo"
date: 2004-12-27
forum: Installation &amp; Upgrades
---

### Post by Thanatos9602 on 2004-12-27
I just redid the linux partitions & reinstalled Ubuntu on hda5. I set it up with Lilo for a boot manager. When I first got into it? I used "sudo gedit /etc/lilo.conf" & renamed the windows just plain '98' & set it as default. I exited gedit, type 'lilo', hit enter & then rebooted. Problem is, it rebooted straight into '98' without giving me a choice menu. How can I get it to give me the menu for at least 10 or 20 seconds at boot? Tell me what I need to do & I can edit the 'lilo.conf' using the DamnSmall live CD. Can't figure that out. Lilo should give you a choice menu. Thanks for any help. I'm beggining to loose hope in useing Ubuntu. Thanks again for all the help.

---

### Post by Thanatos9602 on 2004-12-27
I give up. I removed Ubuntu from my computer. Then loaded DamnSmall & modified it, no problems. Until Ubuntu can be set up with lilo to run with Win98SE, WinXP & other linuxes, I'll just leave it in the back of my CD case. Sorry, I liked the features. It just has to learn to play well with others, for me to use it.

---

### Post by cafeina on 2005-01-10
how did you install Ubuntu with lilo ? I always get grub :(

---

### Post by Thanatos9602 on 2005-01-10
When it starts to load the Grub, hit the 'Esc' key like a machine gun. When it takes you back to the menu, select the Lilo, hit the enter key very, very easily. It may take two or three tries, eventually it'll work. I had to reinstall Ubuntu & the escape didn't work this time. That's OK. I saved the lilo.conf from the other time. I will use it to edit DamnSmallLinux's lilo.conf. Then I'll have all three working. Win98SE, DSL & Ubuntu. Wish me luck.8-[ Sorry so long for reply. I've been working on the computer early morning & late night. During the day, I'm helping remodel my Mother's kitchen. Hell, I haven't done carpenter work in almost twenty years, I'm afraid of close places (however it's spelled), & I'm disabled. About another week & a half & the kitchen should be through. Me & my step-father are a little slow. We're both older & disabled. Lord, what you won't do for Momma. Hope the escape button helps you get lilo. I can edit it all day. I can't edit grub for shit. Good luck.

---

### Post by eldados on 2005-01-10
All you need to do is set the timeout in the lilo.conf you can use your favourite editor or use the gui from the system setting menu and use boot config you can change setting there, after you finish apply and exit, open term and sudo lilo, reboot and you good to go :)

---

### Post by Thanatos9602 on 2005-01-10
Thanks. Like I keep saying. Playing with Lilo is easy. I redid Grub once. Took over an hour to figure it out. Really do care at all for grub. I'll play with Lilo sometime tonight or tomorrow. 8.5 hours of carpenter work, make computer thinking harder. I'm to damn old for this manuel stuff. I gave it up 10 years ago. Body's a whole lot older & in worse shape. I use to weigh around 150-160, now it's 190-200. Middle age plus. :-(  Stay cool. Talk to you later.

---

