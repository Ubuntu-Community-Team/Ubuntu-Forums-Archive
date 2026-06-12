---
title: "No Audio With Asus P5NE-SLI (ALC883)"
date: 2011-12-28
forum: Installation &amp; Upgrades
---

### Post by robn30 on 2011-12-28
Ok this is really frustrating me.  I can't get audio no matter what I try.  Everything seems to look ok but no audio makes it to the speakers.  Works fine in Windows BTW.  So I know the MB is working fine.  I see online there is all sorts of issues with ALC883.  Can anyone point me to the right area to get this resolved.  I am at my wits end.  I have tried the alsa.conf file and tried various model= variables, and none have worked.  Please someone help me get this fixed!  Thanks.

---

### Post by robn30 on 2011-12-28
Somebody Please, I am so frustrated.  Need Sound.

---

### Post by drackololord on 2011-12-29
Hi [robn30]("http://ubuntuforums.org/member.php?u=864597")

Couple of quick questions to get started:

[LIST=1]
[*]What version of Ubuntu are you running? 32 or 64 bits??
[*]Which Windows version are you running? 32 or 64 bits??
[/LIST]
Is it this right?


Realtek ALC883  6  -Channel  CODEC 
 Coaxial / Optical S/PDIF out ports 
Support Jack-Sensing, Enumeration, Multi-streaming


The specifications works great, is this web right?


[http://www.asus.com/Motherboards/Intel_Socket_775/P5NE_SLI/#specifications](http://www.asus.com/Motherboards/Intel_Socket_775/P5NE_SLI/#specifications)

---

### Post by robn30 on 2011-12-29
I am using 32 bit for both.  Everything else you said is also correct about my MB.  Also to add to this issue, I also have a old Sound Blaster Live card and have installed that in the PCI slot.  This card will not work either.  It works fine in another machine running Ubuntu 11.10 and the alsa.conf files look the same.  Futhermore I even reinstalled the machine with just the SB Live card enabled and the onboard audio disabled and the sound was working perfect during 11.10 installation.  Then upon first boot into Ubuntu I had no sound once again.  This is really crazy stuff.  For sound to be working during the installation process but then to break after installation is complete, its crazy.  The alsa.conf file even has the correct driver identified as emu10k1.  Not sure where to go from here.  I am becoming very frustrated and am wanting to throw in the towel on Ubuntu, although I love it.

---

### Post by robn30 on 2011-12-29
Also just to add I did a lspci -v and here is the result showing the 2 instances of SB Live

03:06.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
    Subsystem: Creative Labs CT4780 SBLive! Value
    Flags: bus master, medium devsel, latency 32, IRQ 16
    I/O ports at ac00 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: EMU10K1_Audigy
    Kernel modules: snd-emu10k1

03:06.1 Input device controller: Creative Labs SB Live! Game Port (rev 0a)
    Subsystem: Creative Labs Gameport Joystick
    Flags: bus master, medium devsel, latency 32
    I/O ports at a800 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: Emu10k1_gameport
    Kernel modules: emu10k1-gp

Not sure if that helps anything but I figured I would include it.  Also did aplay -l and the following was the result.

**** List of PLAYBACK Hardware Devices ****
card 0: Live [SB Live! Value [CT4780]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Live [SB Live! Value [CT4780]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Live [SB Live! Value [CT4780]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by robn30 on 2011-12-29
Latest update.  After realizing that sound works during installation it had to be an update that was fragging it.  So I installed Ubuntu without any extras at all and sound worked.  As soon as I installed updates again no audio.  I think it was after the 280 updates plus the NVidia update that broke the audio.  I am ready to throw this damn machine out the window and forget about Ubuntu unless someone can enlighten me to what the freaking issue is.  Again I now know why Windows was created.  If your not a programmer or Unix Guru then Ubuntu is going to kick your a**.

---

### Post by robn30 on 2011-12-29
Bump.  Still can't get it working.  Of the 280 updates which one is going to cause this issue.  Also if I have not mentioned yet, I can also use the Try Ubuntu Option from my flash drive and everything works perfect there as well.  So it is definitely an update issue that is breaking sound.  Out of 5 installations this is the only one causing this type of issue.  I guess using Ubuntu with ALC883 NVidia MCP51 chips is problematic.

---

### Post by lidex on 2011-12-31
Sorry for your distress. Can you provide more info. Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by robn30 on 2012-01-01
> **lidex said:**
> Sorry for your distress. Can you provide more info. Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```Choose the upload option and provide a link for the output.

Unfortunately I don't have the machine here right now but as soon as I get back to it I will run that command and post back.  I very much appreciate the info and hopefully it can help me get this thing up and running eventually.  Thanks.

---

### Post by robn30 on 2012-01-02
Ok here is the link to the information about the sound devices.  Sure does give a lot of info.  Hopefully it will help. 
[http://www.alsa-project.org/db/?f=f431aa0f76bf4232f6edfa0e4444b75f4dc2422c](http://www.alsa-project.org/db/?f=f431aa0f76bf4232f6edfa0e4444b75f4dc2422c)

I tested this link and it works.  Thanks in advance for any advice you can provide.

---

### Post by Magnetron1 on 2012-01-02
> **robn30 said:**
> Ok here is the link to the information about the sound devices.  Sure does give a lot of info.  Hopefully it will help. 
[http://www.alsa-project.org/db/?f=f431aa0f76bf4232f6edfa0e4444b75f4dc2422c](http://www.alsa-project.org/db/?f=f431aa0f76bf4232f6edfa0e4444b75f4dc2422c)

I tested this link and it works.  Thanks in advance for any advice you can provide.


I had a similar loss of sound on one of my PCs and here's what fixed it...
[http://www.upubuntu.com/2011/11/how-to-fix-no-sound-after-login-on.html](http://www.upubuntu.com/2011/11/how-to-fix-no-sound-after-login-on.html)

---

### Post by robn30 on 2012-01-02
> **Magnetron1 said:**
> I had a similar loss of sound on one of my PCs and here's what fixed it...
[http://www.upubuntu.com/2011/11/how-to-fix-no-sound-after-login-on.html](http://www.upubuntu.com/2011/11/how-to-fix-no-sound-after-login-on.html)

Not sure this will work for me as I believe I have no sound at all.  When I go to system setting-->then sound and perform speaker test, I get nothing at all.  It is not an issue of not hearing the login sound.  I believe the sound is broke completely.  Not sure I want to try this fix yet as I dont want to mess anything up.  BTW when I mean broke I dont mean the MB, I mean the drivers that allow sound to occur.  As stated previously sound works until I install the latest updates for Oneiric 11.10.

---

### Post by lidex on 2012-01-03
Don't see anything in your alsa-info. Try step one on this page:
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

---

### Post by robn30 on 2012-01-03
> **lidex said:**
> Don't see anything in your alsa-info. Try step one on this page:
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

Thanks for checking it out.  This issue is really crazy.  Step 1 did not seem to fix the problem.  At this point it is looking more and more like Windows 7 will be the way to go.  It's a real shame because I hate to do that but it seems I have exhausted all other means.  It shouldn't be this difficult to make something as simple as sound work.  Never have I had these issues with Windows.  Of course other issues come with Windows but Linux is clearly only for Super Users when problems arise.  The normal user has no way to fix these things.  I don't believe I had these issues with previous releases of ubuntu.  Oneiric seems to be the most problematic yet.  Really a shame as I love Ubuntu and really want to use it and have my family use it as well.

---

### Post by robn30 on 2012-01-04
I have not tried headphones yet.  Is that worth a try.  This issue is just weird.  I have never experienced anything like this ever.  I can't imagine Ubuntu not working with ALC883.  Anybody have any other thoughts on what I can try.  Thanks.

---

### Post by robn30 on 2012-01-07
Well I found out what was causing the issue.  It was the NVidia Display Driver that you can install from the additional drivers software.  I have reinstalled and done all updates and all is still good.  I have not done the NVidia Driver installation because it breaks my sound for some reason.  Not sure why this happens or if will still happen after doing all the updates, but I think I will just go with the default display drivers.  Has anyone else had this happen to them and why is it happening?  Either way I am happy that this installation is now working.  Not going to say this is solved yet as I am unsure if the issue still exists.  Maybe I will give it a shot as I have backed up my current installation and if it breaks sound again I can just reinstall from my backup.

---

### Post by robn30 on 2012-01-16
It still breaks as soon as I apply the NVidia Driver and then restart.  If I then remove the driver the sound comes back.  So it is 100% the Nvidia Driver causing the sound to break.  Pretty weird if you ask me.  Would be nice to get this working and am hoping someone more experienced than me can help me out.  I also tried all 4 versions of the Nvidia Driver available from the Additional Driver Application.  Thanks for anyone who can provide me some guidance in regards to this problem.

---

### Post by robn30 on 2012-02-25
Ok so I have tried this Nvidia Driver install yet again and you guessed it, the same result, broken sound.  I do have an update to report and that is the front panel headphone does provide perfect sound.  Left and right ear are perfect when I plug in headphones.  Its just the speakers built into my Asus Monitor that will not work.  Of course they work perfect before the application of the Nvidia Driver.  After reboot is when the sound breaks.  This is such a mind boggling issue and really frustrating.  Out of all the machines I have running Linux, this is the only one with this issue.  I really wish I could get it squared away.  Next I am going to remove the Nvidia Driver and see if I have sound both at the speakers and with headphones.  Hopefully someone can come up with something that may help given this new data.  Thanks.

---

### Post by robn30 on 2012-02-25
> **robn30 said:**
> Ok so I have tried this Nvidia Driver install yet again and you guessed it, the same result, broken sound.  I do have an update to report and that is the front panel headphone does provide perfect sound.  Left and right ear are perfect when I plug in headphones.  Its just the speakers built into my Asus Monitor that will not work.  Of course they work perfect before the application of the Nvidia Driver.  After reboot is when the sound breaks.  This is such a mind boggling issue and really frustrating.  Out of all the machines I have running Linux, this is the only one with this issue.  I really wish I could get it squared away.  Next I am going to remove the Nvidia Driver and see if I have sound both at the speakers and with headphones.  Hopefully someone can come up with something that may help given this new data.  Thanks.

After removing the driver I now have sound at both the speakers and the headphones.  I should note that if I plug in the headphones I still have sound at the speakers as well.  I just also hear it through the headphones as well.  I am sure I can mute the speakers somehow with alsamixer or something, but the short of it is the sound is working with the Nvidia driver removed.  With the driver activated I only get headphone sound.  Ok thats all I have, hopefully someone can help me out.  Thanks again.

---

### Post by robn30 on 2012-03-31
Still have not been able to fix this issue.  Should I try removing the Alsa and Pulse audio drivers and installing the Realtek Drivers from their site?  This is so frustrating to me and I really want to get it working.  If so is there a tutorial for installing the Realtek Drivers?  Thanks.

---

### Post by robn30 on 2012-03-31
I put the Sound Blaster Card back in and it is the same, except it plays absolutely no sound.  At least the onboard audio worked at the front panel headphone jack.  I also reinstalled all Alsa and Pulse Audio components.  I am reposting my Alsa Info again in hope that someone can take a look at it and see if anything looks incorrect.  This first post is with the Nvidia Driver installed and using the SB Live Card w/ onboard audio disabled in BIOS. Next I will post with Nvidia Driver removed w/ SB Live. After that will be Onboard audio w/ Nvidia Driver.  Last I will post onboard audio w/o Nvidia Driver.  Keep in mind the audio works fine in the last configuration.  Once I remove the Nvidia Display Driver the onboard audio will work.  So here is the link to the first attempt.

[http://www.alsa-project.org/db/?f=f2b5958e70c68caa007cabd1663e8ae910b3eaf3](http://www.alsa-project.org/db/?f=f2b5958e70c68caa007cabd1663e8ae910b3eaf3)

---

### Post by robn30 on 2012-03-31
Result of first test is that the sound starts working after Nvidia Driver removal and reboot.  Here is the Alsa Info with SB Live w/o Nvidia Driver.

[http://www.alsa-project.org/db/?f=e93270b2e41e5a39e75b2703fe7cc210eeca7c39](http://www.alsa-project.org/db/?f=e93270b2e41e5a39e75b2703fe7cc210eeca7c39)

---

### Post by robn30 on 2012-03-31
Onboard audio w/ Nvidia Driver installed.  Result is front panel headphone audio only.  Alsa Info below

[http://www.alsa-project.org/db/?f=737c52c16f972d6866cab412f9d7d669aecc1cf9](http://www.alsa-project.org/db/?f=737c52c16f972d6866cab412f9d7d669aecc1cf9)

---

### Post by robn30 on 2012-03-31
Last but not least, onboard audio w/o Nvidia Driver.  Of course as soon as I reboot audio returns perfectly.  Alsa Info below.  I still have the SB Live card in but it is not being used.

[http://www.alsa-project.org/db/?f=d19a859d903008f9380bb00473f0a109d137f51c](http://www.alsa-project.org/db/?f=d19a859d903008f9380bb00473f0a109d137f51c)

---

### Post by robn30 on 2012-04-01
Bump, any other ideas on this.  Thanks.

---

### Post by Rockstarever on 2012-12-16
type in terminal alsamixer press enter. now press F6 to select the card select the appropriate card and u have doe. it must be mainly due to change in driver config after the upgrade. hope this helps.

---

