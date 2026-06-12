---
title: "Boot Errors: nothing seems to help"
date: 2020-05-30
forum: Installation &amp; Upgrades
---

### Post by Aktrop on 2020-05-30
I'm back to Ubuntu after a gap of 12 years (I quit after realising I was spending more time on my xorg file than my dissertation!). I've installed the latest Ubuntu LTS on an old MacBook Air (circa 2010). Everything was working fine. 

Then I screwed it up by installing the proprietary NVIDIA drivers.

Now, when I boot the computer, all I get is a very small white line that never changes. I have tried calling the Grub screen during the boot process, but that doesn't work (I've tried 'Esc', spacebar, 'Command', 'Control', 'Del', 'Return', 'Shift' and many combinations thereof, but no luck. I tried booting off the USB stick that I used to install Ubuntu, but that didn't work either. 

Any help would be much appreciated.

---

### Post by dino99 on 2020-05-30
i suppose you still can boot in 'recovery' mode; then purge the installed nvidia driver (that will set 'nouveau' on the next normal boot)
From synaptic, select and install the nidia driver required by your graphic card/chipset

---

### Post by jp41 on 2020-05-30
try holding down the [FONT=Roboto]holding down the &#8220;Command,&#8221; &#8220;Option,&#8221; &#8220;0&#8221; and &#8220;F&#8221; keys simultaneously as the machine boots.[/FONT]

---

### Post by Aktrop on 2020-05-30
dino99 thanks, but the problem is that I can't even get as far as booting in recovery mode. 

jp41, many thanks for your suggestion, but it didn't work. I'm still stuck with that very small white line. It used to just stall there and not change at all. Now, after a few seconds, the screen goes blank.

---

