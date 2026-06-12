---
title: "How to reset default profile in Gnome-colour-manager"
date: 2010-03-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Regenweald on 2010-03-31
I thought I'd install the gnome-colour-manager to test it and attempted some changes. Initially they were fine but after some recent updates, i went back in to adjust some settings and attempted toggling the gamma setting. Screen went almost totally white. Logout and in solves the gamma issue as well as launching nvidia-settings.

The white screen still happens at login though even though I removed the session setting for colour-manager from my startup items. What I'd like to know is how to reset the colour-manager settings to default.

Any help appreciated.

---

### Post by Mr. Picklesworth on 2010-03-31
If you can get to the Colour Profiles Preferences, head for the Defaults tab where you can tell it not to apply display correction.

Otherwise, the way this works (as I understand it) is gnome-color-manager runs a little app at login (see Startup Applications Preferences) which applies your chosen profiles. You can remove those choices by deleting ~/.config/gnome-color-manager/device-profiles.conf

Interestingly, I made a similar mistake ;)

Seems that the section to "fine tune" the profile (adjusting Gamma for no apparent reason) has been removed in a recent update, so either I'm crazy or we weren't the only ones. Good call, in my opinion.

(Note I may just be crazy; it's as if this entire app has suddenly blossomed into something completely different. I don't remember all this stuff being here! How exciting!)

Edit: Yep, we got a new upstream release today (March 30), version 2.30.0-0ubuntu3. More substantial than the usual, but maybe we were a bit behind or something...

---

### Post by Regenweald on 2010-03-31
Sir, thank you very much :) take a look at my conf
```

[xrandrdefault]
title=default
type=display
brightness=90
gamma=0.69999998807907104

```

Freshly deleted of course! Did not look in .config when I was attempting the manual removal, I will remember that. Will keep testing now that I know where the .conf lies :P Thanks again...Updating now so I should see the new app, I did however notice a rather large difference in what I had to the screenshot I saw in the Software-Centre( when I almost removed it altogether)

---

