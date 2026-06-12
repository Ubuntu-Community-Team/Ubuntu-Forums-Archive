---
title: "Upgrade from 11.10 to 12.04 - Upgrade did not complete"
date: 2012-05-13
forum: Installation &amp; Upgrades
---

### Post by JonUK76 on 2012-05-13
Upgrading from 11.10 to 12.04, the upgrade process seemed to be going OK, until it stopped on a particular item.  The computer did not crash but the upgrade process simply stopped doing anything (no disk activity).  I left it for a couple of hours to see whether it would recover in some way but no luck.  The only thing I could think to do was  reboot (using the shut down menu).

Prior to shutting down, the terminal part of the upgrade window showed that it was stuck on downloading what appeared to be some MS font files from SourceForge?  There were no dialogue boxes requesting any input from me.

On rebooting, the Grub menu is still intact and I can boot to Windows 7, but Ubuntu does not start.  It goes to a "garbled" log in screen, that does not respond to any mouse or keyboard input.

My questions are:

1) I think I know what the answers going to be, but is there anything I can do other than wiping the Ubuntu partition and re-installing from scratch?

2) Assuming answer to 1) is no, I backed up my /home folder using the Backup program prior to attempting the upgrade.  Is restoring that once 12.04 is installed going to be simple, or is there anything to know in advance?

Thanks

---

### Post by zvacet on 2012-05-13
Boot in recovery mode and try

```
apt-get update && apt-get upgrade
 dpkg --configure -a
apt-get -f install
```

---

### Post by JonUK76 on 2012-05-14
Thank you for the suggestion.  Unfortunately recovery mode would not start, it just went to the flickering, garbled log in screen like the standard boot.  And still had no response to mouse or keyboard input.  I opted to re-install 12.04 from CD and its now working fine, as did restoring my backup.

---

### Post by jadtech on 2012-05-14
most likly the problem was  just this the up grade will stop  and in the back ground on the terminal is a question you have to answer yes or no to there is 2 question of this nature during the up grade ..

just a guess based on what I have  noticed ..

---

### Post by TorMike on 2012-05-14
The same thing happened to me when I opted to upgrade from 11 to 12.

The install simply stopped.

Like you I left the update to install and walked away from my machine.  When I return an hour or so later my screen was completely blank.  Thinking it had gone to sleep while waiting for a response to a question I tapped on the keyboard (usually the means to revile the machine) and waited for the screen to reappear.

Nothing.  I tried the power switch on my machine.  Again, nothing.

I thought maybe there were background jobs needed to complete prior to the screen reappearing so I waited a few minutes.  Nothing.

The only option, power off and hope the reboot would 'fix' the problem.

Three days later after I completely rebuilt the 11.10 O/S from CD I recovered my server.

Something maybe amiss with this upgrade procedure.  Until then, I'm staying with 11.10.

---

### Post by ricflomag on 2012-05-14
@JonUK76 : It is a little known fact, but you can reinstall ubuntu on top of your previous ubuntu install without formatting the root partition. Your home folder will not be touched. So you can create a user with the same name, same password, and you will even find that, in case you had an encrypted home folder, the new install will use it as if nothing had happened. It's now my preferred way of upgrading ubuntu :)

---

### Post by jackluu on 2012-05-14
I had the same problem and I just reinstall it. From my experience, you should have a separate partition for you home folder. This way, you won't lost any software configuration and preference. The only things left to do are to install the softwares :)

---

### Post by rpaskudniak on 2012-05-14
I had a similar experience:

When I came back to it in the morning, I found my desktop with all the icons intact but no prompt, no sign that an upgrade had taken place, no prompts.  Strange but I figured it would automatically prompt me for any incomplete updates upon the next boot.

Ah, no such luck: When I rebooted, I got the Grub menu.  But instead of the nice white on blue, squint-mode font, I got the old-looking white on black font. (I don't recall how I got that into the nice display mode.)  That was just the harbinger of things to come.  And come they did: Whether I chose Windows or Linux, it responded with "No such partition" (Or was it "Partition not found"? I forget.)

SIGHhhh.. Again?  This is a variation of what has happened to me nearly EVERY time I upgrade.  Until now I didn't even get the Grub menu!  (Oh yes, 11.04->11.10 ran without a hitch.)  Here we go again!

So, after using the Gparted-Live CD to insure that my partitions were all still in place, I went back to the Windows-7 installation CD and ran "bootrec /fixmbr" in a command window.

My PC now boots straight into Windows, *sans* Grub.  When I have time I will use the Ubuntu-secured live CD to repair the grub. I have the printed doc of how to do this, though I wish I had printed it full size.  (My eyes aren't as sharp since I was poisoned and stabbed in 1917. :p )

---

### Post by ricflomag on 2012-05-14
> **jackluu said:**
> I had the same problem and I just reinstall it. From my experience, you should have a separate partition for you home folder. This way, you won't lost any software configuration and preference. The only things left to do are to install the softwares :)

A separate partition for the home folder is not necessary (see my previous comment).

---

### Post by voy108 on 2012-05-15
> **ricflomag said:**
> @JonUK76 : It is a little known fact, but you can reinstall ubuntu on top of your previous ubuntu install without formatting the root partition. Your home folder will not be touched. So you can create a user with the same name, same password, and you will even find that, in case you had an encrypted home folder, the new install will use it as if nothing had happened. It's now my preferred way of upgrading ubuntu :)

OK..now being a really new to the in's and out's of Ubuntu, how do I do this?  I upgraded online from 11.10 to 12.04. It seemed to go OK but on reboot...no wireless nor wired network and cannot revive it. I booted into GRUB and tried "previous Linux version" and voila, got the network working.  Now, how can I tell Grub to boot into that version. It is on menu as "generic" not generic-pae.  I would like to "redo" install from live CD but it wants me to do something about the root directory.  I'm dual booting into Win 7 so am not aware of how to show it where to install.  I indicated the large ext 4 which is where my Unity is but it wanted me to do something about "root".  Obviously I'm lost.  I can run Unity from Grub but have to go thru Previous Linux versions. I'm hoping that a reinstall will correct Grub.  

Any Ideas?

Oh, also, I tried recovery and told it to update Grub...nada.

---

### Post by jadtech on 2012-05-15
you are booting with the previous kernel and all is working  that is ok  to do as long as its working you got wireless and everything else works , not sure you might need to up date grub so it will boot from that kernal  so you dont need to choose it at every boot  .. 

if this is your problem start another thread asking for that help you will get a quicker responce :)

---

