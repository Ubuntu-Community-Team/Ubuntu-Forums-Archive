---
title: "Where can I find Lubuntu 10.04 Alternate ISO"
date: 2012-11-23
forum: Installation &amp; Upgrades
---

### Post by tbaugh on 2012-11-23
I have an old Toshiba Satellite 4300 series laptop with 320MB memory. I am able to install Lubuntu 10.04 desktop iso with no problems and it runs fast. The problem is it doesn't recognizes my ethernet PCMCIA card. I found Xubuntu 10.04 Alternate iso and it installed fine and found my ethernet card. The problem is Xubuntu runs noticeably slower that Lubuntu. I googled and look on several sites and I can't find the Lubuntu 10.04 Alternate iso. I am hoping it would resolve my issue if I am able to install it. Your help is greatly appreciated.

---

### Post by snowpine on 2012-11-23
Since you already have a working install of Xubuntu, all you need to do is:

```
sudo apt-get install lubuntu-desktop
```

or for a more thorough "purge" of anything Xfce-related:

[http://www.psychocats.net/ubuntu/purelubuntu](http://www.psychocats.net/ubuntu/purelubuntu) 

(note however you'll have to modify that tutorial for 10.04. also note that 10.04 reaches its "end of support" in less than 6 months!)

---

### Post by tbaugh on 2012-11-24
Thanks Snowpine! It worked just fine. When I was installing the Lubuntu it asked me which display manager to use (gdm or lxdm). I selected lxdm and I had some problems with my display, so I re-installed Xubuntu and then Lubuntu and selected gdm and it worked great.

You mentioned that 10.04 has only 6 months of support left, I read that for "old" computers to install 10.04 because that is the last release with the older drivers. Therefore, I probably won't be able to upgrade to 12.04 with this old laptop. Thanks again.

---

