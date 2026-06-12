---
title: "Recomnmended remote S/W for Ubuntu?"
date: 2024-05-27
forum: Installation &amp; Upgrades
---

### Post by leejenon on 2024-05-27
Hi, can I have a recommendation for remote software for my Ubuntu server please?

I currently have issues with Teamviewer, previous post.
[URL="https://ubuntuforums.org/showthread.php?t=2498035"]
https://ubuntuforums.org/showthread.php?t=2498035[/URL]

Thanks, Lee

---

### Post by &amp;KyT$0P# on 2024-05-27
ssh (package [FONT=monospace]openssh-server[/FONT])

What are you looking to do remotely?

---

### Post by leejenon on 2024-05-27
> **halogen2 said:**
> ssh (package [FONT=monospace]openssh-server[/FONT])

What are you looking to do remotely?

Just control the desktop - files, reboot, admin

My Teamviewer is working now thanks to the other thread.

Lee

---

### Post by MAFoElffen on 2024-05-27
But you said "Server"... Teamviewer is a Desktop application.

???

---

### Post by #&amp;thj^% on 2024-05-27
teamviewer-host is geared to servers

---

### Post by leejenon on 2024-05-28
Hi, It's server SW running on the desktop PC - I access this now with Teamviewer on another laptop. My server language is a loose definition of 'server' as it's not a server from a h/w perspective. 

Lee

---

### Post by TheFu on 2024-05-28
ssh.

That is how professionals manage all their servers around the world.
By default, Ubuntu Server doesn't have any GUI programs, so I'm a bit confused by looking for a "desktop" on a "server" that doesn't have any "desktop".

Regardless, you should still use ssh.

If the systems are on the same LAN, than you can use X11-Forwarding, through ssh tunnels.  This is trivial. I use it daily, currently, all-the-time.  Right now I have 12 windows open on my workstation. 4 are running on the local system, but all the others are using remote X11 though ssh. It is very convenient.

Learn to work the Unix/Linux way, not the MS-Windows way. You'll be more efficient, more secure and have better integration with your workstation desktop doing this.

---

### Post by leejenon on 2024-05-28
Oh, I see what you mean now. 
Thanks for your thoughts.

---

### Post by TheFu on 2024-05-28
> **leejenon said:**
> Oh, I see what you mean now. 
Thanks for your thoughts.

Start here to learn non-GUI management: [https://www.linuxcommand.org/tlcl.php](https://www.linuxcommand.org/tlcl.php)  That's really a beginner book.  At least it is free and current and in many different languages.  Of course, you can walk into any bookstore and buy a copy on paper there too, if you want to support the author.

One of the hardest things for people new to Linux Servers to learn is to change the way they think from "GUI" to non-GUI and setting up automation.  Automation is much easier with out any GUI in the way.  Automation with a GUI cannot be run without a user logged in.  CLI-based automation only needs the computer to be on - no user need be logged in.

Perhaps a simple example comparing the Windows way and the Linux way.  [https://blog.jdpfu.com/2012/02/15/beginning-linux-thought-shift-needed](https://blog.jdpfu.com/2012/02/15/beginning-linux-thought-shift-needed) 
It really is a different way of thinking.

---

### Post by leejenon on 2024-05-29
Ok, thank you.
Lee

---

### Post by ActionParsnip on 2024-05-29
SSH, you can do all the things you said using SSH

---

### Post by leejenon on 2024-05-29
Thank you &#128591;

---

