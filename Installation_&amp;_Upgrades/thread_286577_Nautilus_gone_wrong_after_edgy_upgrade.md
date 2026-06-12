---
title: "Nautilus gone wrong after edgy upgrade"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by tkoopa on 2006-10-27
I've just upgraded to edgy from dapper, most of it went well, but nautilus seems to have gone wrong. 
The top buttons and location bar have gone, and I can't get the "places" sidebar to return (the clickable slider usually on the left isn't there). I think the attached screenshot explains things better. Anyone have an idea of how to fix this ?

---

### Post by Craigus on 2006-10-27
I had a similar, but not identical problem, and it was intermittent in that it would sometimes appear or disappear after a reboot.

I just gave up and did a clean Edgy install.

---

### Post by tkoopa on 2006-10-28
> **Craigus said:**
> I just gave up and did a clean Edgy install.

Thanks for the advice, but this is the only notable bug I've got after upgrading, and since I've spent some time on customizing my installation I'm looking for a real fix ;) 

I mean, if I managed to keep a w2k install running for over four years, I think I'll try repairing nautilus rather than go down the re-installation path

I've tried the following with no success :
- reinstall nautilus from synaptic
- mark all upgrades,  sudo apt-get -f install,   sudo dpkg --configure -a and a few others to make sure I have everything
- using another account (in case it was a user config problem)

I guess I'll have to use Konqueror in the meantime.

---

### Post by tkoopa on 2006-10-28
There's hope yet, when using the File Browser as root in Applications> System Tools (I think that came from Automatix), Nautilus is back to normal. 

This leads me to believe it's just a config problem.

---

### Post by tkoopa on 2006-10-28
arg , I feel like an idiot. It's not a bug, it's a behaviour option. I just checked the "Always open in browser windows" and everything is back to normal (glad I persevered though)

---

### Post by jeecol on 2006-11-24
1. I had the same problem and did the same trials. After this post I learned something.

Open a file manager: Place > Home Folder  then Edit > preferences, tab#2-behavior, and check "always open in browser windows"
 
Then the file manager looked like normal....

Oops, my files were still invisible (but I could see them in terminal). 

I tried and found that they were invisible when "view as list", but they were OK when "view as icons"


2. Solution: open a file manager: Place > Home Folder, then Edit > preferences, tab#4-list columns, and select Name, Size, and Date modified (or more as you want) and they become visible when "view as list"

Thanks everyone!

-----------
jeecol = one dollar

---

