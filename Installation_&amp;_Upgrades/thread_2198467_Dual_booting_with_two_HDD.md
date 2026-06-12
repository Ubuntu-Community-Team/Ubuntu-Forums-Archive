---
title: "Dual booting with two HDD"
date: 2014-01-08
forum: Installation &amp; Upgrades
---

### Post by wolfzrat2 on 2014-01-08
Hi everyone I need your help.

I have a Dell Dimension E251, I have the primary HDD running Windows 7, I recently installed a second HDD and installed Ubuntu 13.04 on it. Everytime I boot my computer I get and error message saying:

Error: no such device: 2b13b036-2205-4705-a89b-acd3817af143.
grub rescue>

What can I do to fix this and boot from my 2nd HDD

---

### Post by deadflowr on 2014-01-08
Have you tried [boot repair]("https://help.ubuntu.com/community/Boot-Repair")?

If it doesn't take, make sure to copy down and post the pastebin output.
But from my amatuer eye, it looks like the UUID for the Ubuntu partition is probably wrong.
boot repair should fix that.
Fingers crossed, and good luck.

---

### Post by wolfzrat2 on 2014-01-08
how do I do that?

---

### Post by deadflowr on 2014-01-08
> **wolfzrat2 said:**
> how do I do that?

What do you mean?
Run boot repair?

Do it from the livecd.
Boot the livecd for ubuntu and select the "try ubuntu" option during boot.
Then follow the direction on installing boot repair from the link I provided.
Then let it run.
When it finishes it'll post a message about the output being in a place something like paste.ubuntu.com/XXXXXX, or something like that.
copy that number down, it's the file that boot repair generated on exactly what happened when it ran. It a big file so it uploads to a website, specifically built for that type of purpose.
If all goes well, you can probably ignore it, but if it doesn't you can post the link here, and we can decipher the problem.

---

### Post by wolfzrat2 on 2014-01-08
thank you all I had to do was turn the HDD on, it works now

---

