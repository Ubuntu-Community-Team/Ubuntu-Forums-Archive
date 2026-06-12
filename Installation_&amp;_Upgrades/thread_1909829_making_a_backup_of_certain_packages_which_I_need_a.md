---
title: "making a backup of certain packages which I need again after formatting"
date: 2012-01-16
forum: Installation &amp; Upgrades
---

### Post by jamesbon on 2012-01-16
Here is a situation due to a wireless card problem I am formatting my laptop again and again.I need to take backup of certain packages like

vim
sources.list (I want only US repos here)
google-chrome
skype
ssh2
nfs
vlc 
wine 
firefox and chrome settings
aptitude
gnome-session-fallback

each time I format my laptop all these are lost and I am back to day 1 again and then a long series of tiring downloads frustrates a lot.Is there a way I can take backup of these some how as I am installing and formatting my same laptop from past 2-3 days again and again.I have seen /var/cache/apt/archives where they are present when but each time when I do an aptitude install vim I see it starts downloading from internet rather than using ones which I already have.

---

### Post by Mark Phelps on 2012-01-16
Take a look at aptoncd:  [http://aptoncd.sourceforge.net/]("http://aptoncd.sourceforge.net/")

---

