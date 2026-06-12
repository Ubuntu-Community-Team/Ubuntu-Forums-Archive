---
title: "No offer to update to 10.04"
date: 2010-05-20
forum: Installation &amp; Upgrades
---

### Post by wg5o on 2010-05-20
I've been running 8.04 for a long time w/o problems.  However, videos tended to hangup, as if waiting for more data.  I have a Nvidia GeForce
8400 GS graphics card, so I attempted to load the latest driver.  That landed me in Low Graphics Hell, where I couldn't change the resolution (even when a better one was offered) because I couldn't get to the bottom of the screen to get to 'Apply.'  I had down loaded 10.04 and burned a couple of CDs, and I attempted to upgrade.  But neither the Update Manager or CD worked because I couldn't get far enough down the update screen.  After a long struggle, I have a reasonable resolution, with the Nividia x server running.  

Now, when I try to up date, 10.04 is no longer offered to me, either by the Update Manager or the CD.  Apparently, I've used up all of my chances to upgrade.  What now?

---

### Post by proggy on 2010-05-20
Press Alt-F2 and type "update-manager --proposed " without the quotes.

[LIST=1]
[*]Click the **Check** button to check  for new updates.
[*]If there are any updates to install, use the **Install  Updates** button to install them, and press **Check**  again after that is complete.
[*]A  message will appear informing you of the availability of the new  release.
[*]Click **Upgrade**.
[*]Follow the onscreen instructions
[/LIST]
[https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades)

---

### Post by wg5o on 2010-05-21
Sorry, that didn't work.  I get "Could not open location 'file: ///home/andy/update-manager-proposed.'

The location or file could not be found."

I did open Update Manager (System, Administration, Update Manager) and, today it offered an update, which I installed, but it did not offer an update to 10.04.

---

### Post by DougieFresh4U on 2010-05-21
In the Software Sources, what do you have selected under 'Update' at the bottom?

---

### Post by Elfy on 2010-05-21
> because I couldn't get to the bottom of the screen to get to 'Apply.'

Alt+left mouse and you'll be able to move things about as you need.

---

### Post by wg5o on 2010-05-21
"In the Software Sources, what do you have selected under 'Update' at the bottom?"

I have "Long term support releases only."  That is what I want, and I was originally offered the update to 10.04, but couldn't get to the buttons to push.

"Alt+left mouse and you'll be able to move things about as you need."  I don't currently have the problem, but it looks like it works when I have the whole window on the screen.  Thank you!  

I escaped by using a suggestion I found that I use Tab to advance and count clicks.  The 'off the bottom' problem appears to be a common trap; it seems strange that these answers are not more widely known.

---

