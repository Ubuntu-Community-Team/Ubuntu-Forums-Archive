---
title: "Some questions concerning migrating a network to Ubuntu"
date: 2007-07-25
forum: Installation &amp; Upgrades
---

### Post by Dave_Man on 2007-07-25
Hi,

I work part time at my university as the Linux administrator and I am migrating our 20 Linux stations from Fedora core 6 to Ubuntu 7.04.

I have a few issues that I just can't seem to find a solution for by googling so it would be great if someone could help me.
I'm no Linux expert, I am learning as I go, so specific and easy instructions would be appreciated.

**My questions:**
1. Our server is a RedHat 9 server and students are able to ssh into it and run various applications remotely.
We are afraid that when the students ssh into it, it will create config files in their home directory which will conflict with the Ubuntu config files.
Is this a problem, and how can I avoid it?

2. How do I change different settings as default for each station and not for each user?
namely: remove start-up processes (like update manager).
customize the language switcher for all users.
maybe even add beryl to be ON by default for all users.
I tried Sabayon but it doesn't do enough.

3. What is the best way to install Ubuntu on all the stations?
I would prefer some sort of imaging solution over automatic installations using network booting because I would like the stations to be identical.
My plan right now is to fully install one station including all post installation add ons like flash, java and codecs and then use partimage to make an image of it.
Then I plan on loading each station using a LiveCD and ssh into the installed station and download the image from there and then install the image on the station.
I am sure there's a better way to do this, so I would appreciate suggestions for improvement.

4. What is the best way to administer all the stations at once?
we have written a small script that sshs into all the stations and sends a command, but it doesn't work that well.
I have also tried using screen to administer all the stations, but that is also not very convenient.
What is the correct way to administer many systems remotely? namely, send the same command to all the stations and then get a log of the results of each station.

5. Aside from their home directory, the students also have another home directory on a Unix server.
I would like to have it mounted automatically so each student account would mount his own home directory on the Unix server.
So I explored the option of sshfs, but found that in order for the students to not have to type in their password each time, I would have to implement password less ssh to the Unix server (public key exchange), which is a security issue.
I am satisfied with the way gnome vfs mounts the drives, since it asks for the password only when someone double clicks the icon, and the student can also save his password.
My problem is that I have only found a way to manually do it by using "connect to server".
How do I set this up automatically for all users?


Thanks a lot.
Dave.

---

### Post by DC@DR on 2007-07-25
For administering the stations, I know that Canonical is now offering Landspace ([http://www.ubuntu.com/news/landscape-system-management-tool](http://www.ubuntu.com/news/landscape-system-management-tool)), which would be available to Ubuntu subscribers. So I think for your situation, the best way is to subscribe for Ubuntu commercial support, they would help to assure everything handled properly and promptly. I'm sure Ubuntu support is much cheaper than Redhat's, and plus, this way you could support Ubuntu/Canonical to make the project better. Just a thought :-)

---

### Post by Dave_Man on 2007-07-25
> **DC@DR said:**
> For administering the stations, I know that Canonical is now offering Landspace ([http://www.ubuntu.com/news/landscape-system-management-tool](http://www.ubuntu.com/news/landscape-system-management-tool)), which would be available to Ubuntu subscribers. So I think for your situation, the best way is to subscribe for Ubuntu commercial support, they would help to assure everything handled properly and promptly. I'm sure Ubuntu support is much cheaper than Redhat's, and plus, this way you could support Ubuntu/Canonical to make the project better. Just a thought :-)

Hi, 

We have though about this route but we don't want to take it just yet..
If all else fails, we might go that way...

Thanks.
Dave.

---

### Post by Dave_Man on 2007-07-26
Sorry to bump my own thread but my questions are still unanswered

---

