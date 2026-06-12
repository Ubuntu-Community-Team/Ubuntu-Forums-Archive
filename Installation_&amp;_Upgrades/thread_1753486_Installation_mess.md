---
title: "Installation mess"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by misoramen on 2011-05-09
Hi. I have a problem. I tried to install ubuntu 8.10 on my old laptop (dell latitude c400 20GB 512Ram)

for some reason windows xp was taking up too much space (about 18GB) so i removed it while installing ubuntu #-o

so now ubuntu won't work - I got as far as login and it dies.

my biggest problem now is i can't use my CD/R to boot.

i set it to boot from CD but it skips straight to grub (with only ubuntu)

so, i deleted grub (thinking it might then see my CD/R) using:

# dd if=/dev/ZERO of=/dev/sd01 bs=446 count=1 (i did it for bs=466 and bs=512 too :idea:)

then i got "GRUB Loading stage1.5. Error 5"

anyway, i used the ubuntu 8.10 CD (which it still recognises) and installed it again. everything seemed ok but it still crashes after login.

I've tried Mint and Puppy (and XP) but CD/R ignores them.

i can get into safe mode. but what to do from there? i've tried all the options. something from the command line maybe? i think i need to tell it to use my CD/R and not grub. but as you can see i have no clue really ](*,)


any ideas please? [-o<

---

### Post by zvacet on 2011-05-09
Try to download and install Lubuntu (it is light version of Ubuntu because it use LXDE as desktop environment,so it make it good choice for your ram).On [this]("https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/AlternateInstall") link you will get alternate CD.It is not eye candy but on that page you have instructions for installation.Try it and if you install it correctly you can then make your system up-to -date from synaptic>refresh and after that mark all updates.When you are done with that updates manager will offer yo to upgrade to 11.04.Do that if you want to or just play with 10.10 for a while.

---

### Post by robert shearer on 2011-05-09
Let us step through slowly...

you have set boot order in bios so as cd boots first but this seems not to have taken.
Try powering down the laptop then unplug from the mains, remove the battery and go have a coffee.

Give it 15 minutes or more then power on again and see if it will boot from cd.

Post result.

Has the laptop capability to boot from usb ??  if the cd drive has failed then you can make a usb installer and use that.
Your ram total is a little light and as the last poster said a lighter distro would be more useful.
Lubuntu is a good choice for starters.Something more up-to date too.  8.10 is no longer supported, try 10.04 for a stable supported release.

---

### Post by misoramen on 2011-05-09
thanks guys. i am running lubuntu 11.04 now ;)

i had iso files linked to winrar so i (naturally #-o) unzipped them before burning the CD :rolleyes:

---

### Post by zvacet on 2011-05-10
Welcome to Ubuntu! :popcorn:

---

### Post by misoramen on 2011-05-10
the plot thickens...

so i had lubuntu 11.04 running like you suggested but i do love my GUIs so i chanced installing Mint - it was fantastic for about 60 seconds until my CPU hit 100% and everything slowed to a crawl

seems to be because of the intel 830m graphics card which is not supported (too old?)

so i gave up - i'm back to XP:-| downloaded the driver easily and it's... ok

---

### Post by iponeverything on 2011-05-10
any version is better than XP IMO. 

don't limit yourself.

---

### Post by misoramen on 2011-05-10
yeah, maybe you're right - i'm having the same problem with XP](*,)

---

### Post by zvacet on 2011-05-11
@ **misoramen**

>  i'm having the same problem with XP

So, isn't Ubuntu better choice in that case? :)

---

### Post by misoramen on 2011-05-12
yes

---

### Post by misoramen on 2011-05-17
only AVI files seem to work (on linux mint 9):???:

---

### Post by misoramen on 2011-05-30
so it must be a hardware problem - is there something new being used for video these days? something that needs more memory/cpu?

anyway, looks like i need a new laptop:(

---

