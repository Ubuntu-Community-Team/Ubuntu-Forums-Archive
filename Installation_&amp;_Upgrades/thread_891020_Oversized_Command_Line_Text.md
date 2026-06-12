---
title: "Oversized Command Line Text"
date: 2008-08-15
forum: Installation &amp; Upgrades
---

### Post by AweD on 2008-08-15
Hello,
Recently, I got back into Ubuntu because of work.
What I'm trying to do is setup a test box at home to bang code in and try to deploy through the box. I chose to get the desktop version because I hadn't used Linux in a few months so I wanted the gui for ease, now that I have everything setup I wanted to run Ubuntu in what would be runlevel 3 in another environment, like say Fedora. But, I've learned that 2-5 are the same with Ubuntu. And, that there isn't an inittab anymore because Ubuntu move to an Upstart system(???). So, on DebianAdmin.com I found this workaround:

sudo mv /etc/rc2.d/S30gdm /etc/rc2.d/K70gdm

And, this makes sense to me, unlike the readme file that advised me to do this. So, I did that command and rebooted. I got the desired affect of a text prompt. Which is good, but the text is huge.

This took up 2/3 the screen: dsingleton@JavaDev:~$

My question is, how do I make this a bit more of a reasonable size?

---

