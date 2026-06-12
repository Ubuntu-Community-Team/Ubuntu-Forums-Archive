---
title: "Rolling back from Edgy to Dapper"
date: 2006-11-06
forum: Installation &amp; Upgrades
---

### Post by Marsol0x on 2006-11-06
Well, I wanted to upgrade to Edgy, but that didn't work as well as I had hoped.

I'm running Kubuntu, btw.

I follow the directions as given by the Kubuntu website on how to upgrade to Edgy, except that instead of using the repositories that I had set up, I found a clean, default set on the forums. I then changed dapper to edgy and proceeded with the updates.

First I used sudo apt-get update
Then I used sudo apt-get dist-upgrade

Everything was going well, all of the downloads downloaded and now it was the install time. I ran into an error or something, it stopped to tell me that an install could not continue because of the /usr/X11R6 folder, it suggested that I clear out the folder and try again. So, I renamed the folders inside /usr/X11R6 to have a -back extention and moved them to my home folder, just in case I needed them again. I ran sudo apt-get dist-upgrade again and it started running into perl error problems when installing. I decided that I didn't want to go through the hassle of figuring out what the problem was and so I put the folders back into X11R6, removed the -back extention, replaced edgy with dapper in my source.list and re-ran sudo apt-get update and sudo apt-get dist-upgrade.

It downloaded and installed without an error message and I became satisfied, though careful. So I rebooted, to see if it'll work. It booted up normally until it got to the point where the Kubuntu logo was supposed to appear with a blue background and a body telling me that it was setting up windows, menus, etc, and then the final, KDE is up. Instead, it stuck with a black background, the Kubuntu logo, and a blue bar below that, no text.

Little help for a newbie?

---

### Post by pgatrick on 2006-11-06
Sounds like you got the edgy boot splash.

---

### Post by Marsol0x on 2006-11-06
> **pgatrick said:**
> Sounds like you got the edgy boot splash.

How do I fix it?

Edit:
Actually, I think it is that X Windows isn't booting up.

---

