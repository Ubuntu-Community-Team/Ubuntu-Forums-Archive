---
title: "Screen Problems After Jun 17 Update"
date: 2008-06-17
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by adamorjames on 2008-06-17
So, I updated and upgraded today. I now have the new kernel 2.6.26-1 but I'm getting screen resolution problems and such. Every time I restart and load Ubuntu it tells me to configure (has the X cursor and such I think). My screen resolution goes up to 1680x1050 and that is what I keep it on but it is now 800x600 and the GUI way to change it does nothing. I looked at my xorg.conf file and it seems to be alright. I will attach my xorg.conf file. Just wondering if anyone else is getting a problem like this after the updates and if there is a new config file somewhere or something I missed when looking at my config file. It probably is just a simple problem and is already known and is going to be fixed but if not I guess I will submit a bug report. So, just let me know what you all think.

---

### Post by psyke83 on 2008-06-17
> **adamorjames said:**
> So, I updated and upgraded today. I now have the new kernel 2.6.26-1 but I'm getting screen resolution problems and such. Every time I restart and load Ubuntu it tells me to configure (has the X cursor and such I think). My screen resolution goes up to 1680x1050 and that is what I keep it on but it is now 800x600 and the GUI way to change it does nothing. I looked at my xorg.conf file and it seems to be alright. I will attach my xorg.conf file. Just wondering if anyone else is getting a problem like this after the updates and if there is a new config file somewhere or something I missed when looking at my config file. It probably is just a simple problem and is already known and is going to be fixed but if not I guess I will submit a bug report. So, just let me know what you all think.

No, your configuration isn't alright. If you have an NVIDIA or ATI card, you shouldn't use kernel 2.6.26 yet as the restricted drivers aren't ready. Unless you know how to configure and use the open source drivers, you should stick to the old kernel. Your configuration is using the generic VESA driver (limited choice of resolution, no acceleration), so that will need to be fixed when you go back to the old kernel.

You definitely should read 23meg's sticky threads. The Intrepid versions aren't ready, but you can read the Hardy versions linked to the first post in this thread: [http://ubuntuforums.org/showthread.php?t=826197](http://ubuntuforums.org/showthread.php?t=826197)

---

### Post by adamorjames on 2008-06-17
Ok, switching to the old kernel works. A simple problem just like I thought.

---

### Post by scradock on 2008-06-17
> **psyke83 said:**
> No, your configuration isn't alright. If you have an NVIDIA or ATI card, you shouldn't use kernel 2.6.26 yet as the restricted drivers aren't ready. Unless you know how to configure and use the open source drivers, you should stick to the old kernel. Your configuration is using the generic VESA driver (limited choice of resolution, no acceleration), so that will need to be fixed when you go back to the old kernel.

You definitely should read 23meg's sticky threads. The Intrepid versions aren't ready, but you can read the Hardy versions linked to the first post in this thread: [http://ubuntuforums.org/showthread.php?t=826197](http://ubuntuforums.org/showthread.php?t=826197)
Will the 2.6.26 kernel work with the OS -ati driver? That was updated today, along with the kernel (Jun 17th). My screen is working fine after the update,except that the login text-box has an enormous font size. Not a great problem, as one usually types in user name and password blind anyway, but it's a glitch.

Apart from that, it was an amazingly smooth kernel upgrade. Well done, everyone concerned!

---

### Post by adamorjames on 2008-06-17
scradock, the font problem may be a DPI issue. One way to fix it if so, that has worked for me is:

sudo gedit /etc/gdm/gdm.conf
Search for, &#8220;command=/usr/bin/X -br -audit 0&#8221;
Add &#8220; -dpi 96&#8221; to each line that has only what is specified above.

There is a more GUI way but I had to do it this way because I had a problem with it crashing in Hardy. Not sure if the more GUI way still crashes.

---

### Post by psyke83 on 2008-06-17
> **scradock said:**
> Will the 2.6.26 kernel work with the OS -ati driver? That was updated today, along with the kernel (Jun 17th). My screen is working fine after the update,except that the login text-box has an enormous font size. Not a great problem, as one usually types in user name and password blind anyway, but it's a glitch.

Apart from that, it was an amazingly smooth kernel upgrade. Well done, everyone concerned!

Yes, the OS drivers should continue work unless there's a kernel bug (not likely, but still possible). As for the font issue, perhaps it's due to an update not related to the kernel? You can configure the DPI in System/Preferences/Appearance/Fonts/Details... (though I think it's only a per-user setting, not for GDM).

---

### Post by scradock on 2008-06-18
Thanks adamorjames - I'll try that suggestion.

psyke83 - yes, the dpi setting in Appearance|Fonts|Details is general, and it is as I left it. There must be something else going on. I'll see what adamorjames' idea does.

---

### Post by Raptor45 on 2008-06-18
GDM DPI is separate from the system wide one. Don't ask me why. You can probably do it adamorjames's way, but to do it via the GUI:

Go to System>Admin>Login Window.
Hit the Security tab, and hit configure X server.
Finally add -dpi 96 to the Command.

---

### Post by scradock on 2008-06-18
> **Raptor45 said:**
> GDM DPI is separate from the system wide one. Don't ask me why. You can probably do it adamorjames's way, but to do it via the GUI:

Go to System>Admin>Login Window.
Hit the Security tab, and hit configure X server.
Finally add -dpi 96 to the Command.
Thanks for the suggestion. I did it by editing the gdm.conf file, as adamorjames suggested, and it worked as he said.

I did try poking around in the Login Window manager, but not knowing what I needed to add to the command line I found little joy there. I was somewhat mystified by the check-box to "allow users to change font", with no indication as to how and where they would actually be able to do it.

Incidentally, when I had the huge fonts in the login text box, I found that the Options menu (though not the word Options in the bottom left of the login window) also used huge fonts, which made it interesting trying to restart after finding that a Ctl-Alt-Backspace restart-X didn't pick up the changes to gdm.conf.

Behavior is now back to normal, but it would be good to find out where and why the dpi changed from the default value.

---

