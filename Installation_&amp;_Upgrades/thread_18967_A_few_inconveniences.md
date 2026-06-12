---
title: "A few inconveniences"
date: 2005-03-09
forum: Installation &amp; Upgrades
---

### Post by JMY1983 on 2005-03-09
After install I am confronted by a $ prompt, but I am going to try startx to get past that. But also, when I first get to the login bit the screen flickers twice and then I get a message saying that Server X failed. And also, when it says 'you have new mail' the actual emails are error messages, so I wonder if I installed correctly. And finally, I don't get a screen where I choose my OS. Each time I restart I have to go to BIOS and choose which drive to boot off. The only thing I can think of is that I installed Ubuntu on my other drive, the one I don't boot off. Thanks for any help.

---

### Post by alastair on 2005-03-09
On the BIOS boot order - looks like the order was wrong at install time, or the bootloader was installed to the wrong disk. It gets confusing.

Email messages? That's OK - deal with them. If there are errors - what errors? Probably something you can fix.

For X - there's something broken with your X config, so ...

- what graphics card?
- what errors? see : /var/log/Xorg.0.log (hoary) or /var/log/Xfree???.log (warty)
- what is in your X config file? /et/X11/xorg.conf (hoary) or /etc/X11/XF86Config (warty)

---

### Post by JMY1983 on 2005-03-09
Yeah I think the bootloader was put on the wrong disk, but I didn't see that I had a choice. I am thinking of wiping the Linux drive and trying over. I have a Leadtek Winfast 6800 GT Nvidia card.  The errors were mostly saying something about not being able to update and that older files were being used. How can I show you that file? The Linux drive isn't visible from windows for some reason.

Update: I tried to do startx but it didn't work, I think its a graphics issue.

---

