---
title: "Re-install Using Downloaded apt pkgs or Fix Upgrade?"
date: 2012-01-07
forum: Installation &amp; Upgrades
---

### Post by ledpepper on 2012-01-07
Hi All,

Firstly, I'd like to mention the Ubuntu forums are an amazing source of information and I take my hat off for all those that contribute.

Points to note before I begin:
[LIST]
[*]You are using Ubuntu 11.04 - the Natty Narwhal 
[*]I'm using a laptop, all drivers are compatible
[*]It has an ATI card, hence additional drivers were needed
[*]I used the following posts for all recovery options:
[*][INDENT][[all variants] Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535") (To recover from startup hang at "Battery stats" etc)[/INDENT] 
[*][INDENT]Google, discovered the option 'nomodeset' which helped me often and got help from every post, blog and random tweet![/INDENT]
[*][INDENT][Other ATI steps from the Graphics Resolution Sticky]("http://ubuntuforums.org/showpost.php?p=10950714&postcount=334")[/INDENT]
[*][INDENT][Create a Packages.gz file for transfer of all update packages]("https://help.ubuntu.com/community/Repositories/Personal")[/INDENT]
[/LIST]

I'm writing this from my Ubuntu 11.4 upgrade. I upgraded via the cmd line from 10.4 to 10.10 by editing */etc/update-manager/release-upgrades* and then using apt-get. This was ~777mb's. Please note I'm severely limited in bandwidth and was rather upset that, even after a lot of research I still had to move from release to release ~1.4GB's instead of 10.4 to 11.4. So if I went about this the wrong way then please enlighten me!

10.4 to 10.10 upgrade was successful including the bootup with the pre-existing ATI drivers.

The upgrade from 10.10 to 11.04 was done via the Package Update Manager and installed without errors. I then encountered Grub problems and the ATI driver issues with failing fallback graphics and startup hangs. A WORKAROUND was using '*nomodeset*' and following MAFoElffen's GFX sticky. This took me all night, basically because I was doing the same thing over and over, expecting a different result. I needed to rollback a kernel on each reboot and use *nomodeset* etc even after all of MAFoElffen's instructions.

I had a working Unity desktop and full GPU support, however I was not happy that I had to use extra kernel parameters. It just didn't feel clean :). Does that make me pedantic? :P

Anyways, after ignoring Einstein's quote > Insanity: doing the same thing over and over again and expecting different results. I carried on playing.

Now, I don't need to use *nomodeset* and have the latest ATI drivers as per MAFoElffen's post. I have however, lost Unity and am back at Gnome Version: 2.32.1. The Style option is correctly set on Ubuntu login.

Phew, breathe and stay with me guys.

My brand new, first and only install of Ubuntu now feels abused and I'm feeling a reformat/reinstall is in order. I can't afford to download the 700mb ISO which should've been my first choice had I not already had a 10.04 ISO. So I've repackaged my */var/cache/apt/archives* folder using the Ubuntu Help article linked above and have moved it to my Ext. HDD.

**To summarise**: Do you help me to fix my current installation issues or help to make sure I have repackaged my update packages correctly for a reinstall?

I'm rather savvy with Centos CLI but not desktop GUI's or Debian (1st Time). I have fortunately haven't run into any major changes between Deb and Centos that Google hasn't solved for me. I'm a Centos network admin so please don't hold back when explaining to me. If I don't understand mighty Google will help!

---

