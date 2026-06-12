---
title: "Can't boot into Recovery Mode in Karmic"
date: 2010-03-29
forum: Installation &amp; Upgrades
---

### Post by Izobalax on 2010-03-29
OK, I'm trying to fix a fresh Karmic install for a friend of mine. In short, she's screwed up user permissions so she can't sudo anymore. I need to get into Recovery mode so I can add her back to the admin group. Apparently, the way into recovery mode is by holding down the shift key when GRUB is booting up.

However, all this seems to be doing is booting up as normal, ignoring my Shift key. 

What am I doing wrong?

/izo\

---

### Post by zvacet on 2010-03-29
Do you see grub while booting?If you do select recovery mode with arrow key and hit enter.

---

### Post by Izobalax on 2010-03-29
> **zvacet said:**
> Do you see grub while booting?If you do select recovery mode with arrow key and hit enter.
No, it says GRUB is loading, then I get the Ubuntu logo. No menu is displayed to me. 

/izo\

---

### Post by sisco311 on 2010-03-29
> **Izobalax said:**
> OK, I'm trying to fix a fresh Karmic install for a friend of mine. In short, she's screwed up user permissions so she can't sudo anymore. I need to get into Recovery mode so I can add her back to the admin group. Apparently, the way into recovery mode is by holding down the shift key when GRUB is booting up.

However, all this seems to be doing is booting up as normal, ignoring my Shift key. 

What am I doing wrong?

/izo\

Nothing, the shift key should work.

Boot a Live CD or USB, mount the root partition & edit the [/mount/point]/etc/group file to add the user to the admin group:
```

...
admin:x:115:**username**
...
```

---

### Post by Izobalax on 2010-03-29
> **sisco311 said:**
> Nothing, the shift key should work.

Boot a Live CD or USB, mount the root partition & edit the [/mount/point]/etc/group file to add the user to the admin group:
```

...
admin:x:115:**username**
...
```

I see, no the Shift key isn't working for me. Looks like I'll have to come back with a Live CD. 

Thanks for the help!

/izo\

---

### Post by sisco311 on 2010-03-29
> **Izobalax said:**
> I see, no the Shift key isn't working for me. 

If it's an upgrade from Jaunty then it still uses grub legacy. Did you try to press ESC?

---

### Post by Izobalax on 2010-03-29
> **sisco311 said:**
> If it's an upgrade from Jaunty then it still uses grub legacy. Did you try to press ESC?


Nope, as said above it's a fresh Karmic install. I did try the ESC key, but that just checked the HDD and carried on booting as normal. 

/izo\

---

