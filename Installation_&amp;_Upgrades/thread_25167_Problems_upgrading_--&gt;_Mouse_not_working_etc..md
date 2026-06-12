---
title: "Problems upgrading --&gt; Mouse not working etc."
date: 2005-04-09
forum: Installation &amp; Upgrades
---

### Post by `Mrk on 2005-04-09
Well, I'm not sure if this is the right place to ask help, but...

I modified my /etc/apt/sources.list -file and changed everything with "warty" to "hoary". 

Then I ran this command:
sudo apt-get dist-upgrade

Everything seemed to go ok, but then there was this part, where it asked, if I wanted to keep my old configuration file (or something like that) or replace it with a new one. There was also this option of displaying the differences between them. I went for that one, and didn't really know, how to go back... [IMG]http://ubuntuforums.org/images/smilies/icon_redface.gif[/IMG] 

My computer got stuck and I just had to reboot. After rebooting, everything was just broken, my mouse didn't work etc... I tried to use the Ubuntu Live cd to do something with my computer, but the keyboard didn't work so I couldn't make my computer to boot from CD. 

Well, it goes on, my keyboard started working again and I tried to change my BIOS-settings, but still, it didn't boot from CD. :-? 

Now I'm just totally confused, what should I do? Any suggestions?

Thanks.

---

### Post by wfx on 2005-04-09
Maybe this helps: sudo dpkg-reconfigure xserver-xorg
More info to upgrade at: [http://www.ubuntulinux.org/wiki/HoaryUpgradeNotes](http://www.ubuntulinux.org/wiki/HoaryUpgradeNotes)

---

