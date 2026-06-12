---
title: "No audio after upgrade from 11.04 to 11.10"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by Silmarunya on 2011-10-15
After upgrading to Ubuntu 11.10, audio no longer works on my system. The audio icon still works, the output settings didn't change and so on, but there just isn't any audio whatsoever (it's not hardware related, as Windows 7 still works perfectly fine).

After some googling, two possible solutions came up: delete the .pulse folder and then reboot (didn't work) and removing and reinstalling pulseaudio via sudo apt-get remove/install pulseaudio (also didn't work).

So now what? Suggestions anyone?

---

### Post by jameseqbonner on 2011-10-16
I'm having the same problem. still looking around on the internet though. By any chance, are your youtube/flash videos being played like 5x as fast with no sound as well?

---

### Post by Silmarunya on 2011-10-16
> **jameseqbonner said:**
> I'm having the same problem. still looking around on the internet though. By any chance, are your youtube/flash videos being played like 5x as fast with no sound as well?

No, Flash videos are played exactly the way they should be. Well, without sound that is :( 

Glad I'm not alone though, this might prompt someone who knows more about this stuff than we do to look into it...

---

### Post by niceguy123 on 2011-10-16
I upgraded from 11.04 to 11.10. Audio is working fine but flash plugin is missing. I am using chrome web browser. How do I get the flash working again. I can not run youtube videos.

---

### Post by Silmarunya on 2011-10-16
> **niceguy123 said:**
> I upgraded from 11.04 to 11.10. Audio is working fine but flash plugin is missing. I am using chrome web browser. How do I get the flash working again. I can not run youtube videos.

Are you sure Flash Player is installed (perhaps via restricted extras?). Although normally Chrome doesn't need Flash, it comes packed with it. Can you play YouTube videos in FireFox?

Oh and please don't take this the wrong way, but isn't different problem = different thread?

---

### Post by rikhartti on 2011-10-17
I had the same problem after upgrading from 11.04 to 11.10. No sound in my system whatsoever.

For some reason, my default sound output devide was set to HDMI connector and speakers were set to mute. I have no idea why this happened. :confused:

Check your sound setting. You can change your default output device from the "Output" tab. I managed to fix my system this easily.


EDIT: I just read your opening post again and noticed you mentioned "output setting didn't change". My apologies.

---

### Post by nitetrkr on 2011-10-18
Tried to reset output device - set to dummy audio and has no other options.  Sound worked before upgrade.  Lenovo V570 laptop.

---

### Post by ProntoAnthony on 2011-10-18
I have the same problem on my desktop. After the upgrade ubuntu 11.10 doesn't see an audio device  (sounds page of System Settings), yet sound and my sound device is still working on my laptop after the upgrade.  

My Dell Dimension E521 has an integrated audio controller, a AMD64 Althon chip and 1GB memory.

---

### Post by claytronic on 2011-10-18
I've got the same post 11.10 upgrade problem with System Settings showing no audio device. I can play music but cannot control the volume. (Dell Latitude E6420)

---

### Post by ballantony on 2011-10-19
> **ProntoAnthony said:**
> I have the same problem on my desktop. After the upgrade ubuntu 11.10 doesn't see an audio device  (sounds page of System Settings), yet sound and my sound device is still working on my laptop after the upgrade.  Very strange.


Same here, except for the fact that it sometime appears for no good reason.  Happening on Dell Inspiron 545, two other machines working fine

---

### Post by claytronic on 2011-10-20
Yes, it's very odd behavior. My audio settings started behaving once I got to work this morning and they worked after two full laptop power cycles since.

---

### Post by ProntoAnthony on 2011-10-20
I have a Dimension E521 desktop with an AMD64 Althon processor with 1GB RAM. I must run Unity 2D. Windows show no borders when I run the Unity 3D version. I'm using the 32-bit version of Ubuntu 11.10.

---

### Post by ProntoAnthony on 2011-10-21
Now this is interesting:

I burned an image of 11.10 on to CD. When I booted from the CD the speakers worked fine. When I went back and booted from my hard drive the audio stopped working.

To me this points out that Ubuntu doesn't have a problem with drivers or the audio hardware. It "should" just be a setting buried somewhere...

---

### Post by OldMozzy on 2011-10-21
For general information to the community: :p

I have the same problem too. Although, if I select and deselect the mute option I can hear clicks in the headphones. Audio was fine before the upgrade. Audio is fine under Fedora 15.
System is a custom build:
Stock standard parts, on-board Video, on-board Audio. No overclocking enabled.
A solid and stable workhorse for my photo editing and DTP.
Dual boot Ubuntu 11.10 /Fedora 15
MB Asus M4A88TD-M/USB
CPU AMD Phenom II X4 955
4GB DDR3 RAM
On-board Audio Realtek ACL 892

For me, audio is not an essential thing. It's nice to play a little background music while I'm working though, hence the headphones rather than speakers.

---

### Post by CiaoCiao on 2011-10-22
> **OldMozzy said:**
> 
MB Asus M4A88TD-M/USB
CPU AMD Phenom II X4 955
4GB DDR3 RAM
On-board Audio Realtek ACL 892


I just noticed I am also having the same problem. Upgrade from 10.10 > 11.04 > 11.10.  Audio is not working.

MB Asus M4A88TD-V EVO/USB3
Onboard Audio ACL 892

---

### Post by CiaoCiao on 2011-10-22
My problem is resolved, but I think it is very specific to my situation.  My audio was working with 11.10 prior to the installation of my new video card.  I was using the onboard video (integrated AI radeon HD 4250) and then I installed a new Asus GTX 560 DCU2.

What I did in the bios some days ago was disable my internal graphics. When I turned my internal graphics back on in the bios just now(UMA+Sideport), my audio is working again. My Nvidia GTX560 is still my primary video card.  I only changed this bios option and audio is working again.  I have no clues as to why this worked for me.

EDIT
Ok I have to retract this statement, I have no idea what is on with my computer. My audio started working again and I can not reproduce the problem. Playing with BIOS settings, etc, my audio is always working now.

---

### Post by ProntoAnthony on 2011-10-23
My problem with no appears to be resolved. Logged off Unity and went into Gnome and was able to set the sound. Went back to Unity and the sound is working!

Now when I go to Sound Settings and choose the Hardware Tab, I see "Internal Audio" instead of "Dummy Audio Output".

-----------

Now here it is the next day and my sound is gone again. When go to Sound Settings and choose the Hardware Tab, I see "Dummy Audio Output" instead of "Internal Audio".

---

### Post by OldMozzy on 2011-10-24
This worked for me:

Open a terminal and type *alsamixer*
A graphic mixer console appears. Press F6 to select your sound card, in my case it is listed as HDA ATI SB.
Check that you have coloured bars in the first 3 columns. Left or right arrow selects the columns and +/- changes the height of the bars. 100% is shown as "00" at the bottom of the column. "MM" means that column is muted. If you're using surround sound, then you'll need to enable additional outputs as listed along the bottom of the mixer screen.
Press *esc* to exit the alsamixer and return to the normal text terminal.
type *sudo alsactl store*
(enter your sudo password if it asks).
I did not need to reboot to get sound, but you may need to.

I now have sound everywhere in video, music, Firefox etc. It won't play the "Ubuntu" sound at startup though, but everything else seems to have sound as required.

I hope this helps someone.

:popcorn:

---

### Post by ReFranz on 2011-10-24
I have the opposite problem. The volume is dangerously loud--for the speakers and neighborly relations--after the 11.04 to 11.10 update. Using the Banshee slider also disrupts streaming. Does anyone know if the method in #18 will work for this?

---

### Post by jmcharg on 2011-10-24
As I have been hunting online for a fix to the same problem without any luck I would add my name to this chat!

really disappointing as I have come to think of Ubuntu as very reliable, and for something as basic as audio not to work really is bad!

---

### Post by ProntoAnthony on 2011-10-25
oops

---

### Post by Roti78 on 2011-10-30
I had the same problem, and the solution was to delete this directory:

```
~/.gconf/system/pulse
```

---

### Post by linuxfreak003 on 2011-11-02
> This worked for me:

Open a terminal and type alsamixer
A graphic mixer console appears. Press F6 to select your sound card, in my case it is listed as HDA ATI SB.
Check that you have coloured bars in the first 3 columns. Left or right arrow selects the columns and +/- changes the height of the bars. 100% is shown as "00" at the bottom of the column. "MM" means that column is muted. If you're using surround sound, then you'll need to enable additional outputs as listed along the bottom of the mixer screen.
Press esc to exit the alsamixer and return to the normal text terminal.
type sudo alsactl store
(enter your sudo password if it asks).
I did not need to reboot to get sound, but you may need to.
Thank you thank you thank you.. I can't believe I didn't even think of it since i've encountered stuff like that before. I'm surprised so many people are having problems with this though. All I had to do was change the speaker volume in alsamixer... although I did that in the sound settings as well but it didn't work...

---

### Post by ProntoAnthony on 2011-11-04
I've had repeated bouts with audio problems. Here is what I have figured out what works for me:

Go into GRUB and choose the second entry. I think it is called a diagnostic boot. Choose FSCK, a file system check. Fix any problems with bad sectors and the like. Next choose DPKG to fix any broken packages. Answer Y to the Continue? prompt even if there isn't anything to fix. Finally, choose continue with normal boot.

Running through this procedure has helped me restore sound and assorted other problems.

---

### Post by mortneff on 2011-11-19
[FONT=Times New Roman][SIZE=2]After my install of Ubuntu 11.10 I had NO audio.  The fix that worked for me was to go to sound settings.  Then open the Hardware tab and make sure that the sound device you have installed is the same as the one listed in the profile, under "Settings for selected device" at the bottom of that window.  If it is not the same, click on the drop down next to profile and select the same device name.  I hope this is helpful.[/SIZE][/FONT]

---

### Post by sshhll on 2011-11-22
I follow this instruction from previous post and work for me.
 

Open a terminal and type *alsamixer*
A graphic mixer console appears. Press F6 to select your sound card, in my case it is listed as HDA ATI SB.
Check that you have coloured bars in the first 3 columns. Left or right  arrow selects the columns and +/- changes the height of the bars. 100%  is shown as "00" at the bottom of the column. "MM" means that column is  muted.
if the adjusting first columns didn't work, move to to the right side of the mixer using the keypad, look for the external amp setting .. if it on press "m" to mute the external AMP.. that work for me.
 If you're using surround sound, then you'll need to enable  additional outputs as listed along the bottom of the mixer screen.
Press *esc* to exit the alsamixer and return to the normal text terminal.
type *sudo alsactl store*
(enter your sudo password if it asks).
I did not need to reboot to get sound, but you may need to.

I now have sound everywhere in video, music, Firefox etc. It won't play  the "Ubuntu" sound at startup though, but everything else seems to have  sound as required.

I hope this helps someone.

---

