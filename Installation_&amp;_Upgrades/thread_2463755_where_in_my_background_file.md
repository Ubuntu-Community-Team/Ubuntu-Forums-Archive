---
title: "where in my background file ?"
date: 2021-06-17
forum: Installation &amp; Upgrades
---

### Post by anneranch on 2021-06-17
I can get to my background setting and see part (?) of my background file but cannot find out where it is located.
Clicking on "picture" does nothing. 
Looking thru "pictures" - it is not there.

---

### Post by MAFoElffen on 2021-06-17
In practice, on Ubuntu 20.04 LTS, Background pictures are in two paths:

1) When you open Settings > Background... The pictures that display in the panel are located in the /usr/share/backgrounds/ directory. Those are shared to all users of that system.

2) When in the above panel, if the user selects the "Add Picture..." button at the top right of the panel, those are located in the user's personal ~/home/Pictures/ directory.

Edit: But from option #2 above... That is just the default path to start from. If the user navigated from that folder, to anywhere they had access to, with their account rights and privilege's, then it could be anywhere on the system that they could have navigated to. It stores the setting in their own personal settings. So to track that down, if they customized it to that point, is to, as that user:
```
gsettings get org.gnome.desktop.background picture-uri

# Or if you are not that user...
sudo runuser -l users_name -c "gsettings get org.gnome.desktop.background picture-uri"

```
Note that the last character on that is a lowercase"I", not a lowercase "L". User's settings for that are stored in a binary database file located at "~/.config/dconf/user" so you can only view it in humanise through gsettings.

---

### Post by ajgreeny on 2021-06-17
Which DE are you using, Ubuntu with gnome, Xubuntu with Xfce4, Ubuntu-Mate with Mate, Kubuntu with KDE?

More info needed to be certain but as a start, have a look in **/usr/share/backgrounds** or maybe **/usr/share/wallpapers**, though you can use any almost image in your filesystem by navigating and searching for what you want.

---

### Post by MAFoElffen on 2021-06-17
> **ajgreeny said:**
> Which DE are you using, Ubuntu with gnome, Xubuntu with Xfce4, Ubuntu-Mate with Mate, Kubuntu with KDE?

More info needed to be certain but as a start, have a look in **/usr/share/backgrounds** or maybe **/usr/share/wallpapers**, though you can use any almost image in your filesystem by navigating and searching for what you want.
If you look at my edit in post#2, I just verified via coming up in gnome, unity, Mate, and Xfce as a DE, and that command tracked it it down the same on each, independent of the DE. All those DE's still use dconf. (Right? LOL) The schema.key for that specific setting (at least) seems to be universal.

EDIT: You got me curious and had to reverify. Yes, I verified that on my test bench. I listed all my schemas recursively, and only found that user background setting in that specific schema's key. That setting seems to be independent of the DE used. 

But if in doubt, a universal round-about way would be
```
gsettings list-recursively | grep -i "picture-uri"
```

---

### Post by anneranch on 2021-06-17
> **MAFoElffen said:**
> In practice, on Ubuntu 20.04 LTS, Background pictures are in two paths:

1) When you open Settings > Background... The pictures that display in the panel are located in the /usr/share/backgrounds/ directory. Those are shared to all users of that system.

2) When in the above panel, if the user selects the "Add Picture..." button at the top right of the panel, those are located in the user's personal ~/home/Pictures/ directory.

Edit: But from option #2 above... That is just the default path to start from. If the user navigated from that folder, to anywhere they had access to, with their account rights and privilege's, then it could be anywhere on the system that they could have navigated to. It stores the setting in their own personal settings. So to track that down, if they customized it to that point, is to, as that user:
```
gsettings get org.gnome.desktop.background picture-uri

# Or if you are not that user...
sudo runuser -l users_name -c "gsettings get org.gnome.desktop.background picture-uri"

```
Note that the last character on that is a lowercase"I", not a lowercase "L". User's settings for that are stored in a binary database file located at "~/.config/dconf/user" so you can only view it in humanise through gsettings.


gsettings get org.gnome.desktop.background picture-uri
That worked.
You have helped to maintain family unity. 
My better half saw my background picture I asked me to send it to her. 
I did not remember where I got it etc...
Now the copy is in my "pictures" ready to e-mail. 
Thanks

---

### Post by ajgreeny on 2021-06-17
> **MAFoElffen said:**
> If you look at my edit in post#2, I just verified via coming up in gnome, unity, Mate, and Xfce as a DE, and that command tracked it it down the same on each, independent of the DE. All those DE's still use dconf. (Right? LOL) The schema.key for that specific setting (at least) seems to be universal.

EDIT: You got me curious and had to reverify. Yes, I verified that on my test bench. I listed all my schemas recursively, and only found that user background setting in that specific schema's key. That setting seems to be independent of the DE used.
Good to know, thanks.
I have only Xubuntu to look for where those images are so could not check any other DEs.

---

### Post by MAFoElffen on 2021-06-17
Good that we could help you and help you get that for your wife!

Please remember to mark this as Solved in Thread Tools, so other users can find your solution.

---

