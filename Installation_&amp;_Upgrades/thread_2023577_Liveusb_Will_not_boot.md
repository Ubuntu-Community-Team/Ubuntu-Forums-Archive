---
title: "Liveusb Will not boot"
date: 2012-07-12
forum: Installation &amp; Upgrades
---

### Post by knightmarh on 2012-07-12
Ok, I press f11 at bios to go to the boot menu and select my sandisk ultra 1.20.
For around 20 seconds there is a little grey box at the bottom left of the screen and then it switches to a blank command line screen, then once more switches to a completely blank screen.

Help :(

Thanks in advance!

---

### Post by knightmarh on 2012-07-12
Live usb created using start up disk creator and the iso from ubuntu's homepage.

Specs:

Processor - i7
Motherboard - AsRock z68 Extreme3 gen3
Memory - Corsair 8GB
Graphics card - Asus Nvidia GTX 550

Hope this helps.

---

### Post by efflandt on 2012-07-12
Initially do you see a purple screen with keyboard and round symbol at the bottom, or is that the screen you mention with little gray box at bottom left?  Anyway when you see that screen with gray box at bottom, try hitting any key and see if something comes up asking what language, and after pressing enter comes up with a text menu.

Since there is apparently a problem with your video, at that point press **F6**, move down to **nomodeset**, hit **SpaceBar** to X that, then **Esc** to close that, then "Try Ubuntu without installing" and see if that works.

I had to do that to boot 64-bit live/install 12.04 iso on USB with nvidia graphics.  But I did not need to use any kernel boot parameters once I installed the system.

PS: You have same video I do.

---

### Post by knightmarh on 2012-07-12
Ok, upon pressing enter at the little grey box, it disappears and when I press f6 it has moved slightly along a little and there is a grey line running under the grey box which has moved to the right slightly, inside the grey box now is a darker box, there is no writing and I can move the darker box up and down to eight different places inside the lighter box.
Thanks for your help so far!

---

### Post by knightmarh on 2012-07-12
Ok, having found a picture of what my screen should look like I have managed to work it out!
Thank you so much for your help efflandt, you are my new hero!
Will i have to do this every boot?

---

### Post by knightmarh on 2012-07-12
After install I reboot and I get a blank purple screen and then blackness, help again please?

---

