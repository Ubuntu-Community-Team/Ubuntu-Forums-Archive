---
title: "Cannot create terminal window"
date: 2008-05-25
forum: Installation &amp; Upgrades
---

### Post by Ralph Boland on 2008-05-25
I was experimenting with profiles of terminal windows created by
Applications/accessories/terminal and have created the situation 
that when I create a new terminal it flashes and then closes.
Thus I cannot create a new terminal.  This is a major pain.
When you have finished laughing can someone suggest how to fix this.
I can still login using ctrl-alt-F1. But then I need to fix a file
somewhere to clean up this mess.  
But where?

Or if someone can send me a replacement default terminal profile 
or tell me where to find one and where to put it that would be great.

Thanks

Ralph Boland

---

### Post by iaculallad on 2008-05-25
> **Ralph Boland said:**
> I was experimenting with profiles of terminal windows created by
Applications/accessories/terminal and have created the situation 
that when I create a new terminal it flashes and then closes.
Thus I cannot create a new terminal.  This is a major pain.
When you have finished laughing can someone suggest how to fix this.
I can still login using ctrl-alt-F1. But then I need to fix a file
somewhere to clean up this mess.  
But where?

Or if someone can send me a replacement default terminal profile 
or tell me where to find one and where to put it that would be great.

Thanks

Ralph Boland

You could try this option:

Hit Ctrl+Alt+F1 to go to terminal then issue the command

**rm -rf .gnome .gnome2 .gconf .gconfd .metacity**

to reset all your gnome settings (Fresh as new).

---

### Post by Ralph Boland on 2008-05-25
I tried the command you proposed and it ran without problem.
But unfortunately my problem did not go away.  Neither
logging out or rebooting helped either.

Ralph Boland

---

### Post by Ralph Boland on 2008-05-25
I found a solution to my problem thanks to the gnome developers.
Under .gconf/apps/*terminal in my home directory is a direcory called Profiles.
I just removed it and logged out.  On login the problem was gone.

Ralph

---

