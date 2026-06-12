---
title: "different vista/ubuntu dual boot problem"
date: 2006-09-25
forum: Installation &amp; Upgrades
---

### Post by sublime on 2006-09-25
So I decided to take the plunge and fall into the trap that is Windows Vista RC1.  I should have know it would be nothing but headaches when I initially tried installing Vista and Windows refused to load onto a brand new freshly formatted 160gb hard drive with the only other OS on the system as Ubuntu on a seperate hard drive.  I sallied fourth, and continued attempting to somehow get Vista on my computer by unplugging the Ubuntu hard drive, leaving the only available disk the empty 160gig.  This worked, with the install being rather smooth and suprisingly quick.  After messing with it for a while getting it setup the way I wanted it, I decided to plug my Ubuntu hard drive back in get grub working.  I plugged the hard drive back in, turned the computer on, grub came up, I selected Ubuntu, it booted just as I expected.  After adding the typical Windows boot command to menu.lst I restarted the computer, went into grub, selected Windows and the computer promptly took a giant crap and restarted.  So I went back into Ubuntu, messed around with grub adding just about every booting option I could think of, but still to no avail, it does the same thing.  After doing some reading I found that the prefered method of dual booting vista was to install Vista then Ubuntu.  I decided no big deal, there isn't a lot on my Ubuntu hard drive to backup.  So after a fresh install of Ubuntu, I added the same boot command for Windows as everyone else, rebooted, selected Windows and just as before, it took a giant crap and rebooted.  Now I've been searching for several days on all different kinds of forums and I have yet to encounter anyone else having this same problem.  Does anyone have any ideas?  I assume what's happening is that the new Vista boot loader doesn't play well with grub, however there do seem to be a lot of people actually getting this to work.  So if anyone has any info or help that would be much appreciated.

Thanks

p.s.  Sorry for the lengthy post.  I needed to vent some frustration.

cliffnotes:  When I select the windows line in grub the computer reboots.  I've been searchign like mad and reading up but I can't seem to find anyone with the same problem.

---

### Post by Sarisar on 2006-09-25
There was a story about the new vista loading program putting some security to 'help protect your PC' which also prevents dual booting... but I don't know specifics as I'm not running vista.  I read that it was off by default so don't know if that is your problem or not.

---

### Post by sublime on 2006-09-25
Yeah, I've looked into this.  It is a potential problem as you need the Trusted Platform Module on your motherboard, which mine has, and the driver needs to be installed on Windows, which I did.  I don't recal going through any of the other steps needed to activate it though.  So I don't think I'm using it.  I'm currently in the process of trying to get Windows wroking again, however I wrote grub to the Windows hard drive so simply unplugging the Ubuntu hard drive no longer boots me into Windows, I get a grub error 23 I think it is.  Stupid Microsoft didn't add fixmbr to the repair console for Vista and going through the startup repair wizard doesn't do jack.  I think what I'm gonna end up doing is formatting the Ubuntu drive and copying over anything important to there, then reinstalling Windows.  I'm running out of activation keys so this is not prefered.  Again if anyone has any other information to try, please post up.  I'll wait on the reinstall till later tonight.

Thanks again

---

