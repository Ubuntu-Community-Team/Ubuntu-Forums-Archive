---
title: "firefox 46 does not use system theme"
date: 2016-04-30
forum: Installation &amp; Upgrades
---

### Post by gdesilva on 2016-04-30
Hi,

After I upgraded to firefox 46, I noticed that firefox does not use the system theme. Other apps including Thunderbird use MurrinaChrome but Firefox now uses a totally different theme.

Any ideas on how to force firefox to use the system theme?

Thanks

---

### Post by vasa1 on 2016-04-30
My understanding is that Thunderbird is still gtk2. Firefox 46 uses gtk3. Does this MurrinaChrome have a gtk-3.0 folder? If it doesn't, Firefox will look rather unthemed.

You should also note that merely having a gtk-3.0 folder isn't enough. The gtk3 theme should be compatible with your system's gtk3.

**Edit**: I did a casual search for MurrinaChrome and couldn't find any recent links. The most recent link I found is this: [http://packages.bodhilinux.com/bodhi/pool/main/b/bodhi-gtk-murrinachrome/](http://packages.bodhilinux.com/bodhi/pool/main/b/bodhi-gtk-murrinachrome/) and the deb doesn't contain a gtk3 folder at all. So what you've seen isn't surprising.

---

### Post by gdesilva on 2016-04-30
@vasa1, you are spot on. MurrinaChrome is gtk2 only. I changed the theme to Adwaita which has gtk3 support and all is good now although I would have preferred to use MurrinaChrome. At least I do not get different themes with different apps.

Thanks again.

---

