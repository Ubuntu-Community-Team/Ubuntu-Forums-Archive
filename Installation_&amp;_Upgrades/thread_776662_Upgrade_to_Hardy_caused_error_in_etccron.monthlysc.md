---
title: "Upgrade to Hardy caused error in /etc/cron.monthly/scrollkeeper"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by davidkahn on 2008-04-30
I received an e-mail:

Subject:
[INDENT]Anacron job 'cron.monthly' on CERTIBY1
[/INDENT]Message:
[INDENT]/etc/cron.monthly/scrollkeeper:
///usr/share/gnome/help/blackjack/el/blackjack.xml:402: parser error : Entity '&#914;&#959;&#942;&#952;&#949;&#953;&#945;' not defined
                  <para><guimenuitem>&#928;&#961;&#959;&#964;&#953;&#956;&#942;&#963;&#949;&#953;&#962;&&#914;&#959;&#942;&#952;&#949;&#953;&#945;;</gui
                                                                           ^
[/INDENT]The contents of line 402 in /usr/share/gnome/help/blackjack/el/blackjack.xml is:
[INDENT]                  <para><guimenuitem>&#928;&#961;&#959;&#964;&#953;&#956;&#942;&#963;&#949;&#953;&#962;&&#914;&#959;&#942;&#952;&#949;&#953;&#945;;</guimenuitem>&mdash; &#913;&#965;&#964;&#972; &#945;&#957;&#959;&#943;&#947;&#949;&#953; &#964;&#959; <interface>&#916;&#953;&#940;&#955;&#959;&#947;&#959; &#928;&#961;&#959;&#964;&#953;&#956;&#942;&#963;&#949;&#953;&#962;</interface>, &#949;&#960;&#953;&#964;&#961;&#941;&#960;&#959;&#957;&#964;&#945;&#962; &#957;&#945; &#961;&#965;&#952;&#956;&#943;&#963;&#949;&#964;&#949; &#964;&#959; &#960;&#945;&#953;&#967;&#957;&#943;&#948;&#953;.</para>
[/INDENT]
It looks like Greek to me. :confused: 

There have been no other symptoms, though someone else has reported that they had a similar message and Synaptic Package Manager is failing -- though it seems okay on my computer.

Thanks.

David

---

### Post by hardmath on 2008-05-12
Today I got the same error reported above during an upgrade from Edgy to Hardy Heron.  There were also some XML errors reported during the subsequent configuration of ekiga that also mention scrollkeeper (in particular tag errors in file scrollkeeper_extended_cl.xml for various language/locale subdirectories).  

The particular error configuring ekiga:

```
subprocess post-installation script returned error exit status 134

```

seems to be a verified (but unresolved) bug.

Although I got a dialog box popped at the end of installation that warned the system might be in an unstable state (and that Update Manager was not successfully configured), my system (an AMD64 based HP laptop) reboots into Hardy Heron successfully (and the Update Manager and Blackjack software seem to be working).

regards, hardmath

---

### Post by seismicmike on 2008-05-14
I'm trying to run an upgrade from 7.10 to 8.04 as I write, and a while ago it game me some parse error about scrollkeeper, saying that some parameter in some file wasn't set. It pretty much looked like that same Greek/Alien language mumbo jumbo to me. As a result, many vital packages were not able to be installed because of dependnecy problems (stuff like ubuntu-desktop, gnome, nautilus... u know... just the side stuff) So I'm anticipating not being able to use this computer after the upgrade completes.

Was this possibly the biggest oversight in Ubuntu history? Anybody else have this problem?

This is a major WTF

---

### Post by LinkinCable on 2008-05-18
I had the same error while going from ubuntu 7. to 8. so i let it finish with all the errors (skrollkeeper), So it booted magicaly so i went ahead to surf for a fix then i had to go to my website, it has flash! so i added it in the plugins and then the whole thing started (upgrade) =) but this time it went thru (all packs well installed even scrollkeeper)


try and add a package and see if it restarts..

---

### Post by e_racer1999 on 2008-05-19
Same thing here. Going from Gutsy to Hardy and my Gutsy froze during the "installing" portion of the upgrade process. I had to force restart and now I have 2 Ubuntus in GRUB (14 & 16) and niether boots (Gutsy gets to login, then freezes on the peach screen; Hardy freezes on initial status bar). I REALLY hope there's a fix to this, 'cause now I'm forced to run *spew* Vista. I D/L'ed Hardy to an ISO and am planning on a reinstall, but I don't want to erase all of my stuff on my Gutsy :(

---

### Post by davidkahn on 2008-05-22
e_racerr

Have you tried booting Gutsy in recovery mode?

If that works, perhaps you could restart the upgrade to Hardy.

David

---

### Post by e_racer1999 on 2008-05-23
> **davidkahn said:**
> e_racerr

Have you tried booting Gutsy in recovery mode?

If that works, perhaps you could restart the upgrade to Hardy.

David

I actually burned a bootable Hardy disc, popped it into the drive, and am successfully (hopefully) running recovery mode in Hardy. I never added a "/home" partition because I was dual-booting Vista, so it has already taken 5 days in recovery and I expect it to take 2 more. Once this install is fixed, you can bet I am redoing my partitions!

---

### Post by e_racer1999 on 2008-05-30
Not to thread-jack, but my hard drive is STILL running recovery mode. How long should this take? It's only a 60GB hard drive with 30GB for Linux!

---

