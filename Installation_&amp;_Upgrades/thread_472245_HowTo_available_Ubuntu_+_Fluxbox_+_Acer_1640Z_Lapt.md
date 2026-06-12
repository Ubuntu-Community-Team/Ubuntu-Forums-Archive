---
title: "HowTo available? Ubuntu + Fluxbox + Acer 1640Z Laptop =&gt; Working + &quot;Slim install&quot;"
date: 2007-06-12
forum: Installation &amp; Upgrades
---

### Post by kentl on 2007-06-12
Hi!

I've decided to liberate my Acer Aspire 1640Z laptop from Windows and let it reach its true potential using Ubuntu and Fluxbox! ;)

My goal:
I want to install Ubuntu 7.04 and use Fluxbox as my window manager. I want to keep the installation as slim as possible, if possible I never want to install any other window manager before Fluxbox (or _completely_ remove it before installing Fluxbox).

My questions:
[LIST]
[*]I have seen some people recommending to use the server edition in this case, while others have recommended the desktop edition. Which one should I use? I know that there is a different kernel in the server version, which detects less hardware, and it doesn't sound good for laptop. Or?
[*]Is there any HOWTO on how to get fluxbox using Ubuntu without installing anything which isn't necessary? (As I want to keep my HDD as clean as possible)
[*]If there isn't any HOWTO, could you give me some tips?
[/LIST]

I would be glad if someone could help me out. I've searched the forums for "fluxbox", "server" and "desktop" and looked through the most promising threads. But I would really need a recommendation I'm afraid.

Thanks for reading this post!

---

### Post by kerry_s on 2007-06-12
No, you don't actually use the server, you want the alternate installer disk or the mini.iso.

it's the same kernel

search low ram or low spec install.

---

### Post by dingo on 2007-06-12
This might be just what you're looking for:

[http://fluxbuntu.org/](http://fluxbuntu.org/)

Good luck.

---

### Post by kentl on 2007-06-13
Well is Fluxbuntu safe to use? It seems like it's still in quite an early stage of development.

Regarding the install. I'm now downloading the alternate install for the Xubuntu distribution. I hope that it lets me install up until text mode only. Then I can install xorg and fluxbox myself. Am I on the right track?

---

### Post by kerry_s on 2007-06-13
> **kentl said:**
> Well is Fluxbuntu safe to use? It seems like it's still in quite an early stage of development.

Regarding the install. I'm now downloading the alternate install for the Xubuntu distribution. I hope that it lets me install up until text mode only. Then I can install xorg and fluxbox myself. Am I on the right track?

Yes, with the alternate cd type> server <to do the server install
than after you reboot
login
sudo su <to become root
nano /etc/apt/sources.list
comment out the cdrom and uncomment all the repo's
ctrl + x and y and enter <to save
apt-get update
apt-get install xorg gdm synaptic fluxbox
reboot
select fluxbox in the session menu <important
login
open synaptic and install what ever else you want.

don't worry about the first error, it's because you don't have that theme, you can fix that when you login go>apps> system> gdm setup, under local just select one of the themes, you can also go to the security tab and setup autologin so you can skip the gdm. I have mine set on plain for the gdm it's lighter and faster to start. I have mine built light and fast, cause i only have 450mhz and 256ram.

I use> apt-get install xorg gdm synaptic fluxbox emelfm mousepad dillo
to start.

---

### Post by kentl on 2007-06-13
[IMG]http://img175.imageshack.us/img175/3529/srvdownxp0.png[/IMG]
I'm currently downloading the server image according to the picture above. Thanks to your rich reply I think I'll get it to work. I was afraid that I would get some strange kernel which wasn't suited for my laptop. But I'm glad that it's the same one as in the desktop edition! :D

---

### Post by kentl on 2007-06-13
Now that I think about it. Did you mean that I should download the alternate install of the Desktop edition and type "server" somewhere? Sorry for my stupidity. I find it confusing with all these different alternatives of media (2 server/desktop * 2 alternate/normal = 4). :redface:

---

