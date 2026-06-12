---
title: "Installed updates, restarted, hung, hard reboot, everything is basic again"
date: 2011-04-07
forum: Installation &amp; Upgrades
---

### Post by chaoticist on 2011-04-07
It seems I'm here every other day, because something has gone wrong.

This time, I had to redo my dual boot Vista/Maverick.

It went fine. Installed Vista. Used Wubi to install Ubuntu. Moved the Ubuntu install to it's own partition. It worked fine.

Then I went and spend a few hours customizing Ubuntu, adding my themes back the way I like them, and my programs. Finally, I set it to updating.

No problem yet.

Then, it told me to restart, as it does when new updates have been installed.

That's where the problems began.

After restart, my computer hung before fully restarting. After a few minutes of it sitting there with some error message that I don't remember and didn't think to write down, I did a hard reboot.

Both OS's still boot fine. The problem is that all my themes, icons, themes, and updates have disappeared from Ubuntu. My password was even changed back to the one I set for Wubi.

I have no idea how this is possible.

I must once again ask for your assistance in this matter.

---

### Post by Rubi1200 on 2011-04-07
Hi,

can you please do the following so we can get a better overview of the setup (if you can boot into Ubuntu, run the script from there, no need for a LiveCD):

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by chaoticist on 2011-04-07
> **Rubi1200 said:**
> Hi,

can you please do the following so we can get a better overview of the setup (if you can boot into Ubuntu, run the script from there, no need for a LiveCD):

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

I have to get ready for and go to work at the moment, but I will do so the moment I get home.

---

### Post by Dutch70 on 2011-04-07
For future reference, you should almost never have to do a hard reboot.
[[COLOR="RoyalBlue"]http://kember.net/articles/reisub-the-gentle-linux-restart/[/COLOR]]("http://kember.net/articles/reisub-the-gentle-linux-restart/")

To help remember the combination of keys, cause you won't be able to find them when you need them most...:P
[COLOR="Red"]R[/COLOR]eboot
[COLOR="Red"]E[/COLOR]ven
[COLOR="Red"]I[/COLOR]f
[COLOR="Red"]S[/COLOR]ystem's
[COLOR="Red"]U[/COLOR]tterly
[COLOR="Red"]B[/COLOR]roken

---

### Post by chaoticist on 2011-04-08
@Dutch: Thank you for telling me about that, it might come in handy sometime.

@Rubi: Thank you for being so willing to help me again.

So...here's the deal. I still have no idea why that happened. I assume Ubuntu was trying to do too much at once, with all the programs, themes, and icons I installed in addition to the updates.

I reinstalled the updates, rebooted, then added my programs and themes, and rebooted, and have had no problem.

In addition, I found a neat replacement for gnome-panel, called Avant Window Navigator. It's like a mixture of Docky and the Panel, and is pretty neat so far.

I've also backed up my entire system onto an external drive. If it crashes again, I'll just reinstall that program, and restore from the external.

Lucky for me, I stopped keeping my data on my OS hard drive, and put it on my external instead.

I'm marking this as solved.

@Rubi: Hopefully I don't need your help again soon lol. I'll try not to do anything dumb :D

---

