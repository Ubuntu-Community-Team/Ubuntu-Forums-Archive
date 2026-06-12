---
title: "Linux Project Help"
date: 2006-08-15
forum: Installation &amp; Upgrades
---

### Post by Necro-File on 2006-08-15
After struggling with trying to set up what I want on my xbox using xubuntu to no effect, I decided to just do away with windows on my laptop and just run Ubuntu linux on it because all I do on my laptop can be done in linux, and so does the project I am working on.

At first, my only objective was to get an SSH server going so I could access a terminal IRC program (BitchX being the one of choice) so I can use IRC from my phone (Danger's Hiptop 3 (aka the T-Mobile Sidekick3)). This I have acomplished, thanks to Ubuntu ^__^

However, after talking to a friend and trying to coax him and a few others to try expanding their PC knowledge, I thought I should try and create sub accounts that have a small (10mb to a few gb depending on a few things) webspace/ftp/whatever as well as SSH access to specific programs/files (like the web/ftp server and IRC). I have a few questions though before I begin my quest.

1. I assume that all the information that anyone can access remotely would be the same as any other user, however, I want to restrict access to these other accounts to their home folder only so they can not look through system files, other user's stuff, or run programs they do not have access to. Being from Windows, I have no idea how to do this in linux.

1a. Also, pertaining to the users home folders, can I set where these are created? My laptop only has a 60GB hard drive, however I have a 250gb external USB drive that, if possible, I would like to create the users personal space on this, thus giving them a larger quota of storage. If I can, what would I do to acomplish this?

2. As I would have access allowed from outside my network, even though I have security measures in place already, it would still be comforting to know who is logged in, who has logged in previously, etc. Where can I find a log of activities, or, which would be better, some sort of active monitor that shows what is going on (simplistically, of course. I don't mean to have something that tells me if the user is typing/picking their nose).

3. Would it be possible to have accounts automatically created with a webform? No need to explain how if you can, this is something I may decide to try sometime in the future if everything works out.

Thanks in advance for any information you can give me ^__^

---

### Post by tappad on 2006-08-15
I am very much interested in doing the same thing as you are planning to do. 

As for number 1. I belive that by default new users are not able to use "sudo". This depends on wich group they belong to. However i dont know if you need to set permissions on everything to disallow new users to see whats on your harddrive. I think that the best way would be to create a special group for this purpose.

1.a - You can set different homepath's when a user is created.
I suggest that you look around in "System->Administration->Users and groups".

2. I think that you should be able to run diffrent batchfiles as users log on and off. I dont know how, but since this is a major feature in Network administration in different OS's there must be one here to ;)

I hope this helps to point you in the right direction and i would be very greatful if you would post any progress you make in this thread. As said before, i will be looking into doing the same thing in a couple weeks.

Regards
David Johansson

---

### Post by tappad on 2006-08-19
You should check out ispconfig btw, might be something for you.

---

