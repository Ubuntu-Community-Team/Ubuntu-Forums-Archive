---
title: "Upgrade 17.04 to 18.04 + custom kernel + passthrough"
date: 2018-04-28
forum: Installation &amp; Upgrades
---

### Post by jayz99 on 2018-04-28
Hi All,

I've been holding off upgrading to 17.10 because of the upcoming 18.04 AND the fact that Wayland was the default on 17.10. My 17.04 has been out of support for a while so keen to get back on track. I checked out the upgrade notes for the new LTS release and noticed that:

1. It only covers upgrading from 17.10 or 16.04. What about upgrading from previous stable releases? Do I HAVE TO upgrade to 17.10 before I upgrade to 18.04? I'm particularly concerned about Wayland and its impact on my Gnome environment.
2. I'm running on a 4.15.5 kernel - the documentation does not mention the specifics save for the fact that the new LTS uses 4.15. What's going to happen? Does the kernel stay the same if 4.15.X? Would the new LTS override it with its own kernel? 
3. I'm running a VM with GPU passthrough - that's the primary concern here as these kind of things are fragile. What's your experience in terms of upgrading such installations?

Any other pointers /comments / etc. would be most welcome as this is the first Ubuntu upgrade I'll be doing!

Thanks!
Janusz

---

### Post by Frogs Hair on 2018-04-28
> [COLOR=#000000]It only covers upgrading from 17.10 or 16.04. What about upgrading from previous stable releases? Do I HAVE TO upgrade to 17.10 before I upgrade to 18.04? I'm particularly concerned about Wayland and its impact on my Gnome environment.[/COLOR]

Upgrades go in order, so 17.10 would be first. Xorg is default on 18.04 though Wayland is available as well. Linux 4.15.20 is default on 18.04. 

```
  uname -a
Linux ubuntu 4.15.0-20-generic #21-Ubuntu SMP Tue Apr 24 06:16:15 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux



```

---

### Post by jayz99 on 2018-04-28
'First' - i.e. every previous release must wait until someone builds an 'upgrade path'? If I'm getting this right, 17.10 users need to wait a few days and then in a few more days (or weeks) someone will announce that they've now developed a 17.04->18.04 upgrade capability and then I can upgrade?

Thanks for the kernel info - so 18.04 REPLACES whatever kernel it finds? For my purposes, anything above what I've got now is alright so no problems there. Just curious about the approach.

---

### Post by Frogs Hair on 2018-04-28
> [COLOR=#000000]18.04 REPLACES whatever kernel it finds? [/COLOR] Your kernel would probably not be removed until the cleanup phase in the upgrade process. There is an option to remove unneeded or obsolete packages. That may not apply if you manually added a newer kernel.

17.04 being end of life may not offer an upgrade option to 17.10. Check the new release setting in software and updates. If there is no upgrade option you would have to add the old repositories to the sources list. I would consider a backup and clean installation of 18.04 just due to the time involved.

---

### Post by jayz99 on 2018-04-28
Ugh... That last bit about reinstall is what I was worried about. So you honestly think upgrading from a mere two version behind is best done via clean install if time is considered? That's a big screw up on the Ubuntu side if you ask me. I just upgraded my FreeBSD server from a release aged 2 years to the most recent one and it was a piece of cake. That's clearly one reason why no server of mine will touch Ubuntu. Right... moan over.

How do upgrade without a clean install in the most time efficient manner? How long do you think it might take? If I HAVE to upgrade to 17.10 do I need to use Wayland? That would suck so bad that I think we can both agree a clean install would be preferred. The X - Wayland - X decision is a bit of a joke too.

---

### Post by deadflowr on 2018-04-28
> If I HAVE to upgrade to 17.10 do I need to use Wayland? 
No.
it'll be installed, but you can log into Xorg .And have never deal with wayland.
And some gpu's won't even let you use wayland, depending on the driver and settings and all:
[https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1724583]("https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1724583")

---

