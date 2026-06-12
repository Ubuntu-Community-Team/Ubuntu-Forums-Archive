---
title: "My laptop goes to sleep before login"
date: 2022-07-25
forum: Installation &amp; Upgrades
---

### Post by pelex on 2022-07-25
Hello. My laptop goes to sleep before login, I have Kubuntu 22.04 installed. In previous versions like 20.04 I fixed it by modifying the sleep.conf file by changing the line:

#AllowSuspend=yes

by:

AllowSuspend=no

Now I have not been able to solve it that way since the LED is on and the screen is off.
Any idea how to fix it? I am a user with very limited knowledge. I don't speak English either, I used Google translate. Thank you very much.

---

### Post by MAFoElffen on 2022-07-27
So it boots up and then it is unresponsive? Are you sure it is asleep/in hibernation? Or just no graphics?

Please explain what it does (what you see) when it is booting up...

Do you every see the grub boot menu? What kind of computer is it? You mentioned LED, so I'm thinking it's some kind of Laptop?

Does it boot from a LiveCD USB?

---

### Post by pelex on 2022-07-27
Hello, thanks for answering. It is a laptop, it stays with the led blinking and the screen off. The problem occurs after I get past the grub menu. If I briefly press the power button, it continues to boot normally.

---

### Post by MAFoElffen on 2022-07-27
If at the grub menu, you press the <E> key (Gets into Edit mode on that menu entry), and <arrow-down> until you get to the line the starts with the word "linux"... That is the kernel boot line... <arrow-right> and remove the words "quiet" and "splash"... Then press <Cntrl><X> to boot that entry.

That would temporarily edit that kernel boot line and display the boot messaging, so you see see what is going on in the background during the boot process.

If you do that, does it give you any indication of what is going on?

---

### Post by pelex on 2022-07-27
Attached to an image of what appears on the screen. My knowledge is almost nil. After that the laptop goes to sleep and pressing the power button continues with the normal startup.

[ATTACH=CONFIG]290773[/ATTACH]

---

### Post by MAFoElffen on 2022-07-28
So, the desktop starts... and before the login screen, it goes to a dark blank screen?

What kind of laptop is it?

---

### Post by pelex on 2022-07-29
Yes. I turn on the laptop, Grub passes, and a few seconds later the screen is off and responds only to a short press of the power button. Then the normal process continues.

---

