---
title: "Problems trying to install 6.10 on amd64"
date: 2007-02-03
forum: Installation &amp; Upgrades
---

### Post by zjd on 2007-02-03
Hi,

I am an absolute Ubuntu beginner. I have been trying to install Ubuntu 6.10 on the following system:

AMD64 3200+
Chaintech VNF4 Ultra Socket 939
160GB IDE
ATI Radeon X800XL


The regular LiveCDs for i386 and 64-bit simply loaded to the splash screen where I have selected both regular install and safe graphics mode. Unfortunately neither can get past the screen w/ the bar that moves side to side. I wait up to 12 hours and nothing happens.

I then tried the alternate i386 install CD. This seems to work however it takes approximately 3 hours to go from the initial splash screen to the Select and Install Software screen immediately after the kernel installs. Currently it has taken around 30 minutes to go from 0% to 1% of configuring the language-en-base. I am now at my gf's and will check the progress in the morning. My roommate who was able to install Ubuntu (Dapper) from the LiveCD says it should not take this long.

Hopefully when I check back in tomorrow it will have finished installing. If it does not what should I do?

Thanks for any help!

---

### Post by rsambuca on 2007-02-04
hmmm...  something is definitely wrong here.  With you specs, installation shouldn't take more than 25-30 minutes.  I wouldn't bother waiting all night.  First, I would try installing with different boot options:

At the main startup screen, press F6 for more boot options.  You will see a line of commands show up, with a double dash "--" at the end.  Use your arrow keys to move your cursor in front of the dashes and try adding some of these boot options:

ide=nodma (make sure you leave a space before the dashes)

then try booting.  If that doesn't work, try adding all of these in:

irqpoll pci=noacpi noapic nolapic acpi=off

and try booting

---

### Post by zjd on 2007-02-04
hey thanks alot it worked!

i used all of the boot options you mentioned and it installed w/in 30 mins. However I am still having graphical problems. After GRUB loads and I select Ubuntu the bar loads almost entirely before the graphics turn like a greyish blue and the screen stalls and I wait like 20 minutes before shutting down.

I know my Ubuntu installation is ok b/c using the recovery boot option in GRUB I can do everything in a terminal, access the internet using w3m, access files, I am also doing apt-get-update and apt-get-upgrade.

In xorg.conf it reads my video card but I am wondering if the default drivers arent the best or something?

Any ideas? Thanks!

---

### Post by rsambuca on 2007-02-04
Yeah, Ati cards are a little finicky apparently.

Try the recovery mode again, and:```
sudo apt-get install xorg-driver-fglrx
```
then```
sudo aticonfig --initial
```
then ```
sudo aticonfig --overlay-type=Xv
```(note X is capitalized)
then ```
startx
``` to see if it worked.  

If that works, you might want to install the radeon driver instead of ati in your xorg.conf file later.

---

