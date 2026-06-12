---
title: "Ubuntu won't go past purple screen."
date: 2012-02-04
forum: Installation &amp; Upgrades
---

### Post by Acutical on 2012-02-04
I've managed to get to the purple screen but after, it turns into a black screen with white text. I've tried installing it with: Wubi, USB, CD, all the same result. :/ Help me?

I have

Asus sabertooth x58
Intel Core i7
Nvidia GTX 560Ti

---

### Post by MG&amp;TL on 2012-02-04
Where are you getting the ISO from? What hardware? Can you install it first?

---

### Post by Acutical on 2012-02-04
Ubuntu.com is where i got the iso. What do you mean by  hardware? I listed most of my specs above. The problem is, I can't install it... I can't get to the install screen.

---

### Post by MG&amp;TL on 2012-02-04
Oops, sorry about the hardware-my bad. :oops:

What sort of black and white text? Can you quote it? Thanks.

---

### Post by Acutical on 2012-02-04
I get this screen when i boot from a CD

[http://i.imgur.com/N1TO9.jpg]("http://i.imgur.com/N1TO9.jpg")

And after that disappears i get this...

[http://i.imgur.com/7AX93.jpg]("http://i.imgur.com/7AX93.jpg")

I've let that screen run for 5 mins and the text changes after awhile but it still won't boot into ubuntu.

---

### Post by MG&amp;TL on 2012-02-04
Well...I'm sorry, but I have no idea, but I didn't like to leave you in the lurch, so you could try reading [this]("http://ubuntuforums.org/showthread.php?t=1613132") thread and trying some of those flags.

---

### Post by Acutical on 2012-02-04
I left it over a hour. Still no luck.

---

### Post by dagroves on 2012-02-04
Okay this may be a long shot, but some computers do not want to boot any distro with the Linux 3.x kernel, mine wont. Here is what I had to do so I could run 11.10.

FROM ANOTHER THREAD I POSTED ON:

> 
I have the same problem but I was installing regular Ubuntu. My computer  was not booting the Linux 3.x kernel correctly. I cannot live book  11.04 or 11.10 of any of the *buntu family of distros (or any distro  that uses the 3.x kernel). What I had to do was install Ubuntu 10.10 (in  your case, Mythbuntu 10.10) then upgrade to 11.04 and upgrade again to  11.10, then when you boot, choose an old 2.x kernel in Grub. Then when  you get to the desktop, open a terminal and execute this command 'sudo  gedit (or whatever text editor you use) /etc/default/grub' without  quotes or anything in the (). Then edit the line that says  'GRUB_CMDLINE_LINUX_DEFAULT="quiet splash', after quite and splash add  this 'acpi=off' no quotes. Save the file and exit the text editor, then  in the terminal type this: 'sudo update-grub' and then 'sudo reboot now'  and then choose the 3.x kernel to boot into. It works for me. If you  have any questions feel free to ask and I hope it all works out. It  seems like a lot of trouble, and it is, but it was the only way I could  get anything newer than 10.10 and the 3.x Kernel to run on my old  Pentium 4 PC. Good luck!


Hope this helps!
David

---

### Post by Acutical on 2012-02-04
That seems like it will work. If no one else has a easier solution I will do that. Thanks for your reply.

---

