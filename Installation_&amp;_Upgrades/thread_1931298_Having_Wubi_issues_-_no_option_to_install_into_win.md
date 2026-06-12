---
title: "Having Wubi issues - no option to install into windows."
date: 2012-02-25
forum: Installation &amp; Upgrades
---

### Post by timtamboy63 on 2012-02-25
When I boot wubi, all I get is:
[img]http://gyazo.com/a14a26c80d363a9802b6d911ff2367d0.png[/img]

There's no option to install into windows like there usually is?

Any ideas?

Cheers!

---

### Post by roelforg on 2012-02-25
That option is implied with using wubi.
It modifies the bootloader settings from windows to call the kernel that loads and works from a diskimage on the hd.

---

### Post by timtamboy63 on 2012-02-25
Oops, sorry I meant install into windows, not boot into windows. I'm editing my original post. To clarify, I'm looking for:
[IMG]https://help.ubuntu.com/community/Wubi?action=AttachFile&do=get&target=Wubi3.png[/IMG]

---

### Post by roelforg on 2012-02-25
Try the "Demo and Full installation".

---

### Post by timtamboy63 on 2012-02-25
Tried it, it gives me:
[IMG]http://gyazo.com/8beb154b20895baa67f14d0f4dd10f6c.png?1330174234[/IMG]

---

### Post by roelforg on 2012-02-25
Yeah, i checked the wiki and it says that, indeed, you're missing a button.

Check if there's already an entry for ubuntu in your "Add or Remove programs" list.
You could try to download/burn the livecd and putting it in your pc while windows is on, it has the Wubi installer, maybe it needs the cd for some files?

---

### Post by timtamboy63 on 2012-02-25
Last option worked perfectly. I didn't burn a Live CD, just mounted, and the options there! Cheers

---

### Post by roelforg on 2012-02-25
> **timtamboy63 said:**
> Last option worked perfectly. I didn't burn a Live CD, just mounted, and the options there! Cheers
My guess?
The cd contains the stuff needed to create a basic ubuntu system (few hundred mb) so the installer needs those packages to create a basic image.

Yeah, the burning isn't needed. I said that b/c most people don't know how to mount cd's in win (i don't, my friend does).

---

