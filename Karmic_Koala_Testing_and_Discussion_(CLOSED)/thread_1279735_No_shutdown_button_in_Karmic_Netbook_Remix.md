---
title: "No shutdown button in Karmic Netbook Remix"
date: 2009-10-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by llazarte on 2009-10-01
Upgrading my eee PC to Karmic Alpha, Netbook Remix, at some point I lost the shutdown button.

I am logging out, shutting down and rebooting using CTL+ALT+DEL. That gives me the logout menu.

Any suggestion on how to reinstall this button?

Also, UNRs initial desktop used to have a left and a right pannel. Now I have just the left pannel. Is this the standard now, or I have lost something?

Thanks!

---

### Post by dino99 on 2009-10-01
you can add it on the panel by right click & choose Add to Panel :"shut down" button.
i'm using it.

---

### Post by victor9098 on 2009-10-01
Hi, 

I do not know about the shutdown button, your name should be in the top right corner. Clicking that should give you options. Pressing the power button once, briefly will also bring up your shutdown options.

If you go into 'settings' then 'startup applications', check to see if 'Indicator Applet' is still listed. If not just press the 'add' button to the right and fill in the following:

Name = Indicator applet
Command = sh -c "sleep 60 && python /usr/share/gnome-panel/add-indicator-applet.py"

Then hit 'save'.

Yes, this is the new look to UNR. Just a left had bar and no right hand bar.

Hope that helps!

---

### Post by TunaCanTommy on 2009-10-01
Same issue with me on my Asus EeePC 701/4G.  Lost the "Indicator applet" at some point and like the OP I'm using CNTL+ALT+DEL to access the "Shut Down/Restart/Log-out" menu.

The "indicator-applet" is in my "Startup Applications Preferences" and the box is checked.  I looked at the parameters and they are exactly as Victor9098 quoted.  Right clicking on the bar and add-panel doesn't seem to be available.  All I get when I click on "Preferences" is a check-box that says "Show windows from all workspaces". There is an option to "Remove from Panel".

Also I can't seem to get the weather part of the "Date/Time" applet to work.

---

### Post by llazarte on 2009-10-01
**[COLOR=Blue]Thanks[/COLOR]**, **victor9098**, **dino99** and **TunaCanTommy**.

Before posting to this forum, I tried the "right click" solution, which I found in other posts, but I only got the "Remove" option, no "add" :(

After reading your messages, I checked by right cliking on several parts of the top bar, until I suddenly got the "add" option, and there is was, the missing shutdown button. I got it! Is is working now. Unfortunately, I tried to repeat this process, but I coud not get the "add" option (same as **TunaCanTommy**).

> **TunaCanTommy said:**
> Same issue with me on my Asus EeePC 701/4G.  Lost the "Indicator applet" at some point and like the OP I'm using CNTL+ALT+DEL to access the "Shut Down/Restart/Log-out" menu.

The "indicator-applet" is in my "Startup Applications Preferences" and the box is checked.  I looked at the parameters and they are exactly as Victor9098 quoted.  Right clicking on the bar and add-panel doesn't seem to be available.  All I get when I click on "Preferences" is a check-box that says "Show windows from all workspaces". There is an option to "Remove from Panel".

But if I go to _System -> Startup .._., there it is, the option to check (or uncheck) "_Indicator applet_" (funny name, no?), and I can repeat this behaviour :)

---

### Post by TunaCanTommy on 2009-10-01
Ah Hah . . . I too have now found it.  I was encouraged by  Leonardo's last  post.  So I started right-clicking all over the bar.  But it didn't work until I moved the "Date/Time" out of the way.

After I did that I was able to right-click and get the "add" option.

All is well . . . thank you Leonardo ! (And the other posters too.)

I think this thread should be marked "Solved".

---

### Post by Napu5 on 2009-10-24
I had the same problem. Is shutdown removed from the new version of netbook-launcher? Shouldn't we file a bug for Karmic about this? Is there a way to get the folders and shutdown button back in the netbook-launcher?

---

### Post by Snapphane on 2009-10-24
I have used my hard-ware button. Set the system to "ask what to do", press it and you get the menu :D

---

### Post by llazarte on 2009-10-25
> **Napu5 said:**
> I had the same problem. Is shutdown removed from the new version of netbook-launcher? Shouldn't we file a bug for Karmic about this? Is there a way to get the folders and shutdown button back in the netbook-launcher?

I think this problem appeared while Karmic was in some early alpha. I have upgraded other machines after that, without losing the shutdown button.

---

