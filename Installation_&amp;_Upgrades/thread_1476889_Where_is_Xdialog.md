---
title: "Where is Xdialog?"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by Paddy Landau on 2010-05-08
I had [Xdialog]("http://xdialog.free.fr/") installed on a Jaunty machine. According to Synaptic, it comes from the section "Miscellaneous - Graphical (Universe)".

I did a fresh installation of Lucid 10.04. But, Synaptic doesn't find Xdialog.

Where is it?

I tried downloading the RPM build from the website, but alien seems unable to correctly convert it.

I know that we're "supposed" to use zenity, but zenity doesn't have some of the features that I need.

---

### Post by Paddy Landau on 2010-05-10
Bump?

---

### Post by graffiX on 2010-05-16
I also am missing xdialog, on 9.10

---

### Post by kerry_s on 2010-05-16
zenity is pretty much the standard, it does the same things.

---

### Post by Paddy Landau on 2010-05-16
> **kerry_s said:**
> zenity is pretty much the standard, it does the same things.
I know, but there are a couple of useful features in Xdialog that I've had to work around in when using Zenity. Xdialog does have more features than Zenity.

I wonder if there's any better program than Zenity or Xdialog? They're OK, but not good.

---

### Post by kerry_s on 2010-05-16
well according to the change log, the last update for xdialog was 18/08/06 so i would assume it's no longer maintained, therefore why it was probably dropped.

what feature are you looking for?

how about xmessage or gxmessage(gtk)?

---

### Post by Paddy Landau on 2010-05-16
> **kerry_s said:**
> ... the last update for xdialog was 18/08/06 so i would assume it's no longer maintained...
Thanks for letting me know. In that case, xdialog wouldn't be a good one to use anyway.

> **kerry_s said:**
> what feature are you looking for?
I mostly need the feature that prevents the xdialog window from being closed. Using zenity, I've worked around it by using devilspie to eliminate the window decoration (so that the user can't close it with the x), and putting it into a loop so that if the user presses Cancel, then it restarts. But it's messy. Oh well.

> **kerry_s said:**
> how about xmessage or gxmessage(gtk)?
Thanks for the ideas. I've had a look at them, and unless I find something better, I'll stick with zenity.

---

### Post by Meneer Jansen on 2010-09-12
> **kerry_s said:**
> zenity is pretty much the standard, it does the same things.
[start_rant_mode]
Probably, thats what the Ubuntu boys thought. But:
[LIST=1]
[*]What about backwards compatibility?
[*]What about people **NOT** wanting, or being able to, re-write 1.000 shell scripts that use Xdialog instead of Dialog (and Lord knows when the 'Buntu boys think that's obsolete). 
[/LIST]
'Buntu is becoming like Steve Jobs: difficult to include something or support it? Simply call it "obsolete" to get rid of the problem. I might as well buy a Mac and rewrite all my scripts every 2 years. 

Where I come from, someting that is not actively developed anymore might just as well be **SO** incredibly stable and brilliant that it does not **need** any developing anymore. So: no bugs, no Ubuntu inclusion? Aaaarrghhh! :(
[end_rant_mode]

---

### Post by Paddy Landau on 2010-09-12
> **Meneer Jansen said:**
> Probably, thats what the Ubuntu boys thought...
You can't blame Canonical; the Ubuntu boys didn't write or support Xdialog. You'll have to rant at the Xdialog developers, and since it's FOSS there's nothing to say.

If you still want Xdialog, you can [download the latest version]("http://xdialog.free.fr/#RELEASE"). But as it's been unsupported for over four years, I would recommend that you gradually convert to Zenity. A big pain, I understand, but what else to do? You could hire a cheap programmer to maintain Xdialog, I suppose.

I still would like to find a decent GUI front-end to scripts. It doesn't look as though anyone has written one, though.

---

### Post by Meneer Jansen on 2010-09-13
Dear Paddy Landau,

Thank you for your kind reply. I do hope that Zenity will be maintained. As of now, I do not believe that much is being done to improve the possibilities of zenity. In Xdialog we had the option to make a "--wizard" with a 'next' an 'back' button. Also, in xdialog we had the option to add a 'help' button.

Zenity looks great, nut lacks in functionality. And will Zenity be gone in a year just like gdialog, kdialog etc.? I hope not...

---

### Post by Paddy Landau on 2010-09-14
> **Meneer Jansen said:**
> I do hope that Zenity will be maintained.
Me too.

> **Meneer Jansen said:**
> In Xdialog we had the option...
If I knew an appropriate programming language and had the time, I'd write my own. Xdialog had some good features that Zenity doesn't, but even it didn't have a sufficiently flexible interface. We really do need something better.

Hmm, maybe I'll hire a programmer at some stage and donate the program to FOSS. When I have a bit more money... ;)

---

