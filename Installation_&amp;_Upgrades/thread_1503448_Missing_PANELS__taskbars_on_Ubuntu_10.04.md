---
title: "Missing PANELS / taskbars on Ubuntu 10.04?"
date: 2010-06-06
forum: Installation &amp; Upgrades
---

### Post by Kharlo on 2010-06-06
It looks some user are having the same problem.

After log in, the  cursor its ok, so its not freeze but there is no taskbar:
[IMG]http://img13.imageshack.us/img13/7681/xxxscreenshotbs.jpg[/IMG]

i used some commands i got here, and other users and bring the panel back but just for that moment, after reboot, there is the problem again and again.

---

### Post by nuwave on 2010-06-06
I've had this problem also but I've had no help. What seemed to help me is locking the taskbars. Hopefully this get more attention

---

### Post by psychoelf on 2010-06-07
I've got a similar issue.  I edited my bottom panel to turn it into a "dock".  After reboot, it appeared on top of my top dock and would not let me move it to bottom.  I tried selecting "bottom" and it would change it back to top.  Even when I went to gconf-editor.  So I deleted it and tried to make a new panel.  Now I have a blank space that shows no evidence of a panel except the empty space from windows just like your screen shot.  WTF?!?! :confused:

---

### Post by RustyWyatt on 2010-06-08
Howdy,

I installed Docky, tried it for a day or so and uninstalled it.

During my playing with Docky I deleted the bottom panel.  I have added a bottom panel back after removing Docky but I can not figure out how to the minimized programs to show on the bottom panel...

All comments Greatly appreciated!

Thanks,
Tom

---

### Post by at0msk on 2010-06-08
> **RustyWyatt said:**
> Howdy,

I installed Docky, tried it for a day or so and uninstalled it.

During my playing with Docky I deleted the bottom panel.  I have added a bottom panel back after removing Docky but I can not figure out how to the minimized programs to show on the bottom panel...

All comments Greatly appreciated!

Thanks,
Tom

This ^.

Answers please! :) 

Try this as I've read that these lines should set your panels back to default.

```

Open Terminal then enter in these commands (hit enter after eac).

1. gconftool-2 &#8211;-shutdown
2. rm -rf ~/.gconf/apps/panel
3. pkill gnome-panel

```

---

### Post by RustyWyatt on 2010-06-08
Thanks for the input!

I found that I needed to add the "Windows List" applet to the panel (right click on panel and select "Add to Panel") and now all is well...

Thanks again,
Tom

---

### Post by at0msk on 2010-06-08
> **RustyWyatt said:**
> Thanks for the input!

I found that I needed to add the "Windows List" applet to the panel (right click on panel and select "Add to Panel") and now all is well...

Thanks again,
Tom

No sir, thank you! :D I was wondering how to do this since Docky leaves the bottom half of my screen black since I cannot enable composition (Dell Inspiron 1100--having display driver issues).

---

### Post by Kharlo on 2010-06-08
problem continue after restart

---

### Post by niiaam on 2010-06-21
Adding the window list worked.  Thanks!

---

### Post by londonerdanny on 2010-06-26
> **RustyWyatt said:**
> Thanks for the input!

I found that I needed to add the "Windows List" applet to the panel (right click on panel and select "Add to Panel") and now all is well...

Thanks again,
Tom
THANK YOU - this worked for me. I don't remember how they disappeared but I'm thankful that they are back

---

### Post by centOS_kDe on 2010-07-05
> **at0msk said:**
> This ^.

Answers please! :) 

Try this as I've read that these lines should set your panels back to default.

```

Open Terminal then enter in these commands (hit enter after eac).

1. gconftool-2 –-shutdown
2. rm -rf ~/.gconf/apps/panel
3. pkill gnome-panel

```

^^ i have same problem above 
and now fixed already using your infos... 

thanks ;)

---

### Post by papichulo on 2010-07-18
it doesnt work for me :(
*pkill gnome-panel* only kill the process but it doesnt solved the problem.
i still dont have a panel.
i think there's a bug on 10.04.

---

### Post by qQChtIhpk1 on 2010-07-18
> **at0msk said:**
> This ^.

Answers please! :) 

Try this as I've read that these lines should set your panels back to default.

```

Open Terminal then enter in these commands (hit enter after eac).

1. gconftool-2 –-shutdown
2. rm -rf ~/.gconf/apps/panel
3. pkill gnome-panel

```

Chazbo - This removed the panels, but on
reboot no change.  No risk, but no help either.

---

### Post by o1hattrick on 2010-10-13
Thank you! I used the tip from at0msk and it worked like a dream.
Replaced the top panel I had accidentally deleted on my 10.10 new installation.:)

---

### Post by pyutaros on 2012-01-18
I filed this bug report with gnome-panel in Bugzilla: [https://bugzilla.gnome.org/show_bug.cgi?id=668202](https://bugzilla.gnome.org/show_bug.cgi?id=668202)

---

### Post by cyberplasma on 2012-06-05
Thank you so much!
I had this problem on a brand new installation, after finishing the updates and I already planned to to the whole installation again. These three steps fixed brought all the panels back immediately!

Thanks again

---

