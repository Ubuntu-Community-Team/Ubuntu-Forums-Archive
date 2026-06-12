---
title: "upgrade to 8.04 now my nivida card is gone?"
date: 2008-04-19
forum: Installation &amp; Upgrades
---

### Post by nacho32 on 2008-04-19
help I went from 7.10 to the 8.04 beta and after I upgraded my 7300gs nivida card is gone and my resolution is at 640 x 480 , it worked before upgrade what happened ? please help

---

### Post by Czar on 2008-04-19
ditto

---

### Post by Pumalite on 2008-04-19
You might have to reinstall the driver.

---

### Post by Czar on 2008-04-19
> **Pumalite said:**
> You might have to reinstall the driver.

uninstalled, reinstalled.. the hard-ware driver manager stats 'in use' with a green light.. Yet on boot I get a message about running in low graphics mode.

---

### Post by giruzz on 2008-04-19
> **Czar said:**
> uninstalled, reinstalled.. the hard-ware driver manager stats 'in use' with a green light.. Yet on boot I get a message about running in low graphics mode.

In my case I had to manually find a backup copy of xorg.conf and replace the one that was used at the time.

The system put a xorg.conf that had only 640x480 or lower for my monitor. I don't know why this happened. I didn't know how to put manually fix the xorg.conf and so I took my chance and deleted the one in use to replace it with an older backup copy.

g.

---

### Post by Czar on 2008-04-19
> **giruzz said:**
> In my case I had to manually find a backup copy of xorg.conf and replace the one that was used at the time.

Could you paste the rez/display section?  I really don't want to type out the missing ones.  ;-x

---

### Post by giruzz on 2008-04-19
> **Czar said:**
> Could you paste the rez/display section?  I really don't want to type out the missing ones.  ;-x

Not sure this will help but you can try:

```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

```

---

### Post by nacho32 on 2008-04-19
ok got everything to work I installed this excellent program that installs the video card drives for me it worked like a charm. even found my tv card to a must have:)
[ENVY]("http://albertomilone.com/envyngfaq.html#A")
[http://albertomilone.com/envyngfaq.html#A](http://albertomilone.com/envyngfaq.html#A)

---

### Post by mophead740 on 2008-04-21
i have a 7300gs and i cant even get it to install because when i try to boot into the live disc, or even do a "vanilla" install i get all these funny colours showing up after the ubuntu logo.

any ideas.

wasnt sure wer to post this but it seems appropriate as everyone here has a 7300gs.

my comps other specs are amd s939 3200+
gigabyte k8nsli mobo (nforce4 sli)
1 gb corsair value ram
80gb and 400gb hdd
16x dvd burner.

not really sure what the issue is here but i figured it must be the display adaptor.

could it be that my primary monitor is connected via dvi?

---

### Post by FredB on 2008-04-21
As xorg.conf syntax changed between gutsy and hardy, it could be a xorg.conf problem.

Try using restricted driver manager. It could help.

---

### Post by Vic Morgan on 2008-04-22
Hi,
I've been bogged down with a similar problem for a couple of days now. Tried installing Nvidia drivers all ways (but recommend EnvyNG) and it appeared that neither the driver nor the utilities were installed. Forever booting up into low graphics mode. 
I now think that the updated configuration is just not being written to the /etc/X11/xorg.conf file, so regardless of all the downloads, etc. it's losing the configuration on reboot.
When I try to save the Nvidia configuration of xorg.conf I get

Unable to remove old X config backup file '/etc/X11/xorg.conf.backup' 

I don't know why this is happening - does anyone know? File permissions? Script errors?

---

### Post by Czar on 2008-04-22
> **Vic Morgan said:**
> Hi,
I've been bogged down with a similar problem for a couple of days now. Tried installing Nvidia drivers all ways (but recommend EnvyNG) and it appeared that neither the driver nor the utilities were installed. Forever booting up into low graphics mode. 
I now think that the updated configuration is just not being written to the /etc/X11/xorg.conf file, so regardless of all the downloads, etc. it's losing the configuration on reboot.
When I try to save the Nvidia configuration of xorg.conf I get

Unable to remove old X config backup file '/etc/X11/xorg.conf.backup' 

I don't know why this is happening - does anyone know? File permissions? Script errors?

Same issues.. what I did to finally fix was.  1)  Re-added my user account to group video.  2)  fixed the broken grub menu opt dealing with kop loading 7.1's kernel 3) deleted all nvidia.ko modules created by the different nvidia installations/dkms 4)  purged every single thing named nvidia, kernel source, & envy.  re-installed envy and made sure the ppa.launchpad.net archive was being accessed for the latest sources and re-installed envy...

After a reboot Nvidia is working (along with rendering) yet the xorg.conf is default without any nvidia information... *shrugs*

---

### Post by Vic Morgan on 2008-04-22
Thanks Czar. I don't think my problem is with the drivers because its just the settings that are lost. For some reason the changes are not being written to xorg.conf and I can't work out why. Other threads would seem to point to the machine reading from another xorg.conf file, perhaps written or stored elsewhere - changes to fstabs and boot images were mentioned - but that's starting to get heavy for a newbei like me.

---

### Post by Vic Morgan on 2008-04-22
Thanks Czar. I don't think my problem is with the drivers because its just the settings that are lost. For some reason the changes are not being written to xorg.conf and I can't work out why. Other threads would seem to point to the machine reading from another xorg.conf file, perhaps written or stored elsewhere - changes to fstabs and boot images were mentioned - but that's starting to get heavy for a newbie like me.

---

### Post by Vic Morgan on 2008-04-26
Just for information, I got so desperate that I wiped my disk and loaded a new Hardy. There still appears to be something amiss, even on a new install. However, I note that Gparted has no problem detecting my nNvidia card and going to high resolution without any interaction from me!

---

### Post by earther on 2008-04-26
I have been having an issue with nVidia 8400GS in a Virtual Box installation of Hardy.  I was stuck at 800 x 600 or lower even after installing the guest additions.  Since I also had Gutsy in Virtual Box, I just copied most of Gutsy's xorg.conf file and it worked even though the syntax is different. Go figure.

---

### Post by Jungle-Cat on 2008-05-18
Hey,
If I enable nvidia drivers via restricted drivers manager, my computer boots into low graphics mode. If I disable them, then at the "warning; low graphics..." set resolution etc then reboot, everything is fine but I am not using the nvidia drivers.

The screen is also shifted to the right... would the nvidia drivers correct this issue? 

Should I attempt to use "Envy" to install the drivers?

Thanks

---

### Post by Czar on 2008-05-18
> **Jungle-Cat said:**
> Should I attempt to use "Envy" to install the drivers?

Enable the Hardy-Proposed repo and install Envyng-gtk, then install your Fx driver.

---

### Post by emshains on 2008-05-18
I had a problem like this. I fully reinstalled my system, after I made backups, and the problem was solved. It was kind of long with all the backup-transfering, but it was quite easy to do.

---

