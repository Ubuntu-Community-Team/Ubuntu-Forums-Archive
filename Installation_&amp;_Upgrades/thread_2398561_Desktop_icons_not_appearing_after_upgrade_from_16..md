---
title: "Desktop icons not appearing after upgrade from 16.04 to 18.04.1"
date: 2018-08-14
forum: Installation &amp; Upgrades
---

### Post by cauliflower on 2018-08-14
I received the 'Upgrade to 18.04.1' prompt and decided to go for it. 

Since the upgrade no icons appear on my Desktop, I can't create files/folders by right-clicking on the Desktop.

The Desktop folders and files do exist when I view with Files or in Terminal. If I create a folder in Terminal it doesn't then appear on the Desktop, same if I touch a file. The same is true from the file viewer GUI.

Any ideas?! Help would be much appreciated, I don't have lots of Linux experience. 

If I remember right I had installed Unity in my 16.04 installation (though I can't remember if I ended up changing that back to Gnome). 

I did a bit of searching and in a previous (quite old) thread someone had had some success by installing the Gnome Tweak tool, when I do an apt-cache search I see two possible candidates:

gnome-tweak-tool - adjust advanced settings for GNOME - transitional package
gnome-tweaks - tool to adjust advanced configuration settings for GNOME

I'm not sure which of these to try (and what to do with it once installed)

Thanks,

Guy

---

### Post by cauliflower on 2018-08-14
> **cauliflower said:**
> I received the 'Upgrade to 18.04.1' prompt and decided to go for it. 

Since the upgrade no icons appear on my Desktop, I can't create files/folders by right-clicking on the Desktop.

The Desktop folders and files do exist when I view with Files or in Terminal. If I create a folder in Terminal it doesn't then appear on the Desktop, same if I touch a file. The same is true from the file viewer GUI.

Any ideas?! Help would be much appreciated, I don't have lots of Linux experience. 

If I remember right I had installed Unity in my 16.04 installation (though I can't remember if I ended up changing that back to Gnome). 

I did a bit of searching and in a previous (quite old) thread someone had had some success by installing the Gnome Tweak tool, when I do an apt-cache search I see two possible candidates:

gnome-tweak-tool - adjust advanced settings for GNOME - transitional package
gnome-tweaks - tool to adjust advanced configuration settings for GNOME

I'm not sure which of these to try (and what to do with it once installed)

Thanks,

Guy



Typical - as soon as I posted this I found gnome-tweaks was already installed. Show Icons was 'Off' (Why?!!!!!!). Turning it on displayed the icons (though they are too large so I'll have to find a way of reducing them).

---

