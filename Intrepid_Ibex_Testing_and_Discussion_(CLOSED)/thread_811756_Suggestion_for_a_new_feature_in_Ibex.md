---
title: "Suggestion for a new feature in Ibex"
date: 2008-05-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by C.A.T.S. CEO on 2008-05-29
I find that the new changing update icon (star for non-security updates and red down arrow for security updates) is very useful, but I find that it is still lacking.  I run a gaming server on my Ubuntu box and I'm the person who likes a up-to-date system all the time, so I usually install new updates immediately.  What I find very annoying is when update manager doesn't tell me that I need to reboot *before* an update.  I'm now stuck not installing updates in fear that I may have to reboot after them and anger the players on my server.

Can the update-manger devs please add a new icon (like the red down arrow) that signifies an update that requires a reboot?

Heres an example from my OS X box's software update, showing the icon that signifies that a reboot is required:

[IMG]http://i92.photobucket.com/albums/l25/CATSCEO/update.png[/IMG]

Thanks a lot for any help.  I appreciate what you guys do. :)

---

### Post by xens on 2008-05-29
Great idea! I think you should create a new "idea" in ubuntu brainstorm

[http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)

---

### Post by Martje_001 on 2008-05-29
+1 from me!

---

### Post by ccw on 2008-05-29
Or report it as a "bug" here:

[https://bugs.launchpad.net/ubuntu/+source/update-manager](https://bugs.launchpad.net/ubuntu/+source/update-manager)

---

### Post by Gina on 2008-05-29
+1 from me too :)

---

### Post by Sockerdrickan on 2008-05-29
That'd be great but it might be next to impossible depending on how update manager currently senses a required reboot

---

### Post by talkingwires on 2008-05-29
This sounds like a great idea! Perhaps not the icon itself, unless it's a badge in the corner, but certainly a notice in update manager itself. +1

---

### Post by plun on 2008-05-29
> **C.A.T.S. CEO said:**
>   I run a gaming server on my Ubuntu box and I'm the person who likes a up-to-date system all the time, so I usually install new updates immediately.  What I find very annoying is when update manager doesn't tell me that I need to reboot *before* an update.  I'm now stuck not installing updates in fear that I may have to reboot after them and anger the players on my server.



Well, the majority of servers is without a GUI and the admin talks with this server with SSH from another PC.

The majority of upgrades is no problem and all "pros" checks Ubuntu USN
and also has a RSS feed from USN

[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)


For a client this is not a problem.

So I cannot see any reason to have Apples solution... but...  after the **openssh "debacle"** its maybe important to wake up an "sleepy" admin. :)

---

### Post by Gina on 2008-05-29
You don't have to restart straight away, of course, if you're in the middle of something.  I leave it if I'm playing music or a video etc.

---

### Post by talkingwires on 2008-05-29
> **plun said:**
> after the **openssh "debacle"** its maybe important to wake up an "sleepy" admin. :)I've been AFK for three weeks. What was the "openssh debacle"?

---

### Post by Sockerdrickan on 2008-05-29
> **Gina said:**
> You don't have to restart straight away, of course, if you're in the middle of something.  I leave it if I'm playing music or a video etc.
he is running a game server, uptime is crucial. :popcorn:

---

### Post by C.A.T.S. CEO on 2008-05-29
> **xens said:**
> Great idea! I think you should create a new "idea" in ubuntu brainstorm

[http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)

Done!  URL: [http://brainstorm.ubuntu.com/idea/9240/](http://brainstorm.ubuntu.com/idea/9240/)

> **Gina said:**
> You don't have to restart straight away, of course, if you're in the middle of something.  I leave it if I'm playing music or a video etc.

As Tux0r said, uptime is critical.  I hate having to reboot that machine all the time (I'm one of those freaks that loves a long uptime too).

Thanks for all the support and replies everyone!

---

### Post by edd07 on 2008-05-29
I think this is a good idea, but until this gets implemented (if it does) you could stay away from the kernel updates, which, in my experience, are the ones that ask to reboot, and install them only when you are ready to reboot the server.

Hope this helps

---

### Post by olskar on 2008-05-29
Perhaps I misunderstand something..you want these icons on packages that require reboot so you can select not to upgrade those packages and not have to reboot?

Isnt the effect of simply upgrading and not rebooting the same?
All updates that can be installed without reboot will be installed and stuff like kernelupdates will be installed on next reboot (which can be several weeks from the time you upgrade?)

---

### Post by igorgue on 2008-05-29
Fedora used to do that too... I don't know now that they use package kit.

---

### Post by C.A.T.S. CEO on 2008-05-29
> **olskar said:**
> Perhaps I misunderstand something..you want these icons on packages that require reboot so you can select not to upgrade those packages and not have to reboot?

Isnt the effect of simply upgrading and not rebooting the same?
All updates that can be installed without reboot will be installed and stuff like kernelupdates will be installed on next reboot (which can be several weeks from the time you upgrade?)

Not exactly, I want to know if any updates require a reboot before I update.  If they do, then I'll hold off updating until a later time when its more convenient for me.

---

### Post by xens on 2008-05-29
voted :-)

I created my first idea today too: [http://brainstorm.ubuntu.com/idea/9236/](http://brainstorm.ubuntu.com/idea/9236/)

This site is great!

---

### Post by neurostu on 2008-05-29
So this feature exists in RHEL 5 (possibly other distrobutions?).  So it really wouldn't be that difficult for the team to include it. It might be simply a matter of implementing already existing code.

---

### Post by autocrosser on 2008-05-30
I voted up your idea. I too have run OSX in the past & think it would be a good idea for the new crowd.

---

