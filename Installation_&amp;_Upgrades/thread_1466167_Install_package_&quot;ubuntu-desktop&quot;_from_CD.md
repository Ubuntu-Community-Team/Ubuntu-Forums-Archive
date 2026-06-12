---
title: "Install package &quot;ubuntu-desktop&quot; from CD"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by Yoshis88 on 2010-04-30
I have installed a system using the 10.04 x64 CD.  I happened to check OpenSSH server and LAMP server, and it completed installation successfully and satisfactorily.

However, I'm now interested in apt-get'ing the package "ubuntu-desktop". So I type to the sudo-privileged user:
```
sudo apt-get ubuntu-desktop
```
Now it starts fetching 500MB from repositories and estimates it'll be done in 7 days.  Too long.

I'd like to install the package from a CD. Basic googling told me to go:
```
sudo apt-cdrom add
sudo aptitude ubuntu-desktop

```But then it goes back to asking the internet for the package, instead of consulting the the CD I fed.  I have only the terminal, so no going to Synaptic and checking CD-rom boxes.

Are these the commands I need? Which CD should I be feeding? Obviously the Ubuntu 10.04 x64 CD, but server/desktop/alternative?

---

### Post by zvacet on 2010-04-30
Edit your source list with 

```
gksudo gedit /etc/apt/sources.list
```

and remove # sign from line referring to CD.Save and close file.

```
sudo apt-get update
```

or 

```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ubuntu-desktop
```

If you downloaded server version I don't think you can install desktop from it.I will download alternate CD,because on it you have GNOME,KDE and XFCE desktops.But downloading alternate is ~700MB.

---

### Post by Yoshis88 on 2010-05-03
Ah, I think I was forgetting the update command.

I have no problem downloading the Alternate CD.  I have no problem downloading 500MB, only just with the estimated (7days? sure felt like that was the pace) total time it would take.  I could probably download the Alternate CD and install the packages in less time.

I'll try it out when I find the time. Thank you!

---

