---
title: "is it possible to update to 9.10 via.."
date: 2009-06-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by qjmoss on 2009-06-25
the terminal, I lost my usb drive, and I don't have any cds.. and i heard that 9.10 is supporting Intel a lot better than 9.04. Is there anyway I can update?

---

### Post by hyperdude111 on 2009-06-25
I dont recommend as 9.10 is an alpha and may cause problems but...

Press Alt-F2

then type 
> update manager -d

At the top of the windows click the distrobution upgrade.

---

### Post by qjmoss on 2009-06-25
I had no luck, nothing opened.

---

### Post by blackxored on 2009-06-25
```
sudo aptitude update
update-manager -c
update-manager -d
```

or manually change sources.list to karmic and then update and full-upgrade.

---

### Post by Thingymebob on 2009-06-25
because the command should be
```
update-manager -d
```
small typo I think

---

### Post by qjmoss on 2009-06-25
okay guys i think i got it goin =)

---

### Post by qjmoss on 2009-06-26
Okay, now what I ran 

```
sudo aptitude update
update-manager -c
update-manager -d
```

It updated me to 9.10. But, I'm still using Kubuntu, Is there a way I can get a fresh install of Ubuntu 9.10. I'm not a fan of kde and would like to get back to gnome... and like I said before, I'm out of cd's and no flash drive right now.

---

### Post by psyke83 on 2009-06-26
> **qjmoss said:**
> the terminal, I lost my usb drive, and I don't have any cds.. and i heard that 9.10 is supporting Intel a lot better than 9.04. Is there anyway I can update?

Don't upgrade merely to have better graphics drivers - you're replacing one set of issues (poor 3D performance) for another (an alpha-quality system that's not yet intended for production use).

Take a look at my Intel guide first; doing the equivalent of the Bleeding-Edge configuration will give you a good idea of the state of the Intel driver in Karmic. At least it's somewhat easy to revert changes if the updated drivers and kernel cause issues for your chipset (which is quite possible).

---

### Post by woodbj on 2009-06-26
```
sudo apt-get install ubuntu-desktop
```

---

### Post by qjmoss on 2009-06-26
for some reason i don't think that's going to get the job done..


and about following the bleeding edge setup. I've visited that before, and I followed all the directions, but i had no luck, i understand that 9.10 is super beta, but i decided to give it a shot because of supported graphics.
=/

just kinda in a mess.

---

### Post by psyke83 on 2009-06-26
> **qjmoss said:**
> for some reason i don't think that's going to get the job done..


and about following the bleeding edge setup. I've visited that before, and I followed all the directions, but i had no luck, i understand that 9.10 is super beta, but i decided to give it a shot because of supported graphics.
=/

just kinda in a mess.

Then I can guarantee that Karmic won't be any better either. The xorg-edgers packages contains *newer* drivers than Karmic currently uses, so you won't have a better experience (at least not at the moment).

Edit: too late, it seems you upgraded. You cannot downgrade distributions without reinstalling.

---

