---
title: "New Bug"
date: 2009-11-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by RedSingularity on 2009-11-21
I would like to confirm what appears to be a bug.  When i start Nvidia settings as super user i run into this problem.  To replicate,

1)  sudo nvidia-settings
2)  X server Display Configuration
3)  Change anything in there and click the "Save to x Configuration File"
4)  You will see an error that pops up and says, "Failed to parse existing X config file '/etc/X11/xorg.conf'!"

Let me know if anyone else has this problem so i can report a bug.  Thanks.

---

### Post by RedSingularity on 2009-11-21
Nevermind......found the solution.  Just run "sudo nvidia-xconfig".  Then the above will work.

---

### Post by cariboo on 2009-11-21
+1, file a bug stating that nvidia-settings should be set up to run as root by default.

---

### Post by LKjell on 2009-11-21
> **cariboo907 said:**
> +1, file a bug stating that nvidia-settings should be set up to run as root by default.
I would not like that since that means I have to enter a password to just change the screen resolution. A better idea is to ask for permission when it going to write to xorg.conf

---

### Post by PaulInBHC on 2009-11-21
I just had a look at launchpad. The whole thing is over my head.

I made a launcher on my desktop. The icon is in the upper left corner. When I mount a drive, the drive icon is superimposed over my launcher icon. Is that something to report?

---

### Post by sdowney717 on 2009-11-21
its been like that for at least a year.
the other buggy thing is if xorg.conf does not exist or is an empty file then it throws an error you cant even see the preview and closes.
I am so disgusted with it, what i alwayd do is view preview, select all copy and then open up gksu gedit and make the change manually. 

Also that merge option destroys your config makes a total mess of the file.

 It is irritating stuff like this that turns people off.

---

### Post by RedSingularity on 2009-11-22
I think i am loosing my mind :/

Where is the Report Bug button on launchpad?

---

### Post by RedSingularity on 2009-11-22
Nevermind.....found it.  Bug report made.  Thanks guys.

---

### Post by phenest on 2009-11-22
> **RedSingularity said:**
> Nevermind.....found it.  Bug report made.  Thanks guys.

A link please.

---

