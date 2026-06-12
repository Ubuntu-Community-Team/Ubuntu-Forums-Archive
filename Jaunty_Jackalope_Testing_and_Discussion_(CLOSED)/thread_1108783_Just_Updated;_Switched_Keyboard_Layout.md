---
title: "Just Updated; Switched Keyboard Layout?"
date: 2009-03-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by chris062689 on 2009-03-28
I just updated my Jaunty, and after I rebooted and attempted to login, it appears I was typing in Islamic characters?
I can't even login from the terminal.
Is there a way to change it back to default (USA) Keyboard through a Live CD?

---

### Post by chris062689 on 2009-03-28
Found a solution.
```

sudo gedit /etc/default/console-setup 

```
Find: XKBLAYOUT="___" and put "us" or whatever you want your keyboard language to be.

---

### Post by billyevil on 2009-03-28
I just updated and the same thing happened, only I couldn't get root level priveledges to change it using what you did above since for some reason my password doesn't work in islamic. Instead, to fix it, I went to system--preferences--keyboard and in there under Layouts I added the united states layout and deleted the islamic one, then clicked apply system-wide (though I don't know if this last little bit helped, but it was more of a help for me) I don't know why this happened but it was a little scary not being able to access anything.

---

### Post by seppl82 on 2009-03-28
Fascinating,

the same thing happend to me.
After reboot my keyboard switched to afganistan layout...

Okay, i'm not alone :-)

---

### Post by seppl82 on 2009-03-28
But one issue isn't solved with that change.
If i leave the X-Server and go to the console with ctrl+alt+del the keyboard layout is wront too i think i only got diamonds for my keyboard input.

Any idea how to solve this?

Kind Regards
Seppl

---

### Post by chris062689 on 2009-03-28
> **seppl82 said:**
> But one issue isn't solved with that change.
If i leave the X-Server and go to the console with ctrl+alt+del the keyboard layout is wront too i think i only got diamonds for my keyboard input.

Any idea how to solve this?

Kind Regards
Seppl

Yep.
Simply boot into a Jaunty Live CD, and run this:
```

sudo gedit /media/*YOUR PARTITION*/etc/default/console-setup
```

(Remember to mount your / directory first, and then change the path to the mounted directory]
Find: XKBLAYOUT="___" and put "us" or whatever you want your keyboard language to be. 

May have not explained it very well, so if anyone can clarify, that would be great :)


Then I rebooted, and I was able to login to my Ubuntu box, then I simply went in and changed the keyboard layout through GNOME.

It scared me for a minute, I wasn't able to login after the updates, some kind fellow on the IRC helped me figure out this solution!  Can't remember his name though...

---

