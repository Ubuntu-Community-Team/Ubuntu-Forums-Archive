---
title: "HOWTO Install Ubuntu on USB External"
date: 2010-01-12
forum: Installation &amp; Upgrades
---

### Post by ak9tyOne on 2010-01-12
I ran into some issues installing 9.10 on an external HDD but I worked my way around them and here is what I have learned. I am by no means an expert but I hope that this information will help someone. 


First of all, boot into a live cd as you would when normally installing Ubuntu. 

If you need instructions on normal installation try this [[COLOR="Lime"]_guide_[/COLOR]]("http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml") or your preferred search engine.

Optional: You can first disconnect your internal drive before booting the live cd as this will protect the drive from you accidently messing with it. However, this requires you to open up your computer which can be more harm than help if you do not know what you are doing.
Also, I have read that you only can boot from usb ports on your motherboard not extensions. I do not believe this is true but just do it during installation to be safe.

Now, you need to disable the automatic mounting of drives. In other versions of ubuntu you can do this through the preferences menu. However in 9.10 do this:

open terminal and type gconf-editor followed by the [Enter] key.
Browse to /apps/nautilus/preferences/media_automount
Set value to false.
Next open the file explorer and go edit>preferences>media and at the bottom uncheck browse media when inserted and make sure the never start programs button is checked

Now you can install as you would normally, making sure to install to your external drive. On the last step click advanced and make sure grub is installing to your external drive.

---

