---
title: "New ubuntu window controls (shift back to right side)"
date: 2010-03-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Nightstrike2009 on 2010-03-22
Hiya everyone found this and thought i may be of help to some of us:

Sourced from:

[http://ftbeowulf.wordpress.com/2010/03/21/ubuntu-10-04-window-controls/]("http://ftbeowulf.wordpress.com/2010/03/21/ubuntu-10-04-window-controls/")

> **by Free Trader Beowulf**:

You can change this by:

alt+F2

gconf-editor

Then navigate to ‘apps / metacity / general’ look for the button layout and change it to read:

“menu:minimize,maximize,close”

So, we can change this. This is not lock-in. I would still like, for the common user, a simple option to change the placement of the window controls.

Cheers mate thanks for the heads up

PS: Although this works the window controls appear with a box around the minimize button, while still appear normal with maximize & close buttons.

---

### Post by Nightstrike2009 on 2010-03-22
Apparently Ubuntu Tweak 0.5.3 works too

Source & Instructions:

[http://gericom.wordpress.com/2010/03/15/ubuntu-tweak-0-5-3-released-more-powerful-window-button-control/]("http://gericom.wordpress.com/2010/03/15/ubuntu-tweak-0-5-3-released-more-powerful-window-button-control/")


download link for Ubuntu Tweak 0.5.3 here: [https://launchpad.net/ubuntu-tweak/0.5.x/0.5.3]("https://launchpad.net/ubuntu-tweak/0.5.x/0.5.3")

PS: Would download from the official Ubuntu Tweak Website after Lucid is released as final which is [http://ubuntu-tweak.com/]("http://ubuntu-tweak.com/")

---

### Post by Nightstrike2009 on 2010-03-22
If you wish to revert to looks (no gfx glitches) with gconf-editor use this instead:

> Then navigate to &#8216;apps / metacity / general&#8217; look for the button layout and change it to read:

"menu:maximize,minimize,close"


PS: I have no idea how to get back to left side, or restore firefox icon it gets replaced by a grey dot, other than that your back to normal.

---

### Post by mc4man on 2010-03-22
There is also [mwbuttons]("https://code.launchpad.net/mwbuttons/+download") - I put it in ~/bin and added to preferences menu (also has 'presets'

---

