---
title: "ati x800 and live cd and blank/black screen"
date: 2006-11-28
forum: Installation &amp; Upgrades
---

### Post by racing_snail on 2006-11-28
hello,

I am new to ubuntu/linux, but I am not new to computers (regular user of osx and winxp).

I have been trying to boot up with the ubuntu live cd and I'm having some display issues.

here are some quick specs on my machine:

computer: shuttle xpc SN95V30
proc: amd64 3700+
graphics: ati x800pro
memory: 1 GB ram (2x512mb)
mobo: nvidia nforce3
storage: raid level 1 on two SATA 160GB hard drives (total volume is 160GB because the two drives are mirrored). using latest nvidia raid driver.


I have tried to boot up into ubuntu several times. the first time I tried, I was using the amd64 version of 6.06. when I tried to boot from the CD, I got the menu screen, and I selected the first option to "boot or install" ubuntu. I got the splash screen with the progress bar, and then after that finished, the screen went completely blank. the signal going from the pc to the display was gone and the display said "no signal". so I restarted and when I got to the menu, I tried boot with safe graphics mode. I had the exact same problem, the screen went blank. BUT, the only difference was I heard a musical sound (which was very loud). I assumed this was a startup sound that plays after ubuntu has booted up.

I couldn't fix this issue, and after reading the forums, it looked like there are known problems with my ati x800 card, I decided to wait until 6.10 came out. after 6.10 was released, I saw on the forums that people who were having display problems like mine were switching to the "386" version and having better results. So when 6.10 was released, I downloaded the "386" version of the live cd. but unfortunately, when I try to boot up with the 6.10 386 CD, I get the same problem, with one small difference. after I choose "start or install ubuntu" I see the splash screen, and after I see the progress bar finish, the screen goes black. the video signal is still there, but the screen is black. the difference is the screen has not gone blank, like what happened before with 6.06/amd64.

If anyone knows what I should do, I would really appreciate the help. Thank you in advance!

---

### Post by eyedoc912 on 2006-12-03
I've been having this exact same problem, not only with ubuntu, but with other distros as well.  Evidently there's some problem with x server or xorg or whatever, but I honestly don't understand it, so any help would be much appreciated.  I'm running a sapphire ATI x850xt video card and an AMD X2 4000+ processor.  I was able to get kubuntu to work though...  here's how I did it.

when the live cd first boots up, go to the VGA option and select a resolution that you know will work on your monitor, then when you let it run, instead of freezing up like it always does, it will kick you out to the prompt, which is better than nothing.  Then you type in: 
sudo nano /etc/X11/xorg.conf

This is just a text editor, so just find the line that mentions the video driver "ATI" and change it to "radeon"

Then save it, and when you're back at the prompt type in "startx" and your GUI should show up.

That will hopefully get you going at least.  This hasn't worked for me in ubuntu though, which sucks because I really like gnome.  I haven't had time to mess with it much from there.  I'd love to get the fglrx driver working though, to try out beryl or compiz.  Does anybody have any ideas?

---

### Post by eyedoc912 on 2006-12-03
oh, I forgot to mention that I also had to run kubuntu in safe graphic mode as well

---

