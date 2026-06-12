---
title: "New to ubuntu and have a problem. Any help is good."
date: 2010-02-19
forum: Installation &amp; Upgrades
---

### Post by Diesel317 on 2010-02-19
[SIZE=2]Hello, 

I just joined the forum. I've had unbuntu netbook remix v. 9.04 on my netbook for about 7 months now. I really like it, its nice and speedy and i like how ubuntu works. And this problem I'm posting here is the first real problem I've had. 

Alright, I was trying to install Limewire and I got this error:[/SIZE]

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=147587&stc=1&d=1266605928[/IMG]

[SIZE=2]So I go open up the package manager and close it, just to make sure all is well, and I do the same with the update manager and then went back and got the same thing. 

So, I say, well maybe theres a new version of ubuntu that I could install. So I go onling, check out the site, and there's a new version. I read I can update through the update manager, cool. So I open update manager again. And when I go to "Install Updates" I get this error:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=147588&stc=1&d=1266605928[/IMG]


I don't know what to make of it really. I don't know a whole lot about programming and what not. Coming from a windows background too, so maybe thats the problem? lol

So maybe someone with some more knowledge than I could shed some light on the subject. As I don't know what I'm doing. Thanks in advance for any help. Any information you need to help me, just let me know. But I may need to know how to get that info if it is some system settings or something.

Thanks again,

Diesel.
[/SIZE]

---

### Post by darkod on 2010-02-19
Shut down, to make sure everything closes. Restart. Wait for a while, Update Manager will probably appear letting you know it found updates. Just click Close to close it, don't try to install any updates.

Then in terminal (Applications-Accessories) try running that command it suggested:

sudo dpkg --configure -a

If it doesn't report any errors, reboot again just in case. See whether you can install the updates after that. If you are considering upgrade to 9.10, I would first do the updates for 9.04 fully. Also, you don't really have to upgrade to 9.10 right now. In late April the next LTS 10.04 is released (Long Term Supported). You might consider upgrading then or doing a clean install which is always better than an upgrade.

---

