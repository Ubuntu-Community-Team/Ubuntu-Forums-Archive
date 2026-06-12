---
title: "mplayer gets blocky picture with MTS files"
date: 2012-01-20
forum: Installation &amp; Upgrades
---

### Post by ppqq on 2012-01-20
Hi, I just installed xfce desktop on along with Ubuntu Natty (and yes I like it a lot and soon I'll do a fresh install with xubuntu -which may or may not solve this problem)

But i actually had some random screen freezes with Ubuntu and unity while playing MTS files with Gnome-mplayer, (I pause/play to get still frames) and had to duck out to login screen to recover after some 20 or more files played.

After installing xfce I still had screen freezes.  So I updated mplayer (I tried mplayer2 1st but it was bad to me) with ppa:motumedia/mplayer-daily and of course sudo apt-get install mplayer

so after that the MTS playback is blocky (now and then) and so taking 
still shots is really hit and miss.

I could remove the ppa, uninstall and re-install from the repos, but 
then I'm back to sq 1 with screen freezes.

I've tried installing the newer g-mplayer from the tar ball but can't 
for some reason get the makefile.in to make.

Could it be video driver related?
any ideas? cheers

---

### Post by WasMeHere on 2012-01-20
Hi ppqq,

I am also working with MTS files (from my video camera). In order to get good rendering, I upgraded the computer with a new graphics card that can manage vdpau (hardware computing). This can be used by mplayer from the repositories (run from the command line with alias) in Ubuntu Studio 11.04.

I bought an nvidia card and use the built-in proprietary driver. See also the following post
[[COLOR="RoyalBlue"]_http://ubuntuforums.org/showpost.php?p=11626239&postcount=2_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11626239&postcount=2")

Have fun finding out about Ubuntu :-)
Olle

---

### Post by ppqq on 2012-01-20
I thinks me best option is to make a clean install, cos I've done loads of work before now with no freezes -well maybe it took longer to get one!

---

