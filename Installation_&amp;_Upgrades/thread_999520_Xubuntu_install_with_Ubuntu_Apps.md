---
title: "Xubuntu install with Ubuntu Apps"
date: 2008-12-01
forum: Installation &amp; Upgrades
---

### Post by Mr.Macdonald on 2008-12-01
I used the have Ubuntu (the real one), but I installed xubuntu-desktop (Ubuntu still, I know). I still have gnome apps for ubuntu, how do I move to a complete Xubuntu install without removing important stuff

Should I do this
```
sudo apt-get autoremove gnome*
```
I would uninstall many things like network manager

---

### Post by snowpine on 2008-12-01
Hi Mr. M, is this what you're looking for?

[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)

---

### Post by lisati on 2008-12-02
I'd recommend caution with the "apt-get autoremove gnome*" approcah. I have Xubuntu on one of my laptops (too lazy & stingy to upgrade its RAM) - if memory serves correctly, some of the applications require parts of Gnome (perhaps some other forum user can help shed some light on this.....)

My preference would be to backup important data, then doing a clean install. That way there would be less risk of messing up dependencies, deleting stuff that's really needed, and keeping stuff that's not really necessary.
If you go for the "apt-get autoremove" approach, you might find it advisable to (re)install the xubuntu desktop immediately.

EDIT: I think snowpine's suggestion has some merit. And doing a backup of important data is still a good idea, "just in case" - muck-ups have a sneaky habit of sneaking in when you're least expecting them.

---

### Post by Mr.Macdonald on 2008-12-02
I did the [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce) but I just still saw gnome in dpkg -l and I was worried!

---

### Post by OrangeCrate on 2008-12-02
> **Mr.Macdonald said:**
> I did the [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce) but I just still saw gnome in dpkg -l and I was worried!

I've personally used that tutorial, and didn't have any problems at all. Your mileage **might** vary, but I would doubt it. That's Asiyu's site, and I'm pretty comfortable with anything he has there.

---

