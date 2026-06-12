---
title: "Frustrated Blinking Cursor"
date: 2012-07-28
forum: Installation &amp; Upgrades
---

### Post by finito on 2012-07-28
Yesterday I installed LiinuxMint 13 Maya then Cinnamon then Maya then Cinnamon, then Finally Ubuntu then back to Cinnamon.

The issue you ask?

Right after install system boots to Cursor.

I tried Holding ****, spamming Shift and removed all other hard drives but no go.

I tried mounting sda1 and editing /etc/default/grub and setting nomodeset. Still no go it stay stuck on the cursor.

I tried pressing Cntrl+Alt F1-F2-F3...F9 no go.

I don't get it, system was fine on mint 10 and ubuntu 10.

I thought why not upgrade it, it's seen many installs but never anything like this.

I am going to try getting mint 10 and trying to see if there is another issue I doubt it though.

Please help.

---

### Post by finito on 2012-07-29
I noticed sometimes the blinking cursor would go and it would try to go into X, but it would crash before reaching there and signal would be cut off.

So I started to spam Reset and shift to get into Grub and used the link below.



[http://forums.linuxmint.com/viewtopic.php?f=90&t=105134#p594094](http://forums.linuxmint.com/viewtopic.php?f=90&t=105134#p594094)

> 2. Replace "quiet splash" with "noacpi noapic nomodeset" and hit f10 to boot.
3. When Mint is running, download Daniel Richter's grub-customizer, so as to edit GRUB.
4. In Preferences, replace "quiet splash" with "noacpi noapic nomodeset".
5. Exit and restart. Worked a treat.

This didn't work earlier as it would not always boot to X, and I guess the cursor is preboot even before Grub.

This should help people who have only one OS installed.

Peace.

---

