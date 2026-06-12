---
title: "Ubuntu Jaunty nothing to click!!!"
date: 2009-03-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by CourtJesterG on 2009-03-04
:confused: I need help on this! I've already had reinstalled and set up my Ubuntu on my desktop pc. I am using the Jaunty version disc at this time to even access the internet.

          After I reinstalled and set-up. I had updated jaunty as requested I also didn't installed 2 scripts since I kinda told me not too when asked. So I kept the old defaults. After I had rebooted it was fine so I started taking stuff out example evolution. Personally I am a Mozilla fan base fan, but heard something about flock isn't helping them no more and moving to chrome interesting. I am also using Opera. 

          Back on track as I was saying I was taking programs out and sticking some new ones in from synaptic package manager. I made sure especially when talking evolution out and dependants that I could. Noticed though some dependants had to stay cause of other programs so I left them. Still just talking about evolution email client.

          OK so I am doing what I do best. My video setting don't matter if normal or extra. My vid was installed. and etc.. No I haven't downloaded new drivers.

===The PROBLEM===

        I restarted the computer this is the second time and same exact thing that has happened the gnome panels are missing. If I press alt f2 to even run a program it won't happen. By chance I stick my usb flash drive in my file system is all there everything seems to be still installed. I can't go to root on the desktop not is there anything their to click on or access.

        I've tried back stepping. I ran the fail safe gnome client still nothing, and also the terminal fail-safe. I sudo apt-get install gnome just in case also have tried reinstall evolution since that was the major object I was taking out.

        Anybody have any ideas I mean my desktop background shows but nothing else? It wasn't those two deprecated scripts from the update i didn't install since it was fine during reboot. 

       Please get back to me thanks!!:popcorn:

---

### Post by nyarnon on 2009-03-04
You probably removed ubuntu-desktop it happens when you mess with stuff that gnome considers its own. See in synaptics if unbuntu-desktop is still installed, even if so try reinstalling it.

---

### Post by Nullack on 2009-03-04
Boot into recovery single mode at the grub prompt. Have a look at the debugging X problems pages on the wiki.

---

### Post by CourtJesterG on 2009-03-04
:KS I got it! I found the solution. I did kill all and also. I just reinstall the gnome-panel!! Sudo apt-get Gnome-panel

      After the reboot from the fail-safe terminal then went to gnome. Everything was fine. I did get an error message though that said and asked if i want to delete this applet. Crashes or something like that.

    "OAF11D:GNOME_FastuserSwitch. Applet" caused the error it said during the reboot.

      As for my configuration of panels and everything its fine and everything is here.;)

---

### Post by nyarnon on 2009-03-04
> **Nullack said:**
> Boot into recovery single mode at the grub prompt. Have a look at the debugging X problems pages on the wiki.

That's interesting. What makes you think this is an X problem?

---

### Post by nyarnon on 2009-03-04
> **CourtJesterG said:**
> :KS I got it! I found the solution. I did kill all and also. I just reinstall the gnome-panel!! Sudo apt-get Gnome-panel


I expected as much as that, just to be on the save side check your ubuntu-desktop, really, you might have removed other stuff you don't know about.

---

### Post by CourtJesterG on 2009-03-04
):P):P  Yeah i just checked on that in Synaptic Package Manager. ubuntu-desktop isn't installed version  is 1.138? Odd very odd! I don't even remembering taking it out in the first place when checking. I wonder if this was done during the update. I will get back on that x thing.;)

---

### Post by nyarnon on 2009-03-04
> **CourtJesterG said:**
> ):P):P  Yeah i just checked on that in Synaptic Package Manager. ubuntu-desktop isn't installed version  is 1.138? Odd very odd! I don't even remembering taking it out in the first place when checking. I wonder if this was done during the update. I will get back on that x thing.;)

It was done when you removed one of it's dependencies. I'm not sure for evolution but that's my guess at the moment. As for evolution, just remove the icon and leave the rest it will hardly be in your way and theres to much stuff interconnected with it.

---

