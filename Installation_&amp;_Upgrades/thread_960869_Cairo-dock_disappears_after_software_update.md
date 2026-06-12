---
title: "Cairo-dock disappears after software update"
date: 2008-10-27
forum: Installation &amp; Upgrades
---

### Post by ~jww~ on 2008-10-27
After installing the latest software updates today cairo-dock has completely disappeared. Has anyone else had this problem? (I'm running Intrepid Ibex)

---

### Post by fabounet on 2008-10-28
maybe a dependency problem, I'm still running under Hardy ...
I suggest you re-install the previous version, and do a ```
mv ~/.config/cairo-dock ~/.cairo-dock
```
and then install it from our repository when the final release will be available.

---

### Post by ~jww~ on 2008-10-29
Thank you fabounet, but the command line didn't work :( 
In case anyone else has had this problem, though, I did some research on my own, and I found out that by pressing Alt + F2 that I could bring up a run application window and type in "cairo-dock" and it ran okay. Once I knew it was still there I figured out how to put it back on the menu by going into System > Preferences > Main Menu and then clicking "New Item" It took me a while to find cairo-dock, but it wasn't too difficult.

---

### Post by travis31 on 2008-11-01
The cairo-dock disappeared for me too after upgrading to 8.10. I was able to fix it by running this command in a terminal
cairo-dock -l debug

It opened up the Manage Themes dialog box and once I selected a theme,the dock reappeared on the desktop. Not sure why it stopped working in the first place but you could give this a try if you have the same problem.

---

### Post by meatlegs on 2008-11-01
Hi jww,
I'm just curious, how did you find cairo-dock when you were putting it back in the main menu?
{oops, never mind, i found it with a search. It's in user/bin}

I'm now officially loving Intrepid

---

