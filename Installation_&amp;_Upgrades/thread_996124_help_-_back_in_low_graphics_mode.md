---
title: "help - back in low graphics mode"
date: 2008-11-28
forum: Installation &amp; Upgrades
---

### Post by jebsector on 2008-11-28
All:

I had this problem previously when upgrading ubuntu 8.  I have an n-vidia gforce 9600 GT graphics card, which is too new for the standard linux drivers that accompany ubuntu.

Problem is, it seems every time I install the ubuntu updates on my machine, it hoses my graphics, and I end up in low graphics mode.  Help?  I installed the linux driver via the nvidia instructions online for this graphics card.

Thanks, sorry for the trouble..

---

### Post by inobe on 2008-11-28
how did the driver install go ?


you know that 8.04 **LTS** is still supported and very stable, correct ?

their is no real or logical reason to upgrade !

---

### Post by jebsector on 2008-11-28
Yeah, I know it is another great release of the os.

I get that update icon glaring at me in the upper-right corner and I just itch to install the latest updates.

For this problem, it resolved by installing 'envy', and removing the nvidia drivers.  When I downloaded the latest nvidia driver from their website for the 9600-GT, I installed via the usual 'sudo /etc/init.d/dgm stop', sh nvidia*, /etc/init.d/gdm start sequence of commands.  Installed fine and I'm back up in minutes.  I'm wondering if what I did with 'envy' will keep the problem from happening again when I apply the ubuntu updates.  Don't know until I try a few times.

You know, aside from small things like that, I can't really go back to things like fedora or suse, ubuntu is really getting for me like firefox is to exploder. ;|

---

