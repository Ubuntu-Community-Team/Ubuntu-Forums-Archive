---
title: "(X)Ubuntu installs freeze"
date: 2006-07-18
forum: Installation &amp; Upgrades
---

### Post by JSchwage on 2006-07-18
Alright, I'm finally posting here after trying every possible alternative way to install (X)Ubuntu. I have an old Compaq Presario 1200 notebook and cannot get Ubuntu or Xubuntu to install on it. I've gotten SimplyMepis and Zenwalk to both install flawlessly. But whenever I try to install (X)Ubuntu on the thing, it'll just freeze up at some random point during the installation, whether it be the Live CD installer or the alternative install. I've even tried using a different CD-R with lower capacity with the Ubuntu server install, which also froze during the install.

All I can say is that it seems to freeze up on the Live CD when it gets to configuring the gnome-power-manager package.

I've actually gotten Ubuntu to "sort of" install on it in the past. That's just because it got through the installer enough to run. But the installer just wasn't able to clean up after itself.

I am trying to install Dapper 6.06 and I have 192 MB of RAM. Strangely enough a Breezy Shipit CD seems to install fine, and also an old Hoary Shipit CD I have.

---

### Post by -Phi- on 2006-07-18
Are you using a Dapper Shipit CD? If not, I've seen a number of posts about burned CDs not working. I guess the installer is very very sensitive to errors.

Some Suggestions:
- Make sure your downloads are error free with the checksum
- Re-burn the CD at a slower speed
- Install Breezy and upgrade to Dapper with the Update Manager

Hope this helps

- Phi

---

### Post by JSchwage on 2006-07-18
I've tried your two first suggestions already and they didn't work. If I installed Breezy and then upgraded to Dapper, it wouldn't look like a new Dapper install, would it? I'm supposing it'd still have the old icons and settings from the Breezy install, correct? Also, I really want to run Xubuntu instead of Ubuntu, and I'm not sure how easy that would be to do with all the upgrading crap.

And no, it's not a Shipit CD. I'm still waiting to receive that in the mail.

---

### Post by xptweakerntn on 2006-07-18
now this is weird.
i just got my cds in the mail.
my problem is just about like yours
my hardware
compaq sr 1220nx
2.93 ghz celeron
1024 ddr 2700(512x2)
geforce fx 5500(<--- odd, possibly the problem)???
80 g ide hard drive

---

### Post by tracyapotter on 2006-07-18
Sir,

I have an older 400MHz, 128M RAM Compaq laptop that would run the Xubuntu Live CD, but on install would loose its mind during the disk partitioning phase.  The only fix for me was to download the alternate install cd for low memory and servers that uses the old text based installer.  It worked like a champ.

TA Potter

---

### Post by -Phi- on 2006-07-18
If you just want Xubuntu then I would try doing a server install of Breezy, upgrading to Dapper from the command line (I'm not sure how to do that, but it's certainly possible and should be documented somewhere), then installing the xubuntu-desktop package. The upgrade shouldn't mess up any default settings like icons and such since there won't be any until you install Xubuntu.

However, installing Breezy Ubuntu, then updating to Dapper and installing Xubuntu shouldn't be a problem. In fact, it happens to be what I did to the old Toshiba laptop I'm using right now.

- Phi

---

### Post by JSchwage on 2006-07-20
The funny thing is, I can't even upgrade to Dapper from Breezy without having some kind of problem during the upgrade. I'm thinking I should just stick to Breezy since it's impossible for me to run Dapper on the laptop without a bunch of problems. Except the only problem is that I can't install Xubuntu on a Breezy install.

---

