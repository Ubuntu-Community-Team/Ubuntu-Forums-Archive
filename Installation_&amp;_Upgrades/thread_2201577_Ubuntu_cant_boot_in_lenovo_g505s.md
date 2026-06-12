---
title: "Ubuntu cant boot in lenovo g505s"
date: 2014-01-25
forum: Installation &amp; Upgrades
---

### Post by shahbazkhan425 on 2014-01-25
I have lenovo g505s  AMD A10 /1TB/8gb     
(for more h/w info [http://www.flipkart.com/lenovo-essential-g505s-59-380146-laptop-apu-quad-core-a10-8gb-1tb-dos-2-5gb-graph/p/itmdm79dbkjzewwk?pid=COMDM799ZGJTXAVT&otracker=from-search&srno=t_1&query=lenovo+g505s&ref=74b0fb2f-800c-4120-a422-70ef28b6c8cc](http://www.flipkart.com/lenovo-essential-g505s-59-380146-laptop-apu-quad-core-a10-8gb-1tb-dos-2-5gb-graph/p/itmdm79dbkjzewwk?pid=COMDM799ZGJTXAVT&otracker=from-search&srno=t_1&query=lenovo+g505s&ref=74b0fb2f-800c-4120-a422-70ef28b6c8cc))

i have installed windows 8 (not efi). then installed ubuntu 13.04 amd64 . ubuntu installed successfully but no grub menu appeared on startup, only purple screen and the system freezes there.

i removed ubuntu and installed kali linux 3.7-trunk-amd64 and it worked very well.

then i reinstalled ubuntu 13.10 alongside windows 8 and kali linux .  both win 8 and kali works fine but not ubuntu.

I have searched on internet 
i found this link  [http://ubuntuforums.org/showthread.php?t=2195115&highlight=ubuntu+boot+g505s]("http://http://ubuntuforums.org/showthread.php?t=2195115&highlight=ubuntu+boot+g505s")
the solution didnt work for me.

i used boot-repair-64bit and used recommended repair.
boot info summary [http://paste.ubuntu.com/6809011/](http://paste.ubuntu.com/6809011/)

i tried no nomodeset but didnt work. i think the problem is with dual graphics

please help me fix this problem it really annoying me for a long time.

---

### Post by Bucky Ball on 2014-01-25
Is kali controlling the grub by any chance??? If so, boot into kali, open a terminal and issue:

sudo update-grub

Reboot. Your Ubuntu should be there.

When you are installing Ubuntu, where are you telling it to put its grub? On the same partition it is installed to?

---

### Post by shahbazkhan425 on 2014-01-25
kali is controlling the booting. i did try that before but didnt work. All it shows is purple screen (no grub menu). i used boot-repair to fix. 
THIS purple screen problem (ubuntu freezes) is the main problem i think.  i have ATI radeon HD 8650G + 8570M dual graphics which i think is causing the problem. 
9
the same problem also appeared when i first installed kali linux. i thought i should use boot-repair and it worked.
 i have no clue why kali linux i booting and ubuntu is not, given that kali uses modified ubuntu kernel.

---

### Post by Bucky Ball on 2014-01-25
Sounds like grub is booting fine and getting you are getting a list with your installs to choose from. Your other installs boot without issue, so the problem doesn't appear to be with grub (that's booting you to Ubuntu), but with Ubuntu.

If you haven't tried 'nomodeset' in this current situation, try it at the end of its kernel line in the grub screen. When you are at the grub screen, select Ubuntu but don't hit return, type 'e' instead.

At the end of the line with 'quiet splash' (or any combination of those words) leave a space and add 'nomodeset' so the end of the line would look like this:

quiet splash nomodeset

Follow the instructions at the bottom of the page to boot to Ubuntu. Any different?

---

### Post by Bucky Ball on 2014-01-25
Sounds like you're booting fine and getting a list with your installs to choose from. Everything boots fine except Ubuntu, so this is not to do with Grub but to do with Ubuntu.

Try 'nomodeset' at the end of its kernel line. When you are at the grub screen, select Ubuntu but don't hit return, type 'e' instead.

At the end of the line with 'quiet splash' (or any combination of those words) leave a space and add 'nomodeset' so the end of the line would look like this:

quiet splash nomodeset

Follow the instructions at the bottom of the page to boot to Ubuntu. Any different?

You say you think the problem is with dual-graphics. What do you have? The nomodeset only works with nvidia from memory.

---

### Post by shahbazkhan425 on 2014-01-25
> [COLOR=#000000][INDENT]Sounds like you're booting fine and getting a list with your installs to choose from. Everything boots fine except Ubuntu, so this is not to do with Grub but to do with Ubuntu.

Try 'nomodeset' at the end of its kernel line. When you are at the grub screen, select Ubuntu but don't hit return, type 'e' instead.

At the end of the line with 'quiet splash' (or any combination of those words) leave a space and add 'nomodeset' so the end of the line would look like this:

quiet splash nomodeset

Follow the instructions at the bottom of the page to boot to Ubuntu. Any different?

You say you think the problem is with dual-graphics. What do you have? The nomodeset only works with nvidia from memory.[/INDENT]
[/COLOR]
[INDENT]
[/INDENT]
i tried that but didnt work.

then i tused boot-repair just to upgrade grub. after that i can boot in ubuntu .
thanks guys for the solutions

---

### Post by Bucky Ball on 2014-01-25
Excellent news! I made a major breakthrough today thanks a complete mistake. 

Enjoy. ;)

---

### Post by shahbazkhan425 on 2014-01-25
is it grub problem or something else?

---

### Post by tgrego on 2014-03-30
> **Bucky Ball said:**
> Excellent news! I made a major breakthrough today thanks a complete mistake. 

Enjoy. ;)

Hi,
I've bought a Lenovo G505S, and I'm facing the very same problem! :x

Could you plese let me know how you fixed it?

Thanks

---

