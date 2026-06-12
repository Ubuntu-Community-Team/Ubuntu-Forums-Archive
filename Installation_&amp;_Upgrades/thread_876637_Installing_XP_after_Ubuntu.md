---
title: "Installing XP after Ubuntu?"
date: 2008-07-31
forum: Installation &amp; Upgrades
---

### Post by KaktusJak on 2008-07-31
I have installed Ubuntu Hardy awhile ago, and I love it.  Unfortunately, there are some programs on windows that I miss, and do not work on Ubuntu, so I tried to find out how to install Windows XP as a secondary OS.

I have tried looking up how to do this on the web, but could only find how to install Linux when windows was already installed via live CD, and how to edit GRUB after both OS's are installed.  I really have no idea how to get XP on, could somebody please help? :)

Info you might need (?):

Ubuntu partition takes up all memory (except the 3 gigs for the swap), but I can't resize it to leave space for windows, but maybe that can be done during installation?

---

### Post by tuxxy on 2008-07-31
I prefer to install windows first, could you not backup and do a fresh window install.

---

### Post by collier on 2008-08-01
I have installed Ubuntu alongside Windows several times.
Because Windows takes control I find it better to install Win first, let it think it is incontrol, then install Ubuntu.  The partitioner in the Ubuntu install process is very good and reliable.  It will happily make a partition for Win, one for swap, another for Ubuntu OS, another for /home if you wish, and another for shared use by both OSs for your data.  You may find that you need to use logical partitions rather than primary partitions so as to overcome the limit of four primary partitions per hdd.

---

### Post by Living2007 on 2008-08-01
> **KaktusJak said:**
> I have installed Ubuntu Hardy awhile ago, and I love it.  Unfortunately, there are some programs on windows that I miss, and do not work on Ubuntu, so I tried to find out how to install Windows XP as a secondary OS.

I have tried looking up how to do this on the web, but could only find how to install Linux when windows was already installed via live CD, and how to edit GRUB after both OS's are installed.  I really have no idea how to get XP on, could somebody please help? :)

Info you might need (?):

Ubuntu partition takes up all memory (except the 3 gigs for the swap), but I can't resize it to leave space for windows, but maybe that can be done during installation?
You could try running Wine on your favorite Windows programs on Ubuntu instead on trying to go ahead and install windows!

---

### Post by logos34 on 2008-08-01
Here you go:
[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by KaktusJak on 2008-08-01
I would like to just install Windows and then install Ubuntu again, but it took my dad forever to figure out how to get the wireless card for my internet working, so I don't want to put him through that again for my selfish reasons.  Also I don't have wired internet so I'd have no access to any help online while trying to get the wireless card working.

Also, WINE cannot run some programs I want successfully, such as Mindstorms and GZDoom, so that is why I want Windows installed as well.

Plus thanks for the link to that tutorial; I've been searching online for hours and still couldn't find anything!  I'll see if I can do it.

---

### Post by Vahids on 2008-08-01
it's very easiy install XP by boot CD 
then by live CD ubuntu come up and the you have to configure grub in terminal.

---

### Post by collier on 2008-08-01
In my experience GRUB has always configured itself.  Control over its appearance and operation is available through a package called StartUp Manager which is available through Synaptic.
So far as configuration of your wireless network adapter is concerned, I have had trouble there too.  But if you have the network connected and turned on when you install Ubuntu, usually it will be recognised and properly configured during installation.

---

### Post by KaktusJak on 2008-08-06
The thing is, Collier, it didn't recognize the wireless card, I had to find the driver in my Windows CD then install it on Ubuntu.

OK, now I have a strange problem with the live CD I have.  I boot the computer from the CD, and first the language menu pops up.  I select English, then on the menu scren, "Run Ubuntu Without Making any Changes to Your Computer", then my CD runs for a couple of seconds, then...nothing.  The CD stops, and I'm left to move up and down through the selections again.  None of the other options in the menu work, but the F key options do, and trying to boot from an alternate option using F4 doesn't work either.

Please help?

---

### Post by collier on 2008-08-08
That was my problem too.  Here is the link that saved my bacon.
[https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3](https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3)
Hope this will ease your unease about installing Windoze first . . .


I have had similar difficulty with the live CD for Hardy.  I kept playing and found one of the F4 options that worked.

---

